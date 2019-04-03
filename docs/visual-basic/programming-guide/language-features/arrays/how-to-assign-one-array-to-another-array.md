---
title: 'Nasıl yapılır: Bir diziyi başka diziye (Visual Basic) atama'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835290"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Nasıl yapılır: Bir diziyi başka diziye (Visual Basic) atama
Diziler nesneler olduğundan atama deyimleri diğer nesne türleri gibi kullanabilirsiniz. Bir dizi değişkenini dizi öğeleri ve boyut sayısı ve uzunluk bilgileri oluşturan veri için bir işaretçi tutar ve bu işaretçi atama kopyalar.  
  
### <a name="to-assign-one-array-to-another-array"></a>Bir diziyi başka diziye atama için  
  
1.  İki dizi aynı boyut sayısı (boyut sayısı) ve uyumlu öğe veri türleri olduğundan emin olun.  
  
2.  Hedef dizi için kaynak dizisi atamak için bir standart atama ifadesi kullanın. Parantezler ile ya da dizi adı izlemeyin.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Bir diziyi başka birine atadığınızda, aşağıdaki kurallar geçerlidir:  
  
-   **Eşit sıralamalara sahip.** Hedef dizinin boyut (boyut sayısı), kaynak diziden aynı olmalıdır.  
  
     Sıralamalara sahip iki dizinin eşitse sağlanan boyutları eşit olması gerekmez. Atama sırasında belirli bir boyut içindeki öğelerin sayısını değiştirebilirsiniz.  
  
-   **Öğe türleri.** Her iki ya da bir dizi olmalıdır *başvuru türüne* öğelerin veya her iki dizide olmalıdır *değer türü* öğeleri. Daha fazla bilgi için [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Her iki dizide değer türü öğeleri varsa öğe veri türleri tam olarak aynı olmalıdır. Bunun tek istisnası, bir dizi atayabilirsiniz olan `Enum` , temel türü bir dizi öğelerine `Enum`.  
  
    -   Her iki dizide öğe türü başvurusu varsa, kaynak öğe türü hedef öğenin türünden türetilmesi gerekir. Bu durumda, iki dizi öğeleri olarak aynı devralma ilişkisine sahiptir. Bu adlandırılır *dizi kovaryansı*.  
  
 Derleyici, veri türleri uyumlu değilse, yukarıdaki kuralları, örneğin ihlal bir hata veya sıralamalara sahip eşit bildirir. Hata işleme kodunuzda ödev denemeden önce diziler uyumlu olduğundan emin olmak için ekleyebilirsiniz. Ayrıca [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md) bir özel durum kaçınmak istiyorsanız anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
