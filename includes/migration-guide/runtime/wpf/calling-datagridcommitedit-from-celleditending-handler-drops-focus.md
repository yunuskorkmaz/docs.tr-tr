---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497928"
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
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
