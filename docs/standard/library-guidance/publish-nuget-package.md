---
title: NuGet paketini yayımlama
description: .NET kitaplıklarını NuGet'e yayınlamak için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744558"
---
# <a name="publishing-a-nuget-package"></a>NuGet paketini yayımlama

NuGet paketleri paket depolarından yayınlanır ve tüketilir. NuGet.org en yaygın olarak bilinen ve kullanılan depo olmakla birlikte, NuGet paketlerini yayınlamak için birçok yer vardır:

* **[NuGet.org](https://www.nuget.org/)** NuGet paketleri için birincil çevrimiçi depodur. NuGet.org tüm paketler herkese açıktır. Varsayılan olarak, Visual Studio bir paket kaynağı olarak NuGet.org ve birçok geliştirici için NuGet.org etkileşim edeceğiz tek paket deposudur. NuGet.org, topluluk geri bildirimi istediğiniz kararlı paketleri ve yayın öncesi paketleri yayınlamak için en iyi yerdir.

* **[MyGet,](https://myget.org/)** açık kaynak projeleri için özel paket akışlarını destekleyen bir depo hizmetidir. MyGet genel özel akışı, CI hizmetiniz tarafından oluşturulan yayın öncesi paketleri yayınlamak için ideal bir yerdir. MyGet ayrıca ticari olarak özel yayınlar da sağlar.

* **[Yerel özet akışı,](/nuget/hosting-packages/local-feeds)** bir klasörü paket deposu gibi ele `*.nupkg` almanıza olanak tanır ve klasördeki dosyaları NuGet tarafından erişilebilir hale getirir. Yerel özet akışı, nuget paketini NuGet.org yayınlamadan önce sınamak için yararlıdır.

> [!NOTE]
> NuGet.org bir paketin yüklendikten sonra [silinmesine izin vermez.](/nuget/policies/deleting-packages) Bir paket, UI'de herkese açık olarak görülmeyecek, `*.nupkg` ancak yine de geri yüklenebilecek şekilde liste dışı tutulabilir. Ayrıca, nuget.org yinelenen paket sürümlerine izin vermez. NuGet paketini bir hatayla düzeltmek için yanlış paketin listesini iptal etmeniz, sürüm numarasını artımve paketin yeni bir sürümünü yayınlamanız gerekir.

do ✔️, topluluk geri bildiriminin NuGet.org için olmasını istediğiniz [kararlı paketleri ve yayın öncesi paketleri yayımlar.](/nuget/create-packages/publish-a-package)

✔️, sürekli bir tümleştirme yapısından MyGet akışına yayın öncesi paketleri yayınlamayı düşünün.

✔️ yerel bir özet akışı veya MyGet kullanarak geliştirme ortamınızdaki paketleri test etmeyi düşünün. Paket çalışmalarını denetleyin ve ardından NuGet.org yayınlayın.

## <a name="nugetorg-security"></a>NuGet.org güvenliği

Kötü aktörlerin NuGet hesabınıza erişememesi ve kitaplığınızın kötü amaçlı bir sürümünü yükleyemesi önemlidir. NuGet.org, paket yayımlandığında iki faktörlü kimlik doğrulama ve e-posta bildirimleri sunar. **Hesap ayarları** sayfasında NuGet.org giriş yaptıktan sonra bu özellikleri etkinleştirin.

![alternatif metin](./media/publish-nuget-package/nuget-2fa.png "NuGet Hesap Güvenliği")

✔️ Do NuGet oturum için bir Microsoft hesabı kullanın.

✔️ DO NuGet erişmek için iki faktörlü kimlik doğrulama etkinleştirin.

✔️ bir paket yayımlandığında e-posta bildirimini etkinleştirin.

>[!div class="step-by-step"]
>[Önceki](sourcelink.md)
>[Sonraki](versioning.md)
