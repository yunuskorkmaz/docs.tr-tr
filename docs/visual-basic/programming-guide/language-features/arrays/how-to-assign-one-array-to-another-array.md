---
title: 'Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647936"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)
Diziler nesneler olduğundan, diğer nesne türleri gibi atama deyimleri kullanabilirsiniz. Dizi öğeleri ve derece ve uzunluğu bilgileri oluşturan veri bir işaretçi bir dizi değişkeni tutar ve yalnızca bu işaretçinin atama kopyalar.  
  
### <a name="to-assign-one-array-to-another-array"></a>Bir diziyi başka diziye atama için  
  
1.  İki dizisi aynı derece (dimensions sayısı) ve uyumlu öğesi veri türleri bulunduğundan emin olun.  
  
2.  Hedef dizi kaynak dizi atamak için bir standart atama deyimini kullanın. Parantezler ile ya da dizi adı izlemeyin.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Başka bir dizi atadığınızda, aşağıdaki kurallar geçerlidir:  
  
-   **Eşit sıralar.** Hedef dizi derecesini (dimensions sayısı), kaynak dizinin aynı olması gerekir.  
  
     İki dizi sıralar eşit olması koşuluyla boyutları eşit olması gerekmez. Belirli bir boyut öğe sayısı, atama sırasında değiştirebilirsiniz.  
  
-   **Öğe türleri.** Her iki ya da bir dizi olmalıdır *başvuru türüne* öğeleri veya her iki diziler olmalıdır *değer türü* öğeleri. Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Her iki diziler değer türü öğeleri varsa öğe veri türlerini tam olarak aynı olması gerekir. Bunun tek istisnası, bir dizi atayabilirsiniz olan `Enum` , temel türü bir dizi öğelerine `Enum`.  
  
    -   İki dizi öğeleri türü başvurusu varsa, kaynak öğe türü hedef öğe türünden türetilmelidir. Bu durumda, iki dizi öğeleri olarak aynı devralma ilişkisi vardır. Bu adlı *dizi kovaryansı*.  
  
 Veri türleri uyumlu değilse yukarıdaki kuralları, örneğin ihlal bir hata ya da sıralar eşit olmayan derleyici bildirir. Hata atama denemeden önce dizilerin uyumlu olduğundan emin olmak için kodunuzu işleme ekleyebilirsiniz. Aynı zamanda [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md) bir özel durum atma önlemek isterseniz anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum Deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
