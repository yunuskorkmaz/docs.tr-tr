---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622123"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Bir CellEditEnding işleyicisinden DataGrid. Commitedıt çağrısı odağı bırakır

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Controls.DataGrid.CommitEdit> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> Olay işleyicilerinden birinin çağrılması, odağın kaybetmesine neden olur <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir. Alternatif olarak, çağrıldıktan sonra açıkça yeniden seçilerek bu kaçınılabilir <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
