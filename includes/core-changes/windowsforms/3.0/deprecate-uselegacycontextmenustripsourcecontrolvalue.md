---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721133"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.NET Framework 4.7.2 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` Uyumluluk anahtarı, geliştiricinin özelliğin yeni davranışını devre dışı bırakmanıza olanak tanır <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> . Bu, şimdi kaynak denetimine bir başvuru döndürür. Özelliğin önceki davranışı döndürülecek `null` . Daha fazla bilgi için bkz. [ \< AppContextSwitchOverrides> öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

.NET Core 'da, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtar desteklenmez.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
