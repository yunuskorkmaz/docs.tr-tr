---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644021"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.2 içinde tanıtılan `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı, geliştiricinin artık kaynak denetimine bir başvuru döndüren <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliğinin yeni davranışını geri almasına izin verir. Özelliğin önceki davranışı `null`döndürmemelidir. Daha fazla bilgi için bkz. [\<AppContextSwitchOverrides > öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

.NET Core 'da `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtarı desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
