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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Üretim zamanında sırları korumak için Azure Anahtar Kasası'nı kullanın

Ortam değişkeni olarak depolanan veya Gizli Yönetici aracı tarafından depolanan sırlar hala yerel olarak depolanır ve makinede şifrelenmez. Sırları depolamak için daha güvenli bir seçenek, anahtarları ve sırları saklamak için güvenli ve merkezi bir konum sağlayan [Azure Key Vault'dur.](https://azure.microsoft.com/services/key-vault/)

**Microsoft.Extensions.Configuration.AzureKeyVault** paketi, ASP.NET Core uygulamasının Azure Key Vault'tan yapılandırma bilgilerini okumasına olanak tanır. Azure Anahtar Kasası'nın sırlarını kullanmaya başlamak için aşağıdaki adımları izleyin:

1. Uygulamanızı Azure REKLAM uygulaması olarak kaydedin. (Anahtar kasalarına erişim Azure AD tarafından yönetilir.) Bu işlem Azure yönetim portalı üzerinden yapılabilir.\

   Alternatif olarak, uygulamanızın parola veya istemci sırrı yerine bir sertifika kullanarak kimlik doğrulamasını istiyorsanız, [Yeni-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet'ini kullanabilirsiniz. Azure Key Vault'a kaydolduğunuz sertifikanın yalnızca ortak anahtarınız gerekir. Uygulamanız özel anahtarı kullanacaktır.

2. Yeni bir hizmet ilkesi oluşturarak kayıtlı başvurunun anahtar kasasına erişimini verin. Bunu aşağıdaki PowerShell komutlarını kullanarak yapabilirsiniz:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Bir <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> örnek oluştururken uzantı yöntemini arayarak uygulamanıza yapılandırma kaynağı olarak anahtar kasasını ekleyin. Aramanın, `AddAzureKeyVault` kayıtlı olan ve önceki adımlardaki anahtar kasasına erişim sağlayan uygulama kimliğini gerektirdiğini unutmayın.

   `AddAzureKeyVault` [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) paketine bir başvuru ekleyerek istemci sırrı yerine sertifika alan bir sertifikanın aşırı yükünü de kullanabilirsiniz.

> [!IMPORTANT]
> Önceki sağlayıcıların yapılandırma değerlerini geçersiz kılabilir, böylece Azure Key Vault'u son yapılandırma sağlayıcısı olarak kaydetmenizi öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Uygulama sırlarını korumak için Azure Anahtar Kasası'nı kullanma** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Geliştirme sırasında uygulama sırlarının güvenli şekilde saklanması** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Veri korumayı yapılandırma** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **ASP.NET Core'da Veri Koruma anahtar yönetimi ve kullanım ömrü** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft.Extensions.Configuration.KeyPerFile** GitHub deposu. \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
>[Önceki](developer-app-secrets-storage.md)
>[Sonraki](../key-takeaways.md)
