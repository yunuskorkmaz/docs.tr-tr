---
title: Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-Azure Key Vault, yöneticiler tarafından tamamen denetlenen uygulama gizli dizilerini işlemenin mükemmel bir yoludur. Yöneticiler, geliştiricilerin bunları işlemesi gerekmeden geliştirme değerlerini de atayabilir ve iptal edebilir.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296480"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="93688-104">Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma</span><span class="sxs-lookup"><span data-stu-id="93688-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="93688-105">Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi aracı tarafından depolanan gizlilikler, makinede yerel olarak ve şifrelenmemiş olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="93688-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="93688-106">Gizli dizileri depolamak için daha güvenli bir seçenek [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), anahtar ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.</span><span class="sxs-lookup"><span data-stu-id="93688-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="93688-107">**Microsoft. Extensions. Configuration. AzureKeyVault** paketi, bir ASP.NET Core uygulamasının yapılandırma bilgilerini Azure Key Vault okumasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="93688-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="93688-108">Azure Key Vault gizli dizileri kullanmaya başlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="93688-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="93688-109">Uygulamanızı bir Azure AD uygulaması olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="93688-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="93688-110">(Anahtar kasalarına erişim, Azure AD tarafından yönetilmektedir.) Bu işlem, Azure yönetim portalı üzerinden yapılabilir. </span><span class="sxs-lookup"><span data-stu-id="93688-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="93688-111">Alternatif olarak, uygulamanızın parola veya istemci parolası yerine bir sertifika kullanarak kimlik doğrulaması yapmasını istiyorsanız, [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet 'ini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93688-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="93688-112">Azure Key Vault kayıt yaptığınız sertifikanın yalnızca ortak anahtarınız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="93688-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="93688-113">Uygulamanız özel anahtarı kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="93688-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="93688-114">Yeni bir hizmet sorumlusu oluşturarak kayıtlı uygulamaya anahtar kasasına erişim izni verin.</span><span class="sxs-lookup"><span data-stu-id="93688-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="93688-115">Bunu aşağıdaki PowerShell komutlarını kullanarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93688-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="93688-116">Örnek oluştururken uzantı<xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> yöntemini çağırarak anahtar kasasını uygulamanıza bir yapılandırma kaynağı olarak dahil edin. <xref:Microsoft.Extensions.Configuration.IConfigurationRoot></span><span class="sxs-lookup"><span data-stu-id="93688-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="93688-117">Çağırmanın `AddAzureKeyVault` , kayıtlı ve önceki adımlarda anahtar kasasına erişim verilen uygulama kimliğini gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="93688-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="93688-118">Ayrıca, `AddAzureKeyVault` [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paketine bir başvuru dahil olmak üzere, istemci gizli dizisi yerine bir sertifikayı alan aşırı yüklemesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93688-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93688-119">Azure Key Vault, önceki sağlayıcılardan yapılandırma değerlerini geçersiz kılabilmesi için son yapılandırma sağlayıcısı olarak kaydetmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="93688-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="93688-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="93688-120">Additional resources</span></span>

- <span data-ttu-id="93688-121">**Uygulama gizliliklarını korumak için Azure Key Vault kullanma** </span><span class="sxs-lookup"><span data-stu-id="93688-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="93688-122">**Geliştirme sırasında uygulama gizli dizileri için güvenli depolama** </span><span class="sxs-lookup"><span data-stu-id="93688-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="93688-123">**Veri korumayı yapılandırma** </span><span class="sxs-lookup"><span data-stu-id="93688-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="93688-124">**ASP.NET Core veri koruma anahtarı yönetimi ve ömrü** </span><span class="sxs-lookup"><span data-stu-id="93688-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="93688-125">**Microsoft. Extensions. Configuration. KeyPerFile** GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="93688-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="93688-126">[Önceki](developer-app-secrets-storage.md)İleri
>[](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="93688-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
