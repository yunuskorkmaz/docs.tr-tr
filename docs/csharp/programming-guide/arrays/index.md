---
title: Diziler-C# Programlama Kılavuzu
description: C# ' de bir dizi veri yapısında aynı türde birden çok değişken depolayın. Bir tür belirterek veya herhangi bir türü depolamak için nesne belirttikten sonra bir dizi bildirin.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794762"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="cf53c-104">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cf53c-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="cf53c-105">Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf53c-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="cf53c-106">Öğelerinin türünü belirterek bir dizi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf53c-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="cf53c-107">Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, `object` türü olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf53c-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="cf53c-108">C# Birleşik tür sisteminde, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden devralınır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="cf53c-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="cf53c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf53c-109">Example</span></span>

<span data-ttu-id="cf53c-110">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cf53c-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="cf53c-111">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="cf53c-111">Array overview</span></span>

<span data-ttu-id="cf53c-112">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cf53c-112">An array has the following properties:</span></span>

- <span data-ttu-id="cf53c-113">Bir dizi [tek boyutlu](single-dimensional-arrays.md), [çok boyutlu](multidimensional-arrays.md) veya [pürüzlü](jagged-arrays.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf53c-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="cf53c-114">Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cf53c-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="cf53c-115">Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="cf53c-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="cf53c-116">Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cf53c-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="cf53c-117">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak başlatılır `null` .</span><span class="sxs-lookup"><span data-stu-id="cf53c-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="cf53c-118">Diziler sıfır dizinli: öğeleri olan bir dizi ' dan ' a `n` dizinlenir `0` `n-1` .</span><span class="sxs-lookup"><span data-stu-id="cf53c-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="cf53c-119">Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf53c-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="cf53c-120">Dizi türleri, soyut temel türden türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="cf53c-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="cf53c-121">Bu tür ve uyguladığından <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> , C# ' deki tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf53c-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="cf53c-122">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="cf53c-122">Arrays as Objects</span></span>

<span data-ttu-id="cf53c-123">C# ' de, diziler aslında nesneler ve yalnızca C ve C++ ' da olduğu gibi bitişik belleğin adreslenebilir bölgelerini değildir.</span><span class="sxs-lookup"><span data-stu-id="cf53c-123">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="cf53c-124"><xref:System.Array> tüm dizi türlerinin soyut temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="cf53c-124"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="cf53c-125">Özellikleri ve olan diğer sınıf üyelerini kullanabilirsiniz <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="cf53c-125">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="cf53c-126">Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="cf53c-126">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="cf53c-127">Aşağıdaki kod, dizi uzunluğunu, `numbers` yani `5` adlı bir değişkene atar `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="cf53c-127">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="cf53c-128"><xref:System.Array>Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf53c-128">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="cf53c-129">Aşağıdaki örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf53c-129">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="cf53c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf53c-130">See also</span></span>

- [<span data-ttu-id="cf53c-131">Tek boyutlu dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="cf53c-131">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="cf53c-132">Çok boyutlu dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="cf53c-132">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="cf53c-133">Pürüzlü dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="cf53c-133">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="cf53c-134">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="cf53c-134">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="cf53c-135">Dizileri bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="cf53c-135">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="cf53c-136">Örtük olarak yazılan diziler</span><span class="sxs-lookup"><span data-stu-id="cf53c-136">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="cf53c-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cf53c-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cf53c-138">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="cf53c-138">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
