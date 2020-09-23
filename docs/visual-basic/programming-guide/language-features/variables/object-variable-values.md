---
title: Nesne Değişkeni Değerleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 800b9754ce27cc6a494dd781d06f4bdca8a10e87
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080237"
---
# <a name="object-variable-values-visual-basic"></a>Nesne Değişkeni Değerleri (Visual Basic)

[Nesne veri türü](../../../language-reference/data-types/object-data-type.md) değişkeni herhangi bir türdeki verilere başvurabilir. Bir değişkende depoladığınız değer, bir `Object` yerde, değişkenin kendisi de verilerin bir işaretçisini taşıdığı sürece bellekte tutulur.  
  
## <a name="object-classifier-functions"></a>Nesne sınıflandırıcı Işlevleri  

 Visual Basic `Object` , aşağıdaki tabloda gösterildiği gibi, bir değişkenin başvurduğu durum hakkında bilgi döndüren işlevler sağlar.  
  
|İşlev|Nesne değişkeni öğesine başvuruyorsa true döndürür|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tek bir değer yerine bir değer dizisi|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|[Tarih veri türü](../../../language-reference/data-types/date-data-type.md) değeri veya tarih ve saat değeri olarak yorumlanabilen bir dize|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<xref:System.DBNull>Eksik veya varolmayan verileri temsil eden türünde bir nesne|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Öğesinden türetilen bir özel durum nesnesi <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Hiçbir şey](../../../language-reference/nothing.md)yok, başka bir deyişle, şu anda değişkene atanmış nesne yok|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Sayı veya bir sayı olarak yorumlanabilecek dize|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Bir başvuru türü (dize, dizi, temsilci veya sınıf türü gibi)|  
  
 Bir işleme veya yordama geçersiz bir değer gönderilmesini önlemek için bu işlevleri kullanabilirsiniz.  
  
## <a name="typeof-operator"></a>TypeOf İşleci  

 Bir nesne değişkeninin şu anda belirli bir veri türüne başvuruda bulunup bulunmadığını anlamak için [typeof işlecini](../../../language-reference/operators/typeof-operator.md) de kullanabilirsiniz. `TypeOf`... `Is` İfadesi, `True` işlenenin çalışma zamanı türü belirtilen türden türetildiyse veya uygularsa olarak değerlendirilir.  
  
 Aşağıdaki örnek, `TypeOf` değer ve başvuru türlerine başvuran nesne değişkenlerinde kullanır.  
  
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
  
 Nesne değişkeni `num` , türündeki verileri ifade eder `Integer` ve `frm` bir sınıfının nesnesine başvurur <xref:System.Windows.Forms.Form> .  
  
## <a name="object-arrays"></a>Nesne dizileri  

 Bir değişken dizisi bildirebilir ve kullanabilirsiniz `Object` . Bu, çeşitli veri türlerini ve nesne sınıflarını işlemeniz gerektiğinde faydalıdır. Bir dizideki tüm öğeler aynı tanımlanmış veri türüne sahip olmalıdır. Bu veri türünü olarak bildirmek `Object` , nesneleri ve sınıf örneklerini dizideki diğer veri türleriyle birlikte depolamanıza olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişken Bildirimi](object-variable-declaration.md)
- [Nesne Değişkeni Ataması](object-variable-assignment.md)
- [Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma](how-to-refer-to-the-current-instance-of-an-object.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme](how-to-determine-what-type-an-object-variable-refers-to.md)
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](how-to-determine-whether-two-objects-are-identical.md)
- [Veri türleri](../data-types/index.md)
