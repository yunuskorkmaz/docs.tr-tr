---
title: Dizi Dönüştürmeler
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
ms.openlocfilehash: 1d20b01200d3f967e3355dc6e9651291003d140e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402011"
---
# <a name="array-conversions-visual-basic"></a>Dizi Dönüştürmeleri (Visual Basic)
Aşağıdaki koşulları karşılamanız kaydıyla, bir dizi türünü farklı bir dizi türüne dönüştürebilirsiniz:  
  
- **Eşit derece.** İki dizinin dereceleri aynı olmalıdır, diğer bir deyişle, aynı sayıda boyutlara sahip olmaları gerekir. Ancak, ilgili boyutların uzunluklarının aynı olması gerekmez.  
  
- **Öğe veri türü.** Her iki dizinin öğelerinin veri türleri başvuru türünde olmalıdır. `Integer` `Long` `Object` En az bir değer türü dahil olduğu için bir diziyi diziye veya hatta bir diziye dönüştüremezsiniz. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).  
  
- **Söylebilirlik.** İki dizinin öğe türleri arasında genişletme veya daraltma bir dönüştürme yapılabilir olmalıdır. Bu gereksinimi başarısız yapan bir örnek, bir `String` dizi ve öğesinden türetilen bir sınıfın dizisi arasında dönüştürme girişiminde bulunur <xref:System.Attribute?displayProperty=nameWithType> . Bu iki tür hiçbir şey ortak değildir ve aralarında herhangi bir tür dönüştürme yoktur.  
  
 Bir dizi türünün diğerine dönüştürülmesi, ilgili öğelerin dönüştürülmesine genişleyen veya daraltma olmasına bağlı olarak genişletme veya daraltma. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Bir nesne dizisine dönüştürme  
 Bir diziyi başlatmadan bildirdiğinizde `Object` , öğe türü `Object` başlatılmamış kaldığı sürece. Belirli bir sınıfın dizisine ayarladığınızda, bu sınıfın türünü alır. Ancak, temel alınan türü hala olur `Object` ve daha sonra ilişkisiz bir sınıfın başka bir dizisine ayarlayabilirsiniz. Tüm sınıflar öğesinden türetildiğinden `Object` , dizinin öğe türünü herhangi bir sınıftan başka bir sınıfa dönüştürebilirsiniz.  
  
 Aşağıdaki örnekte, türler arasında dönüştürme yoktur `student` `String` , ancak her ikisi de öğesinden türetilir, bu `Object` nedenle tüm atamalar geçerlidir.  
  
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
  
 Aşağıdaki örnekte `students` bir `student` dizidir. Ve arasında dönüştürme olmadığından `String` `student` , son ifade başarısız olur.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Örtük ve Açık Dönüştürmeler](implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme](how-to-convert-an-object-to-another-type.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
- [Diziler](../arrays/index.md)
