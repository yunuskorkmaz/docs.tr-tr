---
title: 'Son değişiklik: WinForms özellikleri artık ArgumentOutOfRangeException oluşturur'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. bazı Windows Forms özellikleri artık geçersiz bağımsız değişkenler için bir ArgumentOutOfRangeException oluşturur.
ms.date: 06/18/2020
ms.openlocfilehash: 493669af1ed5646d93e7c7d2688afd40f3fa731c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256159"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>WinForms özellikleri artık ArgumentOutOfRangeException oluşturur

Bazı Windows Forms özellikleri artık <xref:System.ArgumentOutOfRangeException> , daha önce olmadıkları durumlarda geçersiz bağımsız değişkenler oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, bu özellikler <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> Aralık dışı bağımsız değişkenler geçirildiğinde, veya gibi çeşitli özel durumlar oluşturdu. .NET 5 ' den itibaren, bu özellikler artık <xref:System.ArgumentOutOfRangeException> Aralık dışı olan bağımsız değişkenleri geçtiğinde bir oluşturur.

<xref:System.ArgumentOutOfRangeException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

- Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.
- Gerekirse, <xref:System.ArgumentOutOfRangeException> özelliği ayarlarken bir işleyin.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen özellikler ve parametreler listelenmektedir:

> [!div class="mx-tdBreakAll"]
> | Özellik | Parametre adı | Sürüm eklendi |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5,0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5,0 Preview 6 |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
