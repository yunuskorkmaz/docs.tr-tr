---
title: Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik ASP.NET Core kullanabileceğiniz seçenekler parolalar, bağlantı dizeleri veya kaynak denetimi, API anahtarlarını anlama gibi uygulama parolalarını depolamak yoksa, "kullanıcı ne yapılacağını anlamak zorunda özellikle Gizli dizileri".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361995"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="4e09e-103">Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında Store</span><span class="sxs-lookup"><span data-stu-id="4e09e-103">Store application secrets safely during development</span></span>

<span data-ttu-id="4e09e-104">Korumalı kaynakları ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgileri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="4e09e-105">Bu hassas bilgilerin adlı *gizli dizileri*.</span><span class="sxs-lookup"><span data-stu-id="4e09e-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="4e09e-106">Gizli dizileri kaynak kodu ve gizli dizileri kaynak denetiminde depolamamayı sağlamaktan içermeyecek şekilde en iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="4e09e-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="4e09e-107">Bunun yerine, gizli dizileri daha güvenli bir konumdan okunamıyor, ASP.NET Core yapılandırma modeli kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4e09e-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="4e09e-108">Geliştirme erişmek ve bu üretim kaynaklarına erişmek için erişim gizli dizilerinin farklı bu kümeleri için farklı kişilerin gerekeceğinden Kullanılanlar kaynaklardan hazırlama için gizli dizileri ayırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="4e09e-109">Geliştirme sırasında kullanılan gizli dizileri depolamak için genel yaklaşımları ya da ortam değişkenleri içindeki veya ASP.NET Core gizli dizi Yöneticisi aracını kullanarak gizli dizileri depolamak üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="4e09e-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="4e09e-110">Üretim ortamlarında daha güvenli depolama için mikro hizmetler, gizli dizileri Azure anahtar Kasası'nda depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e09e-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="4e09e-111">Ortam değişkenlerini Store gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="4e09e-111">Store secrets in environment variables</span></span>

<span data-ttu-id="4e09e-112">Gizli dizileri kaynak kodunun dışında tutmak için bir yoludur dize tabanlı gizli dizi olarak ayarlamak, geliştiriciler için [ortam değişkenlerini](/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerinde.</span><span class="sxs-lookup"><span data-stu-id="4e09e-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="4e09e-113">Yapılandırma bölümleri içinde iç içe geçmiş olanlar gibi hiyerarşik adları ile Parolaları depolamak için ortam değişkenlerini kullandığınızda tam iki nokta (:) ile ayrılmış alt bölümlere hiyerarşisini dahil etmek istediğiniz değişkenleri adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e09e-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="4e09e-114">Örneğin, bir ortam değişkenini ayarlayarak `Logging:LogLevel:Default` için `Debug` değerini aşağıdaki JSON dosyasındaki yapılandırma değeri olarak eşdeğer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="4e09e-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="4e09e-115">Bu değerler, ortam değişkenlerinden erişmek için uygulamayı yalnızca AddEnvironmentVariables üzerinde kendi ConfigurationBuilder IConfigurationRoot nesneyi diziden oluşturulurken çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="4e09e-116">Ortam değişkenleri genellikle düz metin olarak depolandığını unutmayın bir makine ya da işlem ortam değişkenleriyle tehlikedeyse, ortam değişkeni değerlerini görünür olur.</span><span class="sxs-lookup"><span data-stu-id="4e09e-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="4e09e-117">Gizli dizileri ile ASP.NET Core gizli dizi Yöneticisi Store</span><span class="sxs-lookup"><span data-stu-id="4e09e-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="4e09e-118">ASP.NET Core [gizli dizi Yöneticisi](/aspnet/core/security/app-secrets#secret-manager) aracı, kaynak kodunun dışında gizli dizileri tutma başka bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e09e-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="4e09e-119">Gizli dizi Yöneticisi aracını kullanmak için paket yükleme **Microsoft.Extensions.Configuration.SecretManager** proje dosyanızda.</span><span class="sxs-lookup"><span data-stu-id="4e09e-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="4e09e-120">Bu bağımlılık, mevcut olduğundan ve geri yüklendi, sonra `dotnet user-secrets` komutu, komut satırından gizli dizileri değerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="4e09e-121">Bu gizli anahtarları (işletim sistemi tarafından Ayrıntılar değişiklik gösterir) kullanıcının profil dizini, kaynak kodu uzakta bir JSON dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="4e09e-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="4e09e-122">Gizli dizi Yöneticisi belirlediği gizli dizileri tarafından düzenlenir `UserSecretsId` gizli dizileri kullanarak projenin özelliği.</span><span class="sxs-lookup"><span data-stu-id="4e09e-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="4e09e-123">Bu nedenle, aşağıdaki kod parçacığında gösterildiği gibi proje dosyasında UserSecretsId özelliğini ayarladığınızdan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="4e09e-124">Varsayılan değer, Visual Studio tarafından atanan bir GUID olmakla birlikte, bilgisayarınızın benzersiz olduğu sürece gerçek dize önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="4e09e-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="4e09e-125">Gizli dizi Yöneticisi ile bir uygulama içinde depolanan gizli kullanarak gerçekleştirilir çağırarak `AddUserSecrets<T>` yapılandırmasında uygulaması için gizli dizileri içerecek şekilde ConfigurationBuilder örneğinde.</span><span class="sxs-lookup"><span data-stu-id="4e09e-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="4e09e-126">Genel parametre T UserSecretId uygulandığı bir derlemeden bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e09e-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="4e09e-127">Kullanımı genellikle `AddUserSecrets<Startup>` bir sakınca yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e09e-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="4e09e-128">`AddUserSecrets<Startup>()` Geliştirme ortamı için varsayılan seçenekleri kullanarak dahil `CreateDefaultBuilder` yönteminde *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4e09e-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4e09e-129">[Önceki](authorization-net-microservices-web-applications.md)
>[İleri](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="4e09e-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
