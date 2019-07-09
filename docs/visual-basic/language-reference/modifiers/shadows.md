---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: c9dfff99e2634b79ad6b44721f40583d21c9b98e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664139"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Bildirilmiş bir programlama öğesinin redeclares ve bir aynı adlı bir öğe veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler belirtir.

## <a name="remarks"></a>Açıklamalar

Gölgeleme ana amacı (olarak da bilinen olduğu *adına göre gizleme*), sınıf üyelerinin tanımına korumak için. Temel sınıf olarak zaten tanımlanmış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir. Böyle bir durumda `Shadows` değiştiricisi zorlar başvuruyor, sınıf üyesine çözümlenmesi aracılığıyla tanımlanmış, yerine yeni bir temel sınıf öğe için.

Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır. Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Shadows` yalnızca sınıf düzeyinde. Bildirim bağlamı başka bir deyişle bir `Shadows` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.

  Bir tek bir bildirim deyiminde yalnızca bir gölgeleme öğesi bildirebilirsiniz.

- **Birleşik değiştiriciler.** Belirtemezsiniz `Shadows` ile birlikte `Overloads`, `Overrides`, veya `Static` aynı bildirimde.

- **Öğe türleri.** Bildirilen öğe herhangi bir türden başka bir tür ile gölge. Bir özellik ya da başka bir özellik ya da yordamın yordamla gölge, parametreler ve dönüş türü temel sınıfın özellik veya yordamı içindeki alanlarla eşleşmesi gerekmez.

- **Erişme.** Gölgeli öğe temel sınıfta bu gölgeleri türetilmiş sınıf içinde normalde gelen kullanılamıyor. Ancak, aşağıdaki maddeler geçerlidir.

  - Gölgeleme öğesi kendisine başvuran koddan erişilebilir durumda değilse, başvuruyu gölgeli öğesine çözümlenir. Örneğin, bir `Private` öğesi bir temel sınıf öğesi, erişim iznine sahip olmayan kod gölgeliyor `Private` öğe temel sınıf öğe yerine erişir.

  - Bir öğe gölge, gölgeli öğe türü temel sınıfı ile bildirilen bir nesne üzerinden erişmeye devam edebilirsiniz. Üzerinden de erişebilirsiniz `MyBase`.

`Shadows` Bu bağlamda değiştirici kullanılabilir:

- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
