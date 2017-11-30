---
title: "Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0dd2d678bbfdeaa6b12b5b5a4f69d0fbca8c1944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Dizilerle ilgili sorun giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
