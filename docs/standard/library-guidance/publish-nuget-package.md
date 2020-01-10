---
title: NuGet paketi yayımlama
description: NuGet 'e .NET kitaplıklarını yayımlamaya yönelik en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706471"
---
# <a name="publishing-a-nuget-package"></a>NuGet paketi yayımlama

NuGet paketleri, paket depolarından yayımlanır ve kullanılır. NuGet.org, en yaygın olarak bilinen ve kullanılan depoken, NuGet paketlerini yayımlamak için birçok yer vardır:

* **[NuGet.org](https://www.nuget.org/)** , NuGet paketleri için birincil çevrimiçi depodur. NuGet.org üzerindeki tüm paketler herkese açık olarak herkes tarafından kullanılabilir. Varsayılan olarak, Visual Studio 'nun bir paket kaynağı olarak NuGet.org vardır ve birçok geliştirici NuGet.org, etkileşime gitireceğiz tek paket deposudur. NuGet.org, topluluk geri bildirimi sağlamak istediğiniz kararlı paketleri ve yayın öncesi paketleri yayımlamak için en iyi yerdir.

* **[Myget](https://myget.org/)** , açık kaynaklı projeler için özel paket akışlarını destekleyen bir depo hizmetidir. Bir MyGet genel özel akışı, CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayımlamak için ideal bir yerdir. MyGet ayrıca ticari olarak özel akışlar sağlar.

* **[Yerel akış](/nuget/hosting-packages/local-feeds)** , bir klasörü paket deposu gibi davranmanıza ve `*.nupkg` dosyalarını NuGet tarafından erişilebilir hale getirir. Yerel akış, NuGet.org 'de yayımlamadan önce bir NuGet paketini test etmek için kullanışlıdır.

> [!NOTE]
> NuGet.org, bir paketin karşıya yüklendikten sonra [silinmesine izin vermez](/nuget/policies/deleting-packages) . Bir paket, Kullanıcı arabiriminde herkese açık olmayan ancak `*.nupkg` hala geri yükleme sırasında indirilebilecek şekilde listelenmemiş şekilde görünmeyebilir. Ayrıca, nuget.org yinelenen paket sürümlerine izin vermez. Bir NuGet paketini hata ile düzeltmek için yanlış paketi listelemeyi, sürüm numarasını artırmanız ve paketin yeni bir sürümünü yayımlamanız gerekir.

**✔️** , topluluk geri bildirimini NuGet.org 'e göndermek istediğiniz [kararlı paketleri ve yayın öncesi paketleri yayımlayın](/nuget/create-packages/publish-a-package) .

**✔️** yayın öncesi paketleri sürekli tümleştirme derlemesinden bir myget akışına yayımlamayı düşünün.

**✔️** yerel bir akış veya myget kullanarak geliştirme ortamınızda paketleri test etmeyi düşünün. Paketin çalıştığından emin olun ve NuGet.org 'de yayımlayın.

## <a name="nugetorg-security"></a>NuGet.org güvenliği

Kötü aktörlerin NuGet hesabınıza erişebilmeleri ve kitaplığınızın kötü amaçlı bir sürümünü karşıya yüklemesi önemlidir. NuGet.org, bir paket yayımlandığında iki öğeli kimlik doğrulaması ve e-posta bildirimleri sunar. **Hesap ayarları** sayfasında NuGet.org ' da oturum açtıktan sonra bu özellikleri etkinleştirin.

![alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet hesap güvenliği")

**✔️** NuGet 'de oturum açmak için Microsoft hesabı kullanın.

NuGet 'e erişmek için iki öğeli kimlik doğrulamayı etkinleştirme **✔️** .

bir paket yayımlandığında e-posta bildirimini etkinleştir **✔️** .

>[!div class="step-by-step"]
>[Önceki](sourcelink.md)
>[İleri](versioning.md)
