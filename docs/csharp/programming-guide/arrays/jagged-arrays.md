---
title: Basit diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 9fc05c8bdebf9c1c6b613db0b6a121e06765ac00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652006"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="709ea-102">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="709ea-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="709ea-103">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="709ea-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="709ea-104">Düzensiz bir dizi öğelerinden farklı boyutları ve boyutları olabilir.</span><span class="sxs-lookup"><span data-stu-id="709ea-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="709ea-105">Basit bir dizi bazen "oluşan bir dizi." olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="709ea-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="709ea-106">Aşağıdaki örnekler nasıl bildirin, başlatmak ve erişimi, diziler basit.</span><span class="sxs-lookup"><span data-stu-id="709ea-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="709ea-107">Her biri tek boyutlu dizisi olan üç öğeye sahip bir tek boyutlu dizi bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="709ea-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="709ea-108">Kullanmadan önce `jaggedArray`, öğeleri başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="709ea-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="709ea-109">Bunun gibi öğelerin başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="709ea-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="709ea-110">Öğelerin her biri, tamsayı tek boyutlu bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="709ea-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="709ea-111">İlk öğe 5 tamsayı dizisi, ikinci 4 tamsayı dizisi ve üçüncü 2 tamsayılar dizisidir.</span><span class="sxs-lookup"><span data-stu-id="709ea-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="709ea-112">Dizi öğeleri değerlerle doldurmak için başlatıcılar kullanmak da mümkündür, bu durumda, dizi boyutu ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="709ea-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="709ea-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="709ea-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="709ea-114">Ayrıca, dizi bildirimi böyle üzerine başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="709ea-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="709ea-115">Aşağıdaki toplu formu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="709ea-115">You can use the following shorthand form.</span></span> <span data-ttu-id="709ea-116">Dikkat edin, atlayamazsınız `new` öğeleri başlatma operatöründen olmadığı için öğeler için varsayılan başlatma:</span><span class="sxs-lookup"><span data-stu-id="709ea-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="709ea-117">Düzensiz bir dizi, dizilerin bir dizidir ve bu nedenle öğeleri başvuru türleridir ve başlatılır `null`.</span><span class="sxs-lookup"><span data-stu-id="709ea-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="709ea-118">Bu örnekler gibi tek bir dizi öğelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="709ea-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="709ea-119">Basit ve çok boyutlu diziler karıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="709ea-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="709ea-120">Bir bildirimi ve başlatılması farklı boyutlardaki üç iki boyutlu dizi öğeleri içeren tek boyutlu bir düzensiz dizi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="709ea-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="709ea-121">İki boyutlu dizileri hakkında daha fazla bilgi için bkz: [çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="709ea-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="709ea-122">Öğenin değeri görüntüler bu örnekte gösterildiği gibi tek tek öğelerine erişebilirsiniz `[1,0]` ilk dizinin (değer `5`):</span><span class="sxs-lookup"><span data-stu-id="709ea-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="709ea-123">Yöntem `Length` diziler düzensiz dizi içinde yer alan sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="709ea-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="709ea-124">Bu satır önceki dizinin derlendiğinden varsayılarak örneğin:</span><span class="sxs-lookup"><span data-stu-id="709ea-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="709ea-125">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="709ea-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="709ea-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="709ea-126">Example</span></span>

 <span data-ttu-id="709ea-127">Bu örnek, dizileri kendilerini öğeleri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="709ea-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="709ea-128">Dizi öğelerinin her biri farklı bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="709ea-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="709ea-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="709ea-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="709ea-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="709ea-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="709ea-131">Diziler</span><span class="sxs-lookup"><span data-stu-id="709ea-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="709ea-132">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="709ea-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="709ea-133">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="709ea-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
