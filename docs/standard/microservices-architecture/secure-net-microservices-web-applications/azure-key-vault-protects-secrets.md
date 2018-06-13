---
title: Gizli üretim aynı anda korumak için Azure anahtar kasası kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Gizli üretim aynı anda korumak için Azure anahtar kasası kullanma
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5ad5686909c29eba5916cbcc4b7115a16108a004
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580409"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Gizli üretim aynı anda korumak için Azure anahtar kasası kullanma

Ortam değişkenleri olarak depolanır veya gizli anahtarı Yöneticisi aracı tarafından depolanan gizli hala yerel olarak depolanan ve makinede şifrelenmemiş. Parolaları depolamak için daha güvenli bir seçenektir; [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/), anahtarları ve parolaları saklamak için güvenli, merkezi bir konum sağlar.

Azure anahtar Kasası'nı yapılandırma bilgilerini okumak bir ASP.NET Core uygulama Microsoft.Extensions.Configuration.AzureKeyVault paketi sağlar. Gizli anahtarları Azure anahtar Kasası'ndan kullanmaya başlamak için aşağıdaki adımları izleyin:

İlk olarak, uygulamanızı Azure AD uygulaması kaydedin. (Anahtar kasalarını erişimi Azure AD tarafından yönetilir.) Bu, Azure Yönetim Portalı aracılığıyla yapılabilir.

Alternatif olarak, bir parola veya istemci gizli anahtarı yerine bir sertifika kullanarak kimlik doğrulaması için uygulamanızın istiyorsanız kullanabileceğiniz [yeni AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet'i. Azure anahtar kasası ile kaydettiğiniz sertifika, ortak anahtar gerekir. (Uygulamanızın özel anahtarı kullanır.)

İkinci olarak, yeni bir hizmet sorumlusu oluşturarak anahtar Kasası'na kayıtlı uygulama erişimi verin. Aşağıdaki PowerShell komutlarını kullanarak bunu yapabilirsiniz:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Üçüncü anahtar kasası, uygulamanızda yapılandırma kaynağı olarak bir IConfigurationRoot örneği oluşturduğunuzda IConfigurationBuilder.AddAzureKeyVault genişletme yöntemi çağrılarak içerir. AddAzureKeyVault çağrılırken, kayıtlı ve önceki adımları anahtar kasasına erişim verilen uygulama kimliği gerektirecektir unutmayın.

  Şu anda .NET standart ve .NET Core Azure anahtar Kasası'ndan yapılandırma bilgileri alınırken bir istemci kimliği ve istemci gizli anahtarı kullanarak destekler. .NET framework uygulamaları bir aşırı yüklemesini bir sertifika istemci gizli anahtarı yerine geçen IConfigurationBuilder.AddAzureKeyVault kullanabilirsiniz. Bu makalenin yazıldığı sırada iştir [devam eden](https://github.com/aspnet/Configuration/issues/605) Bu aşırı .NET standart ve .NET Core yapmak için. Bir sertifika kullanılabilir kabul AddAzureKeyVault aşırı kadar ASP.NET Core uygulamaları bir Azure anahtar kasası sertifika tabanlı kimlik doğrulaması ile açıkça bir KeyVaultClient nesnesi oluşturarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:

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

Bu örnekte, yapılandırma sağlayıcısı kaydını sonunda AddAzureKeyVault çağrısı gelir. Azure anahtar kasası önceki sağlayıcılardan yapılandırma değerleri geçersiz kılmak fırsatına sahip olması ve böylece hiçbir yapılandırma değerlerini diğer kaynaklardan anahtar Kasası'ndan geçersiz kılabilir son yapılandırma sağlayıcısı olarak kaydetmek için en iyi bir uygulamadır.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Uygulama parolaları korumak için Azure anahtar kasası kullanma**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Geliştirme sırasında uygulama sırrı güvenli depolama**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Veri korumasını yapılandırma**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Anahtar Yönetimi ve yaşam süresi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#veri koruması varsayılan ayarları*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** GitHub depo.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Önceki] (Geliştirici-app-gizli-storage.md) [sonraki] (.. / anahtar takeaways.md)
