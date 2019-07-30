---
title: 'Özel Durumlar: raise İşlevi'
description: F# ' Raise ' işlevinin bir hata veya sıra koşulunun oluştuğunu göstermek için nasıl kullanıldığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630294"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="efa5d-103">Özel Durumlar: raise İşlevi</span><span class="sxs-lookup"><span data-stu-id="efa5d-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="efa5d-104">`raise` İşlevi, bir hata veya sıra koşulunun oluştuğunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efa5d-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="efa5d-105">Hata hakkındaki bilgiler bir özel durum nesnesi içinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="efa5d-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="efa5d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efa5d-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="efa5d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efa5d-107">Remarks</span></span>

<span data-ttu-id="efa5d-108">`raise` İşlevi bir özel durum nesnesi oluşturur ve bir yığın geri sarma işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="efa5d-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="efa5d-109">Yığın geriye doğru izleme işlemi, ortak dil çalışma zamanı (CLR) tarafından yönetilir, bu nedenle bu işlemin davranışı diğer herhangi bir .NET dilinde olduğu gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="efa5d-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="efa5d-110">Yığın geri sarma işlemi, oluşturulan özel durumla eşleşen bir özel durum işleyicisi aramasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="efa5d-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="efa5d-111">Arama, varsa geçerli `try...with` ifadede başlar.</span><span class="sxs-lookup"><span data-stu-id="efa5d-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="efa5d-112">`with` Bloktaki her bir düzen sırasıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="efa5d-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="efa5d-113">Eşleşen bir özel durum işleyicisi bulunduğunda, özel durum işlenmiş olarak kabul edilir; Aksi takdirde, yığın engellenir ve `with` blok bir işleyici bulunana kadar çağrı zinciri denetlenir.</span><span class="sxs-lookup"><span data-stu-id="efa5d-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="efa5d-114">Çağrı `finally` zincirinde karşılaşılan tüm bloklar yığın olarak yığın olarak da yürütülür.</span><span class="sxs-lookup"><span data-stu-id="efa5d-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="efa5d-115">İşlevi veya C++' de ' C# nin `throw` eşdeğeridir. `raise`</span><span class="sxs-lookup"><span data-stu-id="efa5d-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="efa5d-116">Aynı `reraise` özel durumu çağrı zincirine yaymak için bir catch işleyicisinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="efa5d-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="efa5d-117">Aşağıdaki kod örnekleri, bir özel durum oluşturmak için `raise` işlevinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="efa5d-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="efa5d-118">`raise` İşlev, aşağıdaki örnekte gösterildiği gibi .NET özel durumlarını yükseltmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efa5d-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="efa5d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efa5d-119">See also</span></span>

- [<span data-ttu-id="efa5d-120">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="efa5d-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="efa5d-121">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="efa5d-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="efa5d-122">Özel Durumlar: `try...with` İfade</span><span class="sxs-lookup"><span data-stu-id="efa5d-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="efa5d-123">Özel Durumlar: `try...finally` İfade</span><span class="sxs-lookup"><span data-stu-id="efa5d-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="efa5d-124">Özel Durumlar: `failwith` İşlevi</span><span class="sxs-lookup"><span data-stu-id="efa5d-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="efa5d-125">Özel Durumlar: `invalidArg` İşlevi</span><span class="sxs-lookup"><span data-stu-id="efa5d-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
