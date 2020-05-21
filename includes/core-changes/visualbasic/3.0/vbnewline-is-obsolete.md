---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721691"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Sabit, .NET Core 3,0 Preview 8 ' den itibaren [ \[ eski \] ](xref:System.ObsoleteAttribute) olarak işaretlendi.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 8 ' den başlayarak, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı. Constant kullanımı bir derleyici uyarısı oluşturur. .NET Core 'un .NET Framework ve önceki sürümlerinde, eski olarak işaretlenmemiştir.

Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır. <xref:Microsoft.VisualBasic.Constants.vbNewLine>Sabit, `\r\n` Windows 'ta yeni satır karakteri dizisi ile eşdeğerdir. UNIX tabanlı sistemlerde, yeni satır karakteri `\n` .

#### <a name="recommended-action"></a>Önerilen eylem

İçin [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi <xref:Microsoft.VisualBasic.Constants.vbNewLine> aşağıdaki öneriyi içerir:

Bir satır başı ve satır besleme için kullanın <xref:Microsoft.VisualBasic.Constants.vbCrLf> . Geçerli platformun yeni satır için kullanın <xref:System.Environment.NewLine?displayProperty=nameWithType> .

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
