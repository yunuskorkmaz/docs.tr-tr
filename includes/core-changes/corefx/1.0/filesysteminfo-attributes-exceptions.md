---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021793"
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

Çekirdek .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
