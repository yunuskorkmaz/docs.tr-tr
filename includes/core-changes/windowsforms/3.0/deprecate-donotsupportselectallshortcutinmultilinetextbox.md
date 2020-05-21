---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720932"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ' den başlayarak, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> bir denetimde CTRL kısayol tuşunu seçerek <xref:System.Windows.Forms.TextBox> tüm metinler seçilir. .NET Framework 4,6 ve önceki sürümlerde, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties öğelerinin her ikisi de olarak ayarlandığında, CTRL tuşuna bir kısayol tuşu seçmek başarısız oldu `true` . `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

.NET Core 'da, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
