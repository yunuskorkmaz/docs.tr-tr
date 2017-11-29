---
title: "Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cdd319ef6bbb296c7afa5195563b92bdd361f0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="287cf-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="287cf-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="287cf-103">Bir dizi veri yapısında aynı türde birden fazla değişken depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="287cf-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="287cf-104">Dizi öğeleri türü belirterek bildirin.</span><span class="sxs-lookup"><span data-stu-id="287cf-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="287cf-105">Aşağıdaki örnekler tek boyutlu, çok boyutlu ve basit diziler oluşturun:</span><span class="sxs-lookup"><span data-stu-id="287cf-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="287cf-106">Dizi genel bakış</span><span class="sxs-lookup"><span data-stu-id="287cf-106">Array Overview</span></span>  
 <span data-ttu-id="287cf-107">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="287cf-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="287cf-108">Bir dizi olabilir [tek boyutlu](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [çok boyutlu](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) veya [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="287cf-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="287cf-109">Array örneği oluşturulduğunda boyut sayısını ve her boyutun uzunluğu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="287cf-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="287cf-110">Örneğin ömrü boyunca bu değerler değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="287cf-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="287cf-111">Varsayılan değerleri sayısal dizi öğelerinin sıfıra ayarlanır ve başvuru öğeleri ayarlanır null.</span><span class="sxs-lookup"><span data-stu-id="287cf-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="287cf-112">Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.</span><span class="sxs-lookup"><span data-stu-id="287cf-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="287cf-113">Dizi dizini sıfır olan: sahip bir dizi `n` öğeleri dizine `0` için `n-1`.</span><span class="sxs-lookup"><span data-stu-id="287cf-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="287cf-114">Dizi öğeleri bir dizi türü de dahil olmak üzere, herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="287cf-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="287cf-115">Dizi türleri [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md) soyut taban türünden türetilmiş <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="287cf-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="287cf-116">Bu tür uygulayan beri <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>, kullanabileceğiniz [foreach](../../../csharp/language-reference/keywords/foreach-in.md) yineleme tüm diziler C# üzerinde.</span><span class="sxs-lookup"><span data-stu-id="287cf-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="287cf-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="287cf-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="287cf-118">Nesne olarak diziler</span><span class="sxs-lookup"><span data-stu-id="287cf-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="287cf-119">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="287cf-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="287cf-120">Dizileri bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="287cf-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="287cf-121">Dizileri kullanma ref ve out geçirme</span><span class="sxs-lookup"><span data-stu-id="287cf-121">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="287cf-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="287cf-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="287cf-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="287cf-123">See Also</span></span>  
 [<span data-ttu-id="287cf-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="287cf-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="287cf-125">Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="287cf-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="287cf-126">Dizi koleksiyon türü</span><span class="sxs-lookup"><span data-stu-id="287cf-126">Array Collection Type</span></span>](http://msdn.microsoft.com/en-us/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
