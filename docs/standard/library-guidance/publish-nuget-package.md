---
title: Bir NuGet Paketi Yayımlama
description: .NET kitaplıkları için NuGet yayımlamak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49337663"
---
# <a name="publishing-a-nuget-package"></a>Bir NuGet Paketi Yayımlama

NuGet paketlerini yayımlandı ve paket depolarından kullanılan. NuGet.org bilinen ve kullanılan depo en yaygın olsa da, NuGet paketlerini yayımlamak için pek çok yerde vardır:

* **[NuGet.org](https://www.nuget.org/)**  birincil çevrimiçi için NuGet paketlerini depodur. Tüm paketleri NuGet.org üzerinde herkese genel olarak kullanılabilir. Varsayılan olarak, Visual Studio Paket kaynağı olarak NuGet.org sahiptir ve birçok geliştirici için ile etkileşim kuracağınızı yalnızca paket deposu Nuget.org'nin olduğundan. NuGet.org kararlı paketler ve topluluk geri bildirimi almak istediğiniz yayın öncesi paketleri yayımlamak için en iyi yerdir.

* **[MyGet](https://myget.org/)**  depo hizmeti destekleyen [ücretsiz özel paket akışları için açık kaynaklı projelerin](https://www.myget.org/opensource). Bir MyGet genel özel akışı CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayımlamak için ideal yerdir. MyGet ayrıca özel akışları ticari olarak sağlar.

* A **[yerel akış](/nuget/hosting-packages/local-feeds)** yapar ve bir paket deposu gibi bir klasör değerlendirilecek sağlar `*.nupkg` NuGet tarafından erişilebilir klasöründe bulunan dosyaları. Yerel bir akış, bir NuGet paketi için NuGet.org yayımlamadan önce test edilmesi için yararlıdır.

> [!NOTE]
> NuGet.org [silinmesi paket izin vermiyor](/nuget/policies/deleting-packages) karşıya yüklendikten sonra. Bir paketi kullanıcı Arabiriminde herkese görünür olmaması listelenmemiş olabilir ancak `*.nupkg` geri yükleme yine de indirilebilir. Ayrıca, nuget.org yinelenen paket sürümlerini izin vermez. Bir NuGet paketi yanlış paketi listeden kaldırma için sahip olduğunuz hata gidermek için sürüm numarasını Artır ve paketin yeni bir sürüm yayımlayın.

**✔️ YAPMAK** [kararlı paketler ve yayın öncesi paketleri yayımlama](/nuget/create-packages/publish-a-package) NuGet.org açın topluluk geri bildirimi istiyor.

**✔️ DÜŞÜNÜN** sürekli tümleştirme derleme akışı için bir MyGet yayın öncesi paketleri yayımlama.

**✔️ DÜŞÜNÜN** paketleri yerel akış veya MyGet kullanarak geliştirme ortamınızda test etme. Paket çalıştığını denetleyin ardından NuGet.org için yayımlayın.

## <a name="nugetorg-security"></a>NuGet.org güvenlik

Kötü aktörleri NuGet hesabınıza erişmesine olamaz ve kitaplığınızı kötü amaçlı bir sürümünü karşıya önemlidir. Bir paketi yayımlandığında NuGet.org iki öğeli kimlik doğrulama ve e-posta bildirimleri sağlar. Üzerinde NuGet.org oturum açtıktan sonra bu özellikleri etkinleştirmek **hesap ayarları** sayfası.

![Alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet hesap güvenliği")

**✔️ YAPMAK** için NuGet oturum açmak için bir Microsoft hesabı kullanın.

**✔️ YAPMAK** NuGet erişmek için iki öğeli kimlik doğrulamasını etkinleştirin.

**✔️ YAPMAK** paketi yayımlandığında e-posta bildirimi etkinleştir.

>[!div class="step-by-step"]
[Önceki](./sourcelink.md)
[İleri](./versioning.md)
