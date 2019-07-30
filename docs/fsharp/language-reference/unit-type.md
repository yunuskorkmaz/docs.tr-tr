---
title: Birim Türü
description: F# ' Unit ' türünün, hiçbir değer gerekmediği veya istenmiyorsa dil söz konusu olduğunda bir değerin gerekli olduğu yeri tutmak için genellikle nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630166"
---
# <a name="unit-type"></a><span data-ttu-id="8a531-103">Birim Türü</span><span class="sxs-lookup"><span data-stu-id="8a531-103">Unit Type</span></span>

<span data-ttu-id="8a531-104">Tür, belirli bir değerin yokluğunu gösteren bir türdür `unit` ; tür, başka bir değer yoksa veya gerektiğinde yer tutucu görevi gören tek bir değere sahiptir. `unit`</span><span class="sxs-lookup"><span data-stu-id="8a531-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a531-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a531-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="8a531-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a531-106">Remarks</span></span>

<span data-ttu-id="8a531-107">Her F# ifade bir değer olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a531-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="8a531-108">İlgilendiğiniz bir değer üretmeyen ifadeler için, türünün `unit` değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a531-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="8a531-109">Tür, `void` ve C++gibi C# dillerdeki türe benzer. `unit`</span><span class="sxs-lookup"><span data-stu-id="8a531-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="8a531-110">Türün tek bir değeri vardır ve bu değer belirteç `()`tarafından belirtilir. `unit`</span><span class="sxs-lookup"><span data-stu-id="8a531-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="8a531-111">`unit` Türün değeri, genellikle bir değerin dil sözdizimi için F# gerekli olduğu yeri tutmak için programlama sırasında kullanılır, ancak hiçbir değer gerekli veya istenmez.</span><span class="sxs-lookup"><span data-stu-id="8a531-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="8a531-112">Bir `printf` işlevin dönüş değeri bir örnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a531-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="8a531-113">`printf` İşlemin önemli eylemleri işlevde gerçekleştiğinden, işlevin gerçek bir değer döndürmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8a531-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="8a531-114">Bu nedenle, dönüş değeri türündedir `unit`.</span><span class="sxs-lookup"><span data-stu-id="8a531-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="8a531-115">Bazı yapılar bir `unit` değer bekler.</span><span class="sxs-lookup"><span data-stu-id="8a531-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="8a531-116">Örneğin, `do` bir modülün en üst düzeyindeki bir bağlamanın veya kodun bir `unit` değer değerlendirmesi beklenir.</span><span class="sxs-lookup"><span data-stu-id="8a531-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="8a531-117">Bir modülün en üst düzeyindeki bir `do` bağlama veya kod, aşağıdaki örnekte gösterildiği gibi kullanılmayan `unit` değerden farklı bir sonuç üretirse, derleyici bir uyarı bildirir.</span><span class="sxs-lookup"><span data-stu-id="8a531-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="8a531-118">Bu uyarı, işlevsel programlama 'nin bir özelliğidir; diğer .NET programlama dillerinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="8a531-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="8a531-119">Tamamen işlevsel bir programda, işlevleri yan etkileri olmayan, son dönüş değeri bir işlev çağrısının tek sonucudur.</span><span class="sxs-lookup"><span data-stu-id="8a531-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="8a531-120">Bu nedenle, sonuç yoksayılırsa, olası bir programlama hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="8a531-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="8a531-121">Tamamen F# işlevsel programlama dili olmasa da, mümkün olan her durumda işlevsel programlama stilini izlemek iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="8a531-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a531-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a531-122">See also</span></span>

- [<span data-ttu-id="8a531-123">Eleman</span><span class="sxs-lookup"><span data-stu-id="8a531-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="8a531-124">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8a531-124">F# Language Reference</span></span>](index.md)
