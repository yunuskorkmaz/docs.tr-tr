---
title: Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma
description: .NET mikro Hizmetleri ve Web uygulamaları - Azure Key Vault güvenlik tamamen yöneticiler tarafından denetlenen bir uygulama gizli dizilerini işlemek için mükemmel bir yoldur. Yöneticiler, bile atayın ve geliştirme değerleri geliştiricileri kendilerini işlemek zorunda iptal edebilir.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019548"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="a02f0-104">Üretim zamanında gizli dizileri korumak için Azure Key Vault'u kullanma</span><span class="sxs-lookup"><span data-stu-id="a02f0-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="a02f0-105">Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi araç tarafından depolanan gizli dizileri hala yerel olarak depolanır ve makinede şifrelenmemiş.</span><span class="sxs-lookup"><span data-stu-id="a02f0-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="a02f0-106">Gizli dizileri depolamak için daha güvenli bir seçenektir [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/), anahtarları ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.</span><span class="sxs-lookup"><span data-stu-id="a02f0-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="a02f0-107">**Microsoft.Extensions.Configuration.AzureKeyVault** paket, Azure Key Vault'tan yapılandırma bilgilerini okumak için bir ASP.NET Core uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="a02f0-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="a02f0-108">Bir Azure Key Vault gizli diziler'ı kullanmaya başlamak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a02f0-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="a02f0-109">Uygulamanızı bir Azure AD uygulaması kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a02f0-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="a02f0-110">(Anahtar kasalarına erişimi, Azure AD tarafından yönetilir.) Bu Azure Yönetim Portalı aracılığıyla yapılabilir. \\</span><span class="sxs-lookup"><span data-stu-id="a02f0-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\\</span></span>

   <span data-ttu-id="a02f0-111">Alternatif olarak, bir parola veya istemci gizli dizi yerine bir sertifika kullanarak kimlik doğrulaması için uygulamanızı isterseniz kullanabileceğiniz [yeni AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a02f0-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="a02f0-112">Yalnızca genel anahtarınızı Azure anahtar kasası ile kaydetmek bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="a02f0-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="a02f0-113">Uygulamanız, özel anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a02f0-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="a02f0-114">Kayıtlı uygulama erişimi, anahtar Kasası'na yeni hizmet sorumlusu oluşturma tarafından sağlar.</span><span class="sxs-lookup"><span data-stu-id="a02f0-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="a02f0-115">Aşağıdaki PowerShell komutlarını kullanarak bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a02f0-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="a02f0-116">Anahtar kasası, uygulamanızın yapılandırma kaynağı olarak çağırarak dahil <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> oluşturduğunuzda genişletme yöntemi bir <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> örneği.</span><span class="sxs-lookup"><span data-stu-id="a02f0-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="a02f0-117">Çağırmanın Not `AddAzureKeyVault` kayıtlı olan ve önceki adımlarda anahtar kasasına erişim verilen uygulama Kimliğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a02f0-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="a02f0-118">Bir aşırı yüklemesini kullanabilirsiniz `AddAzureKeyVault` başvuru dahil ederek bir sertifika yerine gizli alan [Microsoft.IdentityModel.Clients.activedirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paket.</span><span class="sxs-lookup"><span data-stu-id="a02f0-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a02f0-119">Önceki sağlayıcılarından yapılandırma değerleri geçersiz kılmak için son yapılandırma sağlayıcısı Azure anahtar kasası kaydetmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a02f0-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a02f0-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a02f0-120">Additional resources</span></span>

- <span data-ttu-id="a02f0-121">**Uygulama parolalarını korumak için Azure anahtar Kasası'nı kullanma** \\</span><span class="sxs-lookup"><span data-stu-id="a02f0-121">**Using Azure Key Vault to protect application secrets** \\</span></span>
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="a02f0-122">**Geliştirme sırasında uygulama gizli anahtarlarının güvenli bir şekilde depolanması** \\</span><span class="sxs-lookup"><span data-stu-id="a02f0-122">**Safe storage of app secrets during development** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="a02f0-123">**Veri korumayı yapılandırma** \\</span><span class="sxs-lookup"><span data-stu-id="a02f0-123">**Configuring data protection** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="a02f0-124">**Veri koruma anahtar yönetimi ve ASP.NET Core yaşam süresi** \\</span><span class="sxs-lookup"><span data-stu-id="a02f0-124">**Data Protection key management and lifetime in ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="a02f0-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="a02f0-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="a02f0-126">[Önceki](developer-app-secrets-storage.md)
>[İleri](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="a02f0-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
