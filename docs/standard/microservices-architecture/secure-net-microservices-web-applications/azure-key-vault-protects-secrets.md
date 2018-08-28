---
title: Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 84e016e4620b73444f800b02076489012ea5e844
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001446"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Üretim zamanında gizli dizileri korumak için Azure anahtar Kasası'nı kullanma

Ortam değişkenleri olarak depolanan veya gizli dizi Yöneticisi araç tarafından depolanan gizli dizileri hala yerel olarak depolanır ve makinede şifrelenmemiş. Gizli dizileri depolamak için daha güvenli bir seçenektir [Azure anahtar kasası](https://azure.microsoft.com/services/key-vault/), anahtarları ve gizli dizileri depolamak için güvenli, merkezi bir konum sağlar.

Azure Key Vault'tan yapılandırma bilgilerini okumak için bir ASP.NET Core uygulaması Microsoft.Extensions.Configuration.AzureKeyVault paketi sağlar. Bir Azure Key Vault gizli diziler'ı kullanmaya başlamak için aşağıdaki adımları izleyin:

İlk olarak, bir Azure AD uygulaması kaydedin. (Anahtar kasalarına erişimi, Azure AD tarafından yönetilir.) Bu Azure Yönetim Portalı aracılığıyla yapılabilir.

Alternatif olarak, bir parola veya istemci gizli dizi yerine bir sertifika kullanarak kimlik doğrulaması için uygulamanızı isterseniz kullanabileceğiniz [yeni AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet'i. Yalnızca genel anahtarınızı Azure anahtar kasası ile kaydetmek bir sertifika gerekir. (Uygulamanızın özel anahtarı kullanır.)

İkinci olarak, yeni bir hizmet sorumlusu oluşturarak bir anahtar kasasına kayıtlı uygulama erişimi sağlar. Aşağıdaki PowerShell komutlarını kullanarak bunu yapabilirsiniz:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Üçüncü olarak, anahtar kasası, uygulamanızın yapılandırma kaynağı olarak IConfigurationRoot örneği oluşturduğunuzda IConfigurationBuilder.AddAzureKeyVault genişletme yöntemi çağrılarak içerir. AddAzureKeyVault çağırma kayıtlı olan ve önceki adımlarda anahtar kasasına erişim verilen uygulama kimliği gerektirecek unutmayın.

  Şu anda .NET Standard ve .NET Core yapılandırma bilgileri alınırken bir Azure Key vault'tan bir istemci kimliği ve istemci gizli anahtarını kullanarak destekler. .NET framework uygulamaları bir aşırı yüklemesini bir sertifika yerine istemci gizli anahtarını alır IConfigurationBuilder.AddAzureKeyVault kullanabilirsiniz. Bu makalenin yazıldığı tarih itibarıyla eserleridir [sürüyor](https://github.com/aspnet/Configuration/issues/605) .NET Standard ve .NET Core aşırı yükleyen kullanılabilir olması için. Bir sertifika kullanılabilir kabul eden AddAzureKeyVault aşırı kadar ASP.NET Core uygulamaları sertifika tabanlı kimlik doğrulaması ile bir Azure Key Vault açıkça bir KeyVaultClient nesne oluşturarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:

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

Bu örnekte, yapılandırma sağlayıcısı kaydını sonunda AddAzureKeyVault çağrısı gelir. Önceki sağlayıcılarından yapılandırma değerleri geçersiz kılmak için fırsatına sahip olmasını ve böylece anahtar kasasından diğer kaynaklardan hiçbir yapılandırma değerleri geçersiz kılar son yapılandırma sağlayıcısı olarak Azure anahtar kasası kaydetmek için en iyi bir uygulamadır.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Uygulama parolalarını korumak için Azure anahtar Kasası'nı kullanma**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Geliştirme sırasında uygulama gizli anahtarlarının güvenli bir şekilde depolanması**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Veri korumayı yapılandırma**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Anahtar Yönetimi ve yaşam süresi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** GitHub deposu.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Önceki](developer-app-secrets-storage.md)
[İleri](../key-takeaways.md)
