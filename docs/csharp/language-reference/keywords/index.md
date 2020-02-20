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
ms.openlocfilehash: 2d6a514e52b25e65d9fd8a1efc3f930ce8f08178
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450823"
---
# <a name="c-keywords"></a>C# Anahtar Sözcükleri

Anahtar sözcükler, derleyiciye özel anlamlara sahip olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Ön ek olarak `@` eklemediğiniz sürece, programınızda tanımlayıcı olarak kullanılamaz. Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` `if` bir anahtar sözcüktür.  
  
 Bu konudaki ilk tablo, bir programın herhangi bir C# bölümünde ayrılmış tanımlayıcılar olan anahtar sözcükleri listeler. Bu konudaki ikinci tablo, içindeki C#bağlamsal anahtar sözcükleri listeler. Bağlamsal anahtar sözcüklerde yalnızca sınırlı program bağlamında özel anlamı vardır ve bu bağlamın dışında tanımlayıcılar olarak kullanılabilir. Genellikle, C# dile yeni anahtar sözcükler eklendikçe, önceki sürümlerde yazılmış programları bozmamak için bağlamsal anahtar sözcükler olarak eklenirler.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[yakalaya](try-catch.md)|  
|[char](../builtin-types/char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[değilse](if-else.md)|[enum](../builtin-types/enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[finally](try-finally.md)|[Düzenle](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[kullandıysanız](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[almaya](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[statik kullanma](using-static.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Bağlamsal anahtar sözcükler

 Bağlam anahtar sözcüğü, kodda belirli bir anlamı sağlamak için kullanılır, ancak içinde C#ayrılmış bir sözcük değildir. `partial` ve `where`gibi bazı bağlamsal anahtar sözcükler, iki veya daha fazla bağlamda özel anlamlara sahiptir.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Kaynak](from-clause.md)|[get](get.md)|[global](../operators/namespace-alias-qualifier.md)|
|[grubu](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[atalım](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[OrderBy](orderby-clause.md)|[Kısmi (tür)](partial-type.md)|[partial (Yöntem)](partial-method.md)|
|[remove](remove.md)|[seçin](select-clause.md)|[set](set.md)|
|[yönetilmeyen (genel tür kısıtlaması)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (filtre koşulu)](when.md)|[where (genel tür kısıtlaması)](where-generic-type-constraint.md)|[WHERE (sorgu yan tümcesi)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
