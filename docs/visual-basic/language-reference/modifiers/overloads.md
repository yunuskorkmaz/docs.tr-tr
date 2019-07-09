---
title: Aşırı Yüklemeler (Visual Basic)
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
ms.openlocfilehash: 838207fe3ac5b8f57d030617546b9b7fa25dc939
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663534"
---
# <a name="overloads-visual-basic"></a>Aşırı Yüklemeler (Visual Basic)

Bir özelliğin ya da yordamın bir veya daha fazla var olan özellikler veya aynı ada sahip yordamları gizlediğini belirtir.

## <a name="remarks"></a>Açıklamalar

*Aşırı yükleme* aynı kapsamda belirli bir özellik veya yordam adı için birden fazla tanım sağlayan uygulamadır. Bir özellik veya yordamı farklı imzayla redeclaring bazen adlı *imzaya göre gizleme*.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Overloads` yalnızca bir özellik veya yordamı bildirim deyiminde.

- **Birleşik değiştiriciler.** Belirtemezsiniz `Overloads` ile birlikte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) aynı yordam bildirimi.

- **Farklar gereklidir.** *İmza* Bu bildirimde her bir özellik veya aşırı yordamı imzasının farklı olmalıdır. İmza özelliği ya da yordamın adı ile birlikte aşağıdaki oluşur:

  - parametre sayısı

  - Parametreler sırası

  - parametrelerinin veri türleri

  - Tür parametreleri (için genel bir yordam) sayısı

  - dönüş türü (yalnızca bir dönüştürme işleci yordam)

  Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her diğer tüm kişilerden gelen bir veya daha önceki gizliliğinize farklı olmalıdır. Bu özellik veya yordam kodu çağırdığında, kullanılacak hangi sürümünü ayırt etmek derleyicinin sağlar.

- **İzin verilmeyen farklar.** Bir veya daha fazlasını değiştirme, imzasının parçası olmadıklarından bir özelliği ya da yordamın, aşırı yükleme için geçerli değil:

  - (bir yordam için) bir değer olup olmadığını döndürür

  - (bir dönüşüm işleci dışında) dönüş değerinin veri türü

  - Tür parametreleri ve parametre adları

  - (için genel bir yordam) tür parametrelerindeki kısıtlamalar

  - parametre değiştiricisi anahtar sözcükleri (gibi `ByRef` veya `Optional`)

  - özellik veya yordamı değiştiricisi anahtar sözcükleri (gibi `Public` veya `Shared`)

- **İsteğe bağlı bir değiştirici.** Kullanmak zorunda değil `Overloads` aynı sınıf içinde birden fazla aşırı yüklenmiş özellikler ya da yordamlar tanımlarken değiştiricisi. Ancak, kullanırsanız `Overloads` bildirimleri her birinde, bunların tümünde kullanmanız gerekir.

- **Gölgeleme ve aşırı yükleme.** `Overloads` Ayrıca varolan bir üye gölge ya da taban sınıfında aşırı yüklenmiş üyelerin kümesini kullanılabilir. Kullanırken `Overloads` bu şekilde, özellik veya yöntem ile aynı ada ve aynı parametre listesi temel sınıf üye olarak bildirmek ve sağladığınız değil `Shadows` anahtar sözcüğü.

Kullanırsanız `Overrides`, derleyicinin dolaylı olarak ekler `Overloads` kitaplığınızı API'leri ile çalışmak üzere C# daha kolay.

`Overloads` Bu bağlamda değiştirici kullanılabilir:

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)

- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Yordam Aşırı Yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
