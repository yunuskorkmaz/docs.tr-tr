---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116374"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine eski

Sabit <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> ,NET Core 3.0 Preview 8 ile başlayan [ \[Eski olarak\] ](xref:System.ObsoleteAttribute) işaretlenir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 8

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview 8 ile başlayarak, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabite uygulanmıştır. Sabitin kullanımı derleyici uyarısı üretir. .NET Framework ve .NET Core'un önceki sürümlerinde eski olarak işaretlenmemiştir.

Bu değişiklik, Visual Basic'i çok platformlu geliştirme dili olarak desteklemek için yapılmıştır. Sabit, <xref:Microsoft.VisualBasic.Constants.vbNewLine> Windows'daki yeni satır karakter dizisine `\r\n`eşittir. Unix tabanlı sistemlerde, yeni satır `\n`karakteri .

#### <a name="recommended-action"></a>Önerilen eylem

[Eski](xref:System.ObsoleteAttribute) öznitelik iletisi <xref:Microsoft.VisualBasic.Constants.vbNewLine> için aşağıdaki öneri içerir:

Bir satır başı ve satır <xref:Microsoft.VisualBasic.Constants.vbCrLf>beslemesi için. Geçerli platformun yeni hattı için <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
