# TemplateFox.SDK.Api.IntegrationsApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**DeleteS3Config**](IntegrationsApi.md#deletes3config) | **DELETE** /v1/integrations/s3 | Delete S3 configuration |
| [**GetS3Config**](IntegrationsApi.md#gets3config) | **GET** /v1/integrations/s3 | Get S3 configuration |
| [**SaveS3Config**](IntegrationsApi.md#saves3config) | **POST** /v1/integrations/s3 | Save S3 configuration |
| [**TestS3Connection**](IntegrationsApi.md#tests3connection) | **POST** /v1/integrations/s3/test | Test S3 connection |

<a id="deletes3config"></a>
# **DeleteS3Config**
> S3SuccessResponse DeleteS3Config ()

Delete S3 configuration

Delete S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Remove your S3 integration. Generated PDFs will use the default CDN storage after deletion.  **Warning:** This action is irreversible. You'll need to reconfigure S3 to use it again.  **No credits consumed:** This is a configuration endpoint.

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
    public class DeleteS3ConfigExample
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
            var apiInstance = new IntegrationsApi(httpClient, config, httpClientHandler);

            try
            {
                // Delete S3 configuration
                S3SuccessResponse result = apiInstance.DeleteS3Config();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling IntegrationsApi.DeleteS3Config: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteS3ConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete S3 configuration
    ApiResponse<S3SuccessResponse> response = apiInstance.DeleteS3ConfigWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling IntegrationsApi.DeleteS3ConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Configuration deleted successfully |  -  |
| **403** | Admin privileges required |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gets3config"></a>
# **GetS3Config**
> S3ConfigResponse GetS3Config ()

Get S3 configuration

Get current S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Retrieve your S3 integration settings. Secret access key is masked for security.  **Returns 404** if S3 is not configured.  **No credits consumed:** This is a read-only endpoint.

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
    public class GetS3ConfigExample
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
            var apiInstance = new IntegrationsApi(httpClient, config, httpClientHandler);

            try
            {
                // Get S3 configuration
                S3ConfigResponse result = apiInstance.GetS3Config();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling IntegrationsApi.GetS3Config: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetS3ConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get S3 configuration
    ApiResponse<S3ConfigResponse> response = apiInstance.GetS3ConfigWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling IntegrationsApi.GetS3ConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**S3ConfigResponse**](S3ConfigResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | S3 configuration retrieved successfully |  -  |
| **403** | Admin privileges required |  -  |
| **404** | S3 is not configured |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="saves3config"></a>
# **SaveS3Config**
> S3SuccessResponse SaveS3Config (S3ConfigRequest s3ConfigRequest)

Save S3 configuration

Save or update S3-compatible storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Configure your S3-compatible storage to receive generated PDFs directly in your own bucket instead of the default CDN.  **Supported providers:** - Amazon S3 - DigitalOcean Spaces - Cloudflare R2 - MinIO - Any S3-compatible storage  **Secret key behavior:** - For new configuration: `secret_access_key` is required - For updates: Omit `secret_access_key` to keep existing value  **No credits consumed:** This is a configuration endpoint.

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
    public class SaveS3ConfigExample
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
            var apiInstance = new IntegrationsApi(httpClient, config, httpClientHandler);
            var s3ConfigRequest = new S3ConfigRequest(); // S3ConfigRequest | 

            try
            {
                // Save S3 configuration
                S3SuccessResponse result = apiInstance.SaveS3Config(s3ConfigRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling IntegrationsApi.SaveS3Config: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SaveS3ConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Save S3 configuration
    ApiResponse<S3SuccessResponse> response = apiInstance.SaveS3ConfigWithHttpInfo(s3ConfigRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling IntegrationsApi.SaveS3ConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **s3ConfigRequest** | [**S3ConfigRequest**](S3ConfigRequest.md) |  |  |

### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Configuration saved successfully |  -  |
| **400** | Invalid configuration (e.g., missing secret key for new config) |  -  |
| **403** | Admin privileges required |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="tests3connection"></a>
# **TestS3Connection**
> S3TestResponse TestS3Connection ()

Test S3 connection

Test S3 connection with stored credentials.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Verify your S3 configuration is working correctly. The test will: 1. Connect to the endpoint 2. Verify bucket access 3. Check write permissions by uploading a small test file  **Prerequisite:** S3 must be configured first using `POST /v1/integrations/s3`  **No credits consumed:** This is a diagnostic endpoint.

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
    public class TestS3ConnectionExample
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
            var apiInstance = new IntegrationsApi(httpClient, config, httpClientHandler);

            try
            {
                // Test S3 connection
                S3TestResponse result = apiInstance.TestS3Connection();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling IntegrationsApi.TestS3Connection: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the TestS3ConnectionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Test S3 connection
    ApiResponse<S3TestResponse> response = apiInstance.TestS3ConnectionWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling IntegrationsApi.TestS3ConnectionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**S3TestResponse**](S3TestResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Connection test successful |  -  |
| **400** | Connection test failed |  -  |
| **403** | Admin privileges required |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

