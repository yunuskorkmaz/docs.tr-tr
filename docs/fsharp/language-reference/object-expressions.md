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
# <a name="object-expressions"></a>Nesne İfadeleri

Bir *nesne ifadesi* , var olan temel türü, arabirimi veya arabirim kümesini temel alan dinamik olarak oluşturulan, anonim nesne türünün yeni bir örneğini oluşturan bir ifadedir.

## <a name="syntax"></a>Syntax

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

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *TypeName* varolan bir sınıf türünü veya arabirim türünü temsil eder. *tür-params* isteğe bağlı genel tür parametrelerini açıklar. *Bağımsız değişkenler* yalnızca Oluşturucu parametreleri gerektiren sınıf türleri için kullanılır. *Üye tanımları* , temel sınıf yöntemlerinin veya temel bir sınıftan ya da bir arabirimden soyut yöntemlerin uygulamalarının geçersiz kılınmalarıdır.

Aşağıdaki örnekte birçok farklı nesne ifadesi türü gösterilmektedir.

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

## <a name="using-object-expressions"></a>Nesne Ifadeleri kullanma

Yeni, adlandırılmış bir tür oluşturmak için gereken ek kod ve ek yükün oluşmasını önlemek istediğinizde nesne ifadelerini kullanırsınız. Bir programda oluşturulan tür sayısını en aza indirmek için nesne ifadeleri kullanırsanız, kod satır sayısını azaltabilir ve türlerin gereksiz şekilde kullanılmasını engelleyebilirsiniz. Yalnızca belirli durumları işlemek için çok sayıda tür oluşturmak yerine, var olan bir türü özelleştiren bir nesne ifadesi kullanabilir veya bir arabirimin uygun bir uygulama için uygun bir uygulama sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
