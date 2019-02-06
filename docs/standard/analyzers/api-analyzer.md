---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi kullanım dışı API ve platform uyumluluğu sorunları algılayın nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: d27e5299ad9b1a3dcd89d5a947d91f06a54549e2
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759138"
---
# <a name="net-api-analyzer"></a>.NET API Çözümleyicisi

.NET API Çözümleyicisi olası uyumluluk risk bulduğu Roslyn çözümleyicinizi olduğu C# farklı platformlarda API'leri ve kullanım dışı API'lere giden çağrıların algılar. Tüm kullanıcılar için yararlı olabilir C# geliştiriciler geliştirme herhangi bir aşamasında.

API Çözümleyicisi bir NuGet paketi olarak gelir [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Bir proje başvurusu sonra otomatik olarak kod izler ve sorunlu API kullanımı gösterir. Ampul üzerinde tıklayarak üzerinde olası düzeltmeleri önerileri de sahip olabilirsiniz. Aşağı açılan menüyü uyarıları bastırmak için bir seçenek içerir.

> [!NOTE]
> .NET API Çözümleyicisi hala bir yayın öncesi sürümüdür.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 veya Visual Studio için Mac (tüm sürümler).

## <a name="discovering-deprecated-apis"></a>Kullanım dışı API'lerini keşfetme

### <a name="what-are-deprecated-apis"></a>Hangi API'leri kullanım dışı?

.NET ailesi, sürekli daha iyi müşteri gereksinimlerini karşılamak için yükseltilen büyük ürünleri kümesidir. Bazı API'leri kullanımdan kaldırma ve bunları yenileriyle değiştirme doğaldır. Bir API, daha iyi bir alternatif varsa, kullanım dışı olarak kabul edilir. Bir API kullanım dışıdır ve kullanılmamalıdır bildiren bir yoludur kendisiyle işaretlemek için <xref:System.ObsoleteAttribute> özniteliği. Bu yaklaşımın bir dezavantajı, tüm eski API'ler için yalnızca bir tanılama kimliği olduğundan emin olup (için C#, [CS0612](../../csharp/misc/cs0612.md)). Bunun anlamı:
- Her çalışması için belgelerin adanmış mümkün değildir.
- Belirli kategori uyarıları bastırmak mümkün değildir. Tüm veya bunların hiçbiri gösterilmemesini sağlayabilirsiniz.
- Yeni bir kullanımdan kaldırılma kullanıcılara bildirmek için başvurulan bir derleme veya paket hedef güncelleştirilmesi gerekir.

API Çözümleyicisi, tek tek uyarılar görünümünü denetime izin veren (hangi için kullanımdan kaldırma hatası anlamına gelir) DE ile başlayan API özgü hata kodları kullanır. Kaldırılmış API'ler çözümleyici tarafından tanımlanan tanımlanan [platform/dotnet-compat](https://github.com/dotnet/platform-compat) depo.

### <a name="using-the-api-analyzer"></a>API Çözümleyicisi'ni kullanma

Kullanım dışı API, aşağıdakiler gibi <xref:System.Net.WebClient>, kullanılan bir kod içeren bir yeşil dalgalı satırı vurgular API Çözümleyicisi. API çağrılarında geldiğinizde, aşağıdaki örnekte olduğu gibi API kullanımdan kaldırma hakkında bilgi içeren bir ampul görüntülenir:

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/green-squiggle.jpg)

**Hata listesi** penceresi, aşağıdaki örnekte gösterildiği gibi uyarılarla kullanım dışı API başına benzersiz bir kimlik içerir (`DE004`): 

!["Hata listesi penceresine uyarı'nın kimlik ve açıklama gösteren ekran görüntüsü"](media/api-analyzer/warnings.jpg)

Kimliğinde tıklayarak, API'nin neden kullanım dışı bırakıldı hakkında ayrıntılı bilgi ile bir Web sayfasına gidin ve kullanılabilecek diğer API'ler ile ilgili öneriler.

Tüm uyarılar vurgulanan üyesinde sağ tıklatıp seçerek gizlenebilir **bastır \<tanılama kimliği >**. Uyarıları bastırmak için iki yolu vardır: 

* [yerel olarak (kaynak)](#suppressing-warnings-locally)
* [Genel (içinde bir gizleme dosyası)](#suppressing-warnings-globally) - önerilen

### <a name="suppressing-warnings-locally"></a>Yerel olarak uyarıları gizleme

Yerel olarak uyarıları bastırmak için için uyarıları gösterme ve ardından istediğiniz üyesinde sağ **hızlı Eylemler ve yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **kaynağındaki**. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı önişlemci yönergesi, tanımlanan kapsam içinde kaynak kodunuza eklenir: !["Kod #pragma uyarı ile Çerçeveli ekran devre dışı bırak"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Uyarıları gizleme genel

Bastırmak için uyarıları genel olarak, sağ için uyarıları gösterme ve ardından istediğiniz üyesinde **hızlı Eylemler ve yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **gizleme dosyasında**.

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/suppress-in-sup-file.jpg)

A *GlobalSuppressions.cs* sonra ilk gizleme dosyası projenize eklenir. Yeni genel gizlemeleri bu dosyasına eklenir.

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/suppression-file.jpg)

Genel gizlemeyi API kullanımı projeler arasında tutarlılığı için önerilen yoldur.

## <a name="discovering-cross-platform-issues"></a>Platformlar arası sorunları bulma

Benzer şekilde kullanımdan kaldırılan API'leri, platformlar arası olmayan tüm API'leri Çözümleyicisi tanımlar. Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows ancak Linux ve macOS üzerinde çalışır. Tanılama kimliği gösterilen **hata listesi** penceresi. Sağ tıklayarak bu uyarının gösterilmemesi tıklayıp **hızlı Eylemler ve yeniden düzenlemeler**. İki seçenek olduğu kullanımdan kaldırma çalışmaları aksine (kullanım dışı üye kullanmaya devam edebilirsiniz ve Uyarıları bastırma ya da hiç kullanmayabilirsiniz), burada yalnızca belirli platformlar için kodunuzu geliştiriyorsanız, diğer tüm platformlar için tüm uyarıları sizin gösterilmemesini sağlayabilirsiniz kodunuzu çalıştırmayı planlayın. Bunu yapmak için proje dosyanızı düzenlemeniz ve eklemeniz yeterlidir `PlatformCompatIgnore` yok sayılacak tüm platformları listeler özelliği. Kabul edilen değerler şunlardır: `Linux`, `macOS`, ve `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Kodunuzun birden çok platformu hedefleyen ve bunlardan bazıları üzerinde desteklenmeyen API yararlanmak istiyorsanız kodu ile bu bölümü önleyebilirsiniz bir `if` deyimi:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Hedef framework ve işletim sistemi da koşullu olarak derleyebilirsiniz, ancak şu anda, gerçekleştirmeniz gereken [el ile](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Desteklenen tanılama

Şu anda Çözümleyicisi aşağıdaki durumlarda işler:

* .NET Standard oluşturan API'si kullanımı <xref:System.PlatformNotSupportedException> (PC001).
* Bir .NET standart .NET Framework 4.6.1 (PC002) üzerinde bulunmayan API kullanımı.
* UWP (PC003) mevcut olmayan bir yerel API kullanımı.
* Kullanım dışı (DEXXXX) işaretlenmiş bir API kullanımı.

## <a name="ci-machine"></a>CI makine

Bu tanılama yalnızca IDE içinde kullanılabilir, ancak ayrıca CI sunucu içeren projenizi oluşturma işleminin parçası olarak komut satırında.

## <a name="configuration"></a>Yapılandırma

Kullanıcı tanılama nasıl işleneceğini karar: uyarıları, hataları, önerileri olarak ya da devre dışı. Örneğin, bir mimari, karar verebilirsiniz uyumluluk sorunları hata olarak işlem görecek, diğerleri yalnızca önerileri oluşturmak uyarıları, kullanım dışı bazı API'lere giden çağrıların oluşturmanız. Bunu ayrı olarak tanılama kimliği ve proje göre yapılandırabilirsiniz. Bu nedenle yapmak için **Çözüm Gezgini**, gitmek **bağımlılıkları** projenizi düğümünde. Düğümleri genişletin **bağımlılıkları** > **Çözümleyicileri** > **Microsoft.DotNet.Analyzers.Compatibility**. Select tanılama kimliği sağ tıklayın **kural kümesi önem derecesini ayarlayın** ve istediğiniz seçeneği belirleyin.

!["Tanılama ve açılır iletişim kutusu ile kural kümesi önem derecesi gösteren çözüm Gezgini'nin ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Ayrıca bkz.

- [API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog gönderisi.
- [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım YouTube video.
