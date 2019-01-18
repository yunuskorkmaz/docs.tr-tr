---
title: Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında depolama
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik ASP.NET Core kullanabileceğiniz seçenekler parolalar, bağlantı dizeleri veya kaynak denetimi, API anahtarlarını anlama gibi uygulama parolalarını depolamak yoksa, "kullanıcı ne yapılacağını anlamak zorunda özellikle Gizli dizileri".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361995"
---
# <a name="store-application-secrets-safely-during-development"></a>Uygulama gizli dizilerini güvenli bir şekilde geliştirme sırasında Store

Korumalı kaynakları ve diğer hizmetler ile bağlanmak için ASP.NET Core uygulamaları genelde bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgileri kullanmanız gerekir. Bu hassas bilgilerin adlı *gizli dizileri*. Gizli dizileri kaynak kodu ve gizli dizileri kaynak denetiminde depolamamayı sağlamaktan içermeyecek şekilde en iyi bir uygulamadır. Bunun yerine, gizli dizileri daha güvenli bir konumdan okunamıyor, ASP.NET Core yapılandırma modeli kullanmalısınız.

Geliştirme erişmek ve bu üretim kaynaklarına erişmek için erişim gizli dizilerinin farklı bu kümeleri için farklı kişilerin gerekeceğinden Kullanılanlar kaynaklardan hazırlama için gizli dizileri ayırmanız gerekir. Geliştirme sırasında kullanılan gizli dizileri depolamak için genel yaklaşımları ya da ortam değişkenleri içindeki veya ASP.NET Core gizli dizi Yöneticisi aracını kullanarak gizli dizileri depolamak üzeresiniz. Üretim ortamlarında daha güvenli depolama için mikro hizmetler, gizli dizileri Azure anahtar Kasası'nda depolayabilirsiniz.

## <a name="store-secrets-in-environment-variables"></a>Ortam değişkenlerini Store gizli dizileri

Gizli dizileri kaynak kodunun dışında tutmak için bir yoludur dize tabanlı gizli dizi olarak ayarlamak, geliştiriciler için [ortam değişkenlerini](/aspnet/core/security/app-secrets#environment-variables) kendi geliştirme makinelerinde. Yapılandırma bölümleri içinde iç içe geçmiş olanlar gibi hiyerarşik adları ile Parolaları depolamak için ortam değişkenlerini kullandığınızda tam iki nokta (:) ile ayrılmış alt bölümlere hiyerarşisini dahil etmek istediğiniz değişkenleri adı olmalıdır.

Örneğin, bir ortam değişkenini ayarlayarak `Logging:LogLevel:Default` için `Debug` değerini aşağıdaki JSON dosyasındaki yapılandırma değeri olarak eşdeğer olacaktır:

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

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Gizli dizileri ile ASP.NET Core gizli dizi Yöneticisi Store

ASP.NET Core [gizli dizi Yöneticisi](/aspnet/core/security/app-secrets#secret-manager) aracı, kaynak kodunun dışında gizli dizileri tutma başka bir yöntem sağlar. Gizli dizi Yöneticisi aracını kullanmak için paket yükleme **Microsoft.Extensions.Configuration.SecretManager** proje dosyanızda. Bu bağımlılık, mevcut olduğundan ve geri yüklendi, sonra `dotnet user-secrets` komutu, komut satırından gizli dizileri değerini ayarlamak için kullanılabilir. Bu gizli anahtarları (işletim sistemi tarafından Ayrıntılar değişiklik gösterir) kullanıcının profil dizini, kaynak kodu uzakta bir JSON dosyasında depolanır.

Gizli dizi Yöneticisi belirlediği gizli dizileri tarafından düzenlenir `UserSecretsId` gizli dizileri kullanarak projenin özelliği. Bu nedenle, aşağıdaki kod parçacığında gösterildiği gibi proje dosyasında UserSecretsId özelliğini ayarladığınızdan emin olmanız gerekir. Varsayılan değer, Visual Studio tarafından atanan bir GUID olmakla birlikte, bilgisayarınızın benzersiz olduğu sürece gerçek dize önemli değildir.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Gizli dizi Yöneticisi ile bir uygulama içinde depolanan gizli kullanarak gerçekleştirilir çağırarak `AddUserSecrets<T>` yapılandırmasında uygulaması için gizli dizileri içerecek şekilde ConfigurationBuilder örneğinde. Genel parametre T UserSecretId uygulandığı bir derlemeden bir tür olmalıdır. Kullanımı genellikle `AddUserSecrets<Startup>` bir sakınca yoktur.

`AddUserSecrets<Startup>()` Geliştirme ortamı için varsayılan seçenekleri kullanarak dahil `CreateDefaultBuilder` yönteminde *Program.cs*.

>[!div class="step-by-step"]
>[Önceki](authorization-net-microservices-web-applications.md)
>[İleri](azure-key-vault-protects-secrets.md)
