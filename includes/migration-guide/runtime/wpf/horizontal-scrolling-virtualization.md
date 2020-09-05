---
ms.openlocfilehash: 2ae17e0823ec2fa064c948d9ea7bd19cbd34cb6a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497052"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Yatay kaydırma ve sanallaştırma

#### <a name="details"></a>Ayrıntılar

Bu değişiklik, <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> kendi sanallaştırmasını ana kaydırılan yönle (örneğin, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> EnableColumnVirtualization = true) yönünü gösteren bir öğesine uygular &quot; &quot; .  Belirli yatay kaydırma işlemlerinin sonucu, benzer dikey işlemlerin sonuçlarına daha sezgisel ve daha benzer sonuçlar verecek şekilde değiştirilmiştir.<p/>İşlemler &quot; &quot; &quot; &quot; , bir yatay kaydırma çubuğuna sağ tıklanarak elde edilen menüden adları kullanmak Için buraya ve sağ kenara kaydırma içerir.  Her ikisi de aday bir sapmayı ve çağrıyı hesaplar <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .<p/>Yeni sapmayı kaydırdıktan sonra, yeni &quot; &quot; &quot; &quot; de sanallaştırılan içerik değerini değiştirdiği için burada veya sağ kenar kavramı değişmiş olabilir <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> .<p/>.NET Framework 4.6.2 ' den önce, kaydırma işlemi, &quot; burada &quot; veya &quot; sağ kenarda &quot; daha fazla olmasa dahi, aday sapmasını kullanır.  Bu &quot; &quot; , en iyi örnek olarak gösterildiği gibi, kaydırma parmak izi sıçramasına benzer etkilere neden olur. A <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 'Nın ExtentWidth = 1000 ve Width = 200 olduğunu varsayalım.  &quot;Sağ kenara kaydır, &quot; 1000-200 = 800 aday konumunu kullanır.  Bu uzaklığa kaydırma yaparken, yeni sütunlar de sanallaştırılır; Bunun çok geniş olduğunu varsayalım, böylece <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> 2000 üzerinde değişiklik yapabilirsiniz.  Kaydırma, Horizontalkayması = 800 ile sona erer ve Thumb, &quot; kaydırma çubuğunun &quot; ortasına doğru bir şekilde geri dönerek 800/2000 = %40.<p/>Değişiklik, bu durum oluştuğunda yeni bir aday kaydırın yeniden hesaplanması ve yeniden denemeniz. (Dikey kaydırmanın zaten nasıl çalıştığı.) <p/>Değişiklik, son kullanıcı için daha öngörülebilir ve sezgisel bir deneyim üretir, ancak aynı zamanda <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> , bir yatay kaydırmanın ardından, son kullanıcı tarafından veya açık bir çağrı tarafından çağrılıp çağrılmayacağı tüm uygulamaları da etkileyebilir <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .

#### <a name="suggestion"></a>Öneri

İçin tahmin edilen bir değer kullanan bir uygulama, aynı anda <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> sanallaştırma nedeniyle değiştirilebilen herhangi bir yatay kaydırma sonrasında gerçek değeri (ve değerini) getirmek üzere değiştirilmelidir <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.Primitives.IScrollInfo`

-->
