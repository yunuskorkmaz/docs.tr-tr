---
title: 'Son değişiklik: DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor'
description: DataGridView 'in, hücre stili yazı tipi özelleştirildiyse artık varsayılan hücre stili yazı tiplerini çevresel yazı tipiyle eşleşecek şekilde sıfırlamalarında, .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: fd28fb5a0b508157289dde1b720522ed49163e31
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256145"
---
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a>DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor

Ortam yazı tipi değiştiğinde, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> hücre stili yazı tipi özelleştirildiyse, varsayılan hücre stili yazı tiplerini artık çevresel yazı tipiyle eşleşecek şekilde sıfırlamamıştır.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, ortam yazı tipi değişirse <xref:System.Windows.Forms.DataGridViewElement.DataGridView> <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> ,, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> ve özelliklerinde Kullanıcı tanımlı yazı tiplerini sıfırlar ve geçersiz kılar <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .

.NET 5 ' te başlayarak,, veya özelliklerinde yazı tipi ayarlarını yapılandırırsanız, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> ortam yazı tipi değiştiğinde bile bu ayarlar korunur. Yazı tipini özelleştirmezseniz bu özelliklerden herhangi biri, yazı tipi çevresel yazı tipi ayarlarıyla eşleşecek şekilde değişir.

## <a name="reason-for-change"></a>Değişiklik nedeni

[.NET Core 3,0 ' de varsayılan yazı tipi değişikliği](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt)ile, çeşitli hücre stillerinin varsayılan yazı tipi ayarları da değişir. Bu davranış, denetimlerinde özel stillendirme <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ve bu uygulamaların .NET Framework ' den .net 5,0 ' e geçişini engelleyen uygulamalar için istenmeyen bir davranıştır.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

Sizin bölüminizdeki herhangi bir eylem gerekmez. Ancak,, veya özelliklerinde yazı tipini özelleştirdiyseniz <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> ve yazı tipinin çevresel yazı tipiyle eşleşmesini istiyorsanız, <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> her bir `null` özellik için olarak ayarlayın.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

### Category

- Windows Forms

-->
