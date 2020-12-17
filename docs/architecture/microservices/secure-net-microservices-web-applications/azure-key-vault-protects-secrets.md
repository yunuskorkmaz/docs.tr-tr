---
title: Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-Azure Key Vault, yöneticiler tarafından tamamen denetlenen uygulama gizli dizilerini işlemenin mükemmel bir yoludur. Yöneticiler, geliştiricilerin bunları işlemesi gerekmeden geliştirme değerlerini de atayabilir ve iptal edebilir.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 5d024894fe1540df04514031bf0b6e0754ddc75c
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633929"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Üretim zamanında gizli dizileri korumak için Azure Key Vault kullanma

Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi aracı tarafından depolanan gizlilikler, makinede yerel olarak ve şifrelenmemiş olarak depolanır. Gizli dizileri depolamak için daha güvenli bir seçenek [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), anahtar ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.

**Azure.Extensions.AspNetCore.Configurlama. Gizli** dizileri paketi, bir ASP.NET Core uygulamasının yapılandırma bilgilerini Azure Key Vault okumasına izin verir. Azure Key Vault gizli dizileri kullanmaya başlamak için şu adımları izleyin:

1. Uygulamanızı bir Azure AD uygulaması olarak kaydedin. (Anahtar kasalarına erişim, Azure AD tarafından yönetilmektedir.) Bu işlem, Azure yönetim portalı üzerinden yapılabilir. \

   Alternatif olarak, uygulamanızın parola veya istemci parolası yerine bir sertifika kullanarak kimlik doğrulaması yapmasını istiyorsanız, [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet 'ini kullanabilirsiniz. Azure Key Vault kayıt yaptığınız sertifikanın yalnızca ortak anahtarınız olması gerekir. Uygulamanız özel anahtarı kullanacaktır.

2. Yeni bir hizmet sorumlusu oluşturarak kayıtlı uygulamaya anahtar kasasına erişim izni verin. Bunu aşağıdaki PowerShell komutlarını kullanarak yapabilirsiniz:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Bir örnek oluştururken AzureKeyVaultConfigurationExtensions. Addadurekeykasauzantısı metodunu çağırarak, anahtar kasasını uygulamanıza bir yapılandırma kaynağı olarak ekleyin <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> .

Çağırmanın, `AddAzureKeyVault` kayıtlı ve önceki adımlarda anahtar kasasına erişim verilen uygulama kimliğini gerektirdiğini unutmayın. Ya da Azure CLı komutunu `az login` , daha sonra `AddAzureKeyVault` istemcinin yerine bir DefaultAzureCredential alan aşırı yüklemesini kullanarak çalıştırabilirsiniz.

> [!IMPORTANT]
> Azure Key Vault, önceki sağlayıcılardan yapılandırma değerlerini geçersiz kılabilmesi için son yapılandırma sağlayıcısı olarak kaydetmenizi öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Uygulama gizliliklarını korumak için Azure Key Vault kullanma** \
  [https://docs.microsoft.com/azure/architecture/multitenant-identity](/azure/architecture/multitenant-identity)

- **Geliştirme sırasında uygulama gizli dizileri için güvenli depolama** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Veri korumayı yapılandırma** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **ASP.NET Core veri koruma anahtarı yönetimi ve ömrü** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft.Extensions.Configurlama** GitHub deposu. \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration>

>[!div class="step-by-step"]
>[Önceki](developer-app-secrets-storage.md) 
> [Sonraki](../key-takeaways.md)
