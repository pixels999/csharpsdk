# TemplateFox.SDK.Model.CreatePdfRequest
Request model for PDF generation

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**TemplateId** | **string** | **Required.** Template short ID (12 characters) | 
**Data** | **Dictionary&lt;string, Object&gt;** | **Required.** Key-value data to render in the template. Keys must match template variables. | 
**ExportType** | **ExportType** | Export format: &#x60;url&#x60; uploads to CDN and returns URL, &#x60;binary&#x60; returns raw PDF bytes | [optional] 
**Expiration** | **int** | URL expiration in seconds. Min: 60 (1 min), Max: 604800 (7 days). Only applies to &#x60;url&#x60; export type. | [optional] [default to 86400]
**Filename** | **string** |  | [optional] 
**StoreS3** | **bool** | Upload to your configured S3 bucket instead of CDN | [optional] [default to false]
**S3Filepath** | **string** |  | [optional] 
**S3Bucket** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

