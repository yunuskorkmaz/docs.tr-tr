---
title: Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma
description: .NET mikro Hizmetleri ve Web uygulamaları - Azure Key Vault güvenlik tamamen yöneticiler tarafından denetlenen bir uygulama gizli dizilerini işlemek için mükemmel bir yoldur. Yöneticiler, bile atayın ve geliştirme değerleri geliştiricileri kendilerini işlemek zorunda iptal edebilir.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fd2bff04e06bf0561ee0c95d87978f834f192172
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664048"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Üretim zamanında gizli dizileri korumak için Azure Key Vault'u kullanma

Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi araç tarafından depolanan gizli dizileri hala yerel olarak depolanır ve makinede şifrelenmemiş. Gizli dizileri depolamak için daha güvenli bir seçenektir [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/), anahtarları ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.

**Microsoft.Extensions.Configuration.AzureKeyVault** paket, Azure Key Vault'tan yapılandırma bilgilerini okumak için bir ASP.NET Core uygulaması sağlar. Bir Azure Key Vault gizli diziler'ı kullanmaya başlamak için aşağıdaki adımları izleyin:

1. Uygulamanızı bir Azure AD uygulaması kaydedin. (Anahtar kasalarına erişimi, Azure AD tarafından yönetilir.) Bu Azure Yönetim Portalı aracılığıyla yapılabilir. \

   Alternatif olarak, bir parola veya istemci gizli dizi yerine bir sertifika kullanarak kimlik doğrulaması için uygulamanızı isterseniz kullanabileceğiniz [yeni AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet'i. Yalnızca genel anahtarınızı Azure anahtar kasası ile kaydetmek bir sertifika gerekir. (Uygulamanızın özel anahtarı kullanır.)

2. Kayıtlı uygulama erişimi, anahtar Kasası'na yeni hizmet sorumlusu oluşturma tarafından sağlar. Aşağıdaki PowerShell komutlarını kullanarak bunu yapabilirsiniz:

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Anahtar kasası, uygulamanızın yapılandırma kaynağı olarak çağırarak dahil <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> oluşturduğunuzda genişletme yöntemi bir <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> örneği. Çağırmanın Not `AddAzureKeyVault` kayıtlı olan ve önceki adımlarda anahtar kasasına erişim verilen uygulama Kimliğini gerektirir.

   Bir aşırı yüklemesini kullanabilirsiniz `AddAzureKeyVault` başvuru dahil ederek bir sertifika yerine gizli alan [Microsoft.IdentityModel.Clients.activedirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paket.

> [!IMPORTANT]
> Önceki sağlayıcılarından yapılandırma değerleri geçersiz kılmak için son yapılandırma sağlayıcısı Azure anahtar kasası kaydetmenizi öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Uygulama parolalarını korumak için Azure anahtar Kasası'nı kullanma** \
  [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Geliştirme sırasında uygulama gizli anahtarlarının güvenli bir şekilde depolanması** \
  [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](/aspnet/core/security/app-secrets)

- **Veri korumayı yapılandırma** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](/aspnet/core/security/data-protection/configuration/overview)

- **Veri koruma anahtar yönetimi ve ASP.NET Core yaşam süresi** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings*](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft.Extensions.Configuration.KeyPerFile** GitHub deposu. \
  [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
>[Önceki](developer-app-secrets-storage.md)
>[İleri](../key-takeaways.md)
