---
title: Pürüzlü Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705710"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="fcb4e-102">Basit Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fcb4e-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fcb4e-103">Basit bir dizi, öğeleri dizi olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="fcb4e-104">Pürüzlü bir dizinin öğeleri farklı boyut ve boyutlarda olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="fcb4e-105">Pürüzlü bir dizi bazen "diziler dizisi" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="fcb4e-106">Aşağıdaki örnekler, pürüzlü dizileri nasıl bildirecek, başharfe bildirecek ve bunlara erişeceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="fcb4e-107">Aşağıda, her biri tek boyutlu bir tamsayı dizisi olan üç öğeye sahip tek boyutlu bir dizinin bildirimi veremi ve</span><span class="sxs-lookup"><span data-stu-id="fcb4e-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="fcb4e-108">Kullanmadan `jaggedArray`önce, öğeleri nin baş harfe byönelik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="fcb4e-109">Aşağıdaki gibi öğeleri başlangıç yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="fcb4e-110">Öğelerin her biri tamsayılar tek boyutlu bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="fcb4e-111">İlk öğe 5 tümseci, ikinci 4 tümseci bir dizi ve üçüncü 2 tümsek bir dizi.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="fcb4e-112">Dizi öğelerini değerlerle doldurmak için baş harflerini kullanmak da mümkündür, bu durumda dizi boyutuna ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="fcb4e-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="fcb4e-114">Ayrıca, aşağıdaki gibi bir bildirim üzerine diziyi de başolarak alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="fcb4e-115">Aşağıdaki steno formunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-115">You can use the following shorthand form.</span></span> <span data-ttu-id="fcb4e-116">Öğeler için varsayılan bir `new` başlatma olmadığından işleci eleman başlatmadan atlayamayacağınıza dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="fcb4e-117">Pürüzlü bir dizi dizi dizidir ve bu nedenle öğeleri başvuru `null`türleridir ve '' için başharfler.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="fcb4e-118">Aşağıdaki örnekler gibi tek tek dizi öğelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="fcb4e-119">Pürüzlü ve çok boyutlu dizileri karıştırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="fcb4e-120">Aşağıda, farklı boyutlarda üç iki boyutlu dizi öğesi içeren tek boyutlu pürüzlü bir dizinin bildirimi ve başlatılması dır.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="fcb4e-121">İki boyutlu diziler hakkında daha fazla bilgi için [çok boyutlu diziler'e](./multidimensional-arrays.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="fcb4e-122">İlk dizi (değer) `[1,0]` `5`öğesinin değerini görüntüleyen bu örnekte gösterildiği gibi tek tek öğelere erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="fcb4e-123">Yöntem, `Length` pürüzlü dizide bulunan dizi sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="fcb4e-124">Örneğin, önceki diziyi beyan ettiğinizi varsayarsak, bu satır:</span><span class="sxs-lookup"><span data-stu-id="fcb4e-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="fcb4e-125">3 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb4e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcb4e-126">Example</span></span>

 <span data-ttu-id="fcb4e-127">Bu örnek, öğeleri kendileri dizileri olan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="fcb4e-128">Dizi öğelerinin her birinin farklı bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb4e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="fcb4e-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fcb4e-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fcb4e-131">Diziler</span><span class="sxs-lookup"><span data-stu-id="fcb4e-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="fcb4e-132">Tek Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="fcb4e-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="fcb4e-133">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="fcb4e-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
