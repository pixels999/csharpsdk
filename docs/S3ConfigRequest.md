# TemplateFox.SDK.Model.S3ConfigRequest
Request model for S3 configuration

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**EndpointUrl** | **string** | S3-compatible endpoint URL. Must start with https:// | 
**AccessKeyId** | **string** | Access key ID for S3 authentication | 
**SecretAccessKey** | **string** |  | [optional] 
**BucketName** | **string** | S3 bucket name. Must follow S3 naming conventions (lowercase, no underscores) | 
**DefaultPrefix** | **string** | Default path prefix for uploaded files. Can include slashes for folder structure | [optional] [default to ""]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

