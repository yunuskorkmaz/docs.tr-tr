---
title: .NET API çözümleyicisi
description: .NET API Çözümleyicisinin amortismana alınan API'leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156140"
---
# <a name="net-api-analyzer"></a>.NET API çözümleyicisi

.NET API Çözümleyicisi, farklı platformlarda C# API'leri için olası uyumluluk risklerini keşfeden ve amortismana alınan API'lere yönelik çağrıları algılayan bir Roslyn çözümleyicisidir. Geliştirmenin herhangi bir aşamasında tüm C# geliştiricileri için yararlı olabilir.

API Analyzer bir NuGet paketi [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)olarak gelir. Bir projede başvuruyaptıktan sonra, kodu otomatik olarak izler ve sorunlu API kullanımını gösterir. Ayrıca ampul tıklayarak olası düzeltmeleri hakkında öneriler alabilirsiniz. Açılır menü, uyarıları bastırmak için bir seçenek içerir.

> [!NOTE]
> .NET API çözümleyicisi hala bir ön sürüm sürümüdür.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 ve sonraki sürümleri veya Mac için Visual Studio (tüm sürümler).

## <a name="discover-deprecated-apis"></a>Amortismana kılan API'leri keşfedin

### <a name="what-are-deprecated-apis"></a>Amortismana uğran API'ler nelerdir?

.NET ailesi, müşteri ihtiyaçlarına daha iyi hizmet vermek üzere sürekli olarak yükseltilen bir dizi büyük üründür. Bazı API'leri amortismana tabi tarayıp yenileriyle değiştirmek doğaldır. Daha iyi bir alternatif olduğunda API'nin amortismana ermiş olarak kabul edilir. Bir API'nin amortismana erdiğini ve kullanılmaması gerektiğini bildirmenin <xref:System.ObsoleteAttribute> bir yolu, bu özelliği öznitelikle işaretlemektir. Bu yaklaşımın dezavantajı, tüm eski API'ler için tek bir tanılama kimliği olmasıdır (C#, [CS0612](../../csharp/misc/cs0612.md)için). Bu şu anlama gelir:

- Her dava için özel belgelere sahip olmak imkansız.
- Belirli uyarı kategorilerini bastırmak imkansızdır. Hepsini ya da hiçbirini bastırabilirsin.
- Kullanıcıları yeni bir amortisman konusunda bilgilendirmek için, başvurulan bir derleme veya hedefleme paketinin güncellenmesi gerekir.

API Analyzer, tek tek uyarıların görüntülenmesi üzerinde denetim sağlayan DE (Amortisman Hatası anlamına gelir) ile başlayan API'ye özgü hata kodları kullanır. Çözümleyici tarafından tanımlanan amortismana lı API'ler [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo'da tanımlanır.

### <a name="add-the-api-analyzer-to-your-project"></a>PROJENIZE API Çözümleyicisi ekleme

1. Visual Studio'yu açın.
2. Çözümleyiciyi çalıştırmak istediğiniz projeyi açın.
3. **Solution**Explorer'da, projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin. (Bu seçenek **Proje** menüsünden de kullanılabilir.)
4. NuGet Paket Yöneticisi sekmesinde:
   1. Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.
   2. **Gözat** sekmesine gidin.
   3. **Ön sürüm ekle'yi**seçin.
   4. **Microsoft.DotNet.Analyzers.Compatibility**için arama .
   5. Listedeki paketi seçin.
   6. **Yükle** düğmesini seçin.
   7. **Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.

### <a name="use-the-api-analyzer"></a>API Çözümleyicisini Kullanma

Bir kodda , bir kodda, amortismana uygun bir API <xref:System.Net.WebClient>kullanıldığında, API Çözümleyici squiggly satırı ile vurgular. API çağrısının üzerinde gezinirken, aşağıdaki örnekte olduğu gibi, API amortismanı hakkında bilgi içeren bir ampul görüntülenir:

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/green-squiggle.jpg)

**Hata Listesi** penceresi, aşağıdaki örnekte gösterildiği gibi, amortismana alınan API`DE004`başına benzersiz bir kimlik içeren uyarılar içerir : :

!["Uyarının kimliğini ve açıklamasını gösteren Hata Listesi penceresinin ekran görüntüsü"](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren Hata Listesi penceresi.")

Kimliği tıklayarak, API'nin neden küçümsendiğini ve kullanılabilen alternatif API'lerle ilgili önerileri içeren ayrıntılı bilgileri içeren bir web sayfasına gidersiniz.

Herhangi bir uyarı, vurgulanan üyeye sağ tıklayarak ve ** \<tanıtanı Kimliğini>Bastır'ı **seçerek bastırılabilir. Uyarıları bastırmanın iki yolu vardır:

- [yerel (kaynakta)](#suppress-warnings-locally)
- [küresel olarak (bir bastırma dosyasında)](#suppress-warnings-globally) - önerilen

### <a name="suppress-warnings-locally"></a>Uyarıları yerel olarak bastırma

Uyarıları yerel olarak bastırmak için, uyarıları bastırmak istediğiniz üyeye sağ tıklayın ve ardından **Hızlı Eylemler ve Yeniden Faktörler'i** > seçin** *Tanılama Kimliği Tanılama Kimliği'ni*\< ** **Kaynak'ta**> > bastırın. [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı önişlemci yönergesi tanımlanan kapsamda kaynak ![kodunuza eklenir: "#pragma uyarı devre dışı atılabilir" ile çerçevelenmiş kodun ekran görüntüsü](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>Uyarıları genel olarak bastırma

Uyarıları genel olarak bastırmak için, uyarıları bastırmak istediğiniz üyeye sağ tıklayın ve ardından **Hızlı Eylemler ve Yeniden Faktörler** >  **bastırma dosyasında****tanılama kimliği\<>*diagnostic ID* **  > bastırın'ı seçin.

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/suppress-in-sup-file.jpg)

İlk bastırmadan sonra projenize *GlobalSuppressions.cs* bir dosya eklenir. Bu dosyaya yeni genel bastırmalar eklenir.

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/suppression-file.jpg)

Küresel bastırma, PROJELER ARASıNDA API kullanımının tutarlılığını sağlamanın önerilen yoludur.

## <a name="discover-cross-platform-issues"></a>Platformlar arası sorunları keşfedin

Amortismana yenik amorti edilen API'lere benzer şekilde, çözümleyici çapraz platform olmayan tüm API'leri tanımlar. Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows'da çalışır, ancak Linux ve macOS'ta çalışmaz. Tanılama kimliği Hata **Listesi** penceresinde gösterilir. Hızlı Eylemler ve **Yeniden Düzenleme'yi**sağ tıklayarak ve seçerek bu uyarıyı bastırabilirsiniz. İki seçeneğiniz olan (ya azalan üyeyi kullanmaya devam edin ve uyarıları bastırmaya devam edin ya da hiç kullanmadıysanız), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, olmadığınız diğer tüm platformlar için tüm uyarıları bastırabilirsiniz kodunuzu çalıştırmayı planlayın. Bunu yapmak için proje dosyanızı düzenlemesi ve göz `PlatformCompatIgnore` ardı edilecek tüm platformları listeleyen özelliği eklemeniz gerekir. Kabul edilen değerler `Linux`şunlardır: , `macOS`, ve `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API'den yararlanmak istiyorsanız, `if` kodun bu bölümünü bir deyimle koruyabilirsiniz:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Ayrıca, hedef çerçevesi/işletim sistemi başına koşullu olarak derleyebilirsiniz, ancak şu anda bunu [el ile](../frameworks.md#how-to-specify-target-frameworks)yapmanız gerekir.

## <a name="supported-diagnostics"></a>Desteklenen tanılama

Şu anda, çözümleyici aşağıdaki durumlarda işler:

- Bir .NET Standart API kullanımı <xref:System.PlatformNotSupportedException> atar (PC001).
- .NET Framework 4.6.1 (PC002) üzerinde bulunmayan bir .NET Standart API kullanımı.
- UWP(PC003) bulunmayan yerel bir API kullanımı.
- Delegate.BeginInvoke ve EndInvoke API'lerinin (PC004) kullanımı.
- Amortismana (DEXXXX) olarak işaretlenmiş bir API kullanımı.

## <a name="ci-machine"></a>CI makinesi

Tüm bu tanılama, ci sunucuyu içeren projenizi oluşturmanın bir parçası olarak yalnızca IDE'de değil, komut satırında da kullanılabilir.

## <a name="configuration"></a>Yapılandırma

Kullanıcı tanılamanın nasıl ele alınması gerektiğine karar verir: uyarılar, hatalar, öneriler veya kapatılacak gibi. Örneğin, bir mimar olarak uyumluluk sorunlarının hata olarak ele alınmasına karar verebilirsiniz, bazı amortismana alınan API'lere yapılan çağrılar uyarılar oluştururken, diğerleri yalnızca öneriler oluşturur. Bunu tanılama kimliği ve proje ile ayrı ayrı yapılandırabilirsiniz. **Çözüm Gezgini'nde**bunu yapmak için projenizaltındaki **Bağımlılıklar** düğümüne gidin. Düğümleri Genişlet **Bağımlılıklar** > **Çözümleyiciler** > **Microsoft.DotNet.Analyzers.Compatibility**. Tanılama kimliğine sağ tıklayın, **Kural Kümesi Önem Ayarını seçin** ve istediğiniz seçeneği seçin.

!["Çözüm Gezgini'nin Kural Kümesi Önem Derecesi ile tanılama ve açılır iletişim kutusunu gösteren ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Ayrıca bkz.

- [API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog yazısı tanıtımı.
- [YouTube'da API Analyzer](https://youtu.be/eeBEahYXGd0) demo video.
