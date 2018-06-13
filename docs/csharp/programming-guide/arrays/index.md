---
title: Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e01b9463eca88858633b847be256ae5b063459b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313507"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="e7ce3-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e7ce3-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="e7ce3-103">Bir dizi veri yapısında aynı türde birden fazla değişken depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="e7ce3-104">Dizi öğeleri türü belirterek bildirin.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="e7ce3-105">Aşağıdaki örnekler tek boyutlu, çok boyutlu ve basit diziler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e7ce3-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="e7ce3-106">Dizi genel bakış</span><span class="sxs-lookup"><span data-stu-id="e7ce3-106">Array Overview</span></span>  
 <span data-ttu-id="e7ce3-107">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e7ce3-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="e7ce3-108">Bir dizi olabilir [tek boyutlu](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [çok boyutlu](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) veya [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e7ce3-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="e7ce3-109">Array örneği oluşturulduğunda boyut sayısını ve her boyutun uzunluğu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="e7ce3-110">Örneğin ömrü boyunca bu değerler değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="e7ce3-111">Varsayılan değerleri sayısal dizi öğelerinin sıfıra ayarlanır ve başvuru öğeleri ayarlanır null.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="e7ce3-112">Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="e7ce3-113">Dizi dizini sıfır olan: sahip bir dizi `n` öğeleri dizine `0` için `n-1`.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="e7ce3-114">Dizi öğeleri bir dizi türü de dahil olmak üzere, herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="e7ce3-115">Dizi türleri [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md) soyut taban türünden türetilmiş <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="e7ce3-116">Bu tür uygulayan beri <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>, kullanabileceğiniz [foreach](../../../csharp/language-reference/keywords/foreach-in.md) yineleme tüm diziler C# üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7ce3-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e7ce3-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="e7ce3-118">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="e7ce3-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="e7ce3-119">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="e7ce3-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="e7ce3-120">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="e7ce3-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="e7ce3-121">ref ve out Kullanarak Dizileri Geçirme</span><span class="sxs-lookup"><span data-stu-id="e7ce3-121">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="e7ce3-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e7ce3-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7ce3-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ce3-123">See Also</span></span>  
 [<span data-ttu-id="e7ce3-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7ce3-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e7ce3-125">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="e7ce3-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="e7ce3-126">Dizi koleksiyon türü</span><span class="sxs-lookup"><span data-stu-id="e7ce3-126">Array Collection Type</span></span>](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
