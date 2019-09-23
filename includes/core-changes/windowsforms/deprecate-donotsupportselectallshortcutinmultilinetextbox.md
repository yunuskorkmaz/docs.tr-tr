---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181829"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor

.NET Framework 4.6.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ' den başlayarak <xref:System.Windows.Forms.TextBox> , bir denetimde <kbd>CTRL</kbd> + <kbd>kısayol tuşunu</kbd> seçerek tüm metinler seçilir. .NET Framework 4,6 ve önceki sürümlerde, [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> ve Properties öğelerinin her ikisi de olarak `true`ayarlandığında, <kbd>CTRL</kbd> + tuşuna<kbd>bir</kbd> kısayol tuşu seçmek başarısız oldu. `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur. Daha fazla bilgi için <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>bkz.

.NET Core 'da, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.

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
