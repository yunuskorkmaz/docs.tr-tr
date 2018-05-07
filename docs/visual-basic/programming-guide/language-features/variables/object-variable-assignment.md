---
title: Nesne Değişkeni Ataması (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-assignment-visual-basic"></a>Nesne Değişkeni Ataması (Visual Basic)
Bir nesne bir nesne değişkenine atamak için normal atama deyimini kullanın. Bir nesne ifadesi atayabilir veya [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) anahtar sözcüğü, aşağıdaki örnek olarak gösterilmiştir.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` şu anda değişkenine atanan nesnesi yok anlamına gelir.  
  
## <a name="initialization"></a>Başlatma  
 Kodunuzu başladığı çalıştıran, değişkenleri için başlatılır nesnenizin `Nothing`. Bu, bildirimleri başlatma dahil bildirim deyimleri çalıştırıldığında belirttiğiniz değerleri yeniden başlatılır.  
  
 Başlatma kullanarak, bildiriminde dahil edebilirsiniz [yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü. Aşağıdaki bildirim deyimleri nesne değişkenlerini bildirme `testUri` ve `ver` ve belirli nesneleri atayabilirsiniz. Her uygun sınıfının aşırı yüklenmiş oluşturuculardan birine nesneyi başlatmak için kullanır.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Disassociation  
 Bir nesne değişkeni ayarını `Nothing` herhangi belirli bir nesne değişkeni ilişkilendirmesini sona erdirir. Bu, yanlışlıkla nesne değişkeni değiştirerek değiştirmesini engeller. Ayrıca, nesne değişkeni aşağıdaki örnekte gösterildiği gibi geçerli bir nesneye işaret olup olmadığını sınamak sağlar.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Değişkeniniz başvurduğu nesne başka bir uygulamada ise, bu test, uygulamanın veya sonlandırıldı yalnızca nesne geçersiz kılınan belirlenemiyor.  
  
 Bir nesne değişkeninin değerini `Nothing` olarak da adlandırılan bir *null başvuru*.  
  
## <a name="current-instance"></a>Geçerli örnek  
 *Geçerli örnek* hangi kod şu anda yürütülmekte olan bir nesnedir. Yordam içinde tüm kodu yürütür olduğundan, geçerli, yordamın çağrıldığı bir örneğidir.  
  
 `Me` Anahtar sözcük, geçerli örneğine başvurma bir nesne değişkeni görür. Bir yordam değilse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), kullanabileceği `Me` geçerli örneğini gösteren bir işaretçi almak için anahtar sözcüğü. Paylaşılan yordamları belirli bir sınıf örneği ile ilişkilendirilemez.  
  
 Kullanarak `Me` geçerli örneğini başka bir modül yordamda geçirilmesi özellikle yararlıdır. Örneğin, XML belgelerinin sahiptir ve bunların tümüne bazı standart metin eklemek istediğiniz varsayalım. Aşağıdaki örnek, bunu yapmak için bir yordam tanımlar.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Her XML belge nesnesi, yordam çağrısı ve geçerli örnek bağımsız değişken olarak geçirin. Aşağıdaki örnekte bu gösterir.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Nasıl yapılır: bir nesne değişkeni bildirme ve Visual Basic'te bir nesneyi atayın](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
