---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181841"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.UseLegacyImages`

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Windows.Forms.RichTextBox> denetim, Win32 RichEdit denetimi v 3.0 örneğini oluşturur ve .NET Framework 4.7.1 hedefleyen uygulamalar için <xref:System.Windows.Forms.RichTextBox> , denetim RichEdit v 4.1 örneğini oluşturur (  *Msftedit. dll*). Uyumluluk `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanması için sunulmuştur.

.NET Core 'da, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez. Yalnızca <xref:System.Windows.Forms.RichTextBox> denetimin yeni sürümleri desteklenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
