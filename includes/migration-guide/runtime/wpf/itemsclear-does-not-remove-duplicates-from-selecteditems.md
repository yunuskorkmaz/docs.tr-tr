---
ms.openlocfilehash: 25ce391f917bd270d4d9a75f608e4a8ec763d15c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496215"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items. Clear, Selectedilıtems 'dan yinelenenleri kaldırmaz

#### <a name="details"></a>Ayrıntılar

Bir seçicinin (birden çok seçim etkinleştirilmiş olarak) koleksiyonunda yinelenen öğeler olduğunu varsayalım <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> . aynı öğe birden çok kez görünüyor.  Bu öğeleri veri kaynağından kaldırmak (örneğin, Items. Clear öğesini çağırarak), öğesinden kaldıramazsa <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> ; yalnızca ilk örnek kaldırılır. Ayrıca, <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (ör. Selectedilıtems. Clear ()) öğesinin daha sonra <xref:System.ArgumentException?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> veri kaynağında olmayan öğeler içerdiğinden, ' nin sonraki kullanımı gibi sorunlar oluşabilir.

#### <a name="suggestion"></a>Öneri

4.6.2 .NET Framework için mümkünse yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.MultiSelector.SelectedItems`

-->
