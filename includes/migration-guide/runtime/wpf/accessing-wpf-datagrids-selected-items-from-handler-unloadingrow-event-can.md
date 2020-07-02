---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620693"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Bir WPF DataGrid 'in seçili öğelerine DataGrid 'in UnloadingRow olayının bir bir NullReferenceException öğesine erişmesi bir NullReferenceException öğesine neden olabilir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' deki bir hata nedeniyle, <xref:System.Windows.Controls.DataGrid> bir satırı kaldırmayı içeren olaylar için olay işleyicileri, <xref:System.NullReferenceException?displayProperty=fullName> ya da özelliklerine eriştiklerinde oluşturulmasına neden olabilir <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
