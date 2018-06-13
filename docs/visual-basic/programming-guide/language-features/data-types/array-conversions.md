---
title: Dizi Dönüştürmeleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: a179b7cf5b82132db88fb5412f0ca4be207f0987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651472"
---
# <a name="array-conversions-visual-basic"></a>Dizi Dönüştürmeleri (Visual Basic)
Aşağıdaki koşullara uyması şartıyla farklı dizi türü için bir dizi türü dönüştürebilirsiniz:  
  
-   **Eşit derece.** İki dizi sıralar aynı olması gerekir, diğer bir deyişle, Boyutlar aynı sayıda olmalıdır. Ancak, uzunlukları ilgili boyutlarının aynı olması gerekmez.  
  
-   **Öğe veri türü.** Veri türleri iki dizi öğelerinin başvuru türleri olması gerekir. Dönüştüremezsiniz bir `Integer` için dizi bir `Long` dizi veya hatta için bir `Object` en az bir değer türü olduğundan, dizi. Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Convertibility.** Genişletme veya daraltma, dönüştürme, iki dizi öğesi türleri arasında mümkün olması gerekir. Bu gereksinim başarısız arasında denenen bir dönüştürme örneğidir bir `String` dizi ve bir sınıf bir dizi türetilen <xref:System.Attribute?displayProperty=nameWithType>. Bu iki tür ortak ilgisi yoktur ve bunlar arasında herhangi bir türde bir dönüştürme yok vardır.  
  
 Bir dizi türü bir dönüştürme başka bir genişletme veya daraltma olup ilgili öğeleri dönüştürülmesi genişletme daraltma veya bağlı olarak. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Bir nesne dizisine dönüştürme  
 Ne zaman bildirdiğiniz bir `Object` , alt öğe türü başlatma olmadan dizisi `Object` başlatılmamış kaldığı sürece. Belirli bir sınıfın bir diziye ayarladığınızda, o sınıfın türü alır. Ancak, temel alınan türü hala olduğunu `Object`, ve daha sonra ilişkisiz bir sınıfın başka diziye ayarlayabilirsiniz. Tüm sınıflar türetmek beri `Object`, başka bir sınıf herhangi bir sınıfın dizinin öğesi türünü değiştirebilirsiniz.  
  
 Aşağıdaki örnekte, türleri arasında dönüştürme var `student` ve `String`, ancak her ikisi de öğesinden türetilen `Object`, tüm atamaları geçerlidir.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Bir dizi temel alınan türü  
 İlk olarak bir dizi belirli bir sınıf ile bildirirseniz, temel alınan öğe türü bu sınıftır. Daha sonra başka bir sınıfın bir diziye ayarlarsanız, iki sınıf arasında dönüştürme olmalıdır.  
  
 Aşağıdaki örnekte, `students` olan bir `student` dizi. Arasında dönüştürme mevcut olduğundan `String` ve `student`, son deyim başarısız olur.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
