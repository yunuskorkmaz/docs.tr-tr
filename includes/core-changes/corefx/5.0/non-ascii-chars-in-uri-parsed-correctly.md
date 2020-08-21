---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720220"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="13ee9-101">ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır</span><span class="sxs-lookup"><span data-stu-id="13ee9-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="13ee9-102"><xref:System.Uri?displayProperty=fullName>Sınıfında, ASCII olmayan karakterler içeren mutlak URI yollarının UNIX platformlarında doğru şekilde ayrıştırdığına ilişkin bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="13ee9-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="13ee9-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="13ee9-103">Change description</span></span>

<span data-ttu-id="13ee9-104">.NET 'in önceki sürümlerinde, ASCII olmayan karakterler içeren mutlak URI yolları UNIX platformlarında yanlış ayrıştırılır ve yolun kesimleri yinelenir.</span><span class="sxs-lookup"><span data-stu-id="13ee9-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="13ee9-105">(Mutlak yollar "/" ile başlayan olanlardır.) Ayrıştırma sorunu .NET 5,0 için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="13ee9-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="13ee9-106">.NET 'in önceki bir sürümünden .NET 5,0 veya sonraki bir sürümünü taşırsanız,, <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> <xref:System.Uri.ToString?displayProperty=nameWithType> ve diğer Üyeler tarafından oluşturulan farklı değerler alırsınız <xref:System.Uri> .</span><span class="sxs-lookup"><span data-stu-id="13ee9-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="13ee9-107">UNIX üzerinde çalıştırıldığında aşağıdaki kodun çıkışını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="13ee9-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="13ee9-108">Önceki .NET sürümündeki çıkış:</span><span class="sxs-lookup"><span data-stu-id="13ee9-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="13ee9-109">.NET 5,0 veya sonraki sürümlerinde çıkış:</span><span class="sxs-lookup"><span data-stu-id="13ee9-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="13ee9-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="13ee9-110">Version introduced</span></span>

<span data-ttu-id="13ee9-111">5.0</span><span class="sxs-lookup"><span data-stu-id="13ee9-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="13ee9-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="13ee9-112">Recommended action</span></span>

<span data-ttu-id="13ee9-113">Yinelenen yol segmentlerini bekleyen ve hesapları bekleyen bir kodunuz varsa, bu kodu kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13ee9-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="13ee9-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="13ee9-114">Category</span></span>

<span data-ttu-id="13ee9-115">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="13ee9-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="13ee9-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="13ee9-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
