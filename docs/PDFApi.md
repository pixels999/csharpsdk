# TemplateFox.SDK.Api.PDFApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreatePdf**](PDFApi.md#createpdf) | **POST** /v1/pdf/create | Generate PDF from template |

<a id="createpdf"></a>
# **CreatePdf**
> CreatePdfResponse CreatePdf (CreatePdfRequest createPdfRequest)

Generate PDF from template

Generate a PDF from a saved template with dynamic data.  **Authentication:** API Key required (`x-api-key` header)  ## Request Body  | Field | Type | Required | Description | |- -- -- --|- -- -- -|- -- -- -- -- -|- -- -- -- -- -- --| | `template_id` | string | ✅ Yes | Template short ID (12 characters) | | `data` | object | ✅ Yes | Key-value data to render in template | | `export_type` | string | No | `url` (default) or `binary` | | `expiration` | integer | No | URL expiration in seconds (60-604800, default: 86400) |  ## Export Types - `url` (default): PDF is uploaded to CDN, returns JSON with URL - `binary`: Returns raw PDF bytes directly  **Credits:** 1 credit deducted per successful generation.

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
    public class CreatePdfExample
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
            var apiInstance = new PDFApi(httpClient, config, httpClientHandler);
            var createPdfRequest = new CreatePdfRequest(); // CreatePdfRequest | 

            try
            {
                // Generate PDF from template
                CreatePdfResponse result = apiInstance.CreatePdf(createPdfRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling PDFApi.CreatePdf: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreatePdfWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate PDF from template
    ApiResponse<CreatePdfResponse> response = apiInstance.CreatePdfWithHttpInfo(createPdfRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling PDFApi.CreatePdfWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createPdfRequest** | [**CreatePdfRequest**](CreatePdfRequest.md) |  |  |

### Return type

[**CreatePdfResponse**](CreatePdfResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/pdf


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | PDF generated successfully |  -  |
| **402** | Insufficient credits |  -  |
| **403** | Access denied - not your template |  -  |
| **404** | Template not found |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

