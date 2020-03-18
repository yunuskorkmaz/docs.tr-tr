---
title: Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolama
description: .NET Microservices ve Web Applications Güvenlik - Kaynak kontrolünde şifreler, bağlantı dizeleri veya API anahtarları gibi uygulama sırlarını depolamayın, ASP.NET Core'da kullanabileceğiniz seçenekleri anlayın, özellikle "kullanıcı"yı nasıl kullanacağınızı anlamanız gerekir sırlar".
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501794"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="08397-103">Geliştirme sırasında uygulama sırlarını güvenli bir şekilde saklayın</span><span class="sxs-lookup"><span data-stu-id="08397-103">Store application secrets safely during development</span></span>

<span data-ttu-id="08397-104">Korumalı kaynaklara ve diğer hizmetlere bağlanmak için, ASP.NET Core uygulamalarının genellikle bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgilerini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08397-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="08397-105">Bu hassas bilgilere *sır*denir.</span><span class="sxs-lookup"><span data-stu-id="08397-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="08397-106">Bu kaynak kodusırları içermemek ve kaynak denetiminde sırları depolamak için değil emin olmak için en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="08397-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="08397-107">Bunun yerine, daha güvenli konumlardan sırları okumak için ASP.NET Core yapılandırma modelini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08397-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="08397-108">Farklı bireylerin bu farklı sır kümelerine erişmesi gerekeceği için, geliştirme ve evreleme kaynaklarına erişme sırlarını üretim kaynaklarına erişmek için kullanılanlardan ayırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08397-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="08397-109">Geliştirme sırasında kullanılan sırları depolamak için, ortak yaklaşımlar ya çevre değişkenlerinde veya ASP.NET Core Secret Manager aracını kullanarak sırları depolamak içindir.</span><span class="sxs-lookup"><span data-stu-id="08397-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="08397-110">Üretim ortamlarında daha güvenli depolama için, mikro hizmetler sırları Azure Anahtar Kasası'nda saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="08397-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="08397-111">Sırları çevre değişkenlerinde depolama</span><span class="sxs-lookup"><span data-stu-id="08397-111">Store secrets in environment variables</span></span>

<span data-ttu-id="08397-112">Sırları kaynak kodundan uzak tutmanın bir yolu, geliştiricilerin geliştirme makinelerinde dize tabanlı sırları [ortam değişkenleri](/aspnet/core/security/app-secrets#environment-variables) olarak ayarlamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="08397-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="08397-113">Yapılandırma bölümlerinde iç içe olanlar gibi hiyerarşik adlarla sırları depolamak için ortam değişkenlerini kullandığınızda, değişkenleri, üst üste (:) ile sınırlandırılmış bölümlerinin tam hiyerarşisini içerecek şekilde adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08397-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="08397-114">Örneğin, bir ortam `Logging:LogLevel:Default` değişkenini değere `Debug` ayarlamak, aşağıdaki JSON dosyasındaki yapılandırma değerine eşdeğer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="08397-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="08397-115">Bu değerlere ortam değişkenlerinden erişmek için uygulamanın, bir IConfigurationRoot nesnesi inşa ederken ConfigurationBuilder'ında AddEnvironmentVariables'i araması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08397-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="08397-116">Ortam değişkenlerinin genellikle düz metin olarak depolanır, bu nedenle makine veya ortam değişkenleri ile işlem tehlikeye girerse, ortam değişkendeğerleri görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="08397-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="08397-117">ASP.NET Core Secret Manager ile sırları saklayın</span><span class="sxs-lookup"><span data-stu-id="08397-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="08397-118">ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) aracı geliştirme **sırasında**sırları kaynak kodun dışında tutmak için başka bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="08397-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code **during development**.</span></span> <span data-ttu-id="08397-119">Gizli Yönetici aracını kullanmak için proje dosyanıza **Microsoft.Extensions.Configuration.SecretManager** paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="08397-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="08397-120">Bu bağımlılık mevcut ve geri yüklendikten `dotnet user-secrets` sonra, komut komut satırından sırların değerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08397-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="08397-121">Bu sırlar, kaynak kodundan uzakta, kullanıcının profil dizinindeki (ayrıntılar işletim sistemi'ne göre değişir) bir JSON dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="08397-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="08397-122">Gizli Yönetici aracı tarafından belirlenen sırlar, sırları kullanan projenin `UserSecretsId` özelliği tarafından düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="08397-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="08397-123">Bu nedenle, aşağıdaki parçacıkta gösterildiği gibi, Proje dosyanızda UserSecretsId özelliğini ayarladığınızdan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="08397-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="08397-124">Varsayılan değer Visual Studio tarafından atanan bir GUID'dir, ancak bilgisayarınızda benzersiz olduğu sürece gerçek dize önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="08397-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="08397-125">Bir uygulamada Secret Manager ile depolanan sırları `AddUserSecrets<T>` kullanarak ConfigurationBuilder örneğini kendi yapılandırmasında uygulama için sırları eklemek için çağırarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="08397-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="08397-126">Genel parametre T, UserSecretId'in uygulandığı derlemeden bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08397-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="08397-127">Genellikle `AddUserSecrets<Startup>` kullanmak iyidir.</span><span class="sxs-lookup"><span data-stu-id="08397-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="08397-128">Yöntem `AddUserSecrets<Startup>()` `CreateDefaultBuilder` *Program.cs'da*yöntem kullanırken Geliştirme ortamı için varsayılan seçeneklere dahildir.</span><span class="sxs-lookup"><span data-stu-id="08397-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="08397-129">[Önceki](authorization-net-microservices-web-applications.md)
>[Sonraki](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="08397-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
