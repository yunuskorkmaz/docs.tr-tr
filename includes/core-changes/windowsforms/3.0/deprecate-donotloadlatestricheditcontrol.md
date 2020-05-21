---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721230"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4.7.1 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Windows.Forms.RichTextBox> Denetim, Win32 RichEdit denetimi v 3.0 örneğini oluşturur ve .NET Framework 4.7.1 hedefleyen uygulamalar için, <xref:System.Windows.Forms.RichTextBox> Denetim RichEdit v 4.1 ( *Msftedit. dll*içinde) örneğini oluşturur. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanması için sunulmuştur.

.NET Core 'da, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez. Yalnızca denetimin yeni sürümleri <xref:System.Windows.Forms.RichTextBox> desteklenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı kaldırın. Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
