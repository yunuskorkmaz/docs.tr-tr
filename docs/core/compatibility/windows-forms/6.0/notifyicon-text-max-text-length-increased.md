---
title: 'Son değişiklik: NotifyIcon. Text maksimum metin uzunluğu artırıldı'
description: .NET 6 ' da, NotifyIcon. Text özelliği için en fazla metin uzunluğunun arttığı Son değişiklik hakkında bilgi edinin.
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255782"
---
# <a name="notifyicontext-maximum-text-length-increased"></a>NotifyIcon.Text en fazla metin uzunluğu artırıldı

Özellik için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 ile 127 arasında artar.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, özelliği için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 karakterdir. .NET 6 ' dan başlayarak, izin verilen en fazla metin uzunluğu 127 karakterdir. Herhangi bir sürümde, <xref:System.ArgumentException> sınırdan daha uzun bir değer ayarlamaya çalıştığınızda bir oluşturulur.

## <a name="reason-for-change"></a>Değişiklik nedeni

İzin verilen en büyük metin uzunluğu, [temeldeki Windows API 'sine](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080)sahip olacak şekilde artmıştı. Windows API 'SI Windows 2000 ' de güncelleştirildi, ancak uyumluluk nedeniyle bu özellik için boyut sınırı .NET Framework ' de güncelleştirilmedi.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6 Preview 1

## <a name="recommended-action"></a>Önerilen eylem

Gerekirse, kodunuzu gözden geçirin ve var olan koruma koşullarını rahatdan yapın.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
