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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392034"
---
# <a name="overrides-visual-basic"></a>Geçersiz Kılmalar (Visual Basic)

Bir özellik veya yordamın, bir temel sınıftan devralınan aynı adlı özelliği veya yordamı geçersiz kıldığını belirtir.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Overrides`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.

- **Birleşik değiştiriciler.** `Overrides` `Shadows` Aynı bildirimde veya ile birlikte belirtemezsiniz `Shared` . Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overridable` ile birleştiremezsiniz `Overrides` .

- **Imza eşleşiyor.** Bu bildirimin imzası, geçersiz kıldığından özelliğin veya yordamın *imzasıyla* tam olarak eşleşmelidir. Bu, parametre listelerinin aynı sırada aynı veri türleriyle aynı sayıda parametreye sahip olması gerektiği anlamına gelir.

  İmzaya ek olarak, geçersiz kılma bildirimi de tam olarak aşağıdaki gibi eşleşmelidir:

  - Erişim düzeyi

  - Varsa, dönüş türü

- **Genel Imzalar.** Genel yordam için imza, tür parametrelerinin sayısını içerir. Bu nedenle, geçersiz kılma bildirimi aynı zamanda temel sınıf sürümüyle eşleşmelidir.

- **Ek eşleşme.** Bu bildirimin, temel sınıf sürümünün imzasını eşleştirmesinin yanı sıra aşağıdaki şekilde de eşleşmesi gerekir:

  - Erişim düzeyi değiştiricisi ( [genel](public.md)gibi)

  - Her parametrenin mekanizmasını geçirme ([ByVal](byval.md) veya [ByRef](byref.md))

  - Genel yordamın her tür parametresindeki kısıtlama listeleri

- **Gölgeleme ve geçersiz kılma.** Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.

Kullanırsanız `Overrides` , derleyici `Overloads` kitaplık API 'Lerinizin C# ile daha kolay çalışmasını sağlamak için örtülü olarak ekler.

`Overrides`Değiştirici şu bağlamlarda kullanılabilir:

- [Function Deyimi](../statements/function-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Anahtar sözcükler](../keywords/index.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../statements/type-list.md)
