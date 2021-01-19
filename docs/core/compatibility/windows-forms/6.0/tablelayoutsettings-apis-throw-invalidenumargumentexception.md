---
title: 'Son değişiklik: bazı TableLayoutSettings özellikleri ınvalıdenumargumentexception oluşturur'
description: Bazı TableLayoutSettings API 'Lerinin artık geçersiz bağımsız değişkenler için bir ınvalıdenumargumentexception oluşturandan sonra .NET 6,0 ' deki önemli değişiklik hakkında bilgi edinin.
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570277"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a>Seçili TableLayoutSettings özellikleri throw ınvalıdenumargumentexception

Seçili <xref:System.Windows.Forms.TableLayoutSettings> Özellikler artık <xref:System.ComponentModel.InvalidEnumArgumentException> yanlış bir değer atamaya çalışırsanız bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.ArgumentOutOfRangeException> yanlış bir değer atamaya çalışırsanız bu özellikler bir oluşturur. .NET 6,0 ' den itibaren bu özellikler bu <xref:System.ComponentModel.InvalidEnumArgumentException> tür durumlarda bir oluşturur.

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.ComponentModel.InvalidEnumArgumentException>, Benzer durumlarda mevcut Windows Forms API 'si ile birlikte oluşturuluyor. Bu özel durum, geliştiriciler için daha iyi bir hata ayıklama deneyimi sağlar.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6,0

## <a name="recommended-action"></a>Önerilen eylem

- Yanlış değerlerin atanmasını engellemek için kodu güncelleştirin.
- Gerekirse, <xref:System.ComponentModel.InvalidEnumArgumentException> Bu API 'lere erişirken bir işleme işleyin.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen özellikler listelenmiştir:

| Özellik | Sürüm değişti |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | Önizleme 1 |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | Önizleme 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
