---
title: Geçersiz Kılmalar
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351382"
---
# <a name="overrides-visual-basic"></a>Geçersiz Kılmalar (Visual Basic)

Bir özellik veya yordamın, bir temel sınıftan devralınan aynı adlı özelliği veya yordamı geçersiz kıldığını belirtir.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overrides` kullanabilirsiniz.

- **Birleşik değiştiriciler.** Aynı bildirimde `Shadows` veya `Shared` birlikte `Overrides` belirtemezsiniz. Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overrides``Overridable` birleştiremezsiniz.

- **Imza eşleşiyor.** Bu bildirimin imzası, geçersiz kıldığından özelliğin veya yordamın *imzasıyla* tam olarak eşleşmelidir. Bu, parametre listelerinin aynı sırada aynı veri türleriyle aynı sayıda parametreye sahip olması gerektiği anlamına gelir.

  İmzaya ek olarak, geçersiz kılma bildirimi de tam olarak aşağıdaki gibi eşleşmelidir:

  - Erişim düzeyi

  - Varsa, dönüş türü

- **Genel Imzalar.** Genel yordam için imza, tür parametrelerinin sayısını içerir. Bu nedenle, geçersiz kılma bildirimi aynı zamanda temel sınıf sürümüyle eşleşmelidir.

- **Ek eşleşme.** Bu bildirimin, temel sınıf sürümünün imzasını eşleştirmesinin yanı sıra aşağıdaki şekilde de eşleşmesi gerekir:

  - Erişim düzeyi değiştiricisi ( [genel](../../../visual-basic/language-reference/modifiers/public.md)gibi)

  - Her parametrenin mekanizmasını geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))

  - Genel yordamın her tür parametresindeki kısıtlama listeleri

- **Gölgeleme ve geçersiz kılma.** Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.

`Overrides`kullanırsanız, derleyici kitaplık API 'lerinizin C# daha kolay bir şekilde çalışması için `Overloads` dolaylı olarak ekler.

`Overrides` değiştiricisi şu bağlamlarda kullanılabilir:

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
