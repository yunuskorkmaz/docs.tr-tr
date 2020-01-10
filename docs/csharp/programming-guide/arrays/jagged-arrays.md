---
title: Pürüzlü Diziler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705710"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="61aee-102">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="61aee-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="61aee-103">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="61aee-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="61aee-104">Pürüzlü bir dizinin öğeleri farklı boyutlarda ve boyutlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="61aee-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="61aee-105">Pürüzlü bir dizi bazen "dizi dizisi" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="61aee-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="61aee-106">Aşağıdaki örneklerde, pürüzlü dizileri bildirme, başlatma ve erişme işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61aee-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="61aee-107">Aşağıda, her biri tek boyutlu tamsayılar dizisi olan üç öğesi olan tek boyutlu bir dizinin bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="61aee-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="61aee-108">`jaggedArray`kullanabilmeniz için, onun öğelerinin başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61aee-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="61aee-109">Aşağıdaki gibi öğeleri başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61aee-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="61aee-110">Öğelerin her biri, tamsayıların tek boyutlu dizisidir.</span><span class="sxs-lookup"><span data-stu-id="61aee-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="61aee-111">İlk öğe, 5 tamsayının dizisidir, ikincisi 4 tamsayının dizisidir ve üçüncüsü 2 tamsayının dizisidir.</span><span class="sxs-lookup"><span data-stu-id="61aee-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="61aee-112">Ayrıca, dizi öğelerini değerlerle doldurmanız için başlatıcıları kullanmak mümkündür, bu durumda dizi boyutuna ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="61aee-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="61aee-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="61aee-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="61aee-114">Ayrıca, aşağıdaki gibi bildirim üzerine diziyi de başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61aee-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="61aee-115">Aşağıdaki toplu formu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61aee-115">You can use the following shorthand form.</span></span> <span data-ttu-id="61aee-116">Öğeler için varsayılan başlatma olmadığından, öğelerin başlatılmasında `new` işlecini atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61aee-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="61aee-117">Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve `null`olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="61aee-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="61aee-118">Aşağıdaki örnekler gibi ayrı dizi öğelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61aee-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="61aee-119">Sivri ve çok boyutlu dizileri karıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="61aee-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="61aee-120">Aşağıda, farklı boyutlarda 3 2 boyutlu dizi öğeleri içeren tek boyutlu pürüzlü bir dizinin bildirimi ve başlatılması yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="61aee-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="61aee-121">İki boyutlu diziler hakkında daha fazla bilgi için bkz. [çok boyutlu diziler](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="61aee-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="61aee-122">Bu örnekte gösterildiği gibi ayrı öğelere erişebilirsiniz. Bu, ilk dizinin `[1,0]` öğesinin değerini gösterir (değer `5`):</span><span class="sxs-lookup"><span data-stu-id="61aee-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="61aee-123">`Length` yöntemi, pürüzlü dizide bulunan dizilerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="61aee-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="61aee-124">Örneğin, önceki diziyi bildirdiğiniz varsayılarak, bu satır:</span><span class="sxs-lookup"><span data-stu-id="61aee-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="61aee-125">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="61aee-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61aee-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="61aee-126">Example</span></span>

 <span data-ttu-id="61aee-127">Bu örnek, öğeleri kendi dizileri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61aee-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="61aee-128">Dizi öğelerinden her birinin farklı bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="61aee-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="61aee-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61aee-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="61aee-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61aee-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="61aee-131">Diziler</span><span class="sxs-lookup"><span data-stu-id="61aee-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="61aee-132">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="61aee-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="61aee-133">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="61aee-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
