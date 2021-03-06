---
title: 'Son değişiklik: TextFormatFlags. ModifyString artık kullanılmıyor'
description: .NET 5 ' teki önemli değişiklik hakkında bilgi edinmek için TextFormatFlags. ModifyString alanının bir uyarı olarak artık kullanılmıyor olduğunu öğrenin.
ms.date: 11/05/2020
ms.openlocfilehash: 9fe1e04b1ad36070b08af2affdca1e058ec74bb8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256172"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags.ModifyString kullanımdan kaldırıldı

Bu <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alan, bir uyarı olarak kullanımdan kalkmıştır ve gelecek bir .NET sürümünde kaldırılabilir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> Enumeration alanı kullanılmıyor olarak işaretlenmemiştir. .NET 5 ve sonraki sürümlerinde, uyarı olarak artık kullanılmıyor olarak işaretlenir. Bu alan, gelecekteki bir .NET sürümünde kaldırılabilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

İle bir dize geçirilmesi <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> , bazı durumlarda dizeyi değiştirir. Bu davranış, dize imlik kullanılabilirliği taahhüdünü keser ve önemli bir .NET çalışma zamanı durumu bozulması oluşmasına neden olabilir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

' İ temel alan tüm kodları güncelleştirin <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
