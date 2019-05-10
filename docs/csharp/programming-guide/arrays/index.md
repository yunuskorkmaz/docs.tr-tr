---
title: Diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 258ade63ab7c9008f6c892ed109bf5ea5ab974f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584601"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="271e8-102">Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="271e8-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="271e8-103">Bir dizi veri yapısında aynı türde birden fazla değişken depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="271e8-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="271e8-104">Bir diziyi, öğelerinin türünü belirterek bildirin.</span><span class="sxs-lookup"><span data-stu-id="271e8-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="271e8-105">Aşağıdaki örnek, tek boyutlu, çok boyutlu ve düzensiz diziler oluşturur:</span><span class="sxs-lookup"><span data-stu-id="271e8-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="271e8-106">Diziye genel bakış</span><span class="sxs-lookup"><span data-stu-id="271e8-106">Array Overview</span></span>

 <span data-ttu-id="271e8-107">Bir dizi aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="271e8-107">An array has the following properties:</span></span>  
  
- <span data-ttu-id="271e8-108">Bir dizi olabilir [tek boyutlu](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [çok boyutlu](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) veya [düzensiz](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="271e8-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
- <span data-ttu-id="271e8-109">Boyutların sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="271e8-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="271e8-110">Bu değerler örneğin kullanım süresi boyunca değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="271e8-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
- <span data-ttu-id="271e8-111">Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri ayarlanmış null.</span><span class="sxs-lookup"><span data-stu-id="271e8-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
- <span data-ttu-id="271e8-112">Düzensiz bir dizi, dizilerin bir dizidir ve bu nedenle öğeleri başvuru türleridir ve başlatılır `null`.</span><span class="sxs-lookup"><span data-stu-id="271e8-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
- <span data-ttu-id="271e8-113">Diziler sıfır dizinlidir şunlardır: bir diziyi `n` öğeleri arasında dizinlenir `0` için `n-1`.</span><span class="sxs-lookup"><span data-stu-id="271e8-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
- <span data-ttu-id="271e8-114">Dizi öğeleri, bir dizi türü de dahil olmak üzere, herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="271e8-114">Array elements can be of any type, including an array type.</span></span>  
  
- <span data-ttu-id="271e8-115">Dizi türleri, [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md) soyut temel türünden türetilmiş <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="271e8-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="271e8-116">Bu tür uyguladığından <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>, kullanabileceğiniz [foreach](../../../csharp/language-reference/keywords/foreach-in.md) C# içindeki dizilerde yineleme.</span><span class="sxs-lookup"><span data-stu-id="271e8-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="271e8-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="271e8-117">Related Sections</span></span>  
  
- [<span data-ttu-id="271e8-118">Nesne Olarak Diziler</span><span class="sxs-lookup"><span data-stu-id="271e8-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
- [<span data-ttu-id="271e8-119">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="271e8-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
- [<span data-ttu-id="271e8-120">Dizileri Bağımsız Değişkenler Olarak Geçirme</span><span class="sxs-lookup"><span data-stu-id="271e8-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="271e8-121">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="271e8-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="271e8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="271e8-122">See also</span></span>

- [<span data-ttu-id="271e8-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="271e8-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="271e8-124">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="271e8-124">Collections</span></span>](../../../csharp/programming-guide/concepts/collections.md)
