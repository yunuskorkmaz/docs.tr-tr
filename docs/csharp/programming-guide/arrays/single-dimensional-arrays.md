---
title: Tek boyutlu diziler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 8f093d22da789c6df750475e47a3b4e4685c5651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744202"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="1c231-102">Tek Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1c231-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1c231-103">Aşağıdaki örnekte gösterildiği gibi, beş tamsayının tek boyutlu bir dizisini bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c231-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="1c231-104">Bu dizi `array[4]``array[0]` öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1c231-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="1c231-105">[New](../../language-reference/operators/new-operator.md) işleci diziyi oluşturmak için kullanılır ve dizi öğelerini varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="1c231-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="1c231-106">Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1c231-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="1c231-107">Dize öğelerini depolayan bir dizi aynı şekilde bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="1c231-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="1c231-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1c231-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="1c231-109">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="1c231-109">Array Initialization</span></span>

 <span data-ttu-id="1c231-110">Bildirim üzerine bir diziyi başlatmak mümkündür, bu durumda, başlatma listesindeki öğe sayısı tarafından zaten sağlandığı için uzunluk belirleyicisi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1c231-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="1c231-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1c231-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="1c231-112">Dize dizisi aynı şekilde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c231-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="1c231-113">Aşağıda her dizi öğesinin bir günün adı ile başlatıldığı bir dize dizisinin bildirimi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1c231-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="1c231-114">Bildirim üzerine bir diziyi başlattığınızda, aşağıdaki kısayolları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1c231-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="1c231-115">Başlatma olmadan bir dizi değişkeni bildirmek mümkündür, ancak bu değişkene bir dizi atadığınızda `new` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c231-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="1c231-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1c231-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="1c231-117">C#3,0 örtük olarak yazılmış dizileri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="1c231-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="1c231-118">Daha fazla bilgi için bkz. [örtülü olarak yazılan diziler](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1c231-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="1c231-119">Değer türü ve başvuru türü dizileri</span><span class="sxs-lookup"><span data-stu-id="1c231-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="1c231-120">Aşağıdaki dizi bildirimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1c231-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="1c231-121">Bu deyimin sonucu, `SomeType` bir değer türü veya bir başvuru türü olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c231-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="1c231-122">Değer bir tür ise, ifade, her birinin türü `SomeType`olan 10 öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c231-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="1c231-123">`SomeType` bir başvuru türü ise, ifade her biri null başvuruya başlatılan 10 öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c231-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="1c231-124">Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/builtin-types/value-types.md) ve [başvuru türleri](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1c231-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1c231-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c231-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="1c231-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1c231-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1c231-127">Diziler</span><span class="sxs-lookup"><span data-stu-id="1c231-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="1c231-128">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="1c231-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="1c231-129">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="1c231-129">Jagged Arrays</span></span>](./jagged-arrays.md)
