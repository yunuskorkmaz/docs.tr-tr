---
title: Nesne Değişkeni Değerleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004590"
---
# <a name="object-variable-values-visual-basic"></a>Nesne Değişkeni Değerleri (Visual Basic)
[Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) değişkeni herhangi bir türdeki verilere başvurabilir. @No__t-0 değişkeninde depoladığınız değer bellekte başka bir yerde tutulur, ancak değişken verilerin bir işaretçisini tutar.  
  
## <a name="object-classifier-functions"></a>Nesne sınıflandırıcı Işlevleri  
 Visual Basic, aşağıdaki tabloda gösterildiği gibi `Object` değişkeninin başvurduğu hakkında bilgi döndüren işlevler sağlar.  
  
|İşlev|Nesne değişkeni öğesine başvuruyorsa true döndürür|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tek bir değer yerine bir değer dizisi|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[Tarih veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) değeri veya tarih ve saat değeri olarak yorumlanabilen bir dize|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Eksik veya varolmayan verileri temsil eden <xref:System.DBNull> türünde bir nesne|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|@No__t-0 ' dan türetilen bir özel durum nesnesi|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Hiçbir şey](../../../../visual-basic/language-reference/nothing.md)yok, başka bir deyişle, şu anda değişkene atanmış nesne yok|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Sayı veya bir sayı olarak yorumlanabilecek dize|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Bir başvuru türü (dize, dizi, temsilci veya sınıf türü gibi)|  
  
 Bir işleme veya yordama geçersiz bir değer gönderilmesini önlemek için bu işlevleri kullanabilirsiniz.  
  
## <a name="typeof-operator"></a>TypeOf İşleci  
 Bir nesne değişkeninin şu anda belirli bir veri türüne başvuruda bulunup bulunmadığını anlamak için [typeof işlecini](../../../../visual-basic/language-reference/operators/typeof-operator.md) de kullanabilirsiniz. @No__t-0... `Is` ifadesi, işlenenin çalışma zamanı türü belirtilen türden türetildiyse veya uygularsa, `True` olarak değerlendirilir.  
  
 Aşağıdaki örnek, değer ve başvuru türlerine başvuran nesne değişkenlerinde `TypeOf` kullanır.  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 Yukarıdaki örnek, **hata ayıklama** penceresine aşağıdaki satırları Yazar:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 @No__t-0 nesne değişkeni `Integer` türünde verileri ifade eder ve `frm` <xref:System.Windows.Forms.Form> sınıfının bir nesnesine başvurur.  
  
## <a name="object-arrays"></a>Nesne dizileri  
 @No__t-0 değişkenlerinin dizisini bildirebilir ve kullanabilirsiniz. Bu, çeşitli veri türlerini ve nesne sınıflarını işlemeniz gerektiğinde faydalıdır. Bir dizideki tüm öğeler aynı tanımlanmış veri türüne sahip olmalıdır. Bu veri türünü @no__t olarak bildirmek-0, nesneleri ve sınıf örneklerini dizideki diğer veri türleriyle birlikte depolamanıza olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
