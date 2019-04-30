---
title: Fixed anahtar sözcüğü
description: Öğrenin 'koleksiyonuyla önlemek için bir yerel yığına PIN' F# 'fixed anahtar sözcüğü'.
ms.date: 04/24/2017
ms.openlocfilehash: 7fdf66560f3e2ab7584b00c7e4584d7f6c161858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772664"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="dd645-103">Fixed anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="dd645-103">The fixed keyword</span></span>

<span data-ttu-id="dd645-104">F#4.1 tanıtır `fixed` ", toplanan veya çöp toplama sırasında taşınan önlemek için bir yerel yığına sabitlemek" izin veren anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dd645-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="dd645-105">Bu düşük düzeydeki programlama senaryoları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd645-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd645-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd645-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="dd645-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd645-107">Remarks</span></span>

<span data-ttu-id="dd645-108">Bu, bir işaretçi çıkarma ve toplanan veya çöp toplama sırasında taşınan dan engelleyen bir ad bağlama izin vermek için ifadeler sözdizimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="dd645-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="dd645-109">Bir ifade işaretçisinden aracılığıyla sabit `fixed` anahtar sözcüğü bir tanımlayıcıya bağlı `use` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dd645-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="dd645-110">Bu semantiği kaynak yönetimi benzerdir `use` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dd645-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="dd645-111">İşaretçi sabit kapsamları dahilinde olması ve kapsam dışına olduktan sonra artık sabittir.</span><span class="sxs-lookup"><span data-stu-id="dd645-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="dd645-112">`fixed` bağlamı dışında kullanılamaz bir `use` bağlama.</span><span class="sxs-lookup"><span data-stu-id="dd645-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="dd645-113">İşaretçiyi bir adla bağlamanız gerekir `use`.</span><span class="sxs-lookup"><span data-stu-id="dd645-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="dd645-114">Kullanım `fixed` bir ifadede bir işlev veya yöntem içinde gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="dd645-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="dd645-115">Bir komut dosyası düzeyi veya modül düzeyinde kapsamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd645-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="dd645-116">Tüm işaretçi kodu gibi bu güvenli olmayan bir özelliktir ve bir uyarı yayar.</span><span class="sxs-lookup"><span data-stu-id="dd645-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="dd645-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd645-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd645-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd645-118">See also</span></span>

- [<span data-ttu-id="dd645-119">NativePtr modülü</span><span class="sxs-lookup"><span data-stu-id="dd645-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
