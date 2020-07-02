---
ms.openlocfilehash: fbf3c0c8f1d11f9f5997a4d1027242c4710c7107
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621826"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Öğe-farklı piksel yüksekliğinde öğeleri olan düz bir liste kaydırma

#### <a name="details"></a>Ayrıntılar

Bir <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> koleksiyon, sanallaştırma ( <code>IsVirtualizing=true</code> ) ve öğe kaydırma () kullanarak bir koleksiyon <code>ScrollUnit=Item</code> görüntülediğinde ve denetimin piksel cinsinden yüksekliği, komşularından farklı olan bir öğeyi görüntülemek için kaydırıldığında, <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> koleksiyondaki tüm öğeler üzerinde dolaşır. Kullanıcı arabirimi bu yineleme sırasında yanıt vermiyor; koleksiyon büyükse, bu, askıda bir şekilde algılanır. Yineleme, önceki .NET Framework sürümlerde bile diğer koşullarda oluşur. Örneğin, piksel <code>ScrollUnit=Pixel</code> kaydırdıktan sonra (), farklı piksel yüksekliğine sahip bir öğeyle karşılaşıldığında ve öğe kaydırılırken hiyerarşik veriler (örneğin <xref:System.Windows.Controls.TreeView?displayProperty=fullName> , bir veya bir <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> gruplama etkin gibi), komşularından farklı sayıda alt öğe içeren bir öğeyle karşılaşınca meydana gelir. Öğe kaydırma ve farklı piksel yüksekliğinin olması durumunda yineleme, hiyerarşik verilerin düzeninde hataları onarmak için .NET Framework 4.6.1 ' de tanıtılmıştır.  Veriler düz (hiyerarşi yok) ise ve bu durumda .NET Framework 4.6.2 bunu yapmaz.

#### <a name="suggestion"></a>Öneri

Yineleme, daha önceki sürümlerde değil, .NET Framework 4.6.1 içinde oluşursa, yani <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> öğesi farklı piksel yüksekliğinin bulunduğu düz bir liste içeriyorsa, iki düzeltme vardır:<ol><li>.NET Framework 4.6.2 'yi yükler.</li><li>.NET Framework 4.6.1 için HR 1605 düzeltmesini yükler.</li></ol>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
