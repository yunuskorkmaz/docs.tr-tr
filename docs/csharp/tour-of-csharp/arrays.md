---
title: C# diziler - C# dili turu
description: Dizi en temel C# dili koleksiyon türü olan
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: c0fe65348ab2d41852ed9150571dcb0e5b8553f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351011"
---
# <a name="arrays"></a><span data-ttu-id="2c087-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="2c087-103">Arrays</span></span>

<span data-ttu-id="2c087-104">Bir ***dizi*** içeren bir dizi hesaplanan dizinlerini erişilen değişken bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="2c087-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="2c087-105">Bir dizinin içindeki değişkenleri olarak da bilinir ***öğeleri*** dizinin tümü aynı türde ve bu tür adlı ***öğe türü*** dizi.</span><span class="sxs-lookup"><span data-stu-id="2c087-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="2c087-106">Dizi türleri başvuru türleridir ve bir dizi değişkeni bildirimi yalnızca kenara bir dizi örneğine başvuru için alanı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2c087-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="2c087-107">Gerçek dizi örnekleri yeni işlecini kullanarak çalışma zamanında dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c087-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="2c087-108">Yeni işlem belirtir ***uzunluğu*** sonra örnek ömrü boyunca sabit yeni dizi örneği.</span><span class="sxs-lookup"><span data-stu-id="2c087-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="2c087-109">Bir dizi aralıktan öğelerinin dizinlerini `0` için `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="2c087-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="2c087-110">`new` İşleci, örneğin, sıfır olan tüm sayısal türler için varsayılan değerlerine dizi öğelerini otomatik olarak başlatır ve `null` tüm başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="2c087-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="2c087-111">Aşağıdaki örnek, bir dizi oluşturur `int` öğeleri, dizi başlatır ve dizinin içeriğini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2c087-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="2c087-112">Bu örnek oluşturur ve çalıştırır bir ***tek boyutlu dizi***.</span><span class="sxs-lookup"><span data-stu-id="2c087-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="2c087-113">C# ' yı da destekler ***çok boyutlu diziler***.</span><span class="sxs-lookup"><span data-stu-id="2c087-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="2c087-114">Bir dizinin boyut sayısını yazın, olarak da bilinen ***derece*** dizi türü köşeli ayraç yazılmış virgül sayısı artı bir dizi türünde değil.</span><span class="sxs-lookup"><span data-stu-id="2c087-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="2c087-115">Aşağıdaki örnek bir tek boyutlu, iki boyutlu bir ve üç boyutlu bir dizi sırasıyla ayırır.</span><span class="sxs-lookup"><span data-stu-id="2c087-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="2c087-116">`a1` Dizi 10 öğeleri içeren `a2` dizi içeriyor 50 (10 × 5) öğeleri ve `a3` dizi 100 (10 × 5 × 2) içeriyor öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2c087-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="2c087-117">Bir dizi öğesi türü bir dizi türü de dahil olmak üzere herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c087-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="2c087-118">Bir dizi bir dizi türü öğelerin adlandırılan bir ***Basit dizi*** öğesi diziler uzunlukları tümü aynı olmak zorunda olduğundan.</span><span class="sxs-lookup"><span data-stu-id="2c087-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="2c087-119">Aşağıdaki örnek oluşan bir dizi ayırır `int`:</span><span class="sxs-lookup"><span data-stu-id="2c087-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="2c087-120">İlk satır bir dizi üç öğeleri ile her tür oluşturur `int[]` ve her bir başlangıç değeriyle `null`.</span><span class="sxs-lookup"><span data-stu-id="2c087-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="2c087-121">Sonraki satırların sonra başvuruları, değişken uzunlukta bağımsız dizi örneklerine üç öğeleriyle başlatır.</span><span class="sxs-lookup"><span data-stu-id="2c087-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="2c087-122">New işleci kullanılarak belirtilmesi için dizi öğelerinin ilk değerlerini verir bir ***dizi Başlatıcı***, arasında sınırlayıcıları yazılmış ifadeleri listesi olduğu `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="2c087-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="2c087-123">Aşağıdaki örnek ayırır ve başlatır bir `int[]` üç öğeye sahip.</span><span class="sxs-lookup"><span data-stu-id="2c087-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="2c087-124">Dizi uzunluğu arasında ifadelerin numarasından algılanır Not {ve}.</span><span class="sxs-lookup"><span data-stu-id="2c087-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="2c087-125">Yerel değişken ve alan bildirimleri kısaltılmış daha ayrıntılı şekilde dizi türü açıklandı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2c087-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="2c087-126">Önceki örneklerde her ikisi de şuna eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="2c087-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="2c087-127">[Önceki](structs.md)
[sonraki](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="2c087-127">[Previous](structs.md)
[Next](interfaces.md)</span></span>
