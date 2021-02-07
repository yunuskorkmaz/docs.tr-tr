---
description: 'Daha fazla bilgi edinin: gölgeler (Visual Basic)'
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
ms.openlocfilehash: 4a455a78c36e15db977936b81c22e7a5b03d107e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700851"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Bir temel sınıfta, belirtilen bir programlama öğesinin, aynı adlı bir öğeyi yeniden bildirdiğini ve daha fazla yüklenmiş öğeler kümesini gizlediğini belirtir.

## <a name="remarks"></a>Açıklamalar

Gölgeleme için ana amaç ( *ada göre gizleme* olarak da bilinir), sınıf üyelerinizin tanımını korur. Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir. Bu durumda, değiştirici, `Shadows` sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.

Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Shadows`Yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir öğe için bildirim bağlamı `Shadows` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

  Tek bir bildirim ifadesinde yalnızca bir gölgeleme öğesi bildirebilirsiniz.

- **Birleşik değiştiriciler.** `Shadows` `Overloads` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overrides` `Static` .

- **Öğe türleri.** Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir. Bir özelliği veya yordamı başka bir özellik veya yordamla gölgelendirebiliyorsanız, parametrelerin ve dönüş türünün temel sınıf özelliği veya yordamındakilerle eşleşmesi gerekmez.

- **Erişme.** Temel sınıftaki gölgelendirilmiş öğe, normalde onu gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Ancak aşağıdaki noktalar geçerlidir.

  - Gölgeleme öğesine başvuran koddan erişilebilir değilse, başvuru gölgelendirilmiş öğe olarak çözümlenir. Örneğin, bir öğe bir `Private` temel sınıf öğesini gölerse, öğesine erişim izni olmayan kod, `Private` bunun yerine temel sınıf öğesine erişir.

  - Bir öğeyi gölgelendiriseniz, taban sınıfının türüyle belirtilen bir nesne aracılığıyla gölgelendirilmiş öğeye erişmeye devam edebilirsiniz. Ayrıca, üzerinden de erişebilirsiniz `MyBase` .

`Shadows`Değiştirici şu bağlamlarda kullanılabilir:

- [Class Deyimi](../statements/class-statement.md)

- [Const Deyimi](../statements/const-statement.md)

- [Declare Deyimi](../statements/declare-statement.md)

- [Delegate Deyimi](../statements/delegate-statement.md)

- [Dim Deyimi](../statements/dim-statement.md)

- [Enum Deyimi](../statements/enum-statement.md)

- [Event Deyimi](../statements/event-statement.md)

- [Function Deyimi](../statements/function-statement.md)

- [Interface Deyimi](../statements/interface-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- [Structure Yapısı](../statements/structure-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Paylaşılan](shared.md)
- [Static](static.md)
- [Özel](private.md)
- [Me, My, MyBase ve MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Aşırı Yüklemeler](overloads.md)
- [Overridable](overridable.md)
- [Geçersiz Kılmalar](overrides.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
