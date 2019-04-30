---
title: Tek boyutlu diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 719e4463806c9c7e8b5407f2494c3b548ffa43e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61684035"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="48088-102">Tek Boyutlu Diziler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="48088-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="48088-103">Aşağıdaki örnekte gösterildiği gibi beş tamsayı tek boyutlu bir dizi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="48088-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="48088-104">Bu dizinin öğeleri içeren `array[0]` için `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="48088-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="48088-105">[Yeni](../../../csharp/language-reference/keywords/new.md) işleci dizi oluşturmak ve varsayılan değerlerine dizi öğelerini başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48088-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="48088-106">Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="48088-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="48088-107">Dize öğesi depolayan bir dizi aynı şekilde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="48088-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="48088-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="48088-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="48088-109">Dizi başlatma</span><span class="sxs-lookup"><span data-stu-id="48088-109">Array Initialization</span></span>

 <span data-ttu-id="48088-110">Bildirimi, bağlı bir diziyi başlatmaya mümkündür, bu durumda uzunluğu tanımlayıcısı gerekli değildir çünkü zaten başlatma listedeki öğelerin sayısı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48088-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="48088-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="48088-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="48088-112">Dize dizisi aynı şekilde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="48088-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="48088-113">Bir dize dizisi bildirimi her dizi öğesi günün bir adı nerede başlatılır verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="48088-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="48088-114">Bir dizi bildirimi üzerine başlattığınızda, aşağıdaki kısayolları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="48088-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="48088-115">Bir dizi değişkeni başlatma olmadan belirtmek mümkündür, ancak kullanmalısınız `new` Bu değişken için bir dizi atadığınızda işleci.</span><span class="sxs-lookup"><span data-stu-id="48088-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="48088-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="48088-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="48088-117">C# 3.0, örtük olarak yazılan diziler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="48088-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="48088-118">Daha fazla bilgi için [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="48088-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="48088-119">Değer türü ve referans türü diziler</span><span class="sxs-lookup"><span data-stu-id="48088-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="48088-120">Aşağıdaki dizi bildirimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="48088-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="48088-121">Bu ifade sonucu bağlıdır `SomeType` bir değer türü veya bir başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="48088-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="48088-122">Bir değer türü ise, her biri türüne sahip bir dizi 10 öğelerin deyimi oluşturur `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="48088-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="48088-123">Varsa `SomeType` bir başvuru türüdür deyimi her biri için bir null başvuru başlatılır 10 öğe, bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48088-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="48088-124">Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [türleri](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="48088-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48088-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48088-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="48088-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="48088-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="48088-127">Diziler</span><span class="sxs-lookup"><span data-stu-id="48088-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="48088-128">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="48088-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="48088-129">Düzensiz Diziler</span><span class="sxs-lookup"><span data-stu-id="48088-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
