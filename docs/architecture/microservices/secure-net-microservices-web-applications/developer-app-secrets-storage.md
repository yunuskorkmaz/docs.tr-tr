---
title: Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolama
description: .NET Microservices ve Web Applications Güvenlik - Kaynak kontrolünde şifreler, bağlantı dizeleri veya API anahtarları gibi uygulama sırlarını depolamayın, ASP.NET Core'da kullanabileceğiniz seçenekleri anlayın, özellikle "kullanıcı"yı nasıl kullanacağınızı anlamanız gerekir sırlar".
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501794"
---
# <a name="store-application-secrets-safely-during-development"></a>Geliştirme sırasında uygulama sırlarını güvenli bir şekilde saklayın

Korumalı kaynaklara ve diğer hizmetlere bağlanmak için, ASP.NET Core uygulamalarının genellikle bağlantı dizeleri, parolalar veya hassas bilgiler içeren diğer kimlik bilgilerini kullanması gerekir. Bu hassas bilgilere *sır*denir. Bu kaynak kodusırları içermemek ve kaynak denetiminde sırları depolamak için değil emin olmak için en iyi uygulamadır. Bunun yerine, daha güvenli konumlardan sırları okumak için ASP.NET Core yapılandırma modelini kullanmanız gerekir.

Farklı bireylerin bu farklı sır kümelerine erişmesi gerekeceği için, geliştirme ve evreleme kaynaklarına erişme sırlarını üretim kaynaklarına erişmek için kullanılanlardan ayırmanız gerekir. Geliştirme sırasında kullanılan sırları depolamak için, ortak yaklaşımlar ya çevre değişkenlerinde veya ASP.NET Core Secret Manager aracını kullanarak sırları depolamak içindir. Üretim ortamlarında daha güvenli depolama için, mikro hizmetler sırları Azure Anahtar Kasası'nda saklayabilir.

## <a name="store-secrets-in-environment-variables"></a>Sırları çevre değişkenlerinde depolama

Sırları kaynak kodundan uzak tutmanın bir yolu, geliştiricilerin geliştirme makinelerinde dize tabanlı sırları [ortam değişkenleri](/aspnet/core/security/app-secrets#environment-variables) olarak ayarlamalarıdır. Yapılandırma bölümlerinde iç içe olanlar gibi hiyerarşik adlarla sırları depolamak için ortam değişkenlerini kullandığınızda, değişkenleri, üst üste (:) ile sınırlandırılmış bölümlerinin tam hiyerarşisini içerecek şekilde adlandırmanız gerekir.

Örneğin, bir ortam `Logging:LogLevel:Default` değişkenini değere `Debug` ayarlamak, aşağıdaki JSON dosyasındaki yapılandırma değerine eşdeğer olacaktır:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Bu değerlere ortam değişkenlerinden erişmek için uygulamanın, bir IConfigurationRoot nesnesi inşa ederken ConfigurationBuilder'ında AddEnvironmentVariables'i araması gerekir.

Ortam değişkenlerinin genellikle düz metin olarak depolanır, bu nedenle makine veya ortam değişkenleri ile işlem tehlikeye girerse, ortam değişkendeğerleri görünür olacaktır.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>ASP.NET Core Secret Manager ile sırları saklayın

ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) aracı geliştirme **sırasında**sırları kaynak kodun dışında tutmak için başka bir yöntem sağlar. Gizli Yönetici aracını kullanmak için proje dosyanıza **Microsoft.Extensions.Configuration.SecretManager** paketini yükleyin. Bu bağımlılık mevcut ve geri yüklendikten `dotnet user-secrets` sonra, komut komut satırından sırların değerini ayarlamak için kullanılabilir. Bu sırlar, kaynak kodundan uzakta, kullanıcının profil dizinindeki (ayrıntılar işletim sistemi'ne göre değişir) bir JSON dosyasında depolanır.

Gizli Yönetici aracı tarafından belirlenen sırlar, sırları kullanan projenin `UserSecretsId` özelliği tarafından düzenlenir. Bu nedenle, aşağıdaki parçacıkta gösterildiği gibi, Proje dosyanızda UserSecretsId özelliğini ayarladığınızdan emin olmalısınız. Varsayılan değer Visual Studio tarafından atanan bir GUID'dir, ancak bilgisayarınızda benzersiz olduğu sürece gerçek dize önemli değildir.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Bir uygulamada Secret Manager ile depolanan sırları `AddUserSecrets<T>` kullanarak ConfigurationBuilder örneğini kendi yapılandırmasında uygulama için sırları eklemek için çağırarak gerçekleştirilir. Genel parametre T, UserSecretId'in uygulandığı derlemeden bir tür olmalıdır. Genellikle `AddUserSecrets<Startup>` kullanmak iyidir.

Yöntem `AddUserSecrets<Startup>()` `CreateDefaultBuilder` *Program.cs'da*yöntem kullanırken Geliştirme ortamı için varsayılan seçeneklere dahildir.

>[!div class="step-by-step"]
>[Önceki](authorization-net-microservices-web-applications.md)
>[Sonraki](azure-key-vault-protects-secrets.md)
