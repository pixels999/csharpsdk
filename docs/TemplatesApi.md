# TemplateFox.SDK.Api.TemplatesApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetTemplateFields**](TemplatesApi.md#gettemplatefields) | **GET** /v1/templates/{template_id}/fields | Get template fields |
| [**ListTemplates**](TemplatesApi.md#listtemplates) | **GET** /v1/templates | List templates |

<a id="gettemplatefields"></a>
# **GetTemplateFields**
> List&lt;TemplateField&gt; GetTemplateFields (string templateId)

Get template fields

Get the dynamic fields for a template.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for Zapier Dynamic Fields integration. It returns an array of field definitions that Zapier uses to dynamically generate input forms.  **Response format:** Array of objects compatible with Zapier InputFieldsSchema. Each field has: `key`, `label`, `type`, `required`, and optional `helpText`.  **Field types:** - `string`: Text input (also used for JSON arrays/objects) - `integer`: Integer number - `number`: Decimal number - `boolean`: True/False checkbox  **Arrays and objects:** Complex types are returned as `string` type with a `helpText` showing the expected JSON format.  **No credits consumed:** This is a read-only endpoint.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using TemplateFox.SDK.Api;
using TemplateFox.SDK.Client;
using TemplateFox.SDK.Model;

namespace Example
{
    public class GetTemplateFieldsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.pdftemplateapi.com";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("x-api-key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("x-api-key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new TemplatesApi(httpClient, config, httpClientHandler);
            var templateId = "templateId_example";  // string | 

            try
            {
                // Get template fields
                List<TemplateField> result = apiInstance.GetTemplateFields(templateId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TemplatesApi.GetTemplateFields: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTemplateFieldsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get template fields
    ApiResponse<List<TemplateField>> response = apiInstance.GetTemplateFieldsWithHttpInfo(templateId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TemplatesApi.GetTemplateFieldsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **templateId** | **string** |  |  |

### Return type

[**List&lt;TemplateField&gt;**](TemplateField.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of template fields |  -  |
| **403** | Invalid or missing API key |  -  |
| **404** | Template not found |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtemplates"></a>
# **ListTemplates**
> TemplatesListResponse ListTemplates ()

List templates

List all templates for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for no-code tools (Zapier, Make, n8n) to populate template selection dropdowns.  **No credits consumed:** This is a read-only endpoint.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using TemplateFox.SDK.Api;
using TemplateFox.SDK.Client;
using TemplateFox.SDK.Model;

namespace Example
{
    public class ListTemplatesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://api.pdftemplateapi.com";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("x-api-key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("x-api-key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new TemplatesApi(httpClient, config, httpClientHandler);

            try
            {
                // List templates
                TemplatesListResponse result = apiInstance.ListTemplates();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TemplatesApi.ListTemplates: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTemplatesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List templates
    ApiResponse<TemplatesListResponse> response = apiInstance.ListTemplatesWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TemplatesApi.ListTemplatesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**TemplatesListResponse**](TemplatesListResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of templates |  -  |
| **403** | Invalid or missing API key |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

