---
title: Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolama
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-kaynak denetimindeki parolalar, bağlantı dizeleri veya API anahtarları gibi uygulama gizli dizilerini depolamayın, ASP.NET Core içinde kullanabileceğiniz seçenekleri anlayın, özellikle de "Kullanıcı gizli dizileri ".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296486"
---
# <a name="store-application-secrets-safely-during-development"></a>Geliştirme sırasında uygulama gizli dizilerini güvenli bir şekilde depolayın

Korunan kaynaklarla ve diğer hizmetlerle bağlantı kurmak için ASP.NET Core uygulamaların genellikle bağlantı dizelerini, parolaları veya gizli bilgiler içeren diğer kimlik bilgilerini kullanması gerekir. Bu hassas bilgi parçaları *gizli*dizileri olarak adlandırılır. Kaynak kodunda gizli dizileri içermemelidir ve kaynak denetiminde gizli dizileri depolamadığınızdan emin olmak iyi bir uygulamadır. Bunun yerine, daha güvenli konumlardan gizli dizileri okumak için ASP.NET Core yapılandırma modelini kullanmanız gerekir.

Farklı kişilerin bu farklı gizli dizi kümelerine erişmesi gerektiğinden, üretim kaynaklarına erişmek için kullanılan gizli dizileri, geliştirme ve hazırlama kaynaklarına erişmek için ayırmalısınız. Geliştirme sırasında kullanılan gizli dizileri depolamak için, yaygın yaklaşımlar ortam değişkenlerinde gizli dizileri depolamak veya ASP.NET Core gizli dizi Yöneticisi aracını kullanmaktır. Mikro hizmetler, üretim ortamlarında daha güvenli depolama için gizli dizileri bir Azure Key Vault depolayabilirler.

## <a name="store-secrets-in-environment-variables"></a>Ortam değişkenlerinde gizli dizileri depolayın

Gizli dizileri kaynak kodu dışında tutmanın bir yolu, geliştiricilerin dize tabanlı gizli dizileri geliştirme makinelerinde [ortam değişkenleri](/aspnet/core/security/app-secrets#environment-variables) olarak ayarlaması içindir. Yapılandırma bölümlerine yuvalanmış olanlar gibi hiyerarşik adlarla gizli dizileri depolamak için ortam değişkenlerini kullandığınızda, değişkenlerini, iki nokta üst üste (:)) ayrılmış olarak, bölümlerinin tamamını içerecek şekilde isimsiz olarak vermelisiniz.

Örneğin, bir ortam değişkenini `Debug` değere `Logging:LogLevel:Default` ayarlamak aşağıdaki JSON dosyasındaki bir yapılandırma değerine eşdeğerdir:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Bu değerlere ortam değişkenlerinden erişim sağlamak için, uygulamanın bir IBir Iconationroot nesnesi oluştururken ConfigurationBuilder üzerinde AddEnvironmentVariables çağırması gerekir.

Ortam değişkenlerinin yaygın olarak düz metin olarak depolandığını unutmayın. bu nedenle, ortam değişkenleri ile makine veya işlem tehlikeye girerse, ortam değişkeni değerleri görünür olur.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>ASP.NET Core gizli Yöneticisi ile gizli dizileri depolayın

ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) Aracı, kaynak kodu dışında gizli dizileri tutmanın başka bir yöntemini sağlar. Gizli dizi Yöneticisi aracını kullanmak için, proje dosyanıza **Microsoft. Extensions. Configuration. SecretManager** paketini yükle. Bu bağımlılık mevcut olduğunda ve geri yüklendikten sonra, komut satırındaki gizli dizi değerlerini ayarlamak için `dotnet user-secrets` komutu kullanılabilir. Bu gizli diziler, kullanıcının profil dizinindeki bir JSON dosyasında (Ayrıntılar işletim sistemine göre değişir) kaynak koddan uzakta saklanır.

Gizli dizi Yöneticisi aracı tarafından ayarlanan gizlilikler, parolaların kullanıldığı projenin `UserSecretsId` özelliğine göre düzenlenir. Bu nedenle, aşağıdaki kod parçacığında gösterildiği gibi, proje dosyanızda Usersecretsıd özelliğini ayarladığınızdan emin olmanız gerekir. Varsayılan değer, Visual Studio tarafından atanan bir GUID 'dir, ancak bilgisayarınızda benzersiz olduğu sürece gerçek dize önemli değildir.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Bir uygulamada gizli yönetici ile depolanan gizli dizileri kullanmak, yapılandırmasındaki uygulamanın gizli dizileri içermesi için ConfigurationBuilder örneğindeki `AddUserSecrets<T>` çağırarak gerçekleştirilir. Genel parametre T, Usersecretıd 'nin uygulandığı derlemeden bir tür olmalıdır. Genellikle `AddUserSecrets<Startup>` kullanımı iyidir.

`AddUserSecrets<Startup>()`, *program.cs*içinde `CreateDefaultBuilder` yöntemi kullanılırken geliştirme ortamı için varsayılan seçeneklere dahil edilir.

>[!div class="step-by-step"]
>[Önceki](authorization-net-microservices-web-applications.md)
>[İleri](azure-key-vault-protects-secrets.md)
