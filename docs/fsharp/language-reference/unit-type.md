---
title: Birim Türü (F#)
description: "Nasıl F # 'birimi' türü genellikle herhangi bir değer gerekli ya da istenen burada bir değer dili sözdizimi tarafından gerekli yer tutmak için kullanılan öğrenin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a><span data-ttu-id="f2aea-103">Birim Türü</span><span class="sxs-lookup"><span data-stu-id="f2aea-103">Unit Type</span></span>

<span data-ttu-id="f2aea-104">`unit` Türüdür belirli bir değere; olmadığını gösteren bir tür `unit` türüne sahip başka bir değer yok veya gerekli olduğunda bir yer tutucu olarak davranan yalnızca tek bir değer.</span><span class="sxs-lookup"><span data-stu-id="f2aea-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="f2aea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2aea-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="f2aea-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2aea-106">Remarks</span></span>
<span data-ttu-id="f2aea-107">Her F # ifadesi bir değerde hesaplanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2aea-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="f2aea-108">İlgi türü değeri olan bir değer oluşturmaz ifadeler için `unit` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2aea-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="f2aea-109">`unit` Türü benzer `void` C# ve C++ gibi dillerde türü.</span><span class="sxs-lookup"><span data-stu-id="f2aea-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="f2aea-110">`unit` Türü tek bir değer içeriyor ve bu değeri belirtecin tarafından gösterilen `()`.</span><span class="sxs-lookup"><span data-stu-id="f2aea-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="f2aea-111">Değeri `unit` türü genellikle kullanılan F bir değer dili sözdizimi tarafından gerektiğinde, ancak hiçbir değer gerekli ya da istenen yer tutacak programlama # '.</span><span class="sxs-lookup"><span data-stu-id="f2aea-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="f2aea-112">Bir örnek dönüş değeri olabilir bir `printf` işlevi.</span><span class="sxs-lookup"><span data-stu-id="f2aea-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="f2aea-113">Çünkü önemli eylemleri `printf` işlemi ortaya işlevinde Gerçek bir değer döndürüleceğini işlevi yok.</span><span class="sxs-lookup"><span data-stu-id="f2aea-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="f2aea-114">Bu nedenle, dönüş değeri türünde `unit`.</span><span class="sxs-lookup"><span data-stu-id="f2aea-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="f2aea-115">Bazı yapıları beklediğiniz bir `unit` değeri.</span><span class="sxs-lookup"><span data-stu-id="f2aea-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="f2aea-116">Örneğin, bir `do` bağlama veya en üst düzeyinde bir modülün herhangi bir kod için değerlendirilecek beklenmektedir bir `unit` değeri.</span><span class="sxs-lookup"><span data-stu-id="f2aea-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="f2aea-117">Derleyici bir uyarı bildirir, bir `do` bağlama veya kod en üst düzeyinde bir modülün bir sonuç üretir dışında `unit` , aşağıdaki örnekte gösterildiği gibi kullanılmaz değeri.</span><span class="sxs-lookup"><span data-stu-id="f2aea-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="f2aea-118">Bu uyarı, işlevsel programlama özelliğidir; Diğer .NET programlama dilleri görünmez.</span><span class="sxs-lookup"><span data-stu-id="f2aea-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="f2aea-119">İşlevler herhangi yan etkileri olmayan tamamen işlevsel bir programda son dönen değer işlev çağrısı yalnızca sonucudur.</span><span class="sxs-lookup"><span data-stu-id="f2aea-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="f2aea-120">Sonuç göz ardı edilir, bu nedenle, bu olası bir programlama hatası değildir.</span><span class="sxs-lookup"><span data-stu-id="f2aea-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="f2aea-121">F # tamamen işlevsel bir programlama dili olmamasına rağmen işlevsel programlama stili mümkün olduğunca izlemek için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="f2aea-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2aea-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2aea-122">See Also</span></span>
[<span data-ttu-id="f2aea-123">İlkel</span><span class="sxs-lookup"><span data-stu-id="f2aea-123">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="f2aea-124">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f2aea-124">F# Language Reference</span></span>](index.md)
