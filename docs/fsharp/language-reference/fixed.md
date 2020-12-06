---
title: Fixed anahtar sözcüğü
description: "F # ' fixed ' anahtar sözcüğüyle toplamayı engellemek için yerel olarak yığına nasıl ' sabitleyebileceğinizi öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740360"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="d8a78-103">Fixed anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d8a78-103">The fixed keyword</span></span>

<span data-ttu-id="d8a78-104">`fixed`Anahtar sözcüğü, atık toplama sırasında toplanmasını veya taşınmasını engellemek için yerel olarak yığına "sabitlemenizi" sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8a78-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="d8a78-105">Alt düzey programlama senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8a78-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8a78-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8a78-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="d8a78-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8a78-107">Remarks</span></span>

<span data-ttu-id="d8a78-108">Bu, bir işaretçinin ayıklanmasına izin vermek ve atık toplama sırasında toplanmasının veya taşınmasını önleyen bir ada bağlamak için ifadelerin sözdizimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="d8a78-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="d8a78-109">Bir ifadeden bir işaretçi, anahtar sözcüğü aracılığıyla `fixed` bir tanımlayıcıya bağlanır `use` .</span><span class="sxs-lookup"><span data-stu-id="d8a78-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="d8a78-110">Bunun semantiği, anahtar sözcüğü aracılığıyla kaynak yönetimine benzerdir `use` .</span><span class="sxs-lookup"><span data-stu-id="d8a78-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="d8a78-111">İşaretçi kapsamdayken sabitlenmiştir ve kapsam dışına alındıktan sonra artık sabit değildir.</span><span class="sxs-lookup"><span data-stu-id="d8a78-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="d8a78-112">`fixed` bağlama bağlamı dışında kullanılamaz `use` .</span><span class="sxs-lookup"><span data-stu-id="d8a78-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="d8a78-113">İşaretçiyi ile bir ada bağlamanız gerekir `use` .</span><span class="sxs-lookup"><span data-stu-id="d8a78-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="d8a78-114">Öğesinin kullanımı, `fixed` bir işlev veya metot içindeki bir ifadede gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8a78-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="d8a78-115">Betik düzeyinde veya modül düzeyinde bir kapsamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8a78-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="d8a78-116">Tüm işaretçi kodu gibi, bu güvenli olmayan bir özelliktir ve kullanıldığında bir uyarı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d8a78-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="d8a78-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8a78-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="d8a78-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a78-118">See also</span></span>

- [<span data-ttu-id="d8a78-119">NativePtr modülü</span><span class="sxs-lookup"><span data-stu-id="d8a78-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
