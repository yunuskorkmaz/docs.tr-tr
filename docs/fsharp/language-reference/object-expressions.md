---
title: Nesne İfadeleri
description: 'Yeni, adlandırılmış bir tür oluşturmak için gereken ek kod ve ek yükün oluşmasını önlemek istediğinizde F # nesne ifadelerini nasıl kullanacağınızı öğrenin.'
ms.date: 02/08/2019
ms.openlocfilehash: 8a3e40b7833b551eefb95ec62b935acd1ba7b1f9
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740308"
---
# <a name="object-expressions"></a><span data-ttu-id="1ea47-103">Nesne İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1ea47-103">Object Expressions</span></span>

<span data-ttu-id="1ea47-104">Bir *nesne ifadesi* , var olan temel türü, arabirimi veya arabirim kümesini temel alan dinamik olarak oluşturulan, anonim nesne türünün yeni bir örneğini oluşturan bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1ea47-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ea47-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ea47-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="1ea47-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ea47-106">Remarks</span></span>

<span data-ttu-id="1ea47-107">Önceki sözdiziminde, *TypeName* varolan bir sınıf türünü veya arabirim türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ea47-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="1ea47-108">*tür-params* isteğe bağlı genel tür parametrelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ea47-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="1ea47-109">*Bağımsız değişkenler* yalnızca Oluşturucu parametreleri gerektiren sınıf türleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea47-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="1ea47-110">*Üye tanımları* , temel sınıf yöntemlerinin veya temel bir sınıftan ya da bir arabirimden soyut yöntemlerin uygulamalarının geçersiz kılınmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea47-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="1ea47-111">Aşağıdaki örnekte birçok farklı nesne ifadesi türü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ea47-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn $"{obj1}"

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="1ea47-112">Nesne Ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1ea47-112">Using Object Expressions</span></span>

<span data-ttu-id="1ea47-113">Yeni, adlandırılmış bir tür oluşturmak için gereken ek kod ve ek yükün oluşmasını önlemek istediğinizde nesne ifadelerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1ea47-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="1ea47-114">Bir programda oluşturulan tür sayısını en aza indirmek için nesne ifadeleri kullanırsanız, kod satır sayısını azaltabilir ve türlerin gereksiz şekilde kullanılmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ea47-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="1ea47-115">Yalnızca belirli durumları işlemek için çok sayıda tür oluşturmak yerine, var olan bir türü özelleştiren bir nesne ifadesi kullanabilir veya bir arabirimin uygun bir uygulama için uygun bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ea47-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ea47-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea47-116">See also</span></span>

- [<span data-ttu-id="1ea47-117">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="1ea47-117">F# Language Reference</span></span>](index.md)
