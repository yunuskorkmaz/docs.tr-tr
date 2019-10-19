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
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581856"
---
# <a name="array-conversions-visual-basic"></a>Dizi Dönüştürmeleri (Visual Basic)
Aşağıdaki koşulları karşılamanız kaydıyla, bir dizi türünü farklı bir dizi türüne dönüştürebilirsiniz:  
  
- **Eşit derece.** İki dizinin dereceleri aynı olmalıdır, diğer bir deyişle, aynı sayıda boyutlara sahip olmaları gerekir. Ancak, ilgili boyutların uzunluklarının aynı olması gerekmez.  
  
- **Öğe veri türü.** Her iki dizinin öğelerinin veri türleri başvuru türünde olmalıdır. En az bir değer türü dahil olduğu için `Integer` dizisini `Long` dizisine veya hatta `Object` dizisine dönüştüremezsiniz. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
- **Söylebilirlik.** İki dizinin öğe türleri arasında genişletme veya daraltma bir dönüştürme yapılabilir olmalıdır. Bu gereksinimi başarısız yapan bir örnek, bir `String` dizisi ile <xref:System.Attribute?displayProperty=nameWithType> türetilen bir sınıfın dizisi arasında bir dönüştürme girişiminde bulunur. Bu iki tür hiçbir şey ortak değildir ve aralarında herhangi bir tür dönüştürme yoktur.  
  
 Bir dizi türünün diğerine dönüştürülmesi, ilgili öğelerin dönüştürülmesine genişleyen veya daraltma olmasına bağlı olarak genişletme veya daraltma. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Bir nesne dizisine dönüştürme  
 @No__t_0 bir diziyi başlatmadan bildirdiğinizde, öğe türü başlatılmamış kaldığı sürece `Object`. Belirli bir sınıfın dizisine ayarladığınızda, bu sınıfın türünü alır. Ancak, temel alınan türü hala `Object` ve daha sonra ilişkisiz bir sınıfın başka bir dizisine ayarlayabilirsiniz. Tüm sınıflar `Object` türediğinden, dizinin öğe türünü herhangi bir sınıftan başka bir sınıfa dönüştürebilirsiniz.  
  
 Aşağıdaki örnekte `student` ve `String` türleri arasında dönüştürme yoktur, ancak her ikisi de `Object` türetilir, bu nedenle tüm atamalar geçerlidir.  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Bir dizinin temel alınan türü  
 Özgün olarak belirli bir sınıf içeren bir diziyi bildirirseniz, temel alınan öğe türü bu sınıftır. Daha sonra başka bir sınıfın dizisine ayarlarsanız, iki sınıf arasında bir dönüştürme olmalıdır.  
  
 Aşağıdaki örnekte, `students` bir `student` dizisidir. @No__t_0 ve `student` arasında dönüştürme olmadığından, son ifade başarısız olur.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Visual Basic bir nesneyi başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
