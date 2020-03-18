---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936984"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>DoNotSupportSelectAllShortcutInMultilineTextBox uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1'de tanıtılan `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.6.1 ile başlayarak, tüm metni seçen <xref:System.Windows.Forms.TextBox> bir denetimde <kbd>Ctrl</kbd> + <kbd>A</kbd> kısayol anahtarını seçin. .NET Framework 4.6 ve önceki sürümlerde, <kbd>Ctrl</kbd> + <kbd>A</kbd> kısayol tuşu seçilerek [Textbox.ShortcutsEtkin](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> özellikleri her ikisi de ayarlanmışsa tüm metni seçmek için `true`başarısız oldu. Uyumluluk `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtarı,.NET Framework 4.6.1'de özgün davranışı korumak için tanıtıldı. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

.NET Core'da `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
