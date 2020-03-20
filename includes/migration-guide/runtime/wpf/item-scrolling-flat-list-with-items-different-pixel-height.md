---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997738"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Farklı piksel yüksekliğindeki öğelerle düz bir listeyi öğe kaydırma

|   |   |
|---|---|
|Ayrıntılar|Bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> koleksiyon sanallaştırma (<code>IsVirtualizing=true</code>) ve öğe kaydırma<code>ScrollUnit=Item</code>() kullanarak görüntülendiğinde ve denetim piksel yüksekliği komşularından farklı olan <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> bir öğeyi görüntülemek için kaydırıldığında, bu koleksiyondaki tüm öğelerüzerinde gerçekleştirilir. UI bu yineleme sırasında yanıt vermiyor; koleksiyon büyükse, bu bir askı olarak algılanabilir. Yineleme, önceki .NET Framework sürümlerinde bile diğer durumlarda oluşur. Örneğin, piksel kaydırma (<code>ScrollUnit=Pixel</code>) farklı piksel yüksekliğine sahip bir öğeyle karşılaştığında ve madde kaydırma hiyerarşik <xref:System.Windows.Controls.TreeView?displayProperty=name> verileri <xref:System.Windows.Controls.ItemsControl?displayProperty=name> (örneğin, gruplandırma etkinleştirilmiş) komşularından farklı sayıda soyundan gelen öğeye sahip bir öğeyle karşılaştığında oluşur. Öğe kaydırma ve farklı piksel yüksekliği durumunda, hiyerarşik verilerin düzenindeki hataları düzeltmek için .NET Framework 4.6.1'de yineleme tanıtıldı.  Veriler düz (hiyerarşi yok) ve .NET Framework 4.6.2 bu durumda bunu yapmıyorsa gerekli değildir.|
|Öneri|Yineleme .NET Framework 4.6.1'de oluşuyorsa ancak önceki sürümlerde yoksa <xref:System.Windows.Controls.ItemsControl?displayProperty=name> - yani, öğe farklı piksel yüksekliğindeki öğelerle düz bir liste kaydırma durumunda - iki çözüm vardır:<ol><li>.NET Framework 4.6.2'yi yükleyin.</li><li>.NET Framework 4.6.1 için hotfix HR 1605'i yükleyin.</li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
