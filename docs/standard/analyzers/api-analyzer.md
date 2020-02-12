---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi 'nin kullanım dışı API 'Leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: efbfa89f431bd02cdf86b8eff8704aec63a29b6c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124253"
---
# <a name="net-api-analyzer"></a>.NET API Çözümleyicisi

.NET API Çözümleyicisi, farklı platformlarda API 'ler için C# olası uyumluluk risklerini bulan ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn çözümleyicisidir. Herhangi bir geliştirme aşamasında tüm C# geliştiriciler için yararlı olabilir.

API Çözümleyicisi, [Microsoft. DotNet. çözümleyiciler. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)bir NuGet paketi olarak sunulur. Bir projede başvurulduktan sonra kodu otomatik olarak izler ve sorunlu API kullanımını gösterir. Hafif ampul ' i tıklatarak olası düzeltmeler hakkında öneriler de alabilirsiniz. Açılan menü, uyarıları gösterme seçeneğini içerir.

> [!NOTE]
> .NET API Çözümleyicisi, hala yayın öncesi bir sürümdür.

## <a name="prerequisites"></a>Prerequisites

- Visual Studio 2017 ve üzeri sürümleri veya Mac için Visual Studio (tüm sürümler).

## <a name="discovering-deprecated-apis"></a>Kullanımdan kaldırılan API 'Ler bulunuyor

### <a name="what-are-deprecated-apis"></a>Kullanımdan kaldırılan API 'Ler nelerdir?

.NET ailesi, müşteri ihtiyaçlarını daha iyi karşılamak üzere sürekli olarak yükseltilen büyük ürünlerden oluşan bir kümesidir. Bazı API 'Leri kullanımdan kaldırma ve yenilerini yenisiyle değiştirme doğal bir şekilde yapılır. Daha iyi bir alternatif olduğunda bir API kullanım dışı olarak kabul edilir. Bir API 'nin kullanım dışı olduğunu ve kullanılması gerekmemesi gerektiğini bildirmek için bir yol <xref:System.ObsoleteAttribute> özniteliğiyle işaretlenmektir. Bu yaklaşımın dezavantajı, artık kullanılmayan tüm API 'ler için yalnızca bir tanılama kimliği (for C#, [CS0612](../../csharp/misc/cs0612.md)) olacaktır. Bunun anlamı:

- Her durum için adanmış belgeler olması olanaksızdır.
- Belirli uyarı kategorisini bastırmak imkansız olabilir. Bunlardan hiçbirini veya hiçbirini gizleyebilirsiniz.
- Kullanıcıları yeni bir kullanımdan kaldırma hakkında bilgilendirmek için, başvurulan bir derleme veya hedefleme paketi güncelleştirilmeleri gerekir.

API Çözümleyicisi, tek tek uyarıların görüntülenmesi üzerinde denetime izin veren, DE (kullanımdan kaldırma hatası anlamına gelir) ile başlayan API 'ye özel hata kodları kullanır. Çözümleyici tarafından tanımlanan kullanım dışı API 'Ler [DotNet/platform-COMPAT](https://github.com/dotnet/platform-compat) deposunda tanımlanmıştır.

### <a name="using-the-api-analyzer"></a>API Çözümleyicisi 'ni kullanma

<xref:System.Net.WebClient>gibi kullanım dışı bir API bir kodda kullanıldığında, API Çözümleyicisi bunu yeşil dalgalı çizgi ile vurgular. API çağrısının üzerine geldiğinizde, aşağıdaki örnekte olduğu gibi, API 'nin kullanımdan kaldırılması hakkında bilgiler içeren bir ampul görüntülenir:

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/green-squiggle.jpg)

**Hata listesi** penceresinde, aşağıdaki örnekte gösterildiği gibi KULLANıMDAN kaldırılan API başına BENZERSIZ bir kimliğe sahip uyarılar bulunur (`DE004`): 

!["Uyarının KIMLIĞINI ve açıklamasını gösteren Hata Listesi penceresinin ekran görüntüsü"](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren Hata Listesi pencere.")

KIMLIĞE tıkladığınızda, API 'nin neden kullanım dışı olduğuna ilişkin ayrıntılı bilgiler ve kullanılabilecek alternatif API 'Ler ile ilgili öneriler içeren bir Web sayfasına gidebilirsiniz.

Vurgulanan üyeye sağ tıklayıp **\<tanılama kimliği > Gizle**' yi seçerek herhangi bir uyarı gizlenebilir. Uyarıları basmanın iki yolu vardır: 

- [Yerel olarak (kaynakta)](#suppressing-warnings-locally)
- [küresel olarak (bir gizleme dosyasında)](#suppressing-warnings-globally) önerilir

### <a name="suppressing-warnings-locally"></a>Uyarıları yerel olarak gizleme

Uyarıları yerel olarak gizlemek için, uyarılarını gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler** > tanılama kimliği **\<tanı kimliği >**  > . [#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı ön işlemci yönergesi, tanımlanan kapsamdaki kaynak kodunuza eklenir: !["#pragma uyarı devre dışı ile çerçeveli kod ekran görüntüsü"](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Uyarıları küresel olarak gizleme

Uyarıları küresel olarak gizlemek için, uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler** > tanılama kimliği **\<tanılama kimliği > > **  **gizleme dosyası**' nı gizleyin.

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/suppress-in-sup-file.jpg)

İlk göstermeme sonrasında projenize bir *GlobalSuppressions.cs* dosyası eklenir. Bu dosyanın yeni genel gizlemeleri eklenir.

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/suppression-file.jpg)

Genel gizleme, projeler genelinde API kullanımının tutarlılığını sağlamak için önerilen yoldur.

## <a name="discovering-cross-platform-issues"></a>Platformlar arası sorunları keşfetme

Kullanım dışı olan API 'Lerle benzer şekilde, çözümleyici platformlar arası olmayan tüm API 'Leri tanımlar. Örneğin <xref:System.Console.WindowWidth?displayProperty=nameWithType>, Linux ve macOS 'ta değil, Windows üzerinde çalışmaktadır. Tanılama KIMLIĞI **hata listesi** penceresinde gösterilir. Sağ tıklayıp **Hızlı Eylemler ve yeniden düzenlemeler '** i seçerek bu uyarının görüntülenmesini sağlayabilirsiniz. İki seçeneğe sahip olduğunuz kullanım dışı durumların aksine (kullanımdan kaldırılan üyeyi kullanmaya devam edin, uyarıları gizleyin veya hiç kullanmayın), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, tüm diğer platformlar için tüm uyarıları gizleyebilirsiniz kodunuzu üzerinde çalıştırmayı planlayın. Bunu yapmak için yalnızca proje dosyanızı düzenlemeniz ve tüm platformları listeleyen `PlatformCompatIgnore` özelliğini yok sayılacak şekilde eklemeniz yeterlidir. Kabul edilen değerler şunlardır: `Linux`, `macOS`ve `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API 'nin avantajlarından yararlanmak istiyorsanız kodun bu bölümünü bir `if` ifadesiyle koryükleyebilirsiniz:

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Ayrıca, hedef çerçeve/işletim sistemi için koşullu olarak derleyebilirsiniz, ancak şu anda [el ile](../frameworks.md#how-to-specify-target-frameworks)yapmanız gerekir.

## <a name="supported-diagnostics"></a>Desteklenen Tanılamalar

Şu anda, çözümleyici aşağıdaki durumları işler:

- <xref:System.PlatformNotSupportedException> oluşturan .NET Standard API kullanımı (PC001).
- .NET Framework 4.6.1 (PC002) üzerinde kullanılamayan bir .NET Standard API kullanımı.
- UWP 'de mevcut olmayan bir yerel API kullanımı (PC003).
- Delegate. BeginInvoke ve EndInvoke API 'Leri (PC004) kullanımı.
- Kullanım dışı (DEXXXX) olarak işaretlenen bir API kullanımı.

## <a name="ci-machine"></a>CI makinesi

Tüm bu Tanılamalar yalnızca IDE 'de değil, aynı zamanda, CI sunucusunu içeren projenizi oluşturmanın bir parçası olarak komut satırında de mevcuttur.

## <a name="configuration"></a>Yapılandırma

Kullanıcı, tanılama nasıl ele alınacağına karar verir: uyarılar, hatalar, öneriler veya kapatılacak. Örneğin, bir mimari olarak uyumluluk sorunlarının hata olarak değerlendirilip bazı kullanım dışı API 'lere yapılan çağrılar uyarı üretirken, diğerleri yalnızca öneriler üretmeye karar verebilirsiniz. Bunu, tanılama KIMLIĞI ve proje tarafından ayrı ayrı yapılandırabilirsiniz. **Çözüm Gezgini**için, projenizin altındaki **Bağımlılıklar** düğümüne gidin. **Microsoft. DotNet. çözümleyiciler. Compatibility** >  > **çözümleyicilerinin** düğümleri **bağımlılıklarını** genişletin. Tanılama KIMLIĞI ' ne sağ tıklayın, **kural kümesi önem derecesini ayarla** ' yı seçin ve istediğiniz seçeneği belirleyin.

!["Kural kümesi önem derecesine sahip tanılama ve açılır iletişim iletişimini gösteren Çözüm Gezgini ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Ayrıca bkz.

- [API Çözümleyicisi blog gönderisine giriş](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .
- YouTube 'da [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım videosu.
