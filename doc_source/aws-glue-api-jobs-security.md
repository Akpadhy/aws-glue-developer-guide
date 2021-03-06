# Security APIs in AWS Glue<a name="aws-glue-api-jobs-security"></a>

## Data Types<a name="aws-glue-api-jobs-security-objects"></a>
+ [DataCatalogEncryptionSettings Structure](#aws-glue-api-jobs-security-DataCatalogEncryptionSettings)
+ [EncryptionAtRest Structure](#aws-glue-api-jobs-security-EncryptionAtRest)
+ [EncryptionConfiguration Structure](#aws-glue-api-jobs-security-EncryptionConfiguration)
+ [S3Encryption Structure](#aws-glue-api-jobs-security-S3Encryption)
+ [CloudWatchEncryption Structure](#aws-glue-api-jobs-security-CloudWatchEncryption)
+ [JobBookmarksEncryption Structure](#aws-glue-api-jobs-security-JobBookmarksEncryption)
+ [SecurityConfiguration Structure](#aws-glue-api-jobs-security-SecurityConfiguration)

## DataCatalogEncryptionSettings Structure<a name="aws-glue-api-jobs-security-DataCatalogEncryptionSettings"></a>

Contains configuration information for maintaining Data Catalog security\.

**Fields**
+ `EncryptionAtRest` – An [EncryptionAtRest](#aws-glue-api-jobs-security-EncryptionAtRest) object\.

  Specifies encryption\-at\-rest configuration for the Data Catalog\.

## EncryptionAtRest Structure<a name="aws-glue-api-jobs-security-EncryptionAtRest"></a>

Specifies encryption\-at\-rest configuration for the Data Catalog\.

**Fields**
+ `CatalogEncryptionMode` – *Required:* UTF\-8 string \(valid values: `DISABLED` \| `SSE-KMS="SSEKMS"`\)\.

  The encryption\-at\-rest mode for encrypting Data Catalog data\.
+ `SseAwsKmsKeyId` – UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The ID of the AWS KMS key to use for encryption at rest\.

## EncryptionConfiguration Structure<a name="aws-glue-api-jobs-security-EncryptionConfiguration"></a>

Specifies an encryption configuration\.

**Fields**
+ `S3Encryption` – An array of [S3Encryption](#aws-glue-api-jobs-security-S3Encryption) objects\.

  The encryption configuration for S3 data\.
+ `CloudWatchEncryption` – A [CloudWatchEncryption](#aws-glue-api-jobs-security-CloudWatchEncryption) object\.

  The encryption configuration for CloudWatch\.
+ `JobBookmarksEncryption` – A [JobBookmarksEncryption](#aws-glue-api-jobs-security-JobBookmarksEncryption) object\.

  The encryption configuration for Job Bookmarks\.

## S3Encryption Structure<a name="aws-glue-api-jobs-security-S3Encryption"></a>

Specifies how S3 data should be encrypted\.

**Fields**
+ `S3EncryptionMode` – UTF\-8 string \(valid values: `DISABLED` \| `SSE-KMS="SSEKMS"` \| `SSE-S3="SSES3"`\)\.

  The encryption mode to use for S3 data\.
+ `KmsKeyArn` – UTF\-8 string, matching the [Custom string pattern #10](aws-glue-api-common.md#regex_10)\.

  The AWS ARN of the KMS key to be used to encrypt the data\.

## CloudWatchEncryption Structure<a name="aws-glue-api-jobs-security-CloudWatchEncryption"></a>

Specifies how CloudWatch data should be encrypted\.

**Fields**
+ `CloudWatchEncryptionMode` – UTF\-8 string \(valid values: `DISABLED` \| `SSE-KMS="SSEKMS"`\)\.

  The encryption mode to use for CloudWatch data\.
+ `KmsKeyArn` – UTF\-8 string, matching the [Custom string pattern #10](aws-glue-api-common.md#regex_10)\.

  The AWS ARN of the KMS key to be used to encrypt the data\.

## JobBookmarksEncryption Structure<a name="aws-glue-api-jobs-security-JobBookmarksEncryption"></a>

Specifies how Job bookmark data should be encrypted\.

**Fields**
+ `JobBookmarksEncryptionMode` – UTF\-8 string \(valid values: `DISABLED` \| `CSE-KMS="CSEKMS"`\)\.

  The encryption mode to use for Job bookmarks data\.
+ `KmsKeyArn` – UTF\-8 string, matching the [Custom string pattern #10](aws-glue-api-common.md#regex_10)\.

  The AWS ARN of the KMS key to be used to encrypt the data\.

## SecurityConfiguration Structure<a name="aws-glue-api-jobs-security-SecurityConfiguration"></a>

Specifies a security configuration\.

**Fields**
+ `Name` – UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The name of the security configuration\.
+ `CreatedTimeStamp` – Timestamp\.

  The time at which this security configuration was created\.
+ `EncryptionConfiguration` – An [EncryptionConfiguration](#aws-glue-api-jobs-security-EncryptionConfiguration) object\.

  The encryption configuration associated with this security configuration\.

## Operations<a name="aws-glue-api-jobs-security-actions"></a>
+ [GetDataCatalogEncryptionSettings Action \(Python: get\_data\_catalog\_encryption\_settings\)](#aws-glue-api-jobs-security-GetDataCatalogEncryptionSettings)
+ [PutDataCatalogEncryptionSettings Action \(Python: put\_data\_catalog\_encryption\_settings\)](#aws-glue-api-jobs-security-PutDataCatalogEncryptionSettings)
+ [CreateSecurityConfiguration Action \(Python: create\_security\_configuration\)](#aws-glue-api-jobs-security-CreateSecurityConfiguration)
+ [DeleteSecurityConfiguration Action \(Python: delete\_security\_configuration\)](#aws-glue-api-jobs-security-DeleteSecurityConfiguration)
+ [GetSecurityConfiguration Action \(Python: get\_security\_configuration\)](#aws-glue-api-jobs-security-GetSecurityConfiguration)
+ [GetSecurityConfigurations Action \(Python: get\_security\_configurations\)](#aws-glue-api-jobs-security-GetSecurityConfigurations)

## GetDataCatalogEncryptionSettings Action \(Python: get\_data\_catalog\_encryption\_settings\)<a name="aws-glue-api-jobs-security-GetDataCatalogEncryptionSettings"></a>

Retrieves the security configuration for a specified catalog\.

**Request**
+ `CatalogId` – Catalog id string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The ID of the Data Catalog for which to retrieve the security configuration\. If none is supplied, the AWS account ID is used by default\.

**Response**
+ `DataCatalogEncryptionSettings` – A [DataCatalogEncryptionSettings](#aws-glue-api-jobs-security-DataCatalogEncryptionSettings) object\.

  The requested security configuration\.

**Errors**
+ `InternalServiceException`
+ `InvalidInputException`
+ `OperationTimeoutException`

## PutDataCatalogEncryptionSettings Action \(Python: put\_data\_catalog\_encryption\_settings\)<a name="aws-glue-api-jobs-security-PutDataCatalogEncryptionSettings"></a>

Sets the security configuration for a specified catalog\. Once the configuration has been set, the specified encryption is applied to every catalog write thereafter\.

**Request**
+ `CatalogId` – Catalog id string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The ID of the Data Catalog for which to set the security configuration\. If none is supplied, the AWS account ID is used by default\.
+ `DataCatalogEncryptionSettings` – *Required:* A [DataCatalogEncryptionSettings](#aws-glue-api-jobs-security-DataCatalogEncryptionSettings) object\.

  The security configuration to set\.

**Response**
+ *No Response parameters\.*

**Errors**
+ `InternalServiceException`
+ `InvalidInputException`
+ `OperationTimeoutException`

## CreateSecurityConfiguration Action \(Python: create\_security\_configuration\)<a name="aws-glue-api-jobs-security-CreateSecurityConfiguration"></a>

Creates a new security configuration\.

**Request**
+ `Name` – *Required:* UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The name for the new security configuration\.
+ `EncryptionConfiguration` – *Required:* An [EncryptionConfiguration](#aws-glue-api-jobs-security-EncryptionConfiguration) object\.

  The encryption configuration for the new security configuration\.

**Response**
+ `Name` – UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The name assigned to the new security configuration\.
+ `CreatedTimestamp` – Timestamp\.

  The time at which the new security configuration was created\.

**Errors**
+ `AlreadyExistsException`
+ `InvalidInputException`
+ `InternalServiceException`
+ `OperationTimeoutException`
+ `ResourceNumberLimitExceededException`

## DeleteSecurityConfiguration Action \(Python: delete\_security\_configuration\)<a name="aws-glue-api-jobs-security-DeleteSecurityConfiguration"></a>

Deletes a specified security configuration\.

**Request**
+ `Name` – *Required:* UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The name of the security configuration to delete\.

**Response**
+ *No Response parameters\.*

**Errors**
+ `EntityNotFoundException`
+ `InvalidInputException`
+ `InternalServiceException`
+ `OperationTimeoutException`

## GetSecurityConfiguration Action \(Python: get\_security\_configuration\)<a name="aws-glue-api-jobs-security-GetSecurityConfiguration"></a>

Retrieves a specified security configuration\.

**Request**
+ `Name` – *Required:* UTF\-8 string, not less than 1 or more than 255 bytes long, matching the [Single-line string pattern](aws-glue-api-common.md#aws-glue-api-regex-oneLine)\.

  The name of the security configuration to retrieve\.

**Response**
+ `SecurityConfiguration` – A [SecurityConfiguration](#aws-glue-api-jobs-security-SecurityConfiguration) object\.

  The requested security configuration

**Errors**
+ `EntityNotFoundException`
+ `InvalidInputException`
+ `InternalServiceException`
+ `OperationTimeoutException`

## GetSecurityConfigurations Action \(Python: get\_security\_configurations\)<a name="aws-glue-api-jobs-security-GetSecurityConfigurations"></a>

Retrieves a list of all security configurations\.

**Request**
+ `MaxResults` – Number \(integer\), not less than 1 or more than 1000\.

  The maximum number of results to return\.
+ `NextToken` – UTF\-8 string\.

  A continuation token, if this is a continuation call\.

**Response**
+ `SecurityConfigurations` – An array of [SecurityConfiguration](#aws-glue-api-jobs-security-SecurityConfiguration) objects\.

  A list of security configurations\.
+ `NextToken` – UTF\-8 string\.

  A continuation token, if there are more security configurations to return\.

**Errors**
+ `EntityNotFoundException`
+ `InvalidInputException`
+ `InternalServiceException`
+ `OperationTimeoutException`