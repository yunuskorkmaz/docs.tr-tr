---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643993"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1 içinde tanıtılan `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ' den başlayarak <kbd>, bir <xref:System.Windows.Forms.TextBox></kbd> denetimindeki kısayol tuşu + <kbd>CTRL</kbd> ' i seçerek tüm metni seçin. .NET Framework 4,6 ve önceki sürümlerde, [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> özelliklerinin ikisi de `true`olarak ayarlanana kadar, <kbd>CTRL</kbd> <kbd> + kısayol</kbd> tuşu seçimi başarısız oldu. `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı, özgün davranışı sürdürmek için .NET Framework 4.6.1 eklenmiştir. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

.NET Core 'da `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtarı desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
