---
title: 'Sabit anahtar sözcüğü (F #)'
description: "'Sabitleyebilir nasıl' ile F # koleksiyon önlemek için bir yerel yığına 'anahtar sözcüğü sabit' öğrenin."
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563882"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="d681d-103">Sabit anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d681d-103">The Fixed Keyword</span></span>

<span data-ttu-id="d681d-104">F # 4.1 tanıtır `fixed` anahtar sözcüğü "toplanan veya çöp toplama sırasında taşınmış önlemek için bir yerel yığına sabitlemek" sağlar.</span><span class="sxs-lookup"><span data-stu-id="d681d-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="d681d-105">Alt düzey programlama senaryolar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d681d-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="d681d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d681d-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="d681d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d681d-107">Remarks</span></span>

<span data-ttu-id="d681d-108">Bu işaretçi ayıklanması ve toplanan veya çöp toplama sırasında taşınmış engelleyen bir adı bağlama izin ifadenin sözdizimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="d681d-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="d681d-109">Bir ifade işaretçi aracılığıyla sabit `fixed` anahtar sözcüğü bir tanımlayıcıya bağlı `use` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d681d-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="d681d-110">Bu semantiği kaynak yönetimi benzer `use` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d681d-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="d681d-111">İşaretçinin kapsamında olduğunu ve kapsamının dışına olduktan sonra artık sabittir düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d681d-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="d681d-112">`fixed` bağlamı dışında kullanılamaz bir `use` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d681d-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="d681d-113">İşaretçinin bir adla bağlamak gerekir `use`.</span><span class="sxs-lookup"><span data-stu-id="d681d-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="d681d-114">Kullanımı `fixed` bir ifadede bir işlev veya yöntem içinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="d681d-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="d681d-115">Bir komut dosyası düzeyi veya modül düzeyi kapsamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d681d-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="d681d-116">Tüm işaretçi kodu gibi bu güvensiz bir özelliktir ve kullanıldığında bir uyarı yayma.</span><span class="sxs-lookup"><span data-stu-id="d681d-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="d681d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d681d-117">Example</span></span>

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
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="d681d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d681d-118">See Also</span></span>

[<span data-ttu-id="d681d-119">NativePtr modülü</span><span class="sxs-lookup"><span data-stu-id="d681d-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
