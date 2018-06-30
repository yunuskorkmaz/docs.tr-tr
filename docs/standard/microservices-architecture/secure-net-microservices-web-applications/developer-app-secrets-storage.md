---
title: Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 560120db35ae190bdef1f95d72ac1e5de697124e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105952"
---
# <a name="storing-application-secrets-safely-during-development"></a>Uygulama parolaları güvenli bir şekilde geliştirme sırasında depolama

Korumalı kaynaklar ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgilerini kullanmanız gerekir. Bu hassas bilgilerin adlı *gizli*. Bu gizli kaynak kodunda içermeyecek şekilde ve kesinlikle gizli kaynak denetiminde depolamamayı en iyi bir uygulamadır. Bunun yerine, daha güvenli konumlardan gizli anahtarları okumak için ASP.NET Core yapılandırma modeli kullanmanız gerekir.

Geliştirme erişmek ve kaynakları kullanılanlardan farklı kişilerin gizli farklı bu kümeleri erişmesi için üretim kaynaklara erişmek için hazırlama gizli ayırın. Geliştirme sırasında kullanılan parolaları depolamak için ortak yaklaşımlar ya da gizli ortam değişkenleri içindeki veya ASP.NET Core gizli Yöneticisi aracını kullanarak depolama üzeresiniz. Üretim ortamlarında daha güvenli depolama için mikro gizli bir Azure anahtar kasası depolayabilirsiniz.

## <a name="storing-secrets-in-environment-variables"></a>Gizli ortam değişkenleri depolanması

Gizli kaynak kodu dışında tutmak için bir yoldur dize tabanlı gizlilikleri olarak ayarlamak geliştiricilere [ortam değişkenleri](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerde. Ortam değişkenleri kullandığınızda hiyerarşik adları (olanlar yapılandırma bölümlerinin iç içe geçmiş) ile Parolaları depolamak için ortam değişkenleri için parolanın adının tam hiyerarşiyi içeren bir ad oluşturun, iki nokta (:) ile ayrılmış.

Örneğin, bir ortam değişkeni günlüğe kaydetme: LogLevel:Default Debug ayarı aşağıdaki JSON dosyasından bir yapılandırma değeri eşdeğer olacaktır:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Ortam değişkenlerinin bu değerleri erişmek için uygulamanın yalnızca bir IConfigurationRoot nesne oluşturulurken üzerinde kendi ConfigurationBuilder AddEnvironmentVariables çağrılacak gerekir.

Ortam değişkenleri genellikle düz metin olarak depolanır Not makine ya da ortam değişkenleri işlemine aşılıp aşılmadığını ortam değişkeni değerlerini görünür olur.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>ASP.NET Core gizli Yöneticisi'ni kullanarak gizli anahtarları depolama

ASP.NET Core [gizli Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) aracı kaynak kodu dışında gizli tutmak başka bir yöntem sağlar. Gizli Yöneticisi aracını kullanmak için proje dosyanızdaki Microsoft.Extensions.SecretManager.Tools pakete araçları başvurusu (DotNetCliToolReference) ekleyin. Bu bağımlılık var ve geri yüklendikten sonra dotnet kullanıcı parolaları komutu komut satırından gizli değerini ayarlamak için kullanılabilir. Bu gizli anahtarları (işletim sistemi tarafından ayrıntıları değişir) kullanıcının profil dizini, kaynak kodu çıktığınızda JSON dosyasında depolanır.

Gizli Manager aracısının belirlediği gizli gizli anahtarları kullanarak proje UserSecretsId özelliği tarafından düzenlenir. Bu nedenle, proje dosyası (parçacığında gösterildiği gibi) UserSecretsId özelliği ayarladığınızdan emin olmalıdır. Projesi içinde benzersiz olduğu sürece kimliği olarak kullanılan gerçek dizesi önemli değildir.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Parola Yöneticisi ile bir uygulamada depolanan parolaları kullanarak gerçekleştirilir AddUserSecrets çağırarak&lt;T&gt; yapılandırmasıyla uygulama parolaları eklemek için ConfigurationBuilder örneği. Genel parametresini T UserSecretId uygulandığı derlemesinden bir türü olmalıdır. Genellikle AddUserSecrets kullanarak&lt;başlangıç&gt; uygundur.


>[!div class="step-by-step"]
[Önceki](authorization-net-microservices-web-applications.md)
[sonraki](azure-key-vault-protects-secrets.md)
