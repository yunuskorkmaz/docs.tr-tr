---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032078"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException

.NET Core 'da, <xref:System.UnauthorizedAccessException> çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmadığında bir oluşturulur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.ArgumentException> çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ancak yazma iznine sahip olmadığında oluşur. .NET Core 'da <xref:System.UnauthorizedAccessException> bunun yerine bir oluşturulur. (.NET Core 'da, <xref:System.ArgumentException> çağıran geçersiz bir dosya özniteliği ayarlamaya çalışırsa yine bir oluşturulur.)

#### <a name="version-introduced"></a>Sunulan sürüm

1,0

#### <a name="recommended-action"></a>Önerilen eylem

Gerektiğinde, `catch` veya buna ek olarak, bir yerine yakalamak için herhangi bir deyimi değiştirin <xref:System.UnauthorizedAccessException> <xref:System.ArgumentException> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
