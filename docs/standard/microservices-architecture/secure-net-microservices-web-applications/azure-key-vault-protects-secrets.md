---
title: Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 84e016e4620b73444f800b02076489012ea5e844
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752168"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="d79b9-103">Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma</span><span class="sxs-lookup"><span data-stu-id="d79b9-103">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="d79b9-104">Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi araç tarafından depolanan gizli dizileri hala yerel olarak depolanır ve makinede şifrelenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d79b9-104">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="d79b9-105">Gizli dizileri depolamak için daha güvenli bir seçenektir [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/), anahtarları ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.</span><span class="sxs-lookup"><span data-stu-id="d79b9-105">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="d79b9-106">Azure Key Vault'tan yapılandırma bilgilerini okumak için bir ASP.NET Core uygulaması Microsoft.Extensions.Configuration.AzureKeyVault paketi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d79b9-106">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="d79b9-107">Bir Azure Key Vault gizli diziler'ı kullanmaya başlamak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d79b9-107">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="d79b9-108">İlk olarak, bir Azure AD uygulaması kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d79b9-108">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="d79b9-109">(Anahtar kasalarına erişimi, Azure AD tarafından yönetilir.) Bu Azure Yönetim Portalı aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d79b9-109">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="d79b9-110">Alternatif olarak, bir parola veya istemci gizli dizi yerine bir sertifika kullanarak kimlik doğrulaması için uygulamanızı isterseniz kullanabileceğiniz [yeni AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d79b9-110">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="d79b9-111">Yalnızca genel anahtarınızı Azure anahtar kasası ile kaydetmek bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="d79b9-111">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="d79b9-112">(Uygulamanızın özel anahtarı kullanır.)</span><span class="sxs-lookup"><span data-stu-id="d79b9-112">(Your application will use the private key.)</span></span>

<span data-ttu-id="d79b9-113">İkinci olarak, yeni bir hizmet sorumlusu oluşturarak bir anahtar kasasına kayıtlı uygulama erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d79b9-113">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="d79b9-114">Aşağıdaki PowerShell komutlarını kullanarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d79b9-114">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="d79b9-115">Üçüncü olarak, anahtar kasası, uygulamanızın yapılandırma kaynağı olarak IConfigurationRoot örneği oluşturduğunuzda IConfigurationBuilder.AddAzureKeyVault genişletme yöntemi çağrılarak içerir.</span><span class="sxs-lookup"><span data-stu-id="d79b9-115">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="d79b9-116">AddAzureKeyVault çağırma kayıtlı olan ve önceki adımlarda anahtar kasasına erişim verilen uygulama kimliği gerektirecek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d79b9-116">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="d79b9-117">Şu anda .NET Standard ve .NET Core yapılandırma bilgileri alınırken bir Azure Key vault'tan bir istemci kimliği ve istemci gizli anahtarını kullanarak destekler.</span><span class="sxs-lookup"><span data-stu-id="d79b9-117">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="d79b9-118">.NET framework uygulamaları bir aşırı yüklemesini bir sertifika yerine istemci gizli anahtarını alır IConfigurationBuilder.AddAzureKeyVault kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d79b9-118">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="d79b9-119">Bu makalenin yazıldığı tarih itibarıyla eserleridir [sürüyor](https://github.com/aspnet/Configuration/issues/605) .NET Standard ve .NET Core aşırı yükleyen kullanılabilir olması için.</span><span class="sxs-lookup"><span data-stu-id="d79b9-119">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="d79b9-120">Bir sertifika kullanılabilir kabul eden AddAzureKeyVault aşırı kadar ASP.NET Core uygulamaları sertifika tabanlı kimlik doğrulaması ile bir Azure Key Vault açıkça bir KeyVaultClient nesne oluşturarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d79b9-120">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

<span data-ttu-id="d79b9-121">Bu örnekte, yapılandırma sağlayıcısı kaydını sonunda AddAzureKeyVault çağrısı gelir.</span><span class="sxs-lookup"><span data-stu-id="d79b9-121">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="d79b9-122">Önceki sağlayıcılarından yapılandırma değerleri geçersiz kılmak için fırsatına sahip olmasını ve böylece anahtar kasasından diğer kaynaklardan hiçbir yapılandırma değerleri geçersiz kılar son yapılandırma sağlayıcısı olarak Azure anahtar kasası kaydetmek için en iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="d79b9-122">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d79b9-123">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d79b9-123">Additional resources</span></span>

-   <span data-ttu-id="d79b9-124">**Uygulama parolalarını korumak için Azure anahtar Kasası'nı kullanma**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="d79b9-124">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="d79b9-125">**Geliştirme sırasında uygulama gizli anahtarlarının güvenli bir şekilde depolanması**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="d79b9-125">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="d79b9-126">**Veri korumayı yapılandırma**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="d79b9-126">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="d79b9-127">**Anahtar Yönetimi ve yaşam süresi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="d79b9-127">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="d79b9-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="d79b9-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="d79b9-129">GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="d79b9-129">GitHub repo.</span></span>
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="d79b9-130">[Önceki](developer-app-secrets-storage.md)
[İleri](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="d79b9-130">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
