---
title: Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715051"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="4e1c6-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4e1c6-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="4e1c6-103">Aynı türdeki birden çok değişkeni bir dizi veri yapısında depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="4e1c6-104">Öğelerinin türünü belirterek bir dizi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="4e1c6-105">Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, dizinin türü olarak belirtebilirsiniz. `object`</span><span class="sxs-lookup"><span data-stu-id="4e1c6-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="4e1c6-106">C#'ın birleşik tip sisteminde, önceden tanımlanmış ve kullanıcı tarafından tanımlanan tüm türler, referans <xref:System.Object>türleri ve değer türleri, doğrudan veya dolaylı olarak .</span><span class="sxs-lookup"><span data-stu-id="4e1c6-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="4e1c6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e1c6-107">Example</span></span>

<span data-ttu-id="4e1c6-108">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="4e1c6-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="4e1c6-109">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="4e1c6-109">Array overview</span></span>

<span data-ttu-id="4e1c6-110">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4e1c6-110">An array has the following properties:</span></span>

- <span data-ttu-id="4e1c6-111">Bir dizi [Tek Boyutlu,](single-dimensional-arrays.md) [Çok Boyutlu](multidimensional-arrays.md) veya [Pürüzlü](jagged-arrays.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="4e1c6-112">Dizi örneği oluşturulduğunda boyut sayısı ve her boyutun uzunluğu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="4e1c6-113">Bu değerler, örneğin ömrü boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="4e1c6-114">Sayısal dizi öğelerinin varsayılan değerleri sıfıra, başvuru öğeleri null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="4e1c6-115">Pürüzlü bir dizi dizi dizidir ve bu nedenle öğeleri başvuru `null`türleridir ve '' için başharfler.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="4e1c6-116">Diziler sıfır dizilimi vardır: öğeleri `n` olan `0` `n-1`bir dizi ' den .</span><span class="sxs-lookup"><span data-stu-id="4e1c6-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="4e1c6-117">Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="4e1c6-118">Dizi türleri soyut temel türünden <xref:System.Array>türetilen başvuru [türleridir.](../../language-reference/keywords/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="4e1c6-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="4e1c6-119">Bu tür uygular <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>ve , C# tüm dizileri [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4e1c6-120">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="4e1c6-120">Related sections</span></span>

- [<span data-ttu-id="4e1c6-121">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="4e1c6-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="4e1c6-122">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="4e1c6-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="4e1c6-123">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="4e1c6-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="4e1c6-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4e1c6-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e1c6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e1c6-125">See also</span></span>

- [<span data-ttu-id="4e1c6-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e1c6-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4e1c6-127">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="4e1c6-127">Collections</span></span>](../concepts/collections.md)
