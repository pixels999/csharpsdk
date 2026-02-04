# TemplateFox.SDK.Api.AccountApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetAccount**](AccountApi.md#getaccount) | **GET** /v1/account | Get account info |
| [**ListTransactions**](AccountApi.md#listtransactions) | **GET** /v1/account/transactions | List transactions |

<a id="getaccount"></a>
# **GetAccount**
> AccountInfoResponse GetAccount ()

Get account info

Get account information including remaining credits.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** Check credit balance before performing operations.  **No credits consumed:** This is a read-only endpoint.

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
    public class GetAccountExample
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
            var apiInstance = new AccountApi(httpClient, config, httpClientHandler);

            try
            {
                // Get account info
                AccountInfoResponse result = apiInstance.GetAccount();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountApi.GetAccount: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAccountWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get account info
    ApiResponse<AccountInfoResponse> response = apiInstance.GetAccountWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountApi.GetAccountWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**AccountInfoResponse**](AccountInfoResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account information |  -  |
| **403** | Invalid or missing API key |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtransactions"></a>
# **ListTransactions**
> TransactionsResponse ListTransactions (int? limit = null, int? offset = null)

List transactions

List transaction history for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Pagination:** Use `limit` and `offset` query parameters.  **Transaction types:** - `PDFGEN`: PDF generation (consumes credits) - `REFUND`: Credit refund (on failed generation) - `PURCHASE`: Credit purchase - `BONUS`: Bonus credits  **Credits field:** - Positive value = credits consumed - Negative value = credits added  **No credits consumed:** This is a read-only endpoint.

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
    public class ListTransactionsExample
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
            var apiInstance = new AccountApi(httpClient, config, httpClientHandler);
            var limit = 300;  // int? | Number of records to return (optional)  (default to 300)
            var offset = 0;  // int? | Number of records to skip (optional)  (default to 0)

            try
            {
                // List transactions
                TransactionsResponse result = apiInstance.ListTransactions(limit, offset);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AccountApi.ListTransactions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTransactionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List transactions
    ApiResponse<TransactionsResponse> response = apiInstance.ListTransactionsWithHttpInfo(limit, offset);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AccountApi.ListTransactionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **limit** | **int?** | Number of records to return | [optional] [default to 300] |
| **offset** | **int?** | Number of records to skip | [optional] [default to 0] |

### Return type

[**TransactionsResponse**](TransactionsResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **403** | Invalid or missing API key |  -  |
| **422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

