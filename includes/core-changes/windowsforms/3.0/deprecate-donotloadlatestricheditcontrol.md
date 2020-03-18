---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936999"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.1'de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.6.2 ve önceki <xref:System.Windows.Forms.RichTextBox> sürümlerde, kontrol Win32 RichEdit kontrol v3.0 anında ve .NET Framework 4.7.1 <xref:System.Windows.Forms.RichTextBox> hedef uygulamalar için, kontrol RichEdit v4.1 *(msftedit.dll)* anında olacaktır. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` Uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v4.1 denetimini devre dışı bırakmalarına ve bunun yerine eski RichEdit v3 denetimini kullanmalarına olanak sağlamak için kullanıma sunulmuştur.

.NET Core'da `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez. Denetimin <xref:System.Windows.Forms.RichTextBox> yalnızca yeni sürümleri desteklenir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Anahtarı çıkarın. Anahtar desteklenmez ve alternatif bir işlevsellik yok.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
