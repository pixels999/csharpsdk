# TemplateFox C# SDK

Official .NET SDK for [TemplateFox](https://pdftemplateapi.com) - Generate PDFs from HTML templates via API.

[![NuGet version](https://badge.fury.io/nu/TemplateFox.SDK.svg)](https://www.nuget.org/packages/TemplateFox.SDK)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Installation

### Package Manager

```powershell
Install-Package TemplateFox.SDK
```

### .NET CLI

```bash
dotnet add package TemplateFox.SDK
```

### PackageReference

```xml
<PackageReference Include="TemplateFox.SDK" Version="1.0.0" />
```

## Quick Start

```csharp
using TemplateFox.SDK.Api;
using TemplateFox.SDK.Client;
using TemplateFox.SDK.Model;

// Initialize the client
var config = new Configuration
{
    ApiKey = new Dictionary<string, string>
    {
        { "x-api-key", "your-api-key" }
    }
};

var api = new PDFApi(config);

// Generate a PDF
var request = new CreatePdfRequest(
    templateId: "YOUR_TEMPLATE_ID",
    data: new Dictionary<string, object>
    {
        { "name", "John Doe" },
        { "invoice_number", "INV-001" },
        { "total_amount", 150.00 }
    }
);

try
{
    var response = await api.CreatePdfAsync(request);
    Console.WriteLine($"PDF URL: {response.Url}");
    Console.WriteLine($"Credits remaining: {response.CreditsRemaining}");
}
catch (ApiException e)
{
    Console.WriteLine($"Error: {e.Message}");
}
```

## Features

- **Template-based PDF generation** - Create templates with dynamic variables, generate PDFs with your data
- **Multiple export options** - Get a signed URL (default) or raw binary PDF
- **S3 integration** - Upload generated PDFs directly to your own S3-compatible storage
- **.NET Standard 2.0** - Compatible with .NET Core 2.0+, .NET 5+, and .NET Framework 4.6.1+

## API Methods

### PDF Generation

```csharp
var request = new CreatePdfRequest(
    templateId: "TEMPLATE_ID",
    data: new Dictionary<string, object> { { "name", "John Doe" } },
    exportType: ExportType.Url,       // Url or Binary
    expiration: 86400,                // URL expiration in seconds
    filename: "invoice-001"           // Custom filename
);

var response = await api.CreatePdfAsync(request);
```

### Templates

```csharp
var templatesApi = new TemplatesApi(config);

// List all templates
var templates = await templatesApi.ListTemplatesAsync();
foreach (var template in templates.Templates)
{
    Console.WriteLine($"{template.Id}: {template.Name}");
}

// Get template fields
var fields = await templatesApi.GetTemplateFieldsAsync("TEMPLATE_ID");
foreach (var field in fields)
{
    Console.WriteLine($"{field.Key}: {field.Type} (required: {field.Required})");
}
```

### Account

```csharp
var accountApi = new AccountApi(config);

// Get account info
var account = await accountApi.GetAccountAsync();
Console.WriteLine($"Credits: {account.Credits}");
Console.WriteLine($"Email: {account.Email}");

// List transactions
var transactions = await accountApi.ListTransactionsAsync(limit: 100, offset: 0);
foreach (var tx in transactions.Transactions)
{
    Console.WriteLine($"{tx.TransactionType}: {tx.Credits} credits");
}
```

### S3 Integration

```csharp
var integrationsApi = new IntegrationsApi(config);

// Save S3 configuration
var s3Config = new S3ConfigRequest(
    endpointUrl: "https://s3.amazonaws.com",
    accessKeyId: "AKIAIOSFODNN7EXAMPLE",
    secretAccessKey: "your-secret-key",
    bucketName: "my-pdf-bucket",
    defaultPrefix: "generated/pdfs/"
);

await integrationsApi.SaveS3ConfigAsync(s3Config);

// Test connection
var test = await integrationsApi.TestS3ConnectionAsync();
Console.WriteLine($"Connection: {(test.Success ? "OK" : "Failed")}");
```

## Configuration

```csharp
var config = new Configuration
{
    BasePath = "https://api.pdftemplateapi.com",  // Default API URL
    ApiKey = new Dictionary<string, string>
    {
        { "x-api-key", Environment.GetEnvironmentVariable("TEMPLATEFOX_API_KEY") }
    }
};
```

## Error Handling

```csharp
try
{
    var response = await api.CreatePdfAsync(request);
}
catch (ApiException e)
{
    switch (e.ErrorCode)
    {
        case 402:
            Console.WriteLine("Insufficient credits");
            break;
        case 403:
            Console.WriteLine("Access denied - check your API key");
            break;
        case 404:
            Console.WriteLine("Template not found");
            break;
        default:
            Console.WriteLine($"Error: {e.Message}");
            break;
    }
}
```

## Dependency Injection (ASP.NET Core)

```csharp
// Program.cs or Startup.cs
builder.Services.AddSingleton<Configuration>(sp =>
{
    return new Configuration
    {
        ApiKey = new Dictionary<string, string>
        {
            { "x-api-key", builder.Configuration["TemplateFox:ApiKey"] }
        }
    };
});

builder.Services.AddTransient<PDFApi>();

// In your controller or service
public class PdfController : ControllerBase
{
    private readonly PDFApi _api;

    public PdfController(PDFApi api)
    {
        _api = api;
    }

    public async Task<IActionResult> GenerateInvoice(InvoiceDto invoice)
    {
        var request = new CreatePdfRequest(
            templateId: _configuration["TemplateFox:InvoiceTemplateId"],
            data: invoice.ToTemplateData()
        );
        var response = await _api.CreatePdfAsync(request);
        return Ok(new { url = response.Url });
    }
}
```

## Documentation

- [API Documentation](https://pdftemplateapi.com/docs)
- [Swagger UI](https://api.pdftemplateapi.com/docs)
- [Dashboard](https://pdftemplateapi.com/dashboard)

## Support

- Email: support@pdftemplateapi.com
- Issues: [GitHub Issues](https://github.com/TemplateFoxPDF/csharpsdk/issues)

## License

MIT License - see [LICENSE](LICENSE) for details.
