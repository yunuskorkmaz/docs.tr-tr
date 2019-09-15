---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997738"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Öğe-farklı piksel yüksekliğinde öğeleri olan düz bir liste kaydırma

|   |   |
|---|---|
|Ayrıntılar|Bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> koleksiyonu, sanallaştırma (<code>IsVirtualizing=true</code>) ve öğe kaydırma (<code>ScrollUnit=Item</code>) kullanarak bir koleksiyon görüntülediğinde ve denetimin piksel <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> cinsinden yüksekliği, komşularından farklı olan bir öğeyi görüntülemek için kaydırıldığında, tümünü yineleme koleksiyondaki öğeler. Kullanıcı arabirimi bu yineleme sırasında yanıt vermiyor; koleksiyon büyükse, bu, askıda bir şekilde algılanır. Yineleme, önceki .NET Framework sürümlerde bile diğer koşullarda oluşur. Örneğin, piksel kaydırması (<code>ScrollUnit=Pixel</code>), farklı piksel yüksekliğine sahip bir öğeyle karşılaşdıktan sonra ve öğe kaydırılırken hiyerarşik veriler (örneğin <xref:System.Windows.Controls.ItemsControl?displayProperty=name> , bir <xref:System.Windows.Controls.TreeView?displayProperty=name> veya bir gruplama etkin gibi) ile bir öğeyle karşılaşınca oluşur Komşulardan farklı sayıda alt öğe. Öğe kaydırma ve farklı piksel yüksekliğinin olması durumunda yineleme, hiyerarşik verilerin düzeninde hataları onarmak için .NET Framework 4.6.1 ' de tanıtılmıştır.  Veriler düz (hiyerarşi yok) ise ve bu durumda .NET Framework 4.6.2 bunu yapmaz.|
|Öneri|Yineleme, daha önceki sürümlerde değil, .NET Framework 4.6.1 içinde oluşursa, yani öğesi farklı piksel yüksekliğinin bulunduğu <xref:System.Windows.Controls.ItemsControl?displayProperty=name> düz bir liste içeriyorsa, iki düzeltme vardır:<ol><li>.NET Framework 4.6.2 'yi yükler.</li><li>.NET Framework 4.6.1 için HR 1605 düzeltmesini yükler.</li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
