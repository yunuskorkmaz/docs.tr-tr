---
title: 'Nasıl yapılır: Bir Diziyi Başka Diziye Atama'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351884"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)

Diziler nesneler olduğundan, bunları diğer nesne türleri gibi atama deyimleriyle kullanabilirsiniz. Dizi değişkeni, dizi öğeleri ve derecelendirme ve uzunluk bilgilerini constituting veri için bir işaretçi tutar ve bir atama yalnızca bu işaretçiyi kopyalar.

### <a name="to-assign-one-array-to-another-array"></a>Bir diziyi başka bir diziye atamak için

1. İki dizinin aynı dereceye (boyut sayısına) ve uyumlu öğe veri türlerine sahip olduğundan emin olun.

2. Kaynak diziyi hedef diziye atamak için standart atama ekstresi kullanın. Parantez ile dizi adını takip etmez.

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

Bir diziyi diğerine atadığınızda, aşağıdaki kurallar geçerlidir:

- **Eşit dereceleri.** Hedef dizinin derecesi (boyut sayısı), kaynak dizinin ile aynı olmalıdır.

  İki dizinin dereceleri eşitse, boyutların eşit olması gerekmez. Belirli boyuttaki öğelerin sayısı atama sırasında değişebilir.

- **Öğe türleri.** Her iki dizide de *başvuru türü* öğeler olmalıdır ya da her iki dizi de *değer türü* öğelerine sahip olmalıdır. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).

  - Her iki dizide de değer türü öğeler varsa, öğe veri türleri tam olarak aynı olmalıdır. Bunun tek istisnası, bir dizi `Enum` öğeyi bu `Enum`temel türünün dizisine atayabilmenizi sağlar.

  - Her iki dizide de başvuru türü öğeleri varsa, kaynak öğe türünün hedef öğe türünden türetilmesi gerekir. Bu durumda, iki dizi öğeleriyle aynı devralma ilişkisine sahiptir. Buna *dizi Kovaryans*adı verilir.

Yukarıdaki kurallar ihlal edildiğinde derleyici bir hata bildirir, örneğin, veri türleri uyumlu değilse veya derecelendirmelerinin eşit olduğu durumlarda. Bir atamayı denemeden önce dizilerin uyumlu olduğundan emin olmak için kodunuza hata işleme ekleyebilirsiniz. Özel durum oluşturmamak istiyorsanız [TryCast İşleci](../../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğünü de kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
