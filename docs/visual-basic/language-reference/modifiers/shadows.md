---
title: Shadows
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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351270"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Bir temel sınıfta, belirtilen bir programlama öğesinin, aynı adlı bir öğeyi yeniden bildirdiğini ve daha fazla yüklenmiş öğeler kümesini gizlediğini belirtir.

## <a name="remarks"></a>Açıklamalar

Gölgeleme için ana amaç ( *ada göre gizleme*olarak da bilinir), sınıf üyelerinizin tanımını korur. Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir. Bu durumda `Shadows` değiştirici, sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.

Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Shadows` yalnızca sınıf düzeyinde kullanabilirsiniz. Yani, bir `Shadows` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

  Tek bir bildirim ifadesinde yalnızca bir gölgeleme öğesi bildirebilirsiniz.

- **Birleşik değiştiriciler.** Aynı bildirimde `Overloads`, `Overrides`veya `Static` birlikte `Shadows` belirtemezsiniz.

- **Öğe türleri.** Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir. Bir özelliği veya yordamı başka bir özellik veya yordamla gölgelendirebiliyorsanız, parametrelerin ve dönüş türünün temel sınıf özelliği veya yordamındakilerle eşleşmesi gerekmez.

- **Erişme.** Temel sınıftaki gölgelendirilmiş öğe, normalde onu gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Ancak aşağıdaki noktalar geçerlidir.

  - Gölgeleme öğesine başvuran koddan erişilebilir değilse, başvuru gölgelendirilmiş öğe olarak çözümlenir. Örneğin, bir `Private` öğesi bir temel sınıf öğesini göltikten sonra, `Private` öğesine erişim izni olmayan kod bunun yerine temel sınıf öğesine erişir.

  - Bir öğeyi gölgelendiriseniz, taban sınıfının türüyle belirtilen bir nesne aracılığıyla gölgelendirilmiş öğeye erişmeye devam edebilirsiniz. Ayrıca, `MyBase`aracılığıyla da erişebilirsiniz.

`Shadows` değiştiricisi şu bağlamlarda kullanılabilir:

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
- [Visual Basic gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
