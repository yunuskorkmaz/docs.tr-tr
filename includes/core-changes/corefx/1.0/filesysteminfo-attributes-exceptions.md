---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449419"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException

.NET Core 'da, çağıran bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmadığında <xref:System.UnauthorizedAccessException> oluşur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, çağıran <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> bir dosya özniteliği değeri ayarlamaya çalıştığında ancak yazma iznine sahip olmayan bir <xref:System.ArgumentException> oluşturulur. .NET Core 'da bunun yerine bir <xref:System.UnauthorizedAccessException> oluşturulur. (.NET Core 'da, çağıran geçersiz bir dosya özniteliği ayarlamaya çalışırsa <xref:System.ArgumentException> yine de oluşturulur.)

#### <a name="version-introduced"></a>Sunulan sürüm

1.0

#### <a name="recommended-action"></a>Önerilen eylem

`catch` deyimlerini, gerektiğinde bir <xref:System.ArgumentException>veya buna ek olarak <xref:System.UnauthorizedAccessException> yakalamak üzere değiştirin.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
