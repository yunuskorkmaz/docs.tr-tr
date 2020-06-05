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
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392112"
---
# <a name="overloads-visual-basic"></a>Aşırı Yüklemeler (Visual Basic)

Bir özellik veya yordamın, aynı ada sahip bir veya daha fazla var olan özelliği ya da yordamları yeniden bildirdiğini belirtir.

## <a name="remarks"></a>Açıklamalar

*Aşırı yükleme* , aynı kapsamda verilen bir özellik veya yordam adı için birden fazla tanım sağlama uygulamasıdır. Farklı imzaya sahip bir özellik veya yordamın yeniden bildirilmesi bazen *imzaya göre gizleme*olarak adlandırılır.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** `Overloads`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.

- **Birleşik değiştiriciler.** `Overloads`Aynı yordam bildiriminde [gölgilerle](shadows.md) birlikte belirtemezsiniz.

- **Gerekli farklar.** Bu Bildirimdeki *imza* , aşırı yüklediği her özellik veya yordamın imzasıyla farklı olmalıdır. İmza, özellik veya yordam adını aşağıdakiler ile birlikte içerir:

  - parametre sayısı

  - Parametrelerin sırası

  - parametrelerin veri türleri

  - tür parametrelerinin sayısı (genel yordam için)

  - dönüş türü (yalnızca bir dönüştürme işleci yordamı için)

  Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her biri bir veya daha fazla önceki yönden daha fazla diğerlerinden farklı olmalıdır. Bu, derleyicinin kodu özellik veya yordamı çağırdığında hangi sürümün kullanılacağını ayırt etmesine olanak tanır.

- **İzin verilmeyen farklar.** Aşağıdakilerden bir veya daha fazla değişiklik yapmak, imzanın bir parçası olmadıklarından bir özellik veya yordamı aşırı yüklemek için geçerli değildir:

  - bir değer döndürüp döndürmeksizin (bir yordam için)

  - dönüş değerinin veri türü (dönüştürme işleci dışında)

  - parametrelerin veya tür parametrelerinin adları

  - Tür Parametrelerindeki Kısıtlamalar (genel yordam için)

  - parametre değiştirici anahtar sözcükleri ( `ByRef` veya gibi `Optional` )

  - Özellik veya yordam değiştirici anahtar sözcükleri ( `Public` veya gibi `Shared` )

- **İsteğe bağlı değiştirici.** `Overloads`Aynı sınıfta birden fazla aşırı yüklenmiş özellik veya yordam tanımlarken değiştirici kullanmanız gerekmez. Ancak, `Overloads` bildirimlerden birinde kullanıyorsanız, bunların tümünde kullanmanız gerekir.

- **Gölgeleme ve aşırı yükleme.** `Overloads`, bir temel sınıfta varolan bir üyeyi veya aşırı yüklenmiş üyelerin gölgesini almak için de kullanılabilir. `Overloads`Bu şekilde kullandığınızda, temel sınıf üyesiyle aynı ada ve aynı parametre listesine sahip özelliği veya yöntemi bildirirsiniz ve `Shadows` anahtar sözcüğünü sağlamamalısınız.

Kullanırsanız `Overrides` , derleyici `Overloads` kitaplık API 'Lerinizin C# ile daha kolay çalışmasını sağlamak için örtülü olarak ekler.

`Overloads`Değiştirici şu bağlamlarda kullanılabilir:

- [Function Deyimi](../statements/function-statement.md)

- [Operator Deyimi](../statements/operator-statement.md)

- [Property Deyimi](../statements/property-statement.md)

- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](shadows.md)
- [Yordam Aşırı Yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [İşleç Yordamları](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
