---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116374"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabiti .NET Core 3,0 Preview 8 ' den itibaren [kullanımdan kalkmış\]\[](xref:System.ObsoleteAttribute) olarak işaretlendi.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı. Constant kullanımı bir derleyici uyarısı oluşturur. .NET Core 'un .NET Framework ve önceki sürümlerinde, eski olarak işaretlenmemiştir.

Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır. <xref:Microsoft.VisualBasic.Constants.vbNewLine> sabiti, Windows 'ta yeni satır karakteri dizisi olan `\r\n`eşdeğerdir. UNIX tabanlı sistemlerde, yeni satır karakteri `\n`.

#### <a name="recommended-action"></a>Önerilen eylem

<xref:Microsoft.VisualBasic.Constants.vbNewLine> için [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:

Satır başı ve satır besleme için <xref:Microsoft.VisualBasic.Constants.vbCrLf>kullanın. Geçerli platformun yeni satır için <xref:System.Environment.NewLine?displayProperty=nameWithType>kullanın.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
