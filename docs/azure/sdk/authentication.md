---
title: .NET için Azure kitaplıklarıyla kimlik doğrulaması
description: .NET için Azure kitaplıklarında kimlik doğrulaması
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072153"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="0c610-103">.NET için Azure Kitaplıkları ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0c610-103">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="0c610-104">Bağlantı dizeleriyle hizmetlere bağlanma</span><span class="sxs-lookup"><span data-stu-id="0c610-104">Connect to services with connection strings</span></span>

<span data-ttu-id="0c610-105">Azure hizmet kitaplıkların çoğu kimlik doğrulaması için bir bağlantı dizesi veya anahtar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c610-105">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="0c610-106">Örneğin, SQL Veritabanı standart bir SQL bağlantı dizesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="0c610-106">For example, SQL Database uses a standard SQL connection string:</span></span>

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;

using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

<span data-ttu-id="0c610-107">Azure Depolama bir depolama anahtarı kullanır:</span><span class="sxs-lookup"><span data-stu-id="0c610-107">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="0c610-108">Hizmet bağlantı dizeleri [CosmosDB,](https://docs.microsoft.com/azure/cosmos-db/) [Redis için Azure Önbelleği](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)ve [Servis Veri Servisi](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)gibi diğer Azure hizmetlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c610-108">Service connection strings are used in other Azure services like [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="0c610-109">Bu dizeleri Azure portalı, CLI veya PowerShell'i kullanarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c610-109">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="0c610-110">Kodunuzda bağlantı dizeleri oluşturmak için kaynakları sorgulamak için .NET için Azure yönetim kitaplıklarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c610-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="0c610-111">Bu parçacık, bir depolama hesabı bağlantı dizesi oluşturmak için yönetim kitaplıklarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="0c610-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

<span data-ttu-id="0c610-112">Diğer kitaplıklar uygulamanızın verilen kimlik bilgileriyle uygulamayı yetkilendiren bir [hizmet sorumlusuyla](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) çalıştırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c610-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="0c610-113">Bu yapılandırma aşağıda listelenen yönetim kitaplığı için nesne tabanlı kimlik doğrulama adımlarına benzer.</span><span class="sxs-lookup"><span data-stu-id="0c610-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a><span data-ttu-id="0c610-114">.NET kimlik doğrulaması için azure yönetim kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="0c610-114">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](../includes/create-sp.md)]

<span data-ttu-id="0c610-115">Hizmet ilkesi oluşturulduğuna göre, kaynakları oluşturmak ve yönetmek için hizmet ilkesine kimlik doğrulaması yapmak için iki seçenek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c610-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="0c610-116">Her iki seçenek için de projenize aşağıdaki NuGet paketlerini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c610-116">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="0c610-117">Belirteç kimlik bilgileriyle kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0c610-117">Authenticate with token credentials</span></span>

<span data-ttu-id="0c610-118">İlk yöntem, koddaki belirteç kimlik bilgisi nesnesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0c610-118">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="0c610-119">Kimlik bilgilerini bir yapılandırma dosyasında, kayıt defterinde veya Azure KeyVault'ta güvenli bir şekilde depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c610-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="0c610-120">Hizmet ilkesini oluşturduğunuzda JSON çıkışındaki *clientId,* *clientSecret*ve *tenantId* değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c610-120">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="0c610-121">Ardından API `Azure` ile çalışmaya başlamak için giriş noktası nesnesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0c610-121">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="0c610-122">Dosya tabanlı kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="0c610-122">File-based authentication</span></span>

<span data-ttu-id="0c610-123">Dosya tabanlı kimlik doğrulama, hizmet temel kimlik bilgilerini düz bir metin dosyasına koymanızı ve dosya sistemi içinde güvenli hale almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c610-123">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](../includes/file-based-auth.md)]

<span data-ttu-id="0c610-124">Dosyanın içeriğini okuyun ve API `Azure` ile çalışmaya başlamak için giriş noktası nesnesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0c610-124">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
