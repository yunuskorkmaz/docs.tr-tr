---
title: Pürüzlü Diziler-C# Programlama Kılavuzu
description: C# ' deki pürüzlü bir dizi, öğeleri farklı boyut ve boyutlarda diziler olan bir dizidir. Pürüzlü dizileri tanımlamayı, başlatmayı ve erişmeyi öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 40da9fbda34aef4e69ebf2ae20485e883b79f871
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474689"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="31544-104">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="31544-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="31544-105">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="31544-105">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="31544-106">Pürüzlü bir dizinin öğeleri farklı boyutlarda ve boyutlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="31544-106">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="31544-107">Pürüzlü bir dizi bazen "dizi dizisi" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="31544-107">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="31544-108">Aşağıdaki örneklerde, pürüzlü dizileri bildirme, başlatma ve erişme işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31544-108">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="31544-109">Aşağıda, her biri tek boyutlu tamsayılar dizisi olan üç öğesi olan tek boyutlu bir dizinin bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="31544-109">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="31544-110">Kullanabilmeniz için `jaggedArray` , öğesinin öğelerinin başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31544-110">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="31544-111">Aşağıdaki gibi öğeleri başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31544-111">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="31544-112">Öğelerin her biri, tamsayıların tek boyutlu dizisidir.</span><span class="sxs-lookup"><span data-stu-id="31544-112">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="31544-113">İlk öğe, 5 tamsayının dizisidir, ikincisi 4 tamsayının dizisidir ve üçüncüsü 2 tamsayının dizisidir.</span><span class="sxs-lookup"><span data-stu-id="31544-113">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="31544-114">Ayrıca, dizi öğelerini değerlerle doldurmanız için başlatıcıları kullanmak mümkündür, bu durumda dizi boyutuna ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="31544-114">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="31544-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="31544-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="31544-116">Ayrıca, aşağıdaki gibi bildirim üzerine diziyi de başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31544-116">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="31544-117">Aşağıdaki toplu formu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31544-117">You can use the following shorthand form.</span></span> <span data-ttu-id="31544-118">`new`Öğeler için varsayılan başlatma olmadığından öğe başlatmasında operatörü atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="31544-118">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="31544-119">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak başlatılır `null` .</span><span class="sxs-lookup"><span data-stu-id="31544-119">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="31544-120">Aşağıdaki örnekler gibi ayrı dizi öğelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31544-120">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="31544-121">Sivri ve çok boyutlu dizileri karıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="31544-121">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="31544-122">Aşağıda, farklı boyutlarda 3 2 boyutlu dizi öğeleri içeren tek boyutlu pürüzlü bir dizinin bildirimi ve başlatılması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="31544-122">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="31544-123">İki boyutlu diziler hakkında daha fazla bilgi için bkz. [çok boyutlu diziler](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="31544-123">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="31544-124">Bu örnekte gösterildiği gibi, her bir öğeye, `[1,0]` ilk dizinin (değer) öğesinin değerini görüntüleyen tek bir erişebilirsiniz `5` :</span><span class="sxs-lookup"><span data-stu-id="31544-124">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="31544-125">Yöntemi, `Length` pürüzlü dizide bulunan dizilerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="31544-125">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="31544-126">Örneğin, önceki diziyi bildirdiğiniz varsayılarak, bu satır:</span><span class="sxs-lookup"><span data-stu-id="31544-126">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="31544-127">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="31544-127">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31544-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="31544-128">Example</span></span>

 <span data-ttu-id="31544-129">Bu örnek, öğeleri kendi dizileri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31544-129">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="31544-130">Dizi öğelerinden her birinin farklı bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="31544-130">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="31544-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31544-131">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="31544-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31544-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31544-133">Diziler</span><span class="sxs-lookup"><span data-stu-id="31544-133">Arrays</span></span>](./index.md)
- [<span data-ttu-id="31544-134">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="31544-134">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="31544-135">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="31544-135">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
