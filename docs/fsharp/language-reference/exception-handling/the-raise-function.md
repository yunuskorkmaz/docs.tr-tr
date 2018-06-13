---
title: 'Özel Durumlar: raise İşlevi (F#)'
description: "F # 'Yükselt' işlevi bir hata veya olağanüstü koşulu oluştu belirtmek için nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564772"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="6560f-103">Özel Durumlar: raise İşlevi</span><span class="sxs-lookup"><span data-stu-id="6560f-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="6560f-104">`raise` İşlevi bir hata veya olağanüstü koşulu oluştu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6560f-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="6560f-105">Hata hakkında bilgi bir özel durum nesnesi yakalanır.</span><span class="sxs-lookup"><span data-stu-id="6560f-105">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="6560f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6560f-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="6560f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6560f-107">Remarks</span></span>
<span data-ttu-id="6560f-108">`raise` İşlevi bir özel durum nesnesi oluşturur ve işlem geriye doğru izleme yığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="6560f-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="6560f-109">Diğer bir .NET dilinde olduğu gibi bu işlemin aynı nedenle davranış yığın unwinding işlem ortak dil çalışma zamanı tarafından (CLR) yönetilir.</span><span class="sxs-lookup"><span data-stu-id="6560f-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="6560f-110">Yığın unwinding oluşturulan özel durum ile eşleşen bir özel durum işleyici için bir arama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="6560f-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="6560f-111">Geçerli aramayı başlatır `try...with` varsa ifade.</span><span class="sxs-lookup"><span data-stu-id="6560f-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="6560f-112">Her desende `with` blok denetlenir, sırayla.</span><span class="sxs-lookup"><span data-stu-id="6560f-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="6560f-113">Eşleşen bir özel durum işleyici bulunduğunda, özel durum işlenen olarak kabul edilir; Aksi takdirde, yığın unwound ve `with` çağrı zincirine yukarı blokları eşleşen bir işleyici bulunana kadar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="6560f-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="6560f-114">Tüm `finally` yığın unwinds olarak çağrı zincirine karşılaşılan blokları sırada da çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6560f-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="6560f-115">`raise` Fonksiyonudur denk `throw` C# veya C++.</span><span class="sxs-lookup"><span data-stu-id="6560f-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="6560f-116">Kullanım `reraise` aynı özel durum çağrı zincirine yukarı yaymak için bir catch işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6560f-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="6560f-117">Aşağıdaki kod örnekleri kullanımını göstermek `raise` bir özel durum oluşturmak için işlev.</span><span class="sxs-lookup"><span data-stu-id="6560f-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="6560f-118">`raise` İşlevi de kullanılabilir .NET özel durumlarını yükseltmek için aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6560f-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="6560f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6560f-119">See Also</span></span>
[<span data-ttu-id="6560f-120">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="6560f-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="6560f-121">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="6560f-121">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="6560f-122">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="6560f-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="6560f-123">Özel durumlar: `try...finally` ifade</span><span class="sxs-lookup"><span data-stu-id="6560f-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="6560f-124">Özel durumlar: `failwith` işlevi</span><span class="sxs-lookup"><span data-stu-id="6560f-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="6560f-125">Özel durumlar: `invalidArg` işlevi</span><span class="sxs-lookup"><span data-stu-id="6560f-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
