---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556228"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor

`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4.7.1 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Windows.Forms.RichTextBox> Denetim, Win32 RichEdit denetimi v 3.0 'ı başlatır ve .NET Framework 4.7.1 hedefleyen uygulamalar için, <xref:System.Windows.Forms.RichTextBox> Denetim RichEdit v 4.1 ( *msftedit.dll*) örneğini oluşturur. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanmasını sağlamak için sunulmuştur.

.NET Core ve .NET 5,0 ve sonraki sürümlerinde, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez. Yalnızca denetimin yeni sürümleri <xref:System.Windows.Forms.RichTextBox> desteklenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

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
