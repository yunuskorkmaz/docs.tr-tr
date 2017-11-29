---
title: "Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="565bb-104">Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama</span><span class="sxs-lookup"><span data-stu-id="565bb-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="565bb-105">Korumalı kaynaklar ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgilerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="565bb-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="565bb-106">Bu hassas bilgilerin adlı *gizli*.</span><span class="sxs-lookup"><span data-stu-id="565bb-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="565bb-107">Bu gizli kaynak kodunda içermeyecek şekilde ve kesinlikle gizli kaynak denetiminde depolamamayı en iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="565bb-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="565bb-108">Bunun yerine, daha güvenli konumlardan gizli anahtarları okumak için ASP.NET Core yapılandırma modeli kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="565bb-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="565bb-109">Geliştirme erişmek ve kaynakları kullanılanlardan farklı kişilerin gizli farklı bu kümeleri erişmesi için üretim kaynaklara erişmek için hazırlama gizli ayırın.</span><span class="sxs-lookup"><span data-stu-id="565bb-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="565bb-110">Geliştirme sırasında kullanılan parolaları depolamak için ortak yaklaşımlar ya da gizli ortam değişkenleri içindeki veya ASP.NET Core gizli Yöneticisi aracını kullanarak depolama üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="565bb-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="565bb-111">Üretim ortamlarında daha güvenli depolama için mikro gizli bir Azure anahtar kasası depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="565bb-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="565bb-112">Gizli ortam değişkenleri depolanması</span><span class="sxs-lookup"><span data-stu-id="565bb-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="565bb-113">Gizli kaynak kodu dışında tutmak için bir yoldur dize tabanlı gizlilikleri olarak ayarlamak geliştiricilere [ortam değişkenleri](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerde.</span><span class="sxs-lookup"><span data-stu-id="565bb-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="565bb-114">Ortam değişkenleri kullandığınızda hiyerarşik adları (olanlar yapılandırma bölümlerinin iç içe geçmiş) ile Parolaları depolamak için ortam değişkenleri için parolanın adının tam hiyerarşiyi içeren bir ad oluşturun, iki nokta (:) ile ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="565bb-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="565bb-115">Örneğin, bir ortam değişkeni günlüğe kaydetme: LogLevel:Default Debug ayarı aşağıdaki JSON dosyasından bir yapılandırma değeri eşdeğer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="565bb-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="565bb-116">Ortam değişkenlerinin bu değerleri erişmek için uygulamanın yalnızca bir IConfigurationRoot nesne oluşturulurken üzerinde kendi ConfigurationBuilder AddEnvironmentVariables çağrılacak gerekir.</span><span class="sxs-lookup"><span data-stu-id="565bb-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="565bb-117">Ortam değişkenleri genellikle düz metin olarak depolanır Not makine ya da ortam değişkenleri işlemine aşılıp aşılmadığını ortam değişkeni değerlerini görünür olur.</span><span class="sxs-lookup"><span data-stu-id="565bb-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="565bb-118">ASP.NET Core gizli Yöneticisi'ni kullanarak gizli anahtarları depolama</span><span class="sxs-lookup"><span data-stu-id="565bb-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="565bb-119">ASP.NET Core [gizli Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) aracı kaynak kodu dışında gizli tutmak başka bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="565bb-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="565bb-120">Gizli Yöneticisi aracını kullanmak için proje dosyanızdaki Microsoft.Extensions.SecretManager.Tools pakete araçları başvurusu (DotNetCliToolReference) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="565bb-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="565bb-121">Bu bağımlılık var ve geri yüklendikten sonra dotnet kullanıcı parolaları komutu komut satırından gizli değerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="565bb-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="565bb-122">Bu gizli anahtarları (işletim sistemi tarafından ayrıntıları değişir) kullanıcının profil dizini, kaynak kodu çıktığınızda JSON dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="565bb-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="565bb-123">Gizli Manager aracısının belirlediği gizli gizli anahtarları kullanarak proje UserSecretsId özelliği tarafından düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="565bb-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="565bb-124">Bu nedenle, proje dosyası (parçacığında gösterildiği gibi) UserSecretsId özelliği ayarladığınızdan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="565bb-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="565bb-125">Projesi içinde benzersiz olduğu sürece kimliği olarak kullanılan gerçek dizesi önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="565bb-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="565bb-126">Parola Yöneticisi ile bir uygulamada depolanan parolaları kullanarak gerçekleştirilir AddUserSecrets çağırarak&lt;T&gt; yapılandırmasıyla uygulama parolaları eklemek için ConfigurationBuilder örneği.</span><span class="sxs-lookup"><span data-stu-id="565bb-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="565bb-127">Genel parametresini T UserSecretId uygulandığı derlemesinden bir türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="565bb-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="565bb-128">Genellikle AddUserSecrets kullanarak&lt;başlangıç&gt; uygundur.</span><span class="sxs-lookup"><span data-stu-id="565bb-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="565bb-129">[Önceki] (yetkilendirme-net-mikro-web-applications.md) [sonraki] (azure-anahtar-kasa-korur-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="565bb-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
