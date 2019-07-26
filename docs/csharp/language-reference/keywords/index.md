---
title: C# Anahtar Sözcükleri
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 2bfd4d9cbac8dbc9c93ceb1c5bb61ecd03f348d7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512364"
---
# <a name="c-keywords"></a>C# Anahtar Sözcükleri

Anahtar sözcükler, derleyiciye özel anlamlara sahip olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Bunlar, ön ek olarak içermedikleri `@` sürece programınızda tanımlayıcı olarak kullanılamaz. Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` bunun nedeni `if` bir anahtar sözcüktür.  
  
 Bu konudaki ilk tablo, bir programın herhangi bir C# bölümünde ayrılmış tanımlayıcılar olan anahtar sözcükleri listeler. Bu konudaki ikinci tablo, içindeki C#bağlamsal anahtar sözcükleri listeler. Bağlamsal anahtar sözcüklerde yalnızca sınırlı program bağlamında özel anlamı vardır ve bu bağlamın dışında tanımlayıcılar olarak kullanılabilir. Genellikle, C# dile yeni anahtar sözcükler eklendikçe, önceki sürümlerde yazılmış programları bozmamak için bağlamsal anahtar sözcükler olarak eklenirler.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-conversion-operators.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[yakalaya](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[değilse](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[Düzenle](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](object.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[almaya](try-catch.md)|[typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[statik kullanma](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Bağlamsal anahtar sözcükler

 Bağlam anahtar sözcüğü, kodda belirli bir anlamı sağlamak için kullanılır, ancak içinde C#ayrılmış bir sözcük değildir. `partial` Ve`where`gibi bazı bağlamsal anahtar sözcükler, iki veya daha fazla bağlamda özel anlamlara sahiptir.  
  
||||  
|---|---|---|  
|[add](add.md)|[ek](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](global.md)|
|[grubu](group-clause.md)|[into](into.md)|[ayrılma](join-clause.md)|
|[atalım](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[OrderBy](orderby-clause.md)|[Kısmi (tür)](partial-type.md)|[partial (Yöntem)](partial-method.md)|
|[remove](remove.md)|[seçin](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (filtre koşulu)](when.md)|
|[where (genel tür kısıtlaması)](where-generic-type-constraint.md)|[WHERE (sorgu yan tümcesi)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
