---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643986"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor

.NET Framework 4.7.1 içinde tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.2 ve önceki sürümlerde, <xref:System.Windows.Forms.RichTextBox> denetimi Win32 RichEdit denetimi v 3.0 'ı örnekleyebilir ve .NET Framework 4.7.1 hedefleyen uygulamalar için <xref:System.Windows.Forms.RichTextBox> denetimi RichEdit v 4.1 ( *Msftedit. dll*içinde) örneğini oluşturur. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanması için sunulmuştur.

.NET Core 'da `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtarı desteklenmez. Yalnızca <xref:System.Windows.Forms.RichTextBox> denetiminin yeni sürümleri desteklenir.

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
