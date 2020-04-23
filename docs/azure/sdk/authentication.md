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
# <a name="authenticate-with-the-azure-libraries-for-net"></a>.NET için Azure Kitaplıkları ile kimlik doğrulaması

## <a name="connect-to-services-with-connection-strings"></a>Bağlantı dizeleriyle hizmetlere bağlanma

Azure hizmet kitaplıkların çoğu kimlik doğrulaması için bir bağlantı dizesi veya anahtar gerektirir. Örneğin, SQL Veritabanı standart bir SQL bağlantı dizesi kullanır:

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

Azure Depolama bir depolama anahtarı kullanır:

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

Hizmet bağlantı dizeleri [CosmosDB,](https://docs.microsoft.com/azure/cosmos-db/) [Redis için Azure Önbelleği](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)ve [Servis Veri Servisi](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)gibi diğer Azure hizmetlerinde kullanılır. Bu dizeleri Azure portalı, CLI veya PowerShell'i kullanarak alabilirsiniz. Kodunuzda bağlantı dizeleri oluşturmak için kaynakları sorgulamak için .NET için Azure yönetim kitaplıklarını da kullanabilirsiniz.

Bu parçacık, bir depolama hesabı bağlantı dizesi oluşturmak için yönetim kitaplıklarını kullanır:

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

Diğer kitaplıklar uygulamanızın verilen kimlik bilgileriyle uygulamayı yetkilendiren bir [hizmet sorumlusuyla](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) çalıştırılmasını gerektirir. Bu yapılandırma aşağıda listelenen yönetim kitaplığı için nesne tabanlı kimlik doğrulama adımlarına benzer.

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a>.NET kimlik doğrulaması için azure yönetim kitaplıkları

[!include[Create service principal](../includes/create-sp.md)]

Hizmet ilkesi oluşturulduğuna göre, kaynakları oluşturmak ve yönetmek için hizmet ilkesine kimlik doğrulaması yapmak için iki seçenek kullanılabilir.

Her iki seçenek için de projenize aşağıdaki NuGet paketlerini eklemeniz gerekir.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Belirteç kimlik bilgileriyle kimlik doğrulaması

İlk yöntem, koddaki belirteç kimlik bilgisi nesnesini oluşturmaktır. Kimlik bilgilerini bir yapılandırma dosyasında, kayıt defterinde veya Azure KeyVault'ta güvenli bir şekilde depolamanız gerekir.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

Hizmet ilkesini oluşturduğunuzda JSON çıkışındaki *clientId,* *clientSecret*ve *tenantId* değerlerini kullanın.

Ardından API `Azure` ile çalışmaya başlamak için giriş noktası nesnesini oluşturun:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Dosya tabanlı kimlik doğrulama

Dosya tabanlı kimlik doğrulama, hizmet temel kimlik bilgilerini düz bir metin dosyasına koymanızı ve dosya sistemi içinde güvenli hale almanızı sağlar.

[!include[File-based authentication](../includes/file-based-auth.md)]

Dosyanın içeriğini okuyun ve API `Azure` ile çalışmaya başlamak için giriş noktası nesnesini oluşturun:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
