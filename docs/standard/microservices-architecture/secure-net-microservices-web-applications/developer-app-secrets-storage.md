---
title: Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143876"
---
# <a name="storing-application-secrets-safely-during-development"></a>Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama

Korumalı kaynakları ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgileri kullanmanız gerekir. Bu hassas bilgilerin adlı *gizli dizileri*. Gizli dizileri kaynak kodunda içermeyecek şekilde ve kesinlikle gizli dizileri kaynak denetiminde depolamamayı en iyi bir yöntemdir. Bunun yerine, gizli dizileri daha güvenli bir konumdan okunamıyor, ASP.NET Core yapılandırma modeli kullanmalısınız.

Geliştirme erişmek ve bu üretim kaynaklarına erişmek için farklı kişilerin bu gizli dizileri farklı kümeleri erişmesi için kullanılan kaynaklardan hazırlama için gizli dizileri ayırmalısınız. Geliştirme sırasında kullanılan gizli dizileri depolamak için genel yaklaşımları ya da ortam değişkenleri içindeki veya ASP.NET Core gizli dizi Yöneticisi aracını kullanarak gizli dizileri depolamak üzeresiniz. Üretim ortamlarında daha güvenli depolama için mikro hizmetler, gizli dizileri Azure anahtar Kasası'nda depolayabilirsiniz.

## <a name="storing-secrets-in-environment-variables"></a>Gizli dizilerin depolanmasında ortam değişkenleri

Gizli dizileri kaynak kodunun dışında tutmak için bir yoludur dize tabanlı gizli dizi olarak ayarlamak, geliştiriciler için [ortam değişkenlerini](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerinde. Ortam değişkenlerini kullandığınızda hiyerarşik (Bu yapılandırma bölümleri içinde iç içe geçmiş) adları ile Parolaları depolamak için parolanın adının tam hiyerarşi içeren ortam değişkenleri için bir ad oluşturun, iki nokta (:) ile ayrılmış.

Örneğin, hata ayıklama için bir ortam değişkenini günlüğe kaydetme: LogLevel:Default ayarlayarak aşağıdaki JSON dosyasındaki yapılandırma değeri olarak eşdeğer olacaktır:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Bu değerler, ortam değişkenlerinden erişmek için uygulamayı yalnızca AddEnvironmentVariables üzerinde kendi ConfigurationBuilder IConfigurationRoot nesneyi diziden oluşturulurken çağırması gerekir.

Ortam değişkenleri genellikle düz metin olarak depolandığını unutmayın bir makine ya da işlem ortam değişkenleriyle tehlikedeyse, ortam değişkeni değerlerini görünür olur.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>ASP.NET Core gizli dizi Yöneticisi'ni kullanarak gizli dizilerin depolanmasında

ASP.NET Core [gizli dizi Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) aracı, kaynak kodunun dışında gizli dizileri tutma başka bir yöntem sağlar. Gizli dizi Yöneticisi aracını kullanmak için proje dosyanızda Microsoft.Extensions.SecretManager.Tools paketine araçları başvurusu (DotNetCliToolReference) içerir. Bu bağımlılık mevcut olduğundan ve geri yüklendikten sonra dotnet kullanıcı parolalarını komutu komut satırından gizli dizileri değerini ayarlamak için kullanılabilir. Bu gizli anahtarları (işletim sistemi tarafından Ayrıntılar değişiklik gösterir) kullanıcının profil dizini, kaynak kodu uzakta bir JSON dosyasında depolanır.

Gizli dizi Yöneticisi belirlediği gizli anahtarları, gizli dizileri kullanarak proje UserSecretsId özelliği tarafından düzenlenir. Bu nedenle, proje dosyanızda (aşağıdaki kod parçacığında gösterildiği gibi) UserSecretsId özelliğini ayarladığınızdan emin olmalıdır. Projesi içinde benzersiz olduğu sürece kimlik olarak kullanılan gerçek dize önemli değildir.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Gizli dizi Yöneticisi ile bir uygulama içinde depolanan gizli kullanarak gerçekleştirilir AddUserSecrets çağırarak&lt;T&gt; yapılandırmasında uygulaması için gizli dizileri içerecek şekilde ConfigurationBuilder örneğinde. Genel parametre T UserSecretId uygulandığı bir derlemeden bir tür olmalıdır. Genellikle AddUserSecrets kullanarak&lt;başlangıç&gt; bir sakınca yoktur.


>[!div class="step-by-step"]
>[Önceki](authorization-net-microservices-web-applications.md)
>[İleri](azure-key-vault-protects-secrets.md)