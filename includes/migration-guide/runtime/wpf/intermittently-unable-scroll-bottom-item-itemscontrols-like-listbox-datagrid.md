---
ms.openlocfilehash: bca76daca6e9c424377a80aa56e1a5ff191be5ca
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497157"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Özel veri şablonları kullanılırken, ara sıra ıtemcontrols (ListBox ve DataGrid gibi) alt öğeye kaydırılamıyor

#### <a name="details"></a>Ayrıntılar

Bazı örneklerde, 4,5 .NET Framework bir hata, ıtemcontrols (gibi,, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> vb.), özel veri şablonları kullanırken kendi alt öğelerini kaydırmamasına neden olur. Kaydırmanın ikinci kez denendiğinde (geri alındıktan sonra), daha sonra çalışır.

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4.5.2 düzeltilmiştir ve bu sürüme (veya sonraki bir sürüme) yükselterek .NET Framework. Alternatif olarak, kullanıcılar kaydırma çubuklarını bu koleksiyonlardaki son öğelere sürüklemeye devam edebilir, ancak bunu iki kez denemek gerekebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
