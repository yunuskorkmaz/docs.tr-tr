---
title: 'Son değişiklik: ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır'
description: ASCII olmayan karakterler içeren mutlak URI yollarının artık UNIX platformlarında doğru şekilde ayrıştırdığına ilişkin temel .NET kitaplıklarında .NET 5 ' in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 50e9b4597a5ac0b73732a38ce662037292777a03
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257420"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="a3a16-103">ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır</span><span class="sxs-lookup"><span data-stu-id="a3a16-103">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="a3a16-104"><xref:System.Uri?displayProperty=fullName>Sınıfında, ASCII olmayan karakterler içeren mutlak URI yollarının UNIX platformlarında doğru şekilde ayrıştırdığına ilişkin bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="a3a16-104">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="a3a16-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a3a16-105">Change description</span></span>

<span data-ttu-id="a3a16-106">.NET 'in önceki sürümlerinde, ASCII olmayan karakterler içeren mutlak URI yolları UNIX platformlarında yanlış ayrıştırılır ve yolun kesimleri yinelenir.</span><span class="sxs-lookup"><span data-stu-id="a3a16-106">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="a3a16-107">(Mutlak yollar "/" ile başlayan olanlardır.) Ayrıştırma sorunu .NET 5,0 için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="a3a16-107">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="a3a16-108">.NET ' in önceki bir sürümünü .NET 5 veya sonraki bir sürümüne taşırsanız,, <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> <xref:System.Uri.ToString?displayProperty=nameWithType> ve diğer Üyeler tarafından oluşturulan farklı değerler alırsınız <xref:System.Uri> .</span><span class="sxs-lookup"><span data-stu-id="a3a16-108">If you move from a previous version of .NET to .NET 5 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="a3a16-109">UNIX üzerinde çalıştırıldığında aşağıdaki kodun çıkışını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a3a16-109">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="a3a16-110">Önceki .NET sürümündeki çıkış:</span><span class="sxs-lookup"><span data-stu-id="a3a16-110">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="a3a16-111">.NET 5 veya sonraki bir sürümde çıkış:</span><span class="sxs-lookup"><span data-stu-id="a3a16-111">Output on .NET 5 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a><span data-ttu-id="a3a16-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a3a16-112">Version introduced</span></span>

<span data-ttu-id="a3a16-113">5.0</span><span class="sxs-lookup"><span data-stu-id="a3a16-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a3a16-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a3a16-114">Recommended action</span></span>

<span data-ttu-id="a3a16-115">Yinelenen yol segmentlerini bekleyen ve hesapları bekleyen bir kodunuz varsa, bu kodu kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3a16-115">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a3a16-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a3a16-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
