---
ms.openlocfilehash: e476039ff9c8d33f54a2f7e4371dc09a3be557c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237477"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor

@No__t-0 sabiti .NET Core 3,0 Preview 8 ' den itibaren [kullanılmıyor](xref:System.ObsoleteAttribute) olarak işaretlenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı. Constant kullanımı bir derleyici uyarısı oluşturur. Hem .NET Core hem de .NET Framework önceki sürümlerinde, eski olarak işaretlenmemiştir.

Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır. @No__t-0 sabiti, Windows 'ta yeni satır karakteri dizisi olan `\r\n` ile eşdeğerdir. UNIX tabanlı sistemlerde, yeni satır karakteri `\n` ' dır.
 
#### <a name="recommended-action"></a>Önerilen eylem

@No__t-1 için [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:

> Satır başı ve satır besleme için [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)kullanın. Geçerli platformun yeni satırı için <xref:System.Environment.NewLine?displayProperty=nameWithType> kullanın.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
