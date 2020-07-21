---
title: Diziler-C# Programlama Kılavuzu
description: C# ' de bir dizi veri yapısında aynı türde birden çok değişken depolayın. Bir tür belirterek veya herhangi bir türü depolamak için nesne belirttikten sonra bir dizi bildirin.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474741"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="5d832-104">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5d832-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5d832-105">Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d832-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="5d832-106">Öğelerinin türünü belirterek bir dizi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d832-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="5d832-107">Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, `object` türü olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d832-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="5d832-108">C# Birleşik tür sisteminde, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden devralınır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="5d832-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="5d832-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d832-109">Example</span></span>

<span data-ttu-id="5d832-110">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5d832-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="5d832-111">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="5d832-111">Array overview</span></span>

<span data-ttu-id="5d832-112">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5d832-112">An array has the following properties:</span></span>

- <span data-ttu-id="5d832-113">Bir dizi [tek boyutlu](single-dimensional-arrays.md), [çok boyutlu](multidimensional-arrays.md) veya [pürüzlü](jagged-arrays.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d832-113">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="5d832-114">Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d832-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="5d832-115">Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5d832-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="5d832-116">Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5d832-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="5d832-117">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak başlatılır `null` .</span><span class="sxs-lookup"><span data-stu-id="5d832-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="5d832-118">Diziler sıfır dizinli: öğeleri olan bir dizi ' dan ' a `n` dizinlenir `0` `n-1` .</span><span class="sxs-lookup"><span data-stu-id="5d832-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="5d832-119">Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d832-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="5d832-120">Dizi türleri, soyut temel türden türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="5d832-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="5d832-121">Bu tür ve uyguladığından <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> , C# ' deki tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d832-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5d832-122">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="5d832-122">Related sections</span></span>

- [<span data-ttu-id="5d832-123">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="5d832-123">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="5d832-124">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="5d832-124">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="5d832-125">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="5d832-125">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="5d832-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5d832-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5d832-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d832-127">See also</span></span>

- [<span data-ttu-id="5d832-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d832-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5d832-129">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="5d832-129">Collections</span></span>](../concepts/collections.md)
