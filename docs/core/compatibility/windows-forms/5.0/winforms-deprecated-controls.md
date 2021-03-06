---
title: 'Son değişiklik: durum çubuğu denetimleri kaldırıldı'
description: Bazı Windows Forms denetimlerinin artık kullanılamadığı .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 07/18/2020
ms.openlocfilehash: c93b16047896b263248858e807b74c547cfa6d9d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256198"
---
# <a name="removed-status-bar-controls"></a>Durum çubuğu denetimleri kaldırıldı

.NET 5 ' den başlayarak bazı Windows Forms denetimleri artık kullanılamaz.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den itibaren, durum çubuğu ile ilgili Windows Forms denetimlerinin bazıları artık kullanılamıyor. Daha iyi tasarım ve destek içeren değiştirme denetimleri .NET Framework 2,0 ' de sunulmuştur. Kullanım dışı bırakılan denetimler daha önce Tasarımcı araç kutularından kaldırılmıştır ancak yine de kullanılabilir. Şimdi tamamen kaldırılmıştır.

Aşağıdaki türler artık kullanılamaz:

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Bu denetimler ve bunların senaryoları için değiştirme API 'Lerine geçin:

| Eski denetim (API) | Önerilen değiştirme                          |
|-------------------|--------------------------------------------------|
| StatusBar         | <xref:System.Windows.Forms.StatusStrip>          |
| StatusBarPanel    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->
