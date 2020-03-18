---
title: C# Dizileri - C# dilinde bir tur
description: Diziler C# dilindeki en temel koleksiyon türüdür
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159201"
---
# <a name="arrays"></a><span data-ttu-id="9c23e-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="9c23e-103">Arrays</span></span>

<span data-ttu-id="9c23e-104">***Dizi,*** hesaplanan endeksler aracılığıyla erişilen bir dizi değişken içeren bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="9c23e-105">Dizinin ***öğeleri*** olarak da adlandırılan bir dizide bulunan değişkenlerin tümü aynı türdendir ve bu türe dizinin ***öğe türü*** denir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="9c23e-106">Dizi türleri başvuru türleridir ve bir dizi değişkeninin bildirimi yalnızca bir dizi örneğine başvuru için bir alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="9c23e-107">Gerçek dizi örnekleri, yeni işleç kullanılarak çalışma zamanında dinamik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9c23e-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="9c23e-108">Yeni işlem, yeni dizi örneğinin ***uzunluğunu*** belirtir ve bu örnek, daha sonra örneğin ömrü için sabitlenir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="9c23e-109">Bir dizinin `0` öğelerinin `Length - 1`endeksleri.</span><span class="sxs-lookup"><span data-stu-id="9c23e-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="9c23e-110">İşletici, `new` örneğin tüm sayısal türler ve `null` tüm başvuru türleri için sıfır olan bir dizinin öğelerini varsayılan değerine otomatik olarak aparat eder.</span><span class="sxs-lookup"><span data-stu-id="9c23e-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="9c23e-111">Aşağıdaki örnek, bir dizi `int` öğe oluşturur, diziyi baş harfe alerler ve dizinin içeriğini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="9c23e-112">Bu ***örnek, tek boyutlu***bir dizi oluşturur ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="9c23e-113">C# aynı zamanda ***çok boyutlu dizileri***de destekler.</span><span class="sxs-lookup"><span data-stu-id="9c23e-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="9c23e-114">Dizi türünün ***sıralaması*** olarak da bilinen bir dizi türünün boyut sayısı, bir artı dizi türünün kare ayraçları arasında yazılmış virgül sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="9c23e-115">Aşağıdaki örnek, sırasıyla tek boyutlu, iki boyutlu ve üç boyutlu bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="9c23e-116">Dizi `a1` 10 eleman `a2` içerir, dizi 50 (10 × `a3` 5) eleman içerir ve dizi 100 (10 × 5 × 2) elemanlar içerir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="9c23e-117">Bir dizinin öğe türü, bir dizi türü de dahil olmak üzere herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="9c23e-118">Öğe dizilerinin uzunluklarının hepsinin aynı olması gerekmedığından, dizi türüöğelerine sahip bir diziye bazen ***pürüzlü dizi*** denir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays don't all have to be the same.</span></span> <span data-ttu-id="9c23e-119">Aşağıdaki örnek, bir dizi dizi `int`ayırır:</span><span class="sxs-lookup"><span data-stu-id="9c23e-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="9c23e-120">İlk satır, her biri tür `int[]` ve her biri başlangıç değeri `null`ne olacak olmak üzere üç öğeden oluşan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c23e-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="9c23e-121">Sonraki satırlar daha sonra değişen uzunluklarda tek tek dizi örneklerine başvurularla üç öğeyi başolarak ortaya alır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="9c23e-122">Yeni işleç, dizi elemanlarının ilk değerlerinin bir ***dizi baş harferkullanılarak***belirtilmesine izin verir, `{` bu `}`da sınırlayıcılar ve .</span><span class="sxs-lookup"><span data-stu-id="9c23e-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="9c23e-123">Aşağıdaki örnek üç öğeli bir `int[]` ayırır ve başharfleri.</span><span class="sxs-lookup"><span data-stu-id="9c23e-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="9c23e-124">Dizinin uzunluğu { ve }arasındaki ifade sayısından çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="9c23e-124">The length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="9c23e-125">Yerel değişken ve alan bildirimleri, dizi türünün yeniden ifade edilmesine gerek olmayacak şekilde daha da kısaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c23e-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="9c23e-126">Önceki örneklerin her ikisi de aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="9c23e-126">Both of the previous examples are equivalent to the following code:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="9c23e-127">[Önceki](classes-and-objects.md)
>[Sonraki](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="9c23e-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
