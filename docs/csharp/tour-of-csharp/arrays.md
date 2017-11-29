---
title: C# diziler - C# dili turu
description: "Dizi en temel C# dili koleksiyon türü olan"
keywords: .NET, csharp, dizi, koleksiyonu
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a><span data-ttu-id="1157d-104">Diziler</span><span class="sxs-lookup"><span data-stu-id="1157d-104">Arrays</span></span>

<span data-ttu-id="1157d-105">Bir ***dizi*** içeren bir dizi hesaplanan dizinlerini erişilen değişken bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="1157d-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="1157d-106">Bir dizinin içindeki değişkenleri olarak da bilinir ***öğeleri*** dizinin tümü aynı türde ve bu tür adlı ***öğe türü*** dizi.</span><span class="sxs-lookup"><span data-stu-id="1157d-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="1157d-107">Dizi türleri başvuru türleridir ve bir dizi değişkeni bildirimi yalnızca kenara bir dizi örneğine başvuru için alanı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1157d-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="1157d-108">Gerçek dizi örnekleri yeni işlecini kullanarak çalışma zamanında dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1157d-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="1157d-109">Yeni işlem belirtir ***uzunluğu*** sonra örnek ömrü boyunca sabit yeni dizi örneği.</span><span class="sxs-lookup"><span data-stu-id="1157d-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="1157d-110">Bir dizi aralıktan öğelerinin dizinlerini `0` için `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="1157d-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="1157d-111">`new` İşleci, örneğin, sıfır olan tüm sayısal türler için varsayılan değerlerine dizi öğelerini otomatik olarak başlatır ve `null` tüm başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="1157d-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="1157d-112">Aşağıdaki örnek, bir dizi oluşturur `int` öğeleri, dizi başlatır ve dizinin içeriğini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1157d-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="1157d-113">Bu örnek oluşturur ve çalıştırır bir ***tek boyutlu dizi***.</span><span class="sxs-lookup"><span data-stu-id="1157d-113">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="1157d-114">C# ' yı da destekler ***çok boyutlu diziler***.</span><span class="sxs-lookup"><span data-stu-id="1157d-114">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="1157d-115">Bir dizinin boyut sayısını yazın, olarak da bilinen ***derece*** dizi türü köşeli ayraç yazılmış virgül sayısı artı bir dizi türünde değil.</span><span class="sxs-lookup"><span data-stu-id="1157d-115">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="1157d-116">Aşağıdaki örnek bir tek boyutlu, iki boyutlu bir ve üç boyutlu bir dizi sırasıyla ayırır.</span><span class="sxs-lookup"><span data-stu-id="1157d-116">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="1157d-117">`a1` Dizi 10 öğeleri içeren `a2` dizi içeriyor 50 (10 × 5) öğeleri ve `a3` dizi 100 (10 × 5 × 2) içeriyor öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1157d-117">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="1157d-118">Bir dizi öğesi türü bir dizi türü de dahil olmak üzere herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1157d-118">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="1157d-119">Bir dizi bir dizi türü öğelerin adlandırılan bir ***Basit dizi*** öğesi diziler uzunlukları tümü aynı olmak zorunda olduğundan.</span><span class="sxs-lookup"><span data-stu-id="1157d-119">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="1157d-120">Aşağıdaki örnek oluşan bir dizi ayırır `int`:</span><span class="sxs-lookup"><span data-stu-id="1157d-120">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="1157d-121">İlk satır bir dizi üç öğeleri ile her tür oluşturur `int[]` ve her bir başlangıç değeriyle `null`.</span><span class="sxs-lookup"><span data-stu-id="1157d-121">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="1157d-122">Sonraki satırların sonra başvuruları, değişken uzunlukta bağımsız dizi örneklerine üç öğeleriyle başlatır.</span><span class="sxs-lookup"><span data-stu-id="1157d-122">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="1157d-123">New işleci kullanılarak belirtilmesi için dizi öğelerinin ilk değerlerini verir bir ***dizi Başlatıcı***, arasında sınırlayıcıları yazılmış ifadeleri listesi olduğu `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="1157d-123">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="1157d-124">Aşağıdaki örnek ayırır ve başlatır bir `int[]` üç öğeye sahip.</span><span class="sxs-lookup"><span data-stu-id="1157d-124">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="1157d-125">Dizi uzunluğu arasında ifadelerin numarasından algılanır Not {ve}.</span><span class="sxs-lookup"><span data-stu-id="1157d-125">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="1157d-126">Yerel değişken ve alan bildirimleri kısaltılmış daha ayrıntılı şekilde dizi türü açıklandı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1157d-126">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="1157d-127">Önceki örneklerde her ikisi de şuna eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="1157d-127">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="1157d-128">[Önceki](structs.md)
[sonraki](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="1157d-128">[Previous](structs.md)
[Next](interfaces.md)</span></span>
