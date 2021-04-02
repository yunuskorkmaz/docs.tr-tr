---
title: ".NET 6 Son değişiklik: DataGridView ile ilgili API 'Ler InvalidOperationException"
description: DataGridView ile ilgili bazı API 'Lerin bir özel durum oluşturması için nesnenin DataGridViewCellAccessibleObject. Owner değeri null ise, .NET 6 ' daki önemli değişiklik hakkında bilgi edinin.
ms.date: 03/29/2021
ms.openlocfilehash: 3726296bb93c88d438e45ea832bf9070ace69dd0
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106080682"
---
# <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a>DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur

Bundan sonra ilgili bazı API 'Ler, <xref:System.Windows.Forms.DataGridView> nesnenin değeri ise öğesini oluşturur <xref:System.InvalidOperationException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> `null` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, etkilenen API 'Ler çağrıldığında bir oluşturur <xref:System.NullReferenceException> ve <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri şeklindedir `null` . .NET 6 ' dan itibaren, <xref:System.InvalidOperationException> <xref:System.NullReferenceException> <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> özellik değeri çağrıldığında, bu API 'ler yerine bir oluşturur `null` .

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.InvalidOperationException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca geçersiz özelliği açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6.0

## <a name="recommended-action"></a>Önerilen eylem

Kodunuzu inceleyin ve gerekirse, özelliği ile etkilenen türlerin oluşturulmasını engellemek için güncelleştirin <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` .

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen özellikler ve Yöntemler listelenmektedir:

> [!div class="mx-tdBreakAll"]
> | Etkilenen Yöntem veya özellik | Sürüm eklendi |
> |-|-|
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name?displayProperty=fullName> | Preview 4 |
>| <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=fullName> | Preview 4 |
> | <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State?displayProperty=fullName> | Preview 4 |

## <a name="see-also"></a>Ayrıca bkz.

- [DataGridView ile ilgili API 'Ler throw (.NET 5)](../5.0/null-owner-causes-invalidoperationexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Name`
- `M:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `P:System.Windows.Forms.DataGridViewTopLeftHeaderCell.DataGridViewTopLeftHeaderCellAccessibleObject.State`

### Category

Windows Forms

-->
