---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440183"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>LastIndexOf, boş arama dizelerinin yönetimini iyileştirmiştir

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve ilgili API 'Ler artık daha büyük bir dize içinde sıfır uzunluklu (veya sıfır uzunluklu eşdeğer) alt dize ararken doğru değerleri döndürüyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 1,0-3,1 ' de, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> çağıran sıfır uzunluklu alt dizeyi ararken Ilgili API 'ler yanlış bir değer döndürebilir.

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

.NET 5,0 ile başlayarak, bu API 'Ler için doğru değeri döndürür `LastIndexOf` .

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

Bu örneklerde `5` doğru yanıt olduğundan, `"Hello".Substring(5)` `"Hello".AsSpan().Slice(5)` her ikisi de, aranan boş alt dizeye eşit ölçüde eşit olan boş bir dize oluşturur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, .NET 5 için dize işlemede oluşan genel hata düzeltme çabalarının bir parçasıdır. Ayrıca Windows ve Windows dışı platformlar arasındaki davranışımızın birleşmesini de sağlar. Daha fazla bilgi için bkz. [DotNet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) ve [DotNet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

Herhangi bir işlem yapmanız gerekmez. .NET 5,0 çalışma zamanı, yeni davranışları otomatik olarak sağlar.

Eski davranışı geri yüklemek için bir uyumluluk anahtarı yok.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
