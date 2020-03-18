---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936986"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.2'de tanıtılan `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.7.2 ile `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` başlayarak, uyumluluk anahtarı geliştiricinin <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> artık kaynak denetimine bir başvuru döndüren özelliğin yeni davranışını devre dışı bırakmasına olanak tanır. Özelliğin önceki davranışı dönmek `null`oldu. Daha fazla bilgi için [ \<AppContextSwitchOverrides> öğesine](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)bakın.

.NET Core'da `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
