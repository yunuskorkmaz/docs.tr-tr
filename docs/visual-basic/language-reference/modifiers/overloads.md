---
title: Aşırı Yüklemeler
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351403"
---
# <a name="overloads-visual-basic"></a>Aşırı Yüklemeler (Visual Basic)

Bir özellik veya yordamın, aynı ada sahip bir veya daha fazla var olan özelliği ya da yordamları yeniden bildirdiğini belirtir.

## <a name="remarks"></a>Açıklamalar

*Aşırı yükleme* , aynı kapsamda verilen bir özellik veya yordam adı için birden fazla tanım sağlama uygulamasıdır. Farklı imzaya sahip bir özellik veya yordamın yeniden bildirilmesi bazen *imzaya göre gizleme*olarak adlandırılır.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overloads` kullanabilirsiniz.

- **Birleşik değiştiriciler.** Aynı yordam bildiriminde [gölgilerle](../../../visual-basic/language-reference/modifiers/shadows.md) birlikte `Overloads` belirtemezsiniz.

- **Gerekli farklar.** Bu Bildirimdeki *imza* , aşırı yüklediği her özellik veya yordamın imzasıyla farklı olmalıdır. İmza, özellik veya yordam adını aşağıdakiler ile birlikte içerir:

  - parametre sayısı

  - Parametrelerin sırası

  - parametrelerin veri türleri

  - tür parametrelerinin sayısı (genel yordam için)

  - dönüş türü (yalnızca bir dönüştürme işleci yordamı için)

  Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her biri bir veya daha fazla önceki yönden daha fazla diğerlerinden farklı olmalıdır. Bu, derleyicinin kodu özellik veya yordamı çağırdığında hangi sürümün kullanılacağını ayırt etmesine olanak tanır.

- **İzin verilmeyen farklar.** Aşağıdakilerden bir veya daha fazla değişiklik yapmak, imzanın bir parçası olmadıklarından bir özellik veya yordamı aşırı yüklemek için geçerli değildir:

  - bir değer döndürüp döndürmeksizin (bir yordam için)

  - Dönüş değerinin veri türü (dönüştürme işleci dışında)

  - parametrelerin veya tür parametrelerinin adları

  - Tür Parametrelerindeki Kısıtlamalar (genel yordam için)

  - parametre değiştirici anahtar sözcükleri (`ByRef` veya `Optional`gibi)

  - Özellik veya yordam değiştirici anahtar sözcükleri (`Public` veya `Shared`gibi)

- **İsteğe bağlı değiştirici.** Aynı sınıfta birden fazla aşırı yüklenmiş özellik veya yordam tanımlarken `Overloads` değiştiricisini kullanmanız gerekmez. Ancak, bildirimlerden birinde `Overloads` kullanıyorsanız, bunların tümünde kullanmanız gerekir.

- **Gölgeleme ve aşırı yükleme.** `Overloads`, bir temel sınıfta varolan bir üyeyi veya aşırı yüklenmiş Üyeler kümesini gölgelendirmek için de kullanılabilir. `Overloads` bu şekilde kullandığınızda, temel sınıf üyesiyle aynı ada ve aynı parametre listesine sahip olan özelliği veya yöntemi bildirirsiniz ve `Shadows` anahtar sözcüğünü sağlamamalısınız.

`Overrides`kullanırsanız, derleyici kitaplık API 'lerinizin C# daha kolay bir şekilde çalışması için `Overloads` dolaylı olarak ekler.

`Overloads` değiştiricisi şu bağlamlarda kullanılabilir:

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Yordam Aşırı Yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
