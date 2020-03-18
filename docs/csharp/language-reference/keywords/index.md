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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399317"
---
# <a name="c-keywords"></a>C# Anahtar Sözcükleri

Anahtar kelimeler, derleyiciye özel anlamları olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Önek olarak içermedikçe `@` programınızda tanımlayıcı olarak kullanılamazlar. Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` bir anahtar `if` kelime olduğu için değildir.  
  
 Bu konudaki ilk tabloda, C# programının herhangi bir bölümünde ayrılmış tanımlayıcılar olan anahtar kelimeler listelenir. Bu konudaki ikinci tabloda C#'daki bağlamsal anahtar kelimeler listelenir. Bağlamsal anahtar kelimeler yalnızca sınırlı bir program bağlamında özel bir anlama sahiptir ve bu bağlamın dışında tanımlayıcı olarak kullanılabilir. Genellikle, C# diline yeni anahtar kelimeler eklendikçe, önceki sürümlerde yazılan programların kırılmasını önlemek için bağlamsal anahtar kelime olarak eklenir.  
  
|||||  
|---|---|---|---|  
|[Soyut](abstract.md)|[Olarak](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[Mola](break.md)|[Bayt](../builtin-types/integral-numeric-types.md)|[Durumda](switch.md)|[Yakalamak](try-catch.md)|  
|[char](../builtin-types/char.md)|[Kontrol](checked.md)|[Sınıfı](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[Varsayılan](default.md)|[temsilci](../builtin-types/reference-types.md)|  
|[yapmak](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[Başka](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[Olay](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[Extern](extern.md)|[yanlış](../builtin-types/bool.md)|  
|[Sonunda](try-finally.md)|[Sabit](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[Için](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[eğer](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[Inç](in.md)|[int](../builtin-types/integral-numeric-types.md)|[Arabirim](interface.md)|[Iç](internal.md)|
|[bir](is.md)|[Kilit](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Yeni](../operators/new-operator.md)|[Null](null.md)|[Nesne](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[çıkış](out.md)|[Geçersiz kılma](override.md)|[params](params.md)|[Özel](private.md)|
|[protected](protected.md)|[Kamu](public.md)|[Readonly](readonly.md)|[Referans](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[Statik](static.md)|[Dize](../builtin-types/reference-types.md)|
|[Yapı](../builtin-types/struct.md)|[Anahtarı](switch.md)|[bu](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[Deneyin](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[Uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Güvenli olmayan](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Kullan -arak](using.md)|[statik kullanarak](using-static.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|
|[volatile](volatile.md)|[Süre](while.md)|

## <a name="contextual-keywords"></a>Bağlamsal anahtar kelimeler

 İçeriksel anahtar kelime, kodda belirli bir anlam sağlamak için kullanılır, ancak C#'da ayrılmış bir sözcük değildir. Bazı bağlamsal anahtar kelimeler, gibi `partial` ve, `where`iki veya daha fazla bağlamlarda özel anlamları vardır.  
  
||||  
|---|---|---|  
|[Ekle](add.md)|[takma ad](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[Tarafından](by.md)|
|[descending](descending.md)|[Dinamik](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Kaynak](from-clause.md)|[get](get.md)|[Küresel](../operators/namespace-alias-qualifier.md)|
|[grup](group-clause.md)|[içine](into.md)|[Katılın](join-clause.md)|
|[Izin](let-clause.md)|[nameof](../operators/nameof.md)|[-ını](on.md)|
|[Orderby](orderby-clause.md)|[kısmi (tür)](partial-type.md)|[kısmi (yöntem)](partial-method.md)|
|[Kaldırmak](remove.md)|[Seçin](select-clause.md)|[Ayarlamak](set.md)|
|[yönetilmemiş (genel tür kısıtlaması)](where-generic-type-constraint.md)|[Değer](value.md)|[var](var.md)|
|[when (filtre koşulu)](when.md)|[where (genel tür kısıtlaması)](where-generic-type-constraint.md)|[where (sorgu yan tümcesi)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
