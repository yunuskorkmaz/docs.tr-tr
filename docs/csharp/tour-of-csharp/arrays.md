---
title: C#Diziler - Turu C# dil
description: En temel koleksiyon türü dizilerdir C# dil
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 56a053ac8525d4c6c34592d6092f3f162cb04247
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634601"
---
# <a name="arrays"></a><span data-ttu-id="00dbf-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="00dbf-103">Arrays</span></span>

<span data-ttu-id="00dbf-104">Bir ***dizi*** hesaplanan dizinlerini erişilen değişken bir sayı içeren bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="00dbf-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="00dbf-105">Bir dizi içindeki değişkenler olarak da bilinir ***öğeleri*** dizinin tümü aynı türde ve bu tür çağrılır ***öğe türü*** dizi.</span><span class="sxs-lookup"><span data-stu-id="00dbf-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="00dbf-106">Dizi türleri, başvuru türleridir ve bir dizi değişkeni bildirimi yalnızca kenara alanı başvuru bir dizi örneği için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00dbf-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="00dbf-107">Gerçek bir dizi örnekleri, new işleci kullanılarak çalışma zamanında dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00dbf-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="00dbf-108">Yeni işlemi belirtir ***uzunluğu*** sonra Örneğin ömrü boyunca sabittir yeni dizi örneği.</span><span class="sxs-lookup"><span data-stu-id="00dbf-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="00dbf-109">Dizinleri öğelerinden oluşan bir dizi aralığından `0` için `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="00dbf-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="00dbf-110">`new` İşleci, örneğin, sıfır olan tüm sayısal türler için varsayılan değerlerine bir dizinin öğeleri otomatik olarak başlatır ve `null` tüm başvuru türleri için.</span><span class="sxs-lookup"><span data-stu-id="00dbf-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="00dbf-111">Aşağıdaki örnek, bir dizi oluşturur. `int` öğeleri, dizi başlatır ve dizinin içeriği yazdırır.</span><span class="sxs-lookup"><span data-stu-id="00dbf-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="00dbf-112">Bu örneği oluşturur ve üzerinde çalıştığı bir ***tek boyutlu dizi***.</span><span class="sxs-lookup"><span data-stu-id="00dbf-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="00dbf-113">C# ' yı da destekler ***çok boyutlu diziler***.</span><span class="sxs-lookup"><span data-stu-id="00dbf-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="00dbf-114">Olarak da bilinen bir dizinin boyut sayısını yazın ***derece*** dizi türü köşeli ayraç yazılan virgül sayısı artı bir dizi türünde olduğu.</span><span class="sxs-lookup"><span data-stu-id="00dbf-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="00dbf-115">Aşağıdaki örnek bir tek boyutlu, iki boyutlu bir ve üç boyutlu bir dizi sırasıyla ayırır.</span><span class="sxs-lookup"><span data-stu-id="00dbf-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="00dbf-116">`a1` Dizi 10 öğe içeriyor `a2` dizi içeriyor 50 (10 × 5) öğeleri ve `a3` dizi içeriyor (10 × 5 × 2) 100 öğeleri.</span><span class="sxs-lookup"><span data-stu-id="00dbf-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="00dbf-117">Bir dizinin öğe türü bir dizi türü de dahil olmak üzere herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="00dbf-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="00dbf-118">Bir dizi türünde öğelere sahip bir dizi adlandırılan bir ***düzensiz dizi*** öğe dizisi uzunluklarının tümünü değil aynı olmak zorunda olduğu.</span><span class="sxs-lookup"><span data-stu-id="00dbf-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="00dbf-119">Aşağıdaki örnekte dizi ayırır `int`:</span><span class="sxs-lookup"><span data-stu-id="00dbf-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="00dbf-120">İlk satır, üç öğeyle her türü bir dizi oluşturur `int[]` ve her bir başlangıç değeri ile `null`.</span><span class="sxs-lookup"><span data-stu-id="00dbf-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="00dbf-121">Sonraki satırların başvurular değişen uzunlukları örneklerini tek bir dizi üç öğeleri ardından başlatın.</span><span class="sxs-lookup"><span data-stu-id="00dbf-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="00dbf-122">New işleci Başlangıç değerlerini kullanarak belirtilen dizi öğelerinin izin veren bir ***dizi Başlatıcısı***, sınırlayıcılar arasında yazılan ifadeler listesi olduğu `{` ve `}`.</span><span class="sxs-lookup"><span data-stu-id="00dbf-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="00dbf-123">Aşağıdaki örnek ayırır ve başlatan bir `int[]` üç öğelerle.</span><span class="sxs-lookup"><span data-stu-id="00dbf-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="00dbf-124">Dizinin uzunluğu arasında ifadelerin sayısından algılanır Not {ve}.</span><span class="sxs-lookup"><span data-stu-id="00dbf-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="00dbf-125">Yerel değişken ve alan bildirimleri kısalttık daha fazla sağlayacak şekilde dizi türü açıklandı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="00dbf-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="00dbf-126">Önceki örneklerin her ikisi de aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="00dbf-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="00dbf-127">[Önceki](structs.md)
>[İleri](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="00dbf-127">[Previous](structs.md)
[Next](interfaces.md)</span></span>
