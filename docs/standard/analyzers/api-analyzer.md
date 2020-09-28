---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi 'nin kullanım dışı API 'Leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: f1268d5f208e19f1b69ed487370fb4c96723a204
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406251"
---
# <a name="net-api-analyzer"></a>.NET API Çözümleyicisi

.NET API Çözümleyicisi, farklı platformlarda C# API 'Leri için olası uyumluluk risklerini bulan ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn çözümleyicisidir. Tüm geliştirme aşamalarında tüm C# geliştiricileri için yararlı olabilir.

API Çözümleyicisi, [Microsoft. DotNet. çözümleyiciler. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)bir NuGet paketi olarak sunulur. Bir projede başvurulduktan sonra kodu otomatik olarak izler ve sorunlu API kullanımını gösterir. Hafif ampul ' i tıklatarak olası düzeltmeler hakkında öneriler de alabilirsiniz. Açılan menü, uyarıları gösterme seçeneğini içerir.

> [!NOTE]
> .NET API Çözümleyicisi, hala yayın öncesi bir sürümdür.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 ve üzeri sürümleri veya Mac için Visual Studio (tüm sürümler).

## <a name="discover-deprecated-apis"></a>Kullanımdan kaldırılan API 'Leri bul

### <a name="what-are-deprecated-apis"></a>Kullanımdan kaldırılan API 'Ler nelerdir?

.NET ailesi, müşteri ihtiyaçlarını daha iyi karşılamak üzere sürekli olarak yükseltilen büyük ürünlerden oluşan bir kümesidir. Bazı API 'Leri kullanımdan kaldırma ve yenilerini yenisiyle değiştirme doğal bir şekilde yapılır. Daha iyi bir alternatif olduğunda bir API kullanım dışı olarak kabul edilir. Bir API 'nin kullanım dışı olduğunu ve kullanılması gerekmemesi gerektiğini bildirmek için bir yol, özniteliği ile işaretmektir <xref:System.ObsoleteAttribute> . Bu yaklaşımın dezavantajı, artık kullanılmayan tüm API 'Ler için yalnızca bir tanılama KIMLIĞI (C#, [CS0612](../../csharp/misc/cs0612.md)için) olacaktır. Bunun anlamı:

- Her durum için adanmış belgeler olması olanaksızdır.
- Belirli uyarı kategorisini bastırmak imkansız olabilir. Bunlardan hiçbirini veya hiçbirini gizleyebilirsiniz.
- Kullanıcıları yeni bir kullanımdan kaldırma hakkında bilgilendirmek için, başvurulan bir derleme veya hedefleme paketi güncelleştirilmeleri gerekir.

API Çözümleyicisi, tek tek uyarıların görüntülenmesi üzerinde denetime izin veren, DE (kullanımdan kaldırma hatası anlamına gelir) ile başlayan API 'ye özel hata kodları kullanır. Çözümleyici tarafından tanımlanan kullanım dışı API 'Ler [DotNet/platform-COMPAT](https://github.com/dotnet/platform-compat) deposunda tanımlanmıştır.

### <a name="add-the-api-analyzer-to-your-project"></a>Projenize API Çözümleyicisi ekleme

1. Visual Studio'yu açın.
2. Çözümleyiciyi çalıştırmak istediğiniz projeyi açın.
3. **Çözüm Gezgini**, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. (Bu seçenek, **Proje** menüsünden de kullanılabilir.)
4. NuGet Paket Yöneticisi sekmesinde:
   1. Paket kaynağı olarak "nuget.org" öğesini seçin.
   2. **Araştır** sekmesine gidin.
   3. **Yayın öncesi Ekle**' yi seçin.
   4. **Microsoft. DotNet. çözümleyiciler**için arama yapın. uyumluluk.
   5. Listeden bu paketi seçin.
   6. **Install** düğmesini seçin.
   7. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.

### <a name="use-the-api-analyzer"></a>API Çözümleyicisi 'ni kullanma

, Gibi kullanım dışı bırakılmış bir API <xref:System.Net.WebClient> bir kodda kullanıldığında, API Çözümleyicisi bunu yeşil dalgalı çizgi ile vurgular. API çağrısının üzerine geldiğinizde, aşağıdaki örnekte olduğu gibi, API 'nin kullanımdan kaldırılması hakkında bilgiler içeren bir ampul görüntülenir:

![Sol tarafta yeşil dalgalı çizgi ve ampul ile WebClient API ekran görüntüsü.](media/api-analyzer/green-squiggle.jpg)

**Hata listesi** penceresinde, aşağıdaki örnekte gösterildiği gibi, kullanım dışı API başına BENZERSIZ bir kimliğe sahip uyarılar bulunur ( `DE004` ):

![Uyarının KIMLIĞINI ve açıklamasını gösteren Hata Listesi penceresinin ekran görüntüsü.](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren Hata Listesi pencere.")

KIMLIĞE tıkladığınızda, API 'nin neden kullanım dışı olduğuna ilişkin ayrıntılı bilgiler ve kullanılabilecek alternatif API 'Ler ile ilgili öneriler içeren bir Web sayfasına gidebilirsiniz.

Vurgulanan üyeye sağ tıklayıp **Gizle \<diagnostic ID> **' yi seçerek herhangi bir uyarı bastırılabilir. Uyarıları basmanın iki yolu vardır:

- [Yerel olarak (kaynakta)](#suppress-warnings-locally)
- [küresel olarak (bir gizleme dosyasında)](#suppress-warnings-globally) önerilir

### <a name="suppress-warnings-locally"></a>Uyarıları yerel olarak gösterme

Uyarıları yerel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**  >  ** *Tanılama kimliğini* \<diagnostic ID> **  >  **kaynak bölümünde**göster ' i seçin. [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı ön işlemci yönergesi, tanımlanan kapsamdaki kaynak kodunuza eklenir: ![ #pragma uyarı devre dışı ile çerçeveli kodun ekran görüntüsü.](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>Uyarıları küresel olarak gösterme

Uyarıları küresel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**  >  gizleme dosyasında** *Tanılama kimliğini* \<diagnostic ID> Gizle**' yi seçin  >  **in Suppression File**.

![Visual Studio 'da bir uyarıyı gösterme seçeneklerini gösteren sağ tıklama menüsünün ekran görüntüsü.](media/api-analyzer/suppress-in-sup-file.jpg)

İlk göstermeme sonrasında projenize bir *GlobalSuppressions.cs* dosyası eklenir. Bu dosyanın yeni genel gizlemeleri eklenir.

![Çözüm Gezgini içindeki GlobalSuppressions.cs dosyasının ekran görüntüsü.](media/api-analyzer/suppression-file.jpg)

Genel gizleme, projeler genelinde API kullanımının tutarlılığını sağlamak için önerilen yoldur.

## <a name="discover-cross-platform-issues"></a>Platformlar arası sorunları bulma

> [!NOTE]
> .NET 5,0, bu özelliğin yerini alacak şekilde [platform uyumluluğu Çözümleyicisi](platform-compat-analyzer.md) 'ni tanıtır. Platform uyumluluğu Çözümleyicisi, .NET SDK 'ya dahildir (Bu uygulamayı ayrı olarak yüklemeniz gerekmez) ve varsayılan olarak açık olur.

Kullanım dışı olan API 'Lerle benzer şekilde, çözümleyici platformlar arası olmayan tüm API 'Leri tanımlar. Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows 'da, Linux ve macOS 'ta değil, üzerinde çalışmaz. Tanılama KIMLIĞI **hata listesi** penceresinde gösterilir. Sağ tıklayıp **Hızlı Eylemler ve yeniden düzenlemeler '** i seçerek bu uyarının görüntülenmesini sağlayabilirsiniz. İki seçeneğe sahip olduğunuz kullanım dışı durumların aksine (kullanımdan kaldırılan üyeyi kullanmaya devam edin, uyarıları gizleyin veya hiç kullanmayın), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, kodunuzu çalıştırmayı planladığınız diğer tüm platformlar için tüm uyarıları gizleyebilirsiniz. Bunu yapmak için yalnızca proje dosyanızı düzenlemeniz ve `PlatformCompatIgnore` tüm platformları listeleyen özelliği yok sayılacak şekilde eklemeniz gerekir. Kabul edilen değerler şunlardır: `Linux` , `macOS` , ve `Windows` .

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API 'nin avantajlarından yararlanmak istiyorsanız kodun bu bölümünü bir ifadesiyle koryükleyebilirsiniz `if` :

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Ayrıca, hedef çerçeve/işletim sistemi için koşullu olarak derleyebilirsiniz, ancak şu anda [el ile](../frameworks.md#how-to-specify-a-target-framework)yapmanız gerekir.

## <a name="supported-diagnostics"></a>Desteklenen Tanılamalar

Şu anda, çözümleyici aşağıdaki durumları işler:

- (PC001) oluşturan .NET Standard API kullanımı <xref:System.PlatformNotSupportedException> .
- .NET Framework 4.6.1 (PC002) üzerinde kullanılamayan bir .NET Standard API kullanımı.
- UWP 'de mevcut olmayan bir yerel API kullanımı (PC003).
- Delegate. BeginInvoke ve EndInvoke API 'Leri (PC004) kullanımı.
- Kullanım dışı (DEXXXX) olarak işaretlenen bir API kullanımı.

## <a name="ci-machine"></a>CI makinesi

Tüm bu Tanılamalar yalnızca IDE 'de değil, aynı zamanda, CI sunucusunu içeren projenizi oluşturmanın bir parçası olarak komut satırında de mevcuttur.

## <a name="configuration"></a>Yapılandırma

Kullanıcı, tanılama nasıl ele alınacağına karar verir: uyarılar, hatalar, öneriler veya kapatılacak. Örneğin, bir mimari olarak uyumluluk sorunlarının hata olarak değerlendirilip bazı kullanım dışı API 'lere yapılan çağrılar uyarı üretirken, diğerleri yalnızca öneriler üretmeye karar verebilirsiniz. Bunu, tanılama KIMLIĞI ve proje tarafından ayrı ayrı yapılandırabilirsiniz. **Çözüm Gezgini**için, projenizin altındaki **Bağımlılıklar** düğümüne gidin. **Dependencies**  >  **Analyzers**  >  **Microsoft. DotNet. çözümleyiciler. uyumluluğu**çözümleyicilerinin düğümleri bağımlılıklarını genişletin. Tanılama KIMLIĞI ' ne sağ tıklayın, **kural kümesi önem derecesini ayarla** ' yı seçin ve istediğiniz seçeneği belirleyin.

![Kural kümesi önem derecesine sahip tanılama ve açılır iletişim iletişimini gösteren Çözüm Gezgini ekran görüntüsü.](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Ayrıca bkz.

- [API Çözümleyicisi blog gönderisine giriş](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .
- YouTube 'da [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım videosu.
- [Platform compatability Çözümleyicisi](platform-compat-analyzer.md)
