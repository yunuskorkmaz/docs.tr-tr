---
ms.openlocfilehash: 82017569128937d344838df850445cf55aa9ea4c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930035"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor

Sabit .NET Framework kullanılmıyor olarak işaretlenmiş, ancak .NET Core 3,0 kitaplığında öznitelik daha önce eksikti. [](xref:System.ObsoleteAttribute) <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="details"></a>Ayrıntılar

.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik, .NET Framework ile uyumlu <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> `vbNewLine` olması için sabitine uygulandı. `vbNewLine` Constant kullanımı bir derleyici uyarısı oluşturur. 

.NET Core `vbNewLine` 'un önceki sürümlerinde bir derleyici uyarısı üretmedi.

#### <a name="recommended-action"></a>Önerilen eylem

İçin`vbNewLine` [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:

> Satır başı ve satır besleme için [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)kullanın. Geçerli platformun yeni satır için kullanın <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategori
Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler
- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

