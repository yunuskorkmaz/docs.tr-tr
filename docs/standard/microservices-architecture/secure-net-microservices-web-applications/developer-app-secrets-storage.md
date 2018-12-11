---
title: Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143876"
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="31a29-103">Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama</span><span class="sxs-lookup"><span data-stu-id="31a29-103">Storing application secrets safely during development</span></span>

<span data-ttu-id="31a29-104">Korumalı kaynakları ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgileri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31a29-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="31a29-105">Bu hassas bilgilerin adlı *gizli dizileri*.</span><span class="sxs-lookup"><span data-stu-id="31a29-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="31a29-106">Gizli dizileri kaynak kodunda içermeyecek şekilde ve kesinlikle gizli dizileri kaynak denetiminde depolamamayı en iyi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="31a29-106">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="31a29-107">Bunun yerine, gizli dizileri daha güvenli bir konumdan okunamıyor, ASP.NET Core yapılandırma modeli kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="31a29-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="31a29-108">Geliştirme erişmek ve bu üretim kaynaklarına erişmek için farklı kişilerin bu gizli dizileri farklı kümeleri erişmesi için kullanılan kaynaklardan hazırlama için gizli dizileri ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="31a29-108">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="31a29-109">Geliştirme sırasında kullanılan gizli dizileri depolamak için genel yaklaşımları ya da ortam değişkenleri içindeki veya ASP.NET Core gizli dizi Yöneticisi aracını kullanarak gizli dizileri depolamak üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="31a29-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="31a29-110">Üretim ortamlarında daha güvenli depolama için mikro hizmetler, gizli dizileri Azure anahtar Kasası'nda depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31a29-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="31a29-111">Gizli dizilerin depolanmasında ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="31a29-111">Storing secrets in environment variables</span></span>

<span data-ttu-id="31a29-112">Gizli dizileri kaynak kodunun dışında tutmak için bir yoludur dize tabanlı gizli dizi olarak ayarlamak, geliştiriciler için [ortam değişkenlerini](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerinde.</span><span class="sxs-lookup"><span data-stu-id="31a29-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="31a29-113">Ortam değişkenlerini kullandığınızda hiyerarşik (Bu yapılandırma bölümleri içinde iç içe geçmiş) adları ile Parolaları depolamak için parolanın adının tam hiyerarşi içeren ortam değişkenleri için bir ad oluşturun, iki nokta (:) ile ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="31a29-113">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="31a29-114">Örneğin, hata ayıklama için bir ortam değişkenini günlüğe kaydetme: LogLevel:Default ayarlayarak aşağıdaki JSON dosyasındaki yapılandırma değeri olarak eşdeğer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="31a29-114">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="31a29-115">Bu değerler, ortam değişkenlerinden erişmek için uygulamayı yalnızca AddEnvironmentVariables üzerinde kendi ConfigurationBuilder IConfigurationRoot nesneyi diziden oluşturulurken çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31a29-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="31a29-116">Ortam değişkenleri genellikle düz metin olarak depolandığını unutmayın bir makine ya da işlem ortam değişkenleriyle tehlikedeyse, ortam değişkeni değerlerini görünür olur.</span><span class="sxs-lookup"><span data-stu-id="31a29-116">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="31a29-117">ASP.NET Core gizli dizi Yöneticisi'ni kullanarak gizli dizilerin depolanmasında</span><span class="sxs-lookup"><span data-stu-id="31a29-117">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="31a29-118">ASP.NET Core [gizli dizi Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) aracı, kaynak kodunun dışında gizli dizileri tutma başka bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="31a29-118">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="31a29-119">Gizli dizi Yöneticisi aracını kullanmak için proje dosyanızda Microsoft.Extensions.SecretManager.Tools paketine araçları başvurusu (DotNetCliToolReference) içerir.</span><span class="sxs-lookup"><span data-stu-id="31a29-119">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="31a29-120">Bu bağımlılık mevcut olduğundan ve geri yüklendikten sonra dotnet kullanıcı parolalarını komutu komut satırından gizli dizileri değerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31a29-120">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="31a29-121">Bu gizli anahtarları (işletim sistemi tarafından Ayrıntılar değişiklik gösterir) kullanıcının profil dizini, kaynak kodu uzakta bir JSON dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="31a29-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="31a29-122">Gizli dizi Yöneticisi belirlediği gizli anahtarları, gizli dizileri kullanarak proje UserSecretsId özelliği tarafından düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="31a29-122">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="31a29-123">Bu nedenle, proje dosyanızda (aşağıdaki kod parçacığında gösterildiği gibi) UserSecretsId özelliğini ayarladığınızdan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31a29-123">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="31a29-124">Projesi içinde benzersiz olduğu sürece kimlik olarak kullanılan gerçek dize önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="31a29-124">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="31a29-125">Gizli dizi Yöneticisi ile bir uygulama içinde depolanan gizli kullanarak gerçekleştirilir AddUserSecrets çağırarak&lt;T&gt; yapılandırmasında uygulaması için gizli dizileri içerecek şekilde ConfigurationBuilder örneğinde.</span><span class="sxs-lookup"><span data-stu-id="31a29-125">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="31a29-126">Genel parametre T UserSecretId uygulandığı bir derlemeden bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31a29-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="31a29-127">Genellikle AddUserSecrets kullanarak&lt;başlangıç&gt; bir sakınca yoktur.</span><span class="sxs-lookup"><span data-stu-id="31a29-127">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
><span data-ttu-id="31a29-128">[Önceki](authorization-net-microservices-web-applications.md)
>[İleri](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="31a29-128">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>