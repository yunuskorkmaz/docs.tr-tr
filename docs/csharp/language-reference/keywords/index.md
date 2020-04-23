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
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102040"
---
# <a name="c-keywords"></a>C# Anahtar Sözcükleri

Anahtar kelimeler, derleyiciye özel anlamları olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Önek olarak içermedikçe `@` programınızda tanımlayıcı olarak kullanılamazlar. Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` bir anahtar `if` kelime olduğu için değildir.  
  
 Bu konudaki ilk tabloda, C# programının herhangi bir bölümünde ayrılmış tanımlayıcılar olan anahtar kelimeler listelenir. Bu konudaki ikinci tabloda C#'daki bağlamsal anahtar kelimeler listelenir. Bağlamsal anahtar kelimeler yalnızca sınırlı bir program bağlamında özel bir anlama sahiptir ve bu bağlamın dışında tanımlayıcı olarak kullanılabilir. Genellikle, C# diline yeni anahtar kelimeler eklendikçe, önceki sürümlerde yazılan programların kırılmasını önlemek için bağlamsal anahtar kelime olarak eklenir.  
  
|||||  
|---|---|---|---|  
|[Soyut](abstract.md)|[Olarak](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[Bayt](../builtin-types/integral-numeric-types.md)|[Durumda](switch.md)|[Yakalamak](try-catch.md)|  
|[char](../builtin-types/char.md)|[Kontrol](checked.md)|[sınıf](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[temsilci](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[False](../builtin-types/bool.md)|  
|[Sonunda](try-finally.md)|[Sabit](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[arabirim](interface.md)|[internal](internal.md)|
|[is](is.md)|[Kilit](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[ad alanı](namespace.md)|
|[Yeni](../operators/new-operator.md)|[null](null.md)|[Nesne](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[çıkış](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[Dize](../builtin-types/reference-types.md)|
|[Yapı](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[True](../builtin-types/bool.md)|[Deneyin](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[Uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Güvenli olmayan](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[kullanma](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>Bağlamsal anahtar kelimeler

 İçeriksel anahtar kelime, kodda belirli bir anlam sağlamak için kullanılır, ancak C#'da ayrılmış bir sözcük değildir. Bazı bağlamsal anahtar kelimeler, gibi `partial` ve, `where`iki veya daha fazla bağlamlarda özel anlamları vardır.  
  
||||  
|---|---|---|  
|[add](add.md)|[takma ad](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[Dinamik](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Kaynak](from-clause.md)|[get](get.md)|[Küresel](../operators/namespace-alias-qualifier.md)|
|[grup](group-clause.md)|[into](into.md)|[Katılın](join-clause.md)|
|[Izin](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[Orderby](orderby-clause.md)|[kısmi (tür)](partial-type.md)|[kısmi (yöntem)](partial-method.md)|
|[remove](remove.md)|[Seçin](select-clause.md)|[Ayarlamak](set.md)|
|[yönetilmemiş (genel tür kısıtlaması)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (filtre koşulu)](when.md)|[where (genel tür kısıtlaması)](where-generic-type-constraint.md)|[where (sorgu yan tümcesi)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
