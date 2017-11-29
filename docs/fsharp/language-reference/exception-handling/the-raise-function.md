---
title: "Özel Durumlar: raise İşlevi (F#)"
description: "F # 'Yükselt' işlevi bir hata veya olağanüstü koşulu oluştu belirtmek için nasıl kullanıldığını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="31ff2-104">Özel Durumlar: raise İşlevi</span><span class="sxs-lookup"><span data-stu-id="31ff2-104">Exceptions: the raise Function</span></span>

<span data-ttu-id="31ff2-105">`raise` İşlevi bir hata veya olağanüstü koşulu oluştu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31ff2-105">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="31ff2-106">Hata hakkında bilgi bir özel durum nesnesi yakalanır.</span><span class="sxs-lookup"><span data-stu-id="31ff2-106">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="31ff2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31ff2-107">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="31ff2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31ff2-108">Remarks</span></span>
<span data-ttu-id="31ff2-109">`raise` İşlevi bir özel durum nesnesi oluşturur ve işlem geriye doğru izleme yığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="31ff2-109">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="31ff2-110">Diğer bir .NET dilinde olduğu gibi bu işlemin aynı nedenle davranış yığın unwinding işlem ortak dil çalışma zamanı tarafından (CLR) yönetilir.</span><span class="sxs-lookup"><span data-stu-id="31ff2-110">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="31ff2-111">Yığın unwinding oluşturulan özel durum ile eşleşen bir özel durum işleyici için bir arama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="31ff2-111">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="31ff2-112">Geçerli aramayı başlatır `try...with` varsa ifade.</span><span class="sxs-lookup"><span data-stu-id="31ff2-112">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="31ff2-113">Her desende `with` blok denetlenir, sırayla.</span><span class="sxs-lookup"><span data-stu-id="31ff2-113">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="31ff2-114">Eşleşen bir özel durum işleyici bulunduğunda, özel durum işlenen olarak kabul edilir; Aksi takdirde, yığın unwound ve `with` çağrı zincirine yukarı blokları eşleşen bir işleyici bulunana kadar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="31ff2-114">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="31ff2-115">Tüm `finally` yığın unwinds olarak çağrı zincirine karşılaşılan blokları sırada da çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="31ff2-115">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="31ff2-116">`raise` Fonksiyonudur denk `throw` C# veya C++.</span><span class="sxs-lookup"><span data-stu-id="31ff2-116">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="31ff2-117">Kullanım `reraise` aynı özel durum çağrı zincirine yukarı yaymak için bir catch işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="31ff2-117">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="31ff2-118">Aşağıdaki kod örnekleri kullanımını göstermek `raise` bir özel durum oluşturmak için işlev.</span><span class="sxs-lookup"><span data-stu-id="31ff2-118">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="31ff2-119">`raise` İşlevi de kullanılabilir .NET özel durumlarını yükseltmek için aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="31ff2-119">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="31ff2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31ff2-120">See Also</span></span>
[<span data-ttu-id="31ff2-121">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="31ff2-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="31ff2-122">Özel durum türleri</span><span class="sxs-lookup"><span data-stu-id="31ff2-122">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="31ff2-123">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="31ff2-123">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="31ff2-124">Özel durumlar: `try...finally` ifade</span><span class="sxs-lookup"><span data-stu-id="31ff2-124">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="31ff2-125">Özel durumlar: `failwith` işlevi</span><span class="sxs-lookup"><span data-stu-id="31ff2-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="31ff2-126">Özel durumlar: `invalidArg` işlevi</span><span class="sxs-lookup"><span data-stu-id="31ff2-126">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
