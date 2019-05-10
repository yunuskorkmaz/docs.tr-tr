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
ms.openlocfilehash: f69ed6e0040f33f810d324a76859d448e9dc7632
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601138"
---
# <a name="array-conversions-visual-basic"></a>Dizi Dönüştürmeleri (Visual Basic)
Aşağıdaki koşulları karşılaması koşuluyla, bir dizi türü farklı bir dizi türüne dönüştürebilirsiniz:  
  
- **Eşit boyut.** Sıralamalara sahip iki dizinin aynı olmalıdır, yani boyut sayıları aynı olmalıdır. Ancak, ilgili boyutların uzunlukları aynı olması gerekmez.  
  
- **Öğe veri türü.** İki dizi öğeleri veri türleri, başvuru türünde olması gerekir. Dönüştüremezsiniz bir `Integer` için dizi bir `Long` dizisi geçirin veya hatta için bir `Object` dizisi en az bir değer türü olduğundan. Daha fazla bilgi için [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
- **Convertibility.** Genişletme veya daraltma, dönüştürme, olası iki dizi öğesi türleri arasında olmalıdır. Bu gereksinim başarısız bir örnek denenen bir dönüştürme arasında olan bir `String` dizi ve bir sınıf bir dizi türetilen <xref:System.Attribute?displayProperty=nameWithType>. Ortak hiçbir şey bu iki tür vardır ve bunlar arasında dönüştürme herhangi bir türde bulunmaktadır.  
  
 Bir dizi türünde bir dönüştürme diğerine genişletme veya ilgili öğelerin dönüştürme genişletme daraltma mı bağlı olarak daraltma. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Bir nesne dizisine dönüştürme  
 Bildirdiğinizde bir `Object` dizisi bu öğe türünün başlatma olmadan `Object` başlatılmamış kaldığı sürece. Belirli bir sınıfın bir diziye ayarladığınızda, bu sınıf türüne göre alır. Ancak, temel alınan türü hala geçerli olduğunu `Object`, ve ardından ilişkisiz bir sınıfın başka bir dizi için ayarlayabilirsiniz. Tüm sınıflar türetilen beri `Object`, dizinin öğe türü herhangi bir sınıfın herhangi bir sınıf için değiştirebilirsiniz.  
  
 Aşağıdaki örnekte, türleri arasında dönüştürme var `student` ve `String`, ancak her ikisini de öğesinden türetilen `Object`, tüm atamalar geçerlidir.  
  
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
 İlk olarak belirli bir sınıfı olan bir dizi bildirirseniz, temel alınan öğe türünün bu sınıftır. Daha sonra başka bir sınıfın bir diziye ayarlarsanız, iki sınıf arasında bir dönüştürme olmalıdır.  
  
 Aşağıdaki örnekte, `students` olduğu bir `student` dizi. Arasında dönüştürme mevcut olduğundan `String` ve `student`, son deyim başarısız olur.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
