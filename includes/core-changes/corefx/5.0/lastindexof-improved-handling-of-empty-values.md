---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440183"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="61d70-101">LastIndexOf, boş arama dizelerinin yönetimini iyileştirmiştir</span><span class="sxs-lookup"><span data-stu-id="61d70-101">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="61d70-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve ilgili API 'Ler artık daha büyük bir dize içinde sıfır uzunluklu (veya sıfır uzunluklu eşdeğer) alt dize ararken doğru değerleri döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="61d70-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

#### <a name="change-description"></a><span data-ttu-id="61d70-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="61d70-103">Change description</span></span>

<span data-ttu-id="61d70-104">.NET Framework ve .NET Core 1,0-3,1 ' de, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> çağıran sıfır uzunluklu alt dizeyi ararken Ilgili API 'ler yanlış bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="61d70-104">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="61d70-105">.NET 5,0 ile başlayarak, bu API 'Ler için doğru değeri döndürür `LastIndexOf` .</span><span class="sxs-lookup"><span data-stu-id="61d70-105">Starting with .NET 5.0, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="61d70-106">Bu örneklerde `5` doğru yanıt olduğundan, `"Hello".Substring(5)` `"Hello".AsSpan().Slice(5)` her ikisi de, aranan boş alt dizeye eşit ölçüde eşit olan boş bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61d70-106">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="61d70-107">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="61d70-107">Reason for change</span></span>

<span data-ttu-id="61d70-108">Bu değişiklik, .NET 5 için dize işlemede oluşan genel hata düzeltme çabalarının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="61d70-108">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="61d70-109">Ayrıca Windows ve Windows dışı platformlar arasındaki davranışımızın birleşmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d70-109">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="61d70-110">Daha fazla bilgi için bkz. [DotNet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) ve [DotNet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).</span><span class="sxs-lookup"><span data-stu-id="61d70-110">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="61d70-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="61d70-111">Version introduced</span></span>

<span data-ttu-id="61d70-112">5.0</span><span class="sxs-lookup"><span data-stu-id="61d70-112">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="61d70-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="61d70-113">Recommended action</span></span>

<span data-ttu-id="61d70-114">Herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="61d70-114">You don't need to take any action.</span></span> <span data-ttu-id="61d70-115">.NET 5,0 çalışma zamanı, yeni davranışları otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d70-115">The .NET 5.0 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="61d70-116">Eski davranışı geri yüklemek için bir uyumluluk anahtarı yok.</span><span class="sxs-lookup"><span data-stu-id="61d70-116">There is no compatibility switch to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="61d70-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="61d70-117">Category</span></span>

<span data-ttu-id="61d70-118">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="61d70-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="61d70-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="61d70-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
