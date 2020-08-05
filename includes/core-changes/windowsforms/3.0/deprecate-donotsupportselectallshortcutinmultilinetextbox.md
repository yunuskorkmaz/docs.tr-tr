---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556251"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 ' de tanıtılan uyumluluk anahtarı .NET Core ve .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.1 ' den başlayarak, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> bir denetimde CTRL kısayol tuşunu seçerek <xref:System.Windows.Forms.TextBox> tüm metinler seçilir. .NET Framework 4,6 ve önceki sürümlerde, <kbd>Ctrl</kbd>  +  <kbd>A</kbd> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) ve <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties öğelerinin her ikisi de olarak ayarlandığında, CTRL tuşuna bir kısayol tuşu seçmek başarısız oldu `true` . `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Uyumluluk anahtarı .NET Framework 4.6.1 ' de özgün davranışı koruyacak şekilde sunulmuştur. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

.NET Core ve .NET 5,0 ve sonraki sürümlerinde, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Hiçbiri

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
