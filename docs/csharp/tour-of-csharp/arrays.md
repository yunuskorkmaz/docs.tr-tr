---
title: C#Diziler- C# dilin turu
description: Diziler, C# dildeki en temel koleksiyon türüdür
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159201"
---
# <a name="arrays"></a><span data-ttu-id="d46ca-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="d46ca-103">Arrays</span></span>

<span data-ttu-id="d46ca-104">***Dizi*** , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="d46ca-105">Bir dizide bulunan değişkenler, dizi ***öğeleri*** de denir, hepsi aynı türdür ve bu tür dizinin ***öğe türü*** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="d46ca-106">Dizi türleri başvuru türlerdir ve bir dizi değişkeninin bildirimi, bir dizi örneğine yönelik bir başvuru için yalnızca alan ayırın.</span><span class="sxs-lookup"><span data-stu-id="d46ca-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="d46ca-107">Gerçek dizi örnekleri, çalışma zamanında yeni işleci kullanılarak dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d46ca-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="d46ca-108">Yeni işlem, daha sonra örneğin ömrü boyunca düzeltilen yeni dizi örneğinin ***uzunluğunu*** belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ca-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="d46ca-109">Dizi aralığının öğelerinin dizinleri `Length - 1``0`.</span><span class="sxs-lookup"><span data-stu-id="d46ca-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="d46ca-110">`new` işleci, bir dizinin öğelerini otomatik olarak varsayılan değerlerine başlatır. Bu, örneğin, tüm sayısal türler için sıfır ve tüm başvuru türleri için `null`.</span><span class="sxs-lookup"><span data-stu-id="d46ca-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="d46ca-111">Aşağıdaki örnek `int` öğelerinden oluşan bir dizi oluşturur, diziyi başlatır ve dizinin içeriğini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="d46ca-112">Bu örnek, ***tek boyutlu bir dizi***üzerinde oluşturur ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="d46ca-113">C#, ***çok boyutlu dizileri***de destekler.</span><span class="sxs-lookup"><span data-stu-id="d46ca-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="d46ca-114">Dizi türünün ***derecesi*** olarak da bilinen bir dizi türünün boyut sayısı, dizi türünün köşeli ayraçları arasına yazılan virgüllerin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="d46ca-115">Aşağıdaki örnek, sırasıyla tek boyutlu, iki boyutlu ve üç boyutlu bir diziyi ayırır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="d46ca-116">`a1` dizi 10 öğe içeriyorsa, `a2` dizisi 50 (10 × 5) öğesi içerir ve `a3` dizisi 100 (10 × 5 × 2) öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="d46ca-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="d46ca-117">Bir dizinin öğe türü, bir dizi türü de dahil olmak üzere herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="d46ca-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="d46ca-118">Dizi türündeki öğeleri içeren bir dizi, bazen öğe dizilerinin uzunluklarının tümünün aynı olması gerektiğinden ***pürüzlü dizi*** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays don't all have to be the same.</span></span> <span data-ttu-id="d46ca-119">Aşağıdaki örnek, `int`dizi dizileri ayırır:</span><span class="sxs-lookup"><span data-stu-id="d46ca-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="d46ca-120">İlk satır, her biri `int[]` her biri `null`başlangıç değeri olan üç öğe içeren bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d46ca-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="d46ca-121">Sonraki satırlar, Farklı uzunluklardaki ayrı dizi örneklerine yapılan başvurularla üç öğeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="d46ca-122">New işleci, dizi öğelerinin başlangıç değerlerinin, `{` ve `}`sınırlayıcılarının yazıldığı bir ifade listesi olan ***dizi başlatıcısı***kullanılarak belirtilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d46ca-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="d46ca-123">Aşağıdaki örnek, üç öğe ile bir `int[]` ayırır ve başlatır.</span><span class="sxs-lookup"><span data-stu-id="d46ca-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="d46ca-124">Dizinin uzunluğu {ve} arasındaki ifade sayısından çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="d46ca-124">The length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="d46ca-125">Yerel değişken ve alan bildirimleri daha fazla kısaltılarak, dizi türünün yeniden oluşturulması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d46ca-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="d46ca-126">Yukarıdaki örneklerin her ikisi de aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="d46ca-126">Both of the previous examples are equivalent to the following code:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="d46ca-127">[Önceki](classes-and-objects.md)
>[İleri](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="d46ca-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
