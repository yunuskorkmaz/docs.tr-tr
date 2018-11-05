---
title: Birim Türü (F#)
description: Nasıl F# 'unit' türü genellikle burada herhangi bir değer gerekli ya da istenen dili sözdizimi tarafından bir değer gereklidir yerde tutmak için kullanılan bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204662"
---
# <a name="unit-type"></a><span data-ttu-id="1599c-103">Birim Türü</span><span class="sxs-lookup"><span data-stu-id="1599c-103">Unit Type</span></span>

<span data-ttu-id="1599c-104">`unit` Türüdür; belirli bir değer devamsızlık gösteren bir türün `unit` türüne sahip başka bir değer yok veya gerekli olduğunda, bir yer tutucu olarak görev yapar yalnızca tek bir değer.</span><span class="sxs-lookup"><span data-stu-id="1599c-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="1599c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1599c-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="1599c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1599c-106">Remarks</span></span>

<span data-ttu-id="1599c-107">Her F# ifadesi bir değer olarak değerlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1599c-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="1599c-108">İlgi, değer türünde bir değer oluşturmaz ifadeler `unit` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1599c-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="1599c-109">`unit` Türü benzer `void` C# ve C++ gibi dillerde türü.</span><span class="sxs-lookup"><span data-stu-id="1599c-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="1599c-110">`unit` Tek bir değer türüne sahip ve bu değer belirteci tarafından belirtilen `()`.</span><span class="sxs-lookup"><span data-stu-id="1599c-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="1599c-111">Değerini `unit` türü genellikle kullanılan bir değer, dili sözdizimi tarafından gerekli olduğu durumlarda, ancak hiçbir değer gerekli ya da istenen bir yerde tutmak için programlama içinde F#.</span><span class="sxs-lookup"><span data-stu-id="1599c-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="1599c-112">Dönüş değeri bir örnek olabilir bir `printf` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1599c-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="1599c-113">Çünkü önemli eylemleri `printf` işlemi meydana işlevde harcanan, gerçek bir değer döndürmek işlev yok.</span><span class="sxs-lookup"><span data-stu-id="1599c-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="1599c-114">Bu nedenle, dönüş değeri türünde `unit`.</span><span class="sxs-lookup"><span data-stu-id="1599c-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="1599c-115">Bazı yapıları beklediğiniz bir `unit` değeri.</span><span class="sxs-lookup"><span data-stu-id="1599c-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="1599c-116">Örneğin, bir `do` bağlama veya en üst düzeyde bir modülün herhangi bir kod için değerlendirilecek beklenmektedir bir `unit` değeri.</span><span class="sxs-lookup"><span data-stu-id="1599c-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="1599c-117">Derleyici bir uyarı bildirir, bir `do` bağlamanız veya kodunuz en üst düzeyde bir modülün bir sonuç üretir dışında `unit` , aşağıdaki örnekte gösterildiği gibi kullanılmayan değer.</span><span class="sxs-lookup"><span data-stu-id="1599c-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="1599c-118">Bu uyarı, işlevsel programlama özelliğidir; Diğer .NET programlama dillerinin görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="1599c-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="1599c-119">İşlevler tüm yan etkileri de yoktur tamamen işlevsel bir programda son dönüş değeri bir işlev çağrısı yalnızca sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1599c-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="1599c-120">Bu nedenle sonuç göz ardı edilir olduğunda, olası bir programlama hatası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1599c-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="1599c-121">F# tamamen işlevsel bir programlama dili olmamasına karşın, işlevsel programlama stil mümkün olduğunca izlemek için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="1599c-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="1599c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1599c-122">See also</span></span>

- [<span data-ttu-id="1599c-123">Temel</span><span class="sxs-lookup"><span data-stu-id="1599c-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="1599c-124">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1599c-124">F# Language Reference</span></span>](index.md)
