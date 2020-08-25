---
ms.openlocfilehash: 87f9cc03f334233ef286abd11e6f5ff82d7988c2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811359"
---
### <a name="ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer"></a>CA1831 Aralık tabanlı dizin oluşturucu yerine AsSpan veya AsMemory kullanın

.Net Code Analyzer Rule [CA1831](/visualstudio/code-quality/ca1831) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir <xref:System.Range> dizede kullanılan bir dizin oluşturucunun kullanıldığı, ancak herhangi bir kopyanın istendiği herhangi bir kod için derleme uyarısı üretir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir. Bu kuralların bazıları varsayılan olarak [CA1831](/visualstudio/code-quality/ca1831)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA1831 <xref:System.Range> , bir dize üzerinde bir-tabanlı dizin oluşturucunun kullanıldığı, ancak hiçbir kopyanın istendiği örnekleri bulur. <xref:System.Range>-Tabanlı dizin oluşturucu örtük bir tür oluşturmak için doğrudan bir dize üzerinde kullanılıyorsa, dizenin istenen bölümünün gereksiz bir kopyası oluşturulur. Örnek:

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

CA1831 <xref:System.Range> , bunun yerine dizenin bir *aralığında* tabanlı dizin oluşturucuyu kullanmayı önerir. Örnek:

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

- Kodunuzu düzeltmek ve gereksiz ayırmaları önlemek için <xref:System.MemoryExtensions.AsSpan(System.String)> <xref:System.MemoryExtensions.AsMemory(System.String)> tabanlı dizin oluşturucuyu kullanmadan önce veya ' i çağırın <xref:System.Range> . Örnek:

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- Kodunuzu değiştirmek istemiyorsanız, önem derecesini veya olarak ayarlayarak kuralı devre dışı bırakabilirsiniz `suggestion` `none` . Daha fazla bilgi için bkz. [kod analizi kurallarını yapılandırma](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Kategori

Kod analizi

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
