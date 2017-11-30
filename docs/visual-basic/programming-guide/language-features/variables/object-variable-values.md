---
title: "Nesne Değişkeni Değerleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccab22920923500a2332db2372e52813c890e5e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-values-visual-basic"></a>Nesne Değişkeni Değerleri (Visual Basic)
Bir değişken [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) herhangi bir türde veri başvurabilir. Deposunda değeri bir `Object` değişkeni tutulur başka bir yerde bellekte değişkenin kendisine bir işaretçi verileri tutar ancak.  
  
## <a name="object-classifier-functions"></a>Nesne sınıflandırıcı işlevleri  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ne hakkında bilgi döndürmek işlevleri sağlayan bir `Object` değişken için aşağıdaki tabloda gösterildiği gibi anlamına gelir.  
  
|İşlev|Nesne değişkeni başvurduğu varsa True değerini döndürür|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Tek bir değer yerine değerleri dizisi|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [tarih veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) değer veya tarih ve saat değeri olarak yorumlanan dize|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Türünde bir nesne <xref:System.DBNull>, eksik veya var olmayan verileri temsil eder|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Türetilen bir özel durum nesnesi<xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Hiçbir şey](../../../../visual-basic/language-reference/nothing.md), hiçbir nesne değişkenine şu anda başka bir deyişle, atanan|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Bir sayı veya bir sayı olarak yorumlanan dize|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Bir başvuru türü (örneğin, bir dize dizisi, temsilci veya sınıf türü)|  
  
 Bu işlev bir işlem veya bir yordam için geçersiz bir değer gönderme önlemek için kullanabilirsiniz.  
  
## <a name="typeof-operator"></a>TypeOf İşleci  
 Aynı zamanda [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) bir nesne değişkeni şu anda bir özel veri türüne başvuruyor olup olmadığını belirlemek için. `TypeOf`... `Is` ifadeyi hesaplar için `True` işleneni çalışma zamanı türü türetildiği veya belirtilen türe uygular.  
  
 Aşağıdaki örnek kullanır `TypeOf` değer ve başvuru türlerine başvuran nesne değişkenleri.  
  
```  
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
  
 Önceki örnekte aşağıdaki satırları Yazar **hata ayıklama** penceresi:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 Nesne değişkeni `num` veri türü için başvuruyor `Integer`, ve `frm` sınıfının bir nesneye başvuruyor <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Nesne dizileri  
 Bildirme ve bir dizi kullanma `Object` değişkenleri. Çeşitli veri türleri ve nesne sınıflarını işlemek gerektiğinde kullanışlıdır. Bir dizinin tüm öğeleri aynı bildirilen veri türü olmalıdır. Bu veri türü olarak bildirme `Object` nesneleri depolamak ve diğer veri türleri dizideki yanında örnekleri sınıf sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nesne değişkeni ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nasıl yapılır: bir nesnenin geçerli örneğine başvurma](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Nasıl yapılır: bir nesne değişkeninin için hangi türe başvurduğunu belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Nasıl yapılır: iki nesnenin ilgili olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Nasıl yapılır: iki nesnenin aynı olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
