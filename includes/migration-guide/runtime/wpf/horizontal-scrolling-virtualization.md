---
ms.openlocfilehash: ac7a56dc654ef4fd966077dd25012f0c50b0fc8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857497"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Yatay kaydırma ve sanallaştırma

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik, ana <xref:System.Windows.Controls.ItemsControl?displayProperty=name> kaydırma yönüne ortogonal yönde kendi sanallaştırma yapan bir için geçerlidir (ana örnek&quot;&quot;EnableColumnVirtualization= True ile). <xref:System.Windows.Controls.DataGrid?displayProperty=name>  Bazı yatay kaydırma işlemlerinin sonucu, karşılaştırılabilir dikey işlemlerin sonuçlarına daha sezgisel ve daha benzer sonuçlar üretmek için değiştirildi.<p/>İşlemler, &quot;yatay&quot; &quot;kaydırma&quot;çubuğuna sağ tıklayarak elde edilen menüdeki adları kullanmak için Burada Ve Sağ Kenar'ı kaydırmayı içerir.  Bu her ikisi de bir aday <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>ofset ve arama hesaplamak.<p/>Yeni ofset kaydırdıktan sonra, &quot;yeni&quot; &quot;sanallaştırılan içerik değerini değiştirdiği için burada veya sağ kenar&quot; kavramı değişmiş <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>olabilir.<p/>.NET Framework 4.6.2'den önce kaydırma &quot;işlemi, artık burada&quot; veya &quot;sağ kenarda&quot; olmasa bile, yalnızca aday mahsup işlemini kullanır.  Bu, en iyi &quot;örnekle gösterildiği kaydırma başparmağını zıplatma&quot; gibi etkilerle sonuçlanır. Bir'in <xref:System.Windows.Controls.DataGrid?displayProperty=name> ExtentWidth=1000 ve Width=200 olduğunu varsayalım.  Right &quot;Edge'e&quot; yapılan bir kaydırma, aday ofset 1000 - 200 = 800 kullanır.  Bu ofset kaydırma sırasında, yeni sütunlar de-sanallaştırılmış; çok geniş olduğunu varsayalım, böylece <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 2000 için değişiklikler.  Kaydırma HorizontalOffset=800 ile sona erer &quot;ve&quot; başparmak kaydırma çubuğunun ortasına doğru geri döner - tam olarak 800/2000 = %40'ta.<p/>Değişiklik, bu durum oluştuğunda yeni bir aday mahsup yeniden hesaplamak ve yeniden denemektir. (Dikey kaydırma zaten nasıl çalışır.) <p/>Değişiklik son kullanıcı için daha öngörülebilir ve sezgisel bir deneyim üretir, ancak aynı zamanda son <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> kullanıcı tarafından çağrılan ya da açık bir çağrı tarafından <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>olsun, yatay bir kaydırma sonra tam değerine bağlı herhangi bir uygulama etkileyebilir.|
|Öneri|Öngörülen değeri kullanan bir uygulama, sanallaştırmayı de-sanallaştırma nedeniyle <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>değişebilecek <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> herhangi bir yatay kaydırmadan sonra gerçek değeri (ve değerini) almak için değiştirilmelidir.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
