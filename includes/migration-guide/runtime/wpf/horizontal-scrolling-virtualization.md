---
ms.openlocfilehash: ac7a56dc654ef4fd966077dd25012f0c50b0fc8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981913"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Yatay kaydırma ve sanallaştırma

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik uygulandığı bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> kendi Sanallaştırma Ana kaydırma yönü dikey yönde yapar (baş örnek <xref:System.Windows.Controls.DataGrid?displayProperty=name> EnableColumnVirtualization ile =&quot;True&quot;).  Belirli bir yatay kaydırma işlemlerin sonucunu daha sezgisel ve karşılaştırılabilir dikey işlemlerinin sonuçlarını daha benzer sonuçlar için değiştirildi.<p/>İşlemler şunlardır &quot;burada kaydırma&quot; ve &quot;sağ kenarı&quot;, elde edilen bir yatay kaydırma çubuğunun sağ tıklayarak menü adları kullanır.  Bu işlem bir aday uzaklığı ve çağrı <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>Yeni uzaklık kavramı kaydırma sonra &quot;burada&quot; veya &quot;sağ kenarı&quot; yeni değerini XML'deki sanallaştırılmış içeriği değiştiğinden değişmiş olabilir <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.<p/>.NET Framework 4.6.2 önce olmayabilir rağmen kaydırma işlemi yalnızca aday uzaklık kullanır. &quot;burada&quot; veya &quot;sağ kenarı&quot; artık.  Efektler gibi sonuçlanır &quot;geçirmek&quot; örnekte gösterildiği kaydırma thumb, en iyi. Varsayalım bir <xref:System.Windows.Controls.DataGrid?displayProperty=name> ExtentWidth sahip = 1000 ve genişlik 200 =.  Bir kaydırma için &quot;sağ kenarı&quot; 1000-200 uzaklığı kullandığı aday = 800.  Bu uzaklık kaydırma yaparken yeni de-sanallaştırılmış sütunlardır; çok geniş olduklarını varsayalım böylece <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 2000 değiştirir.  Kaydırma HorizontalOffset ile biten = 800 ve thumb &quot;geri dönmeler&quot; kaydırma çubuğunu - ortasını geri % 40 tam olarak 800/2000 =.<p/>Bu durum ortaya çıkar ve yeniden deneyin, yeni bir aday uzaklığı yeniden oynatmanız farklıdır. (Bu nasıl dikey kaydırma, zaten çalışır.) <p/>Değişiklik, son kullanıcılar için daha öngörülebilir ve sezgisel bir deneyim üretir, ancak tam değerine bağlıdır herhangi bir uygulamayı etkileyebilecek <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> sonra bir yatay kaydırma, son kullanıcı tarafından veya açık bir çağrı tarafından çağrılan olmadığını <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.|
|Öneri|Tahmin edilen bir değer için kullanan bir uygulamayı <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> gerçek değeri getirilemedi değiştirilmelidir (ve değerini <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) sonra değişebilir bir yatay kaydırma <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> nedeniyle devre dışı bırakma sanallaştırma.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
