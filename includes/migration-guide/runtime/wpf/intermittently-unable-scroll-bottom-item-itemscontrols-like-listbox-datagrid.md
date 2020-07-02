---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622122"
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
