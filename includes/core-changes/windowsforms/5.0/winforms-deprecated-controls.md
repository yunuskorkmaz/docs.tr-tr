---
ms.openlocfilehash: d3bfeda8309af83d8e4199999ed91263a17caeea
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556259"
---
### <a name="removed-status-bar-controls"></a>Durum çubuğu denetimleri kaldırıldı

.NET 5,0 ' den başlayarak bazı Windows Forms denetimleri artık kullanılamaz.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 5,0 ile başlayarak, durum çubuğu ile ilgili Windows Forms denetimlerinin bazıları artık kullanılamıyor. Daha iyi tasarım ve destek içeren değiştirme denetimleri .NET Framework 2,0 ' de sunulmuştur. Kullanım dışı bırakılan denetimler daha önce Tasarımcı araç kutularından kaldırılmıştır ancak yine de kullanılabilir. Şimdi tamamen kaldırılmıştır.

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

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

#### <a name="recommended-action"></a>Önerilen eylem

Bu denetimler ve bunların senaryoları için değiştirme API 'Lerine geçin:

| Eski denetim (API) | Önerilen değiştirme                          |
|-------------------|--------------------------------------------------|
| StatusBar         | <xref:System.Windows.Forms.StatusStrip>          |
| StatusBarPanel    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

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

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
