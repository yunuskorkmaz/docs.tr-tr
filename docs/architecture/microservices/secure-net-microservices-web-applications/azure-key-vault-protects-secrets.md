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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma

Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi aracı tarafından depolanan gizlilikler, makinede yerel olarak ve şifrelenmemiş olarak depolanır. Gizli dizileri depolamak için daha güvenli bir seçenek [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), anahtar ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.

**Microsoft. Extensions. Configuration. AzureKeyVault** paketi, bir ASP.NET Core uygulamasının yapılandırma bilgilerini Azure Key Vault okumasına izin verir. Azure Key Vault gizli dizileri kullanmaya başlamak için şu adımları izleyin:

1. Uygulamanızı bir Azure AD uygulaması olarak kaydedin. (Anahtar kasalarına erişim, Azure AD tarafından yönetilmektedir.) Bu işlem, Azure yönetim portalı üzerinden yapılabilir. \

   Alternatif olarak, uygulamanızın parola veya istemci parolası yerine bir sertifika kullanarak kimlik doğrulaması yapmasını istiyorsanız, [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet 'ini kullanabilirsiniz. Azure Key Vault kayıt yaptığınız sertifikanın yalnızca ortak anahtarınız olması gerekir. Uygulamanız özel anahtarı kullanacaktır.

2. Yeni bir hizmet sorumlusu oluşturarak kayıtlı uygulamaya anahtar kasasına erişim izni verin. Bunu aşağıdaki PowerShell komutlarını kullanarak yapabilirsiniz:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Örnek oluştururken uzantı<xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> yöntemini çağırarak anahtar kasasını uygulamanıza bir yapılandırma kaynağı olarak dahil edin. <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> Çağırmanın `AddAzureKeyVault` , kayıtlı ve önceki adımlarda anahtar kasasına erişim verilen uygulama kimliğini gerektirdiğini unutmayın.

   Ayrıca, `AddAzureKeyVault` [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paketine bir başvuru dahil olmak üzere, istemci gizli dizisi yerine bir sertifikayı alan aşırı yüklemesini de kullanabilirsiniz.

> [!IMPORTANT]
> Azure Key Vault, önceki sağlayıcılardan yapılandırma değerlerini geçersiz kılabilmesi için son yapılandırma sağlayıcısı olarak kaydetmenizi öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Uygulama gizliliklarını korumak için Azure Key Vault kullanma** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Geliştirme sırasında uygulama gizli dizileri için güvenli depolama** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Veri korumayı yapılandırma** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **ASP.NET Core veri koruma anahtarı yönetimi ve ömrü** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft. Extensions. Configuration. KeyPerFile** GitHub deposu. \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
>[Önceki](developer-app-secrets-storage.md)İleri
>[](../key-takeaways.md)
