# TemplateFox.SDK.Model.Transaction
Transaction record

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**TransactionRef** | **string** | Unique transaction reference (UUID) | 
**TransactionType** | **string** | Transaction type: PDFGEN, PURCHASE, REFUND, BONUS | 
**TemplateId** | **string** |  | [optional] 
**ExecTm** | **int?** |  | [optional] 
**Credits** | **int** | Credits consumed (positive) or added (negative) | 
**CreatedAt** | **string** | ISO 8601 timestamp | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

