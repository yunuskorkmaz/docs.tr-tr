---
title: 'Son değişiklik: NotifyIcon. Text maksimum metin uzunluğu artırıldı'
description: ", NotifyIcon. Text özelliği için en fazla metin uzunluğunun arttığı .NET 6,0 ' deki Son değişiklik hakkında bilgi edinin."
ms.date: 01/19/2021
ms.openlocfilehash: 0029556f3ec2795fb079575b329e7fbd187d486f
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98617995"
---
# <a name="notifyicontext-maximum-text-length-increased"></a>NotifyIcon. metin en büyük metin uzunluğu artırıldı

Özellik için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 ile 127 arasında artar.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, özelliği için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 karakterdir. .NET 6,0 ' den başlayarak, izin verilen en fazla metin uzunluğu 127 karakterdir. Herhangi bir sürümde, <xref:System.ArgumentException> sınırdan daha uzun bir değer ayarlamaya çalıştığınızda bir oluşturulur.

## <a name="reason-for-change"></a>Değişiklik nedeni

İzin verilen en büyük metin uzunluğu, [temeldeki Windows API 'sine](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080)sahip olacak şekilde artmıştı. Windows API 'SI Windows 2000 ' de güncelleştirildi, ancak uyumluluk nedeniyle bu özellik için boyut sınırı .NET Framework ' de güncelleştirilmedi.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6,0 Preview 1

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
