---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449419"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum

.NET Core'da, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında ancak yazma izni olmadığında bir <xref:System.UnauthorizedAccessException> atma yapılır.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework'de, arayan bir dosya özniteliği değerini ayarlamaya çalıştığında <xref:System.ArgumentException> <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ancak yazma izni olmadığında bir atma yapılır. .NET Core'da <xref:System.UnauthorizedAccessException> bunun yerine bir atılmıştır. (.NET Core'da, arayan geçersiz bir dosya özniteliği ayarlamaya çalışırsa yine de bir <xref:System.ArgumentException> atılabilir.)

#### <a name="version-introduced"></a>Sürüm tanıtıldı

1.0

#### <a name="recommended-action"></a>Önerilen eylem

Gerekli `catch` olduğu gibi <xref:System.UnauthorizedAccessException> bir yerine veya buna ek <xref:System.ArgumentException>olarak, bir yakalamak için herhangi bir deyimdeğiştirin.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
