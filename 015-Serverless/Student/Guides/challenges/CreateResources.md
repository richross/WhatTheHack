# Challenge 2 - Create Resources

## Prerequisities

1. [Challenge 1 - Setup](./Setup.md) should be done successfuly.


## Introduction

You must provision a few resources in Azure before you start developing the solution. Ensure all resources use the same resource group for easier cleanup.  Put resources in the same region as the resource group.  Remember that some resources need to have unique names.

In this challenge, you will provision a blob storage account using the Hot tier, and create two containers within to store uploaded photos and exported CSV files. You will then provision two Function Apps instances, one you will deploy from Visual Studio, and the other you will manage using the Azure portal. Next, you will create a new Event Grid topic. After that, you will create an Azure Cosmos DB account with two collections. Finally, you will provision a new Cognitive Services Computer Vision API service for applying object character recognition (OCR) on the license plates.

_HINT : Record names and keys_

1. Create a resource group
1. Create a storage account (refer to this one as INIT)
    * Create a container &quot;images&quot;
    * Create a container &quot;export&quot;
1. Create a function app (put &quot;App&quot; in the name)
    * For your tollbooth app, consumption plan, .NET runtime stack
    * Create new storage and disable application insights
1. Create a function app (put &quot;Events&quot; in the name)
    * For your tollbooth events, consumption plan, Javascript runtime stack
    * Create new storage and disable application insights
1. Create an Event Grid Topic (leave schema as Event Grid Schema)
1. Create an Azure Cosmos DB account
    * API : Core (SQL)
    * Disable Geo-redundency and multi-region writes
    * Create a collection
      * Database ID &quot;LicensePlates&quot;
      * Leave **Provision database throughput** unchecked.
      * Container ID &quot;Processed&quot;
      * Partition key **: &quot;**/licensePlateText&quot;
      * 5000 throughput
    * Create a collection
      * Database ID &quot;LicensePlates&quot;
      * Leave **Provision database throughput** unchecked.
      * Container ID &quot;NeedsManualReview&quot;
      * Partition key **: &quot;**/fileName&quot;
      * 5000 throughput
    * _Hint : copy the_ _read-write keys_ _for URI and Primary Key_
1. Create a Computer Vision API service (S1 pricing tier)


## Success criteria
1. You have 8 resources in your resource group in the same region (Includes the 2 storage accounts associated to your function apps)

## Learning resources

|                                            |                                                                                                                                                       |
| ------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------: |
| **Description**                            |                                                                       **Links**                                                                       |
| Creating a storage account (blob hot tier) | <https://docs.microsoft.com/azure/storage/common/storage-create-storage-account?toc=%2fazure%2fstorage%2fblobs%2ftoc.json%23create-a-storage-account> |
| Creating a function app                    |                                <https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal>                                |
| Concepts in Event Grid                     |                                                <https://docs.microsoft.com/azure/event-grid/concepts>                                                 |
| Creating an Azure Cosmos DB account        |                                              <https://docs.microsoft.com/azure/cosmos-db/manage-account>                                              |

[Next challenge (Configuration) >](./Configuration.md)