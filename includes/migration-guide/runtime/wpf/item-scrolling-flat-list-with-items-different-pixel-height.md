---
ms.openlocfilehash: eb3cfdfd39444536f423b65166a3413db67a0e01
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761423"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Farklı piksel yüksekliklerdeki öğelerin ile düz bir liste öğesi kaydırma

|   |   |
|---|---|
|Ayrıntılar|Olduğunda bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> sanallaştırma kullanarak koleksiyon görüntüler (<code>IsVirtualizing=true</code>) ve kaydırma öğesi - (<code>ScrollUnit=Item</code>), ve denetim, yüksekliğini piksel cinsinden Komşuları farklı bir öğeyi görüntülemek için kaydırdığında <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> tüm üzerinde yinelenir. koleksiyondaki öğe. Kullanıcı arabirimini bu yineleme sırasında yanıt vermiyor; koleksiyonu büyükse, bu bir takılma algılanan. Diğer durumlarda, daha önceki sürümlerde .NET Framework yineleme gerçekleşir. Örneğin, piksel kaydırma sırasında gerçekleşir (<code>ScrollUnit=Pixel</code>) öğesi kaydırma sırasında bir öğe farklı piksel yüksekliği ile karşılaşıldığında hiyerarşik veri (gibi bir <xref:System.Windows.Controls.TreeView?displayProperty=name> veya bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> gruplandırma etkin olan) bir öğe ile karşılaşıldığında bir farklı Komşuları daha alt öğe sayısı. Öğe kaydırma ve farklı piksel yüksekliği çalışması için yineleme düzenini hiyerarşik verilerin hataları için .NET Framework 4.6.1 sunulmuştur.  Veriler (hiyerarşi yok) düz ve .NET Framework 4.6.2 Bu durumda, yapmaz ise gerekli değildir.|
|Öneri|Yineleme .NET Framework 4.6.1 ancak önceki sürümlerde - diğer bir deyişle, gerçekleşirse <xref:System.Windows.Controls.ItemsControl?displayProperty=name> iş öğesi-düz liste kaydırma farklı piksel yüksekliği - öğeleriyle iki çözümler vardır:<ol><li>.NET Framework 4.6.2 yükleyin.</li><li>.NET Framework 4.6.1 için düzeltme ik 1605 yükleyin.</li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

