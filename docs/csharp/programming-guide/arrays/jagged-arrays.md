---
title: Basit Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297374"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="9e46b-102">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9e46b-102">Jagged Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="9e46b-103">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="9e46b-104">Basit bir dizinin öğeleri farklı boyutları ve boyutları olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="9e46b-105">Basit dizi bazen "oluşan bir dizi." olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="9e46b-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="9e46b-106">Aşağıdaki örnekler bildirmek üzere, başlatmak ve diziler erişim basit.</span><span class="sxs-lookup"><span data-stu-id="9e46b-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="9e46b-107">Her biri tek boyutlu dizisi olan üç öğeye sahip bir tek boyutlu dizi bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e46b-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="9e46b-108">Kullanmadan önce `jaggedArray`, öğeleri başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="9e46b-109">Bu gibi öğeleri başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e46b-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="9e46b-110">Her öğe tek boyutlu dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="9e46b-111">İlk öğe 5 dizisi ikinci 4 dizisi ve üçüncü 2 tamsayılar dizisidir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="9e46b-112">Dizi öğeleri değerlerle doldurmak için başlatıcıları kullanmak da mümkündür, bu durumda, dizi büyüklüğü gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9e46b-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="9e46b-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9e46b-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="9e46b-114">Dizi bildirimi şöyle üzerine de başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e46b-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="9e46b-115">Aşağıdaki toplu formu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e46b-115">You can use the following shorthand form.</span></span> <span data-ttu-id="9e46b-116">Atlayamazsınız bildirimi `new` öğeleri başlatma operatöründen öğeleri için hiçbir varsayılan başlatma olduğundan:</span><span class="sxs-lookup"><span data-stu-id="9e46b-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="9e46b-117">Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.</span><span class="sxs-lookup"><span data-stu-id="9e46b-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="9e46b-118">Bu örnekler gibi tek bir dizi öğeleri erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e46b-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="9e46b-119">Basit ve çok boyutlu diziler karıştırmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9e46b-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="9e46b-120">Bir bildirim ve başlatma dizisinin farklı boyutlarda üç iki boyutlu dizi öğelerini içeren bir tek boyutlu basit verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e46b-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="9e46b-121">İki boyutlu diziler hakkında daha fazla bilgi için bkz: [çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="9e46b-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="9e46b-122">Öğesinin değerini görüntüler bu örnekte gösterildiği gibi ayrı ayrı öğeler erişebilirsiniz `[1,0]` ilk dizi (değer `5`):</span><span class="sxs-lookup"><span data-stu-id="9e46b-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="9e46b-123">Yöntem `Length` basit dizinin içindeki diziler sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e46b-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="9e46b-124">Bu satırı önceki dizi bildirilen varsayılarak örneğin:</span><span class="sxs-lookup"><span data-stu-id="9e46b-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="9e46b-125">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e46b-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e46b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e46b-126">Example</span></span>  
 <span data-ttu-id="9e46b-127">Bu örnek diziler kendilerini öğeleri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e46b-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="9e46b-128">Dizi öğelerin her biri farklı bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="9e46b-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9e46b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e46b-129">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="9e46b-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e46b-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e46b-131">Diziler</span><span class="sxs-lookup"><span data-stu-id="9e46b-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="9e46b-132">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="9e46b-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="9e46b-133">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="9e46b-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
