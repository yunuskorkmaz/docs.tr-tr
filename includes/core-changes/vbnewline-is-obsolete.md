---
ms.openlocfilehash: 2a0ebcf61fd96df6d2235962c1f1e9cac3fb22e6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988517"
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

