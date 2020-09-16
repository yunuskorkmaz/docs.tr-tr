---
title: .NET için Azure kitaplıklarında kimlik doğrulamasını anlama
description: .NET için Azure SDK ile kimlik doğrulamanın farklı yollarını açıklar.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: dbae72eb9e80801d7338b210f9664f1c4e318ae0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539183"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="7bfea-103">.NET için Azure SDK ile kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="7bfea-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="7bfea-104">Önerilen: Azure. Identity</span><span class="sxs-lookup"><span data-stu-id="7bfea-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="7bfea-105">.NET için Azure SDK 'sindeki en son paketler, kimlik doğrulaması için ortak bir kimlik doğrulama paketi kullanır `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="7bfea-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="7bfea-106">`Azure.Identity`Bu belgenin ilerleyen kısımlarında açıklanan diğer kimlik doğrulama mekanizmaları üzerinde kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="7bfea-107">Tarafından sunulan kimlik bilgilerini destekleyen paketler, üzerine `Azure.Identity` kurulmuştur `Azure.Core` ve *Azure*ile başlayan paket tanımlayıcılarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-107">Packages supporting the credentials provided by `Azure.Identity` are built on top of `Azure.Core` and have package identifiers starting with *Azure*.</span></span> <span data-ttu-id="7bfea-108">Kullanan paketlerin envanterini [görmek için paket listesine bakın](packages.md) `Azure.Core` .</span><span class="sxs-lookup"><span data-stu-id="7bfea-108">[See the package list](packages.md) for an inventory of packages that use `Azure.Core`.</span></span>

<span data-ttu-id="7bfea-109">Projenizde kullanmayla ilgili tüm yönergeler için `Azure.Identity` bkz. [.net Için Azure Identity Client](/dotnet/api/overview/azure/identity-readme)belgeleri.</span><span class="sxs-lookup"><span data-stu-id="7bfea-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="7bfea-110">Azure kaynaklarını yönetmek ve bunlara erişmek için Azure kimliği kullanma örnekleri için bkz. Azure [kimliği, kaynak yönetimi ve depolama örneği](/samples/dotnet/samples/azure-identity-resource-management-storage/) .</span><span class="sxs-lookup"><span data-stu-id="7bfea-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="7bfea-111">Azure. Identity ' ı desteklemeyen kitaplıklarda kimlik doğrulaması yapmak için bu konunun geri kalanına bakın.</span><span class="sxs-lookup"><span data-stu-id="7bfea-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="7bfea-112">Azure kaynaklarına erişin</span><span class="sxs-lookup"><span data-stu-id="7bfea-112">Access Azure resources</span></span>

<span data-ttu-id="7bfea-113">Key Vault bir gizli dizi alma veya depolama alanında BLOB depolama gibi Azure kaynaklarıyla etkileşim kurmak için, birçok Azure hizmet kitaplığı, kimlik doğrulaması için bir bağlantı dizesi veya anahtar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="7bfea-114">Örneğin, SQL veritabanı [Standart BIR SQL bağlantı dizesi](/azure/azure-sql/database/connect-query-dotnet-core)kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bfea-114">For example, SQL Database uses a [standard SQL connection string](/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="7bfea-115">Hizmet bağlantı dizeleri [Cosmosdb](/azure/cosmos-db/), [redin için Azure Cache](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)ve [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)gibi diğer Azure hizmetlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bfea-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="7bfea-116">Bu dizeleri Azure portal, CLı veya PowerShell kullanarak edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bfea-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="7bfea-117">Kodunuzda bağlantı dizeleri oluşturmak üzere kaynakları sorgulamak için .NET için Azure Yönetim kitaplıklarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bfea-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="7bfea-118">Bir bağlantı dizesi kullanma yöntemleri ürüne göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="7bfea-119">[Azure ürününüzün belgelerine bakın](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="7bfea-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="7bfea-120">Azure kaynaklarını yönetme</span><span class="sxs-lookup"><span data-stu-id="7bfea-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="7bfea-121">Hizmet sorumlusu oluşturulduktan sonra, kaynakları oluşturmak ve yönetmek için hizmet sorumlusunun kimliğini doğrulamak üzere iki seçenek mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="7bfea-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="7bfea-122">Her iki seçenek için de aşağıdaki NuGet paketlerini projenize eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="7bfea-123">Belirteç kimlik bilgileriyle kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="7bfea-123">Authenticate with token credentials</span></span>

<span data-ttu-id="7bfea-124">İlk yöntem, koddaki Token Credential nesnesini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bfea-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="7bfea-125">Kimlik bilgilerini bir yapılandırma dosyasında, kayıt defterinde veya Azure Keykasasında güvenli bir şekilde depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bfea-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="7bfea-126">Hizmet sorumlusunu oluştururken JSON çıktısından *ClientID*, *ClientSecret*ve *tenantıd* değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bfea-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="7bfea-127">Ardından, `Azure` API ile çalışmaya başlamak için giriş noktası nesnesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7bfea-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="7bfea-128">JSON çıktısından nesnesine açıkça *abonelik* sağlamanız önerilir `Azure` :</span><span class="sxs-lookup"><span data-stu-id="7bfea-128">It is recommended that you explicitly provide the *subscriptionId* from the JSON output to the `Azure` object:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="7bfea-129">Dosya tabanlı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7bfea-129">File-based authentication</span></span>

<span data-ttu-id="7bfea-130">Dosya tabanlı kimlik doğrulaması, hizmet sorumlusu kimlik bilgilerini bir düz metin dosyasına yerleştirip dosya sistemi içinde güvenli hale getirmeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7bfea-130">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="7bfea-131">API ile çalışmaya başlamak için dosyanın içeriğini okuyun ve giriş noktası `Azure` nesnesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7bfea-131">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
