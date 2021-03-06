# DescribeDisks

You can call this operation to query one or more Elastic Block Storage \(EBS\) devices that you created, including cloud disks and local disks.

## Description

-   You can specify multiple request parameters such as `RegionId`, `ZoneId`, `DiskIds`, and `InstanceId` to be queried. Specified parameters have logical AND relations. Only the specified parameters are used as filter conditions.
-   The `DiskIds` value is a JSON array. If DiskIds is not specified, it is not used as a filter condition. If `DiskIds` is set to an empty JSON array, it is regarded as a valid filter condition and an empty response is returned.
-   You can use one of the following methods to view returned data:
    -   Method 1: Use `NextToken` to configure the query token. Set the value of this parameter to the `NextToken` value that is returned in the last call to the DescribeDisks operation. Then use `MaxResults` to specify the maximum number of entries to return on each page.
    -   Method 2: Use `PageSize` to specify the number of entries to return on each page and then use `PageNumber` to specify the number of the page to return.

        You can use only one of the preceding methods. If a large number of entries are returned, we recommend that you use Method 1. If `NextToken` is specified, `PageSize` and `PageNumber` do not take effect and `TotalCount` in the response is invalid.


When you call an API operation by using Alibaba Cloud CLI, you must specify request parameter values of different data types in the required formats. For more information, see [CLI parameter format](~~110340~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeDisks&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDisks|The operation that you want to perform. Set the value to DescribeDisks. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the disk. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|ZoneId|String|No|cn-hangzhou-g|The zone ID of the node. |
|DiskIds|String|No|\["d-bp67acfmxazb4p\*\*\*\*", "d-bp67acfmxazb4g\*\*\*\*", … "d-bp67acfmxazb4d\*\*\*\*"\]|The IDs of the disks. The value is a JSON array that consists of up to 100 disk IDs. Separate multiple disk IDs with commas \(,\). |
|InstanceId|String|No|i-bp67acfmxazb4q\*\*\*\*|The ID of the instance to which the disk is attached. |
|DiskType|String|No|all|The type of the disk. Valid values:

 -   all: system disk and data disk
-   system: system disk
-   data: data disk

 Default value: all |
|Category|String|No|all|The category of the disk. Valid values:

 -   all: all disk categories
-   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   cloud\_essd: enhanced SSD \(ESSD\)
-   local\_ssd\_pro: I/O intensive local disk
-   local\_hdd\_pro: throughput intensive local disk
-   ephemeral: retired local disk
-   ephemeral\_ssd: retired local SSD

 Default value: all |
|Status|String|No|All|The status of the disk. For more information, see [Cloud disk status table](~~25689~~). Valid values:

 -   In\_use
-   Available
-   Attaching
-   Detaching
-   Creating
-   ReIniting
-   All

 Default value: All |
|SnapshotId|String|No|s-bp67acfmxazb4p\*\*\*\*|The ID of the snapshot used to create the disk. |
|Portable|Boolean|No|false|Specifies whether the disk is removable. Valid values:

 -   true: The disk is removable. A removable disk can exist independently and can be attached to or detached from an instance within the same zone.
-   false: The disk is not removable. A disk that is not removable cannot exist independently or be attached to or detached from an instance within the same zone.

 If the disk is not one of the following categories or types, `Portable` is set to `false` and the lifecycle of the disk is the same as that of the instance to which the disk is attached:

 -   Local disk
-   Local SSD
-   System disk
-   Subscription data disk |
|DeleteWithInstance|Boolean|No|false|Specifies whether the disk is released when its attached instance is released. Valid values:

 -   true: The disk is released when its attached instance is released.
-   false: The disk is not released but is retained as a pay-as-you-go data disk when its attached instance is released.

 Default value: false |
|DeleteAutoSnapshot|Boolean|No|false|Specifies whether the automatic snapshots of the disk are deleted when the disk is released.

 Default value: false |
|PageNumber|Integer|No|1|The number of the page to return.

 Pages start from page 1.

 Default: 1 |
|PageSize|Integer|No|10|The number of entries to return on each page.

 Valid values: 1 to 100

 Default value: 10 |
|NextToken|String|No|AAAAAdDWBF2\*\*\*\*|The query token. Set the value to the `NextToken` value that is returned in the last call to the DescribeDisks operation.

 For more information about how to check responses returned by this operation, see the preceding "Description" section. |
|MaxResults|Integer|No|50|The maximum number of entries to return on each page. Valid values: 1 to 500.

 Default value: 10 |
|DiskName|String|No|testDiskName|The name of the disk. |
|AutoSnapshotPolicyId|String|No|sp-m5e2w2jutw8bv31\*\*\*\*|The ID of the automatic snapshot policy that is applied to the disk. |
|EnableAutoSnapshot|Boolean|No|false|Specifies whether to query the disks that have created and applied an automatic snapshot policy.

 -   true: applied
-   false: not applied |
|EnableAutomatedSnapshotPolicy|Boolean|No|false|Specifies whether to query the disks to which automatic snapshot policies are applied.

 Default value: false |
|DiskChargeType|String|No|PostPaid|The billing method of the disk. Valid values:

 -   PrePaid: subscription
-   PostPaid: pay-as-you-go |
|LockReason|String|No|recycling|The reason why the disk is locked. Valid values:

 -   financial: The instance is locked due to overdue payments.
-   security: The instance is locked for security reasons.
-   recycling: The preemptible instance is locked and pending for release.
-   dedicatedhostfinancial: The instance is locked due to overdue payments for the dedicated host. |
|Filter.1.Key|String|No|CreationStartTime|The key of filter 1 used to query resources. Set the value to CreationStartTime. |
|Filter.2.Key|String|No|CreationEndTime|The key of filter 2 used to query resources. Set the value to CreationEndTime. |
|Filter.1.Value|String|No|2017-12-05T22:40:00Z|The value of filter 1 used to query resources. The value must be the beginning of the time range in which to query created resources. |
|Filter.2.Value|String|No|2017-12-06T22:40:00Z|The value of filter 2 used to query resources. The value must be the end of the time range in which to query created resources. |
|Tag.N.value|String|No|null|The value of tag N of the disk.

 **Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Value parameter to ensure compatibility. |
|Tag.N.key|String|No|null|The key of tag N of the disk.

 **Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Key parameter to ensure compatibility. |
|Tag.N.Key|String|No|TestKey|The key of tag N of the disk. Valid values of N: 1 to 20. |
|Tag.N.Value|String|No|TestValue|The value of tag N of the disk. Valid values of N: 1 to 20. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the disk belongs. |
|EnableShared|Boolean|No|false|Specifies whether the disk is a Shared Block Storage device. |
|Encrypted|Boolean|No|false|Specifies whether to query only encrypted disks.

 Default value: false |
|AdditionalAttributes.N|RepeatList|No|IOPS|Other attribute values. This parameter can be set to IOPS only, which indicates that the maximum IOPS of the queried disk. |
|DryRun|Boolean|No|false|Specifies whether to check the validity of the request without actually making the request. Valid values:

 -   true: The validity of the request is checked but the request is not made. Check items include whether your AccessKey pair is valid, whether RAM users are authorized, and whether the required parameters are specified. If the check fails, the corresponding error message is returned. If the check succeeds, the `DryRunOperation` error code is returned.
-   false: The validity of the request is checked. If the check succeeds, a 2XX HTTP status code is returned and the request is made.

 Default value: false |
|KMSKeyId|String|No|0e478b7a-4262-4802-b8cb-00d3fb40\*\*\*\*|The ID of the KMS key used by the disk. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Disks|Array of Disk| |The collection of details about disks. |
|Disk| | | |
|AttachedTime|String|2018-01-01T01:04:22Z|The time when the disk was attached. The time follows the ISO 8601 standard in the yyyy-MM-ddThh:mmZ format. The time is displayed in UTC.

 This parameter is valid only when the value of `Status` is `Available`. |
|AutoSnapshotPolicyId|String|sp-bp67acfmxazb4p\*\*\*\*|The ID of the automatic snapshot policy applied to the disk. |
|BdfId|String|null|This parameter is in invitational preview and not available. |
|Category|String|cloud\_ssd|The category of the disk. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   cloud\_essd: enhanced SSD
-   local\_ssd\_pro: I/O intensive local disk
-   local\_hdd\_pro: throughput intensive local disk
-   ephemeral: retired local disk
-   ephemeral\_ssd: retired local SSD |
|CreationTime|String|2018-01-01T01:01:22Z|The time when the disk was created. |
|DeleteAutoSnapshot|Boolean|false|Indicates whether the automatic snapshots of the disk are deleted when the disk is released. Valid values:

 -   true: The automatic snapshots of the disk are deleted when the disk is released.
-   false: The automatic snapshots of the disk are retained when the disk is released.

 Snapshots created by calling the [CreateSnapshot](~~25524~~) operation or by using the console are retained permanently and not affected by this parameter setting. |
|DeleteWithInstance|Boolean|true|Indicates whether the disk is released when its attached instance is released. Valid values:

 -   true: The disk is released when its attached instance is released.
-   false: The disk is retained when its attached instance is released. |
|Description|String|testDescription|The description of the disk. |
|DetachedTime|String|2018-01-08T01:01:22Z|The time when the disk was detached.

 This parameter is valid only when the value of `Status` is `Available`. |
|Device|String|/dev/xvdb|The device name of the disk on its attached instance, such as /dev/xvdb.

 This parameter has a value when the value of `Status` is`In_use`. Otherwise, the parameter is empty.

 **Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure compatibility. |
|DiskChargeType|String|PostPaid|The billing method of the disk. Valid values:

 -   PrePaid: subscription
-   PostPaid: pay-as-you-go |
|DiskId|String|d-bp18um4r4f2fve24\*\*\*\*|The ID of the disk. |
|DiskName|String|testDiskName|The name of the disk. |
|EnableAutoSnapshot|Boolean|false|Indicates whether an automatic snapshot policy was applied to the disk. |
|EnableAutomatedSnapshotPolicy|Boolean|false|Indicates whether an automatic snapshot policy was applied to the disk. |
|Encrypted|Boolean|false|Indicates whether the disk was encrypted. |
|ExpiredTime|String|2018-01-10T01:01:22Z|The time when the subscription disk expires. |
|IOPS|Integer|4000|The number of input/output operations per second \(IOPS\). |
|IOPSRead|Integer|2000|The number of I/O reads per second. |
|IOPSWrite|Integer|2000|The number of I/O writes per second. |
|ImageId|String|m-bp13aqm171qynt3u\*\*\*|The ID of the image used to create the instance. This parameter is empty unless the disk was created from an image. The value of this parameter remains unchanged throughout the lifecycle of the disk. |
|InstanceId|String|i-bp1j4i2jdf3owlheb\*\*\*|The ID of the instance to which the disk is attached.

 This parameter has a value only when the value of `Status` is `In_use`. Otherwise, the parameter is empty. |
|KMSKeyId|String|0e478b7a-4262-4802-b8cb-00d3fb408\*\*\*|The ID of the KMS key used by the disk. |
|MountInstanceNum|Integer|1|The number of instances to which the Shared Block Storage device is attached. |
|MountInstances|Array of MountInstance| |The attaching information of the disk. |
|MountInstance| | | |
|AttachedTime|String|2017-12-05T2340:00Z|The time when the disk was attached. The time follows the [ISO8601](~~25696~~) standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|Device|String|/dev/xvda|The mount point of the disk. |
|InstanceId|String|i-bp1j4i2jdf3owlhe\*\*\*\*|The ID of the instance to which the disk is attached. |
|OperationLocks|Array of OperationLock| |The reasons why the disk was locked. |
|OperationLock| | | |
|LockReason|String|security|The security reason why the disk was locked. |
|PerformanceLevel|String|PL2|The performance level of the ESSD. Valid values:

 -   PL1: A single ESSD can deliver up to 50,000 random read/write IOPS.
-   PL2: A single ESSD can deliver up to 100,000 random read/write IOPS.
-   PL3: A single ESSD can deliver up to 1,000,000 random read/write IOPS. |
|Portable|Boolean|false|Indicates whether the disk is removable. |
|ProductCode|String|jxsc000204|The product code in Alibaba Cloud Marketplace. |
|RegionId|String|cn-hangzhou|The region ID of the disk. |
|ResourceGroupId|String|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the disk belongs. |
|SerialNumber|String|bp18um4r4f2fve2\*\*\*\*|The serial number of the disk. |
|Size|Integer|2000|The size of the disk. Unit: GiB. |
|SourceSnapshotId|String|s-bp67acfmxazb4p\*\*\*\*|The ID of the snapshot used to create the disk.

 This parameter is empty unless the disk was created from a snapshot. The value of this parameter remains unchanged throughout the lifecycle of the disk. |
|Status|String|Available|The status of the disk. Valid values:

 -   In\_use
-   Available
-   Attaching
-   Detaching
-   Creating
-   ReIniting |
|StorageSetId|String|ss-i-bp1j4i2jdf3owlhe\*\*\*\*|The ID of the storage set. |
|StorageSetPartitionNumber|Integer|11|The maximum number of partitions in a storage set. |
|Tags|Array of Tag| |The tags bound to the disk. |
|Tag| | | |
|TagKey|String|TestKey|The tag key of the disk. |
|TagValue|String|TestValue|The tag value of the disk. |
|Type|String|data|The type of the disk. Valid values:

 -   system: system disk
-   data: data disk |
|ZoneId|String|cn-hangzhou-g|The zone ID of the disk. |
|NextToken|String|AAAAAdDWBF2\*\*\*\*|The query token that is returned in this call. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|1|The number of entries returned per page. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|76|The total number of entries returned. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeDisks
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDisksResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>76</TotalCount>
      <PageSize>1</PageSize>
      <RequestId>C74847CB-9B69-4360-9969-3595F2B6B9C1</RequestId>
      <Disks>
            <Disk>
                  <DiskChargeType>PostPaid</DiskChargeType>
                  <ImageId>centos_7_06_64_20G_alibase_20190711.vhd</ImageId>
                  <Device>/dev/xvda</Device>
                  <DetachedTime></DetachedTime>
                  <Type>system</Type>
                  <InstanceId>i-bp1j4i2jdf3owlhe****</InstanceId>
                  <Encrypted>false</Encrypted>
                  <ZoneId>cn-hangzhou-f</ZoneId>
                  <EnableAutoSnapshot>true</EnableAutoSnapshot>
                  <AttachedTime>2019-11-11T08:35:32Z</AttachedTime>
                  <PerformanceLevel>PL2</PerformanceLevel>
                  <SerialNumber>bp18um4r4f2fve2****</SerialNumber>
                  <SourceSnapshotId>s-bp67acfmxazb4p****</SourceSnapshotId>
                  <DeleteAutoSnapshot>false</DeleteAutoSnapshot>
                  <KMSKeyId></KMSKeyId>
                  <Size>40</Size>
                  <Description></Description>
                  <BdfId></BdfId>
                  <ProductCode></ProductCode>
                  <Portable>false</Portable>
                  <EnableAutomatedSnapshotPolicy>false</EnableAutomatedSnapshotPolicy>
                  <ResourceGroupId></ResourceGroupId>
                  <DiskName></DiskName>
                  <StorageSetId></StorageSetId>
                  <AutoSnapshotPolicyId></AutoSnapshotPolicyId>
                  <CreationTime>2019-11-11T08:35:29Z</CreationTime>
                  <MountInstances>
            </MountInstances>
                  <Status>In_use</Status>
                  <Tags>
                        <Tag>
                              <TagValue>TestValue</TagValue>
                              <TagKey>TestKey</TagKey>
                        </Tag>
                  </Tags>
                  <Category>cloud_efficiency</Category>
                  <RegionId>cn-hangzhou</RegionId>
                  <DeleteWithInstance>true</DeleteWithInstance>
                  <OperationLocks>
            </OperationLocks>
                  <ExpiredTime>2999-09-08T16:00Z</ExpiredTime>
                  <DiskId>d-bp18um4r4f2fve24****</DiskId>
            </Disk>
      </Disks>
</DescribeDisksResponse>
```

`JSON` format

```
{
	"PageNumber": 1,
	"TotalCount": 76,
	"PageSize": 1,
	"RequestId": "C74847CB-9B69-4360-9969-3595F2B6B9C1",
	"Disks": {
		"Disk": [
			{
				"DiskChargeType": "PostPaid",
				"ImageId": "centos_7_06_64_20G_alibase_20190711.vhd",
				"Device": "/dev/xvda",
				"DetachedTime": "",
				"Type": "system",
				"InstanceId": "i-bp1j4i2jdf3owlhe****",
				"Encrypted": false,
				"ZoneId": "cn-hangzhou-f",
				"EnableAutoSnapshot": true,
				"AttachedTime": "2019-11-11T08:35:32Z",
				"PerformanceLevel": "PL2",
				"SerialNumber": "bp18um4r4f2fve2****",
				"SourceSnapshotId": "s-bp67acfmxazb4p****",
				"DeleteAutoSnapshot": false,
				"KMSKeyId": "",
				"Size": 40,
				"Description": "",
				"BdfId": "",
				"ProductCode": "",
				"Portable": false,
				"EnableAutomatedSnapshotPolicy": false,
				"ResourceGroupId": "",
				"DiskName": "",
				"StorageSetId": "",
				"AutoSnapshotPolicyId": "",
				"CreationTime": "2019-11-11T08:35:29Z",
				"MountInstances": {
					"MountInstance": []
				},
				"Status": "In_use",
				"Tags": {
					"Tag": [
						{
							"TagValue": "TestValue",
							"TagKey": "TestKey"
						}
					]
				},
				"Category": "cloud_efficiency",
				"RegionId": "cn-hangzhou",
				"DeleteWithInstance": true,
				"OperationLocks": {
					"OperationLock": []
				},
				"ExpiredTime": "2999-09-08T16:00Z",
				"DiskId": "d-bp18um4r4f2fve24****"
			}
		]
	}
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidDiskType.ValueNotSupported|The specified disk type is not supported.|The error message returned because the specified DiskType parameter is invalid.|
|400|InvalidCategory.ValueNotSupported|The specified disk category is not supported.|The error message returned because the specified Category parameter is invalid.|
|400|InvalidStatus.ValueNotSupported|The specified disk status is not supported.|The error message returned because the operation is not supported while the disk is in the current state.|
|403|InvalidDiskIds.Malformed|The amount of specified disk Ids exceeds the limit.|The error message returned because the specified DiskIds parameter is invalid.|
|404|InvalidDiskChargeType.NotFound|The DiskChargeType does not exist in our records|The error message returned because the specified DiskChargeType parameter does not exist.|
|404|InvalidLockReason.NotFound|The specified LockReason is not found|The error message returned because the specified type of the reason why the instance was locked does not exist.|
|404|InvalidFilterKey.NotFound| |The error message returned because the specified start time or expiration time is invalid.|
|400|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|The error message returned because the specified Tag.N.Key and Tag.N.Value parameters do not match.|
|400|InvalidTagCount|The specified tags are beyond the permitted range.|The error message returned because the maximum number of tags has been reached.|
|400|InvalidRegion.NotFound|The specified parameter RegionId is not valid.|The error message returned because the specified RegionId parameter is invalid.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|400|InvalidZoneId.NotFound|The zoneId provided does not exist in our records.|The error message returned because the specified ZoneId parameter does not exist.|
|400|MissingParamter.RegionId|The regionId should not be null.|The error message returned because the required RegionId parameter is not specified.|
|400|InvalidParameter.DiskIds|The specified parameter diskIds is not valid.|The error message returned because the specified DiskIds parameter is invalid.|
|400|IncompleteParamter|Some fields can not be null in this request.|The error message returned because a required parameter is not specified.|
|400|InvalidParamter|Some parameters are invalid in this request.|The error message returned because the request contains invalid parameters.|
|400|InvalidSnapshot.NotFound|The specified parameter SnapshotId is not valid.|The error message returned because the specified SnapshotId parameter is invalid.|
|403|UserNotInTheWhiteList|The user is not in volume white list.|The error message returned because you are not authorized to manage Shared Block Storage devices. Submit a ticket to apply for the authorization.|
|404|InvalidDiskIds.ValueNotSupported|The specified parameter "DiskIds" is not supported.|The error message returned because the specified DiskIds parameter is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

