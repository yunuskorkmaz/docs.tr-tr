---
title: C#Lerimi
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 2bdaa2f4cdb19d01948effd599177f68859cb82c
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291065"
---
# <a name="c-keywords"></a>C#Lerimi

Anahtar sözcükler, derleyiciye özel anlamlara sahip olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Önek olarak `@` içermedikleri sürece, programınızda tanımlayıcı olarak kullanılamaz. Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` değildir çünkü `if` bir anahtar sözcüktür.  
  
 Bu konudaki ilk tablo, bir programın herhangi bir C# bölümünde ayrılmış tanımlayıcılar olan anahtar sözcükleri listeler. Bu konudaki ikinci tablo, içindeki C#bağlamsal anahtar sözcükleri listeler. Bağlamsal anahtar sözcüklerde yalnızca sınırlı program bağlamında özel anlamı vardır ve bu bağlamın dışında tanımlayıcılar olarak kullanılabilir. Genellikle, C# dile yeni anahtar sözcükler eklendikçe, önceki sürümlerde yazılmış programları bozmamak için bağlamsal anahtar sözcükler olarak eklenirler.  
  
|||||  
|---|---|---|---|  
|[Soyut](abstract.md)|[gerektiği](../operators/type-testing-and-cast.md#as-operator)|[temel](base.md)|[bool](bool.md)|  
|[sonundan](break.md)|[bayt](../builtin-types/integral-numeric-types.md)|[harflerini](switch.md)|[yakalaya](try-catch.md)|  
|[Char](char.md)|[edildikten](checked.md)|[sınıfı](class.md)|[sabit](const.md)|  
|[devam](continue.md)|[Kategori](../builtin-types/floating-point-numeric-types.md)|[varsayılanını](default.md)|[ğini](delegate.md)|  
|[gösterme](do.md)|[Çift](../builtin-types/floating-point-numeric-types.md)|[değilse](if-else.md)|[yardımının](enum.md)|  
|[olay](event.md)|[anlaşılır](../operators/user-defined-conversion-operators.md)|[Dış](extern.md)|[yanlýþ](false-literal.md)|  
|[son olarak](try-finally.md)|[Düzenle](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[bekleniyor](for.md)|  
|[Foreach](foreach-in.md)|[Git](goto.md)|[kullandıysanız](if-else.md)|[indirgen](../operators/user-defined-conversion-operators.md)|  
|['ndaki](in.md)|['tir](../builtin-types/integral-numeric-types.md)|[arayüz](interface.md)|[iç](internal.md)|
|[eklenir](is.md)|[ine](lock-statement.md)|[kalacağını](../builtin-types/integral-numeric-types.md)|[uzayına](namespace.md)|
|[Yeni](../operators/new-operator.md)|[değer](null.md)|[nesne](object.md)|[operator](../operators/operator-overloading.md)|
|[dışı](out.md)|[manızı](override.md)|[parametrelerin](params.md)|[özelleştirme](private.md)|
|[korunamadı](protected.md)|[geneldir](public.md)|[özelliğinin](readonly.md)|[ref](ref.md)|
|[döndürülmesini](return.md)|[SByte](../builtin-types/integral-numeric-types.md)|[Sealed](sealed.md)|[kısadır](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[se](static.md)|[dizisinde](string.md)|
|[sýný](struct.md)|[değiştirebilirsiniz](switch.md)|[Bunun](this.md)|[yaratır](throw.md)|
|[değeri](true-literal.md)|[almaya](try-catch.md)|[EOF](../operators/type-testing-and-cast.md#typeof-operator)|[u](../builtin-types/integral-numeric-types.md)|
|['tur](../builtin-types/integral-numeric-types.md)|[olmayan](unchecked.md)|[olmayabilecek](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[kullanarak](using.md)|[statik kullanma](using-static.md)|[sanal](virtual.md)|[Kağıt](void.md)|
|[katılımcıdan](volatile.md)|[edilirken](while.md)|

## <a name="contextual-keywords"></a>Bağlamsal anahtar sözcükler

 Bağlam anahtar sözcüğü, kodda belirli bir anlamı sağlamak için kullanılır, ancak içinde C#ayrılmış bir sözcük değildir. @No__t-0 ve `where` gibi bazı bağlamsal anahtar sözcükler, iki veya daha fazla bağlamda özel anlamlara sahiptir.  
  
||||  
|---|---|---|  
|[ekleyemiyorum](add.md)|[alias](extern-alias.md)|[artan](ascending.md)|
|[eş](async.md)|[await](../operators/await.md)|[tarafından](by.md)|
|[sıralamada](descending.md)|[tir](dynamic.md)|[eşittir](equals.md)|
|[Kaynak](from-clause.md)|[Al](get.md)|[Genel](../operators/namespace-alias-qualifier.md)|
|[grubu](group-clause.md)|[birleştirin](into.md)|[join](join-clause.md)|
|[atalım](let-clause.md)|[NameOf](../operators/nameof.md)|[dayanır](on.md)|
|[OrderBy](orderby-clause.md)|[Kısmi (tür)](partial-type.md)|[partial (Yöntem)](partial-method.md)|
|[temizlenmesine](remove.md)|[seçin](select-clause.md)|[kurmak](set.md)|
|[yönetilmeyen (genel tür kısıtlaması)](where-generic-type-constraint.md)|[value](value.md)|[l](var.md)|
|[ne zaman (filtre koşulu)](when.md)|[WHERE (genel tür kısıtlaması)](where-generic-type-constraint.md)|[WHERE (sorgu yan tümcesi)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
