---
title: Tek Boyutlu Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170357"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="5f9a2-102">Tek Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5f9a2-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5f9a2-103">Aşağıdaki örnekte gösterildiği gibi beş tamsayı tek boyutlu bir dizi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="5f9a2-104">Bu dizi, `array[0]` `array[4]`'den.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="5f9a2-105">[Yeni](../../language-reference/operators/new-operator.md) işleç dizioluşturmak ve dizi öğelerini varsayılan değerlerine çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="5f9a2-106">Bu örnekte, tüm dizi öğeleri sıfıra başlanır.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="5f9a2-107">Dize öğelerini depolayan bir dizi aynı şekilde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="5f9a2-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="5f9a2-109">Dizi Başlatma</span><span class="sxs-lookup"><span data-stu-id="5f9a2-109">Array Initialization</span></span>

 <span data-ttu-id="5f9a2-110">Bir diziyi bildirim üzerine başlatmayapmak mümkündür, bu durumda, zaten başlatma listesindeki öğe sayısı tarafından sağlandığı için uzunluk belirtici gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="5f9a2-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="5f9a2-112">Bir dize dizisi aynı şekilde başharfe bilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="5f9a2-113">Aşağıda, her dizi öğesinin bir gün adı ile başharflere verildiği bir dize dizisi bildirimi vereme sayısı veremeği ve</span><span class="sxs-lookup"><span data-stu-id="5f9a2-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="5f9a2-114">Bir diziyi bildirim üzerine başharfe aldığınızda, aşağıdaki kısayolları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="5f9a2-115">Bir dizi değişkenini başlatma olmadan bildirmek mümkündür, `new` ancak bu değişkene bir dizi atadığınızda işleci kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="5f9a2-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="5f9a2-117">C# 3.0 örtülü olarak yazılan dizileri tanır.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="5f9a2-118">Daha fazla bilgi için [bkz.](./implicitly-typed-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="5f9a2-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="5f9a2-119">Değer Türü ve Referans Türü Dizileri</span><span class="sxs-lookup"><span data-stu-id="5f9a2-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="5f9a2-120">Aşağıdaki dizi bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5f9a2-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="5f9a2-121">Bu bildirimin sonucu bir `SomeType` değer türü veya bir başvuru türü olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="5f9a2-122">Bir değer türüyse, deyim, her biri türü `SomeType`olan 10 öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="5f9a2-123">Bir `SomeType` başvuru türüyse, deyim, her biri null başvurusuna başharfle başharfe verilen 10 öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="5f9a2-124">Değer türleri ve başvuru türleri hakkında daha fazla bilgi için [Değer türleri](../../language-reference/builtin-types/value-types.md) ve [Başvuru türlerine](../../language-reference/keywords/reference-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5f9a2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9a2-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5f9a2-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5f9a2-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5f9a2-127">Diziler</span><span class="sxs-lookup"><span data-stu-id="5f9a2-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5f9a2-128">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="5f9a2-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="5f9a2-129">Basit Diziler</span><span class="sxs-lookup"><span data-stu-id="5f9a2-129">Jagged Arrays</span></span>](./jagged-arrays.md)
