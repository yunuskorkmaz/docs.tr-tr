---
title: ".NET API Çözümleyicisi"
description: ".NET API Çözümleyicisi kullanım dışı API ve platform uyumluluğu sorunları algılamak nasıl yardımcı olabileceğini öğrenin."
author: oliag
ms.author: mairaw
ms.date: 01/30/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 81ab7e32b2af6048d822243226f1054ebd1ca419
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="net-api-analyzer"></a>.NET API Çözümleyicisi

.NET API Çözümleyicisi olası uyumluluk için C# API'leri farklı platformlarda risklerini ve kullanım dışı API çağrıları algılar bulur Roslyn Çözümleyicisi ' dir. Bu geliştirme herhangi bir aşamasında tüm C# geliştiricileri için faydalı olabilir.

API Çözümleyicisi bir NuGet paketi olarak gelir [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Projede başvuru sonra otomatik olarak kod izler ve sorunlu API kullanımı gösterir. Ampul üzerinde tıklayarak olası düzeltmeler hakkında öneriler de alabilirsiniz. Aşağı açılan menüden uyarıları gizlemek için bir seçenek içerir.

> [!NOTE]
> .NET API Çözümleyicisi hala bir yayın öncesi sürümüdür.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 veya Mac (tüm sürümler) için Visual Studio.

## <a name="discovering-deprecated-apis"></a>Kullanım dışı API'leri keşfetme

### <a name="what-are-deprecated-apis"></a>Hangi API'leri kullanım?

.NET ailesi, müşteri gereksinimlerini daha iyi karşılamak için sürekli olarak yükseltme büyük ürünleri kümesidir. Bazı API'leri Kaldır ve yenileriyle değiştirme için doğal. Bir API daha iyi bir alternatif mevcut olduğunda kullanım dışı olarak kabul edilir. Bir API kullanım dışıdır ve kullanılmaması bilgilendirmek için bir yoldur ile işaretlemek için <xref:System.ObsoleteAttribute> özniteliği. Bu yaklaşımın bir dezavantajı tüm eski API'leri için yalnızca bir tanılama kimliği olmasıdır (C# ' ta, [CS0612](../../csharp/misc/cs0612.md)). Bunun anlamı:
- Belgeleri her örneği için ayrılmış mümkün değildir.
- Belirli kategorisini uyarıları gizlemek mümkün değildir. Tüm ya da bunların hiçbiri gizleyebilirsiniz.
- Yeni bir kullanımdan kaldırma kullanıcıları bilgilendirmek için başvurulan bir derleme veya paket hedefleme güncelleştirilmesi gerekir.

API Çözümleyicisi bireysel uyarılar görünümünü denetime izin veren (hangi kullanımdan kaldırma hatası için anlamına gelir) DE ile başlayan API özgü hata kodları kullanır. Çözümleyicisi tarafından tanımlanan kullanım dışı API'leri tanımlanan [platform/dotnet-compat](https://github.com/dotnet/platform-compat) deposu.

### <a name="using-the-api-analyzer"></a>API Çözümleyicisi'ni kullanma

Kullanım dışı bir API, gibi <xref:System.Net.WebClient>, kullanılan bir kod yeşil dalgalı çizgi ile vurgular API Çözümleyicisi. Üzerinden API çağrısı geldiğinizde, bir ampul API kullanımdan aşağıdaki örnekteki gibi bilgiler görüntülenir:

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/green-squiggle.jpg)

**Hata listesi** penceresi, aşağıdaki örnekte gösterildiği gibi kullanım dışı API başına benzersiz bir kimliği uyarılarla içerir (`DE004`): 

!["Uyarı'nin kimlik ve açıklama gösteren Hata Listesi penceresi ekran görüntüsü"](media/api-analyzer/warnings.jpg)

Kimliği temel tıklayarak neden API kullanım dışı hakkında ayrıntılı bilgi içeren bir Web sayfası gitmeniz ve kullanılabilir alternatif API'leri ile ilgili öneriler.

Tüm uyarılar vurgulanan üyesinde sağ tıklayıp seçerek gizlenebilir **bastır \<tanılama kimliği >**. Uyarıları gizlemek için iki yolu vardır: 

* [yerel olarak (kaynak)](#suppressing-warnings-locally)
* [Genel (dosyasındaki bir gizleme)](#suppressing-warnings-globally) - önerilen

### <a name="suppressing-warnings-locally"></a>Yerel olarak uyarıları gizleme

Yerel olarak uyarıları gizlemek için için uyarıları bastırma ve ardından istediğiniz üyesinde sağ **hızlı Eylemler ve yapan yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **kaynağındaki**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) önişlemci yönergesi kaynak kodunuzda tanımlanan kapsam eklenen uyarı: !["Kod ekran Çerçeveli ile #pragma uyarısı devre dışı bırak"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Uyarıları gizleme genel

Gizlemek için uyarılar için uyarıları bastırma ve ardından istediğiniz üyesinde genel olarak, sağ **hızlı Eylemler ve yapan yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **gizleme dosyasında**.

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* dosya sonra ilk gizleme projenize eklenir. Yeni genel suppressions bu dosyaya eklenir.

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/suppression-file.jpg)

Genel gizleme, projeler arasında tutarlılığı API kullanımı için önerilen yoldur.

## <a name="discovering-cross-platform-issues"></a>Platformlar arası sorunları bulma

Benzer şekilde kullanım dışı API'leri, platformlar arası olmayan tüm API'leri Çözümleyicisi tanımlar. Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows ancak Linux ve macOS çalışır. Tanılama kimliği gösterilen **hata listesi** penceresi. Sağ tıklayarak bu uyarı gizleyebilirsiniz ve seçerek **hızlı Eylemler ve yapan yeniden düzenlemeler**. Burada iki seçeneğiniz kullanımdan durumlarda aksine (kullanım dışı üye kullanmaya devam et ve Uyarıları bastırma ya da hiç kullanmayabilirsiniz), burada yalnızca belirli platformlar için kodunuzu geliştiriyorsanız, diğer tüm platformlar için tüm uyarıları sizin gizleyebilirsiniz kodunuzu çalıştırmayı planlayın. Bunu yapmak için proje dosyanızı düzenleyin ve eklemek yeterlidir `PlatformCompatIgnore` yok sayılacak tüm platformlar listeler özelliği. Kabul edilen değerler şunlardır: `Linux`, `MacOSX`, ve `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;MacOS</PlatformCompatIgnore>
</PropertyGroup>
```

Kodunuzu birden çok platformu hedefleyen ve bunların bazıları üzerinde desteklenmeyen bir API yararlanmak isterseniz koduyla kısmı önleyebilirsiniz bir `if` deyimi:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Hedef framework ve işletim sistemi ayrıca koşullu derleyebilir, ancak şu anda, gerçekleştirmeniz gereken [el ile](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Desteklenen tanılama

Şu anda Çözümleyicisi aşağıdaki durumlarda işler:

* Bir .NET standart oluşturur API kullanımı <xref:System.PlatformNotSupportedException> (PC001).
* Bir .NET standart .NET Framework 4.6.1 (PC002) kullanılabilir olmayan API kullanımı.
* UWP (PC003) mevcut olmayan yerel bir API kullanımı.
* Kullanım dışı (DEXXXX) işaretlenmiş bir API kullanımı.

## <a name="ci-machine"></a>CI makine

Bu tanılama yalnızca IDE'de kullanılabilir, ancak ayrıca projenizi oluşturmanın bir parçası olarak komut satırında, CI sunucunun içerir.

## <a name="configuration"></a>Yapılandırma

Tanılama nasıl değerlendirilmelidir kullanıcı karar: uyarılar, hatalar, öneriler olarak ya da devre dışı bırakılmış. Örneğin, bir mimari, karar verebilirsiniz uyumluluk sorunları hata olarak ele alınması gerektiğini, diğerleri yalnızca önerileri oluşturmak karşın bazı kullanım dışı API çağrıları uyarılar oluşturun. Bunu ayrı olarak tanılama kimliği ve proje tarafından yapılandırabilirsiniz. Bu nedenle yapmak için **Çözüm Gezgini**, gitmek **bağımlılıkları** projenizi düğümünde. Düğümleri genişletin **bağımlılıkları** > **çözümleyiciler** > **Microsoft.DotNet.Analyzers.Compatibility**. Select tanılama kimliği sağ tıklayın **kural kümesi önem derecesi ayarlanmıştır** ve istediğiniz seçeneği seçin.

!["Tanılama ve açılan iletişim kuralı önem derecesi ayarlanmıştır gösteren çözüm Gezgini'nin ekran"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Ayrıca bkz.

* [API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog postası.
* [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) gösteri video YouTube'da.
