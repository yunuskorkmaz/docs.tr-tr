---
title: "Basit Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f74eaf5334e8e2198f7a058717a4eb2ff0c1e775
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="bb9e3-102">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bb9e3-102">Jagged Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="bb9e3-103">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="bb9e3-104">Basit bir dizinin öğeleri farklı boyutları ve boyutları olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="bb9e3-105">Basit dizi bazen "oluşan bir dizi." olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="bb9e3-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="bb9e3-106">Aşağıdaki örnekler bildirmek üzere, başlatmak ve diziler erişim basit.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="bb9e3-107">Her biri tek boyutlu dizisi olan üç öğeye sahip bir tek boyutlu dizi bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="bb9e3-108">Kullanmadan önce `jaggedArray`, öğeleri başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="bb9e3-109">Bu gibi öğeleri başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="bb9e3-110">Her öğe tek boyutlu dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="bb9e3-111">İlk öğe 5 dizisi ikinci 4 dizisi ve üçüncü 2 tamsayılar dizisidir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="bb9e3-112">Dizi öğeleri değerlerle doldurmak için başlatıcıları kullanmak da mümkündür, bu durumda, dizi büyüklüğü gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="bb9e3-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="bb9e3-114">Dizi bildirimi şöyle üzerine de başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="bb9e3-115">Aşağıdaki toplu formu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-115">You can use the following shorthand form.</span></span> <span data-ttu-id="bb9e3-116">Atlayamazsınız bildirimi `new` öğeleri başlatma operatöründen öğeleri için hiçbir varsayılan başlatma olduğundan:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="bb9e3-117">Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="bb9e3-118">Bu örnekler gibi tek bir dizi öğeleri erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="bb9e3-119">Basit ve çok boyutlu diziler karıştırmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="bb9e3-120">Bir bildirim ve başlatma dizisinin farklı boyutlarda üç iki boyutlu dizi öğelerini içeren bir tek boyutlu basit verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="bb9e3-121">İki boyutlu diziler hakkında daha fazla bilgi için bkz: [çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bb9e3-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="bb9e3-122">Öğesinin değerini görüntüler bu örnekte gösterildiği gibi ayrı ayrı öğeler erişebilirsiniz `[1,0]` ilk dizi (değer `5`):</span><span class="sxs-lookup"><span data-stu-id="bb9e3-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="bb9e3-123">Yöntem `Length` basit dizinin içindeki diziler sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="bb9e3-124">Bu satırı önceki dizi bildirilen varsayılarak örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb9e3-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="bb9e3-125">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb9e3-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb9e3-126">Example</span></span>  
 <span data-ttu-id="bb9e3-127">Bu örnek diziler kendilerini öğeleri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="bb9e3-128">Dizi öğelerin her biri farklı bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bb9e3-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb9e3-129">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="bb9e3-130">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bb9e3-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb9e3-131">Diziler</span><span class="sxs-lookup"><span data-stu-id="bb9e3-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="bb9e3-132">Tek boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="bb9e3-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="bb9e3-133">Çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="bb9e3-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
