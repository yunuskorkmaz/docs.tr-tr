---
title: Diziler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715051"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="0fdcd-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0fdcd-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="0fdcd-103">Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="0fdcd-104">Öğelerinin türünü belirterek bir dizi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="0fdcd-105">Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, türü olarak `object` belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="0fdcd-106">Birleşik tür sisteminde C#, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, <xref:System.Object>doğrudan veya dolaylı olarak devralınır.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="0fdcd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fdcd-107">Example</span></span>

<span data-ttu-id="0fdcd-108">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0fdcd-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="0fdcd-109">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="0fdcd-109">Array overview</span></span>

<span data-ttu-id="0fdcd-110">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0fdcd-110">An array has the following properties:</span></span>

- <span data-ttu-id="0fdcd-111">Bir dizi [tek boyutlu](single-dimensional-arrays.md), [çok boyutlu](multidimensional-arrays.md) veya [pürüzlü](jagged-arrays.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="0fdcd-112">Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="0fdcd-113">Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="0fdcd-114">Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="0fdcd-115">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve `null`olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="0fdcd-116">Diziler sıfır dizinli: `n` öğeler içeren bir dizi `0` `n-1`olarak dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="0fdcd-117">Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="0fdcd-118">Dizi türleri, <xref:System.Array>soyut temel türünden türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="0fdcd-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="0fdcd-119">Bu tür <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>uyguladığından, içindeki C#tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0fdcd-120">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="0fdcd-120">Related sections</span></span>

- [<span data-ttu-id="0fdcd-121">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="0fdcd-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="0fdcd-122">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="0fdcd-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="0fdcd-123">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="0fdcd-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="0fdcd-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0fdcd-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0fdcd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fdcd-125">See also</span></span>

- [<span data-ttu-id="0fdcd-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0fdcd-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0fdcd-127">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="0fdcd-127">Collections</span></span>](../concepts/collections.md)
