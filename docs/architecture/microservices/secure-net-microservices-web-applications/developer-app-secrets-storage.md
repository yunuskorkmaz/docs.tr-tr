---
title: Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolama
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-kaynak denetimindeki parolalar, bağlantı dizeleri veya API anahtarları gibi uygulama gizli dizilerini depolamayın, ASP.NET Core içinde kullanabileceğiniz seçenekleri anlayın, özellikle de "Kullanıcı gizli dizileri ".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296486"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="fecbf-103">Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolayın</span><span class="sxs-lookup"><span data-stu-id="fecbf-103">Store application secrets safely during development</span></span>

<span data-ttu-id="fecbf-104">Korunan kaynaklarla ve diğer hizmetlerle bağlantı kurmak için ASP.NET Core uygulamaların genellikle bağlantı dizelerini, parolaları veya gizli bilgiler içeren diğer kimlik bilgilerini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="fecbf-105">Bu hassas bilgi parçaları *gizli*dizileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fecbf-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="fecbf-106">Kaynak kodunda gizli dizileri içermemelidir ve kaynak denetiminde gizli dizileri depolamadığınızdan emin olmak iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="fecbf-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="fecbf-107">Bunun yerine, daha güvenli konumlardan gizli dizileri okumak için ASP.NET Core yapılandırma modelini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="fecbf-108">Farklı kişilerin bu farklı gizli dizi kümelerine erişmesi gerektiğinden, üretim kaynaklarına erişmek için kullanılan gizli dizileri, geliştirme ve hazırlama kaynaklarına erişmek için ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="fecbf-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="fecbf-109">Geliştirme sırasında kullanılan gizli dizileri depolamak için, yaygın yaklaşımlar ortam değişkenlerinde gizli dizileri depolamak veya ASP.NET Core gizli dizi Yöneticisi aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="fecbf-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="fecbf-110">Mikro hizmetler, üretim ortamlarında daha güvenli depolama için gizli dizileri bir Azure Key Vault depolayabilirler.</span><span class="sxs-lookup"><span data-stu-id="fecbf-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="fecbf-111">Ortam değişkenlerinde gizli dizileri depolayın</span><span class="sxs-lookup"><span data-stu-id="fecbf-111">Store secrets in environment variables</span></span>

<span data-ttu-id="fecbf-112">Gizli dizileri kaynak kodu dışında tutmanın bir yolu, geliştiricilerin dize tabanlı gizli dizileri geliştirme makinelerinde [ortam değişkenleri](/aspnet/core/security/app-secrets#environment-variables) olarak ayarlaması içindir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="fecbf-113">Yapılandırma bölümlerine yuvalanmış olanlar gibi hiyerarşik adlarla gizli dizileri depolamak için ortam değişkenlerini kullandığınızda, değişkenlerini, iki nokta üst üste (:)) ayrılmış olarak, bölümlerinin tamamını içerecek şekilde isimsiz olarak vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fecbf-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="fecbf-114">Örneğin, bir ortam değişkenini `Logging:LogLevel:Default` `Debug` değere ayarlamak aşağıdaki json dosyasından bir yapılandırma değeri ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="fecbf-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="fecbf-115">Bu değerlere ortam değişkenlerinden erişim sağlamak için, uygulamanın bir IBir Iconationroot nesnesi oluştururken ConfigurationBuilder üzerinde AddEnvironmentVariables çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="fecbf-116">Ortam değişkenlerinin yaygın olarak düz metin olarak depolandığını unutmayın. bu nedenle, ortam değişkenleri ile makine veya işlem tehlikeye girerse, ortam değişkeni değerleri görünür olur.</span><span class="sxs-lookup"><span data-stu-id="fecbf-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="fecbf-117">ASP.NET Core gizli Yöneticisi ile gizli dizileri depolayın</span><span class="sxs-lookup"><span data-stu-id="fecbf-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="fecbf-118">ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) Aracı, kaynak kodu dışında gizli dizileri tutmanın başka bir yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fecbf-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="fecbf-119">Gizli dizi Yöneticisi aracını kullanmak için, proje dosyanıza **Microsoft. Extensions. Configuration. SecretManager** paketini yükle.</span><span class="sxs-lookup"><span data-stu-id="fecbf-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="fecbf-120">Bu bağımlılık mevcut olduğunda ve geri `dotnet user-secrets` yüklendikten sonra komut satırı gizli dizi değerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="fecbf-121">Bu gizli diziler, kullanıcının profil dizinindeki bir JSON dosyasında (Ayrıntılar işletim sistemine göre değişir) kaynak koddan uzakta saklanır.</span><span class="sxs-lookup"><span data-stu-id="fecbf-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="fecbf-122">Gizli dizi Yöneticisi aracı tarafından ayarlanan gizlilikler, gizli dizileri kullanan `UserSecretsId` projenin özelliğine göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="fecbf-123">Bu nedenle, aşağıdaki kod parçacığında gösterildiği gibi, proje dosyanızda Usersecretsıd özelliğini ayarladığınızdan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="fecbf-124">Varsayılan değer, Visual Studio tarafından atanan bir GUID 'dir, ancak bilgisayarınızda benzersiz olduğu sürece gerçek dize önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="fecbf-125">Bir uygulamada gizli yönetici ile depolanan gizli dizileri kullanmak, yapılandırmasındaki uygulamanın gizli `AddUserSecrets<T>` dizileri içermesi için configurationbuilder örneğine çağrı yaparak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="fecbf-126">Genel parametre T, Usersecretıd 'nin uygulandığı derlemeden bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fecbf-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="fecbf-127">Genellikle kullanımı `AddUserSecrets<Startup>` iyidir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="fecbf-128">, `AddUserSecrets<Startup>()` *Program.cs*içinde `CreateDefaultBuilder` yöntemi kullanılırken geliştirme ortamı için varsayılan seçeneklere dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fecbf-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fecbf-129">[Önceki](authorization-net-microservices-web-applications.md)İleri
>[](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="fecbf-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
