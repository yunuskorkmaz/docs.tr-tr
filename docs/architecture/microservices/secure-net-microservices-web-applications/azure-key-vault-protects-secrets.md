---
title: Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma
description: .NET Microservices ve Web Applications güvenlik - Azure Key Vault tamamen yöneticiler tarafından kontrol edilen uygulama sırlarını işlemek için mükemmel bir yoldur. Yöneticiler, geliştiricilerin bunları işlemek zorunda kalmadan geliştirme değerlerini atayabilir ve iptal edebilir.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: cc95d491136c945255408cec2bd49d4d6579e29a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501760"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="290a0-104">Üretim zamanında sırları korumak için Azure Anahtar Kasası'nı kullanın</span><span class="sxs-lookup"><span data-stu-id="290a0-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="290a0-105">Ortam değişkeni olarak depolanan veya Gizli Yönetici aracı tarafından depolanan sırlar hala yerel olarak depolanır ve makinede şifrelenmez.</span><span class="sxs-lookup"><span data-stu-id="290a0-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="290a0-106">Sırları depolamak için daha güvenli bir seçenek, anahtarları ve sırları saklamak için güvenli ve merkezi bir konum sağlayan [Azure Key Vault'dur.](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="290a0-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="290a0-107">**Microsoft.Extensions.Configuration.AzureKeyVault** paketi, ASP.NET Core uygulamasının Azure Key Vault'tan yapılandırma bilgilerini okumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="290a0-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="290a0-108">Azure Anahtar Kasası'nın sırlarını kullanmaya başlamak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="290a0-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="290a0-109">Uygulamanızı Azure REKLAM uygulaması olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="290a0-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="290a0-110">(Anahtar kasalarına erişim Azure AD tarafından yönetilir.) Bu işlem Azure yönetim portalı üzerinden yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="290a0-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="290a0-111">Alternatif olarak, uygulamanızın parola veya istemci sırrı yerine bir sertifika kullanarak kimlik doğrulamasını istiyorsanız, [Yeni-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet'ini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="290a0-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="290a0-112">Azure Key Vault'a kaydolduğunuz sertifikanın yalnızca ortak anahtarınız gerekir.</span><span class="sxs-lookup"><span data-stu-id="290a0-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="290a0-113">Uygulamanız özel anahtarı kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="290a0-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="290a0-114">Yeni bir hizmet ilkesi oluşturarak kayıtlı başvurunun anahtar kasasına erişimini verin.</span><span class="sxs-lookup"><span data-stu-id="290a0-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="290a0-115">Bunu aşağıdaki PowerShell komutlarını kullanarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="290a0-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="290a0-116">Bir <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> örnek oluştururken uzantı yöntemini arayarak uygulamanıza yapılandırma kaynağı olarak anahtar kasasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="290a0-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="290a0-117">Aramanın, `AddAzureKeyVault` kayıtlı olan ve önceki adımlardaki anahtar kasasına erişim sağlayan uygulama kimliğini gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="290a0-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="290a0-118">`AddAzureKeyVault` [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paketine bir başvuru ekleyerek istemci sırrı yerine sertifika alan bir sertifikanın aşırı yükünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="290a0-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="290a0-119">Önceki sağlayıcıların yapılandırma değerlerini geçersiz kılabilir, böylece Azure Key Vault'u son yapılandırma sağlayıcısı olarak kaydetmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="290a0-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="290a0-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="290a0-120">Additional resources</span></span>

- <span data-ttu-id="290a0-121">**Uygulama sırlarını korumak için Azure Anahtar Kasası'nı kullanma** </span><span class="sxs-lookup"><span data-stu-id="290a0-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="290a0-122">**Geliştirme sırasında uygulama sırlarının güvenli şekilde saklanması** </span><span class="sxs-lookup"><span data-stu-id="290a0-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="290a0-123">**Veri korumayı yapılandırma** </span><span class="sxs-lookup"><span data-stu-id="290a0-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="290a0-124">**ASP.NET Core'da Veri Koruma anahtar yönetimi ve kullanım ömrü** </span><span class="sxs-lookup"><span data-stu-id="290a0-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="290a0-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="290a0-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="290a0-126">[Önceki](developer-app-secrets-storage.md)
>[Sonraki](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="290a0-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
