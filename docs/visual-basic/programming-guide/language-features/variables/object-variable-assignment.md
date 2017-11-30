---
title: "Nesne Değişkeni Ataması (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 `Nothing`şu anda değişkenine atanan nesnesi yok anlamına gelir.  
  
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
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nesne değişkeni değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Nasıl yapılır: bir nesne değişkeni bildirme ve Visual Basic'te bir nesneyi atayın](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Nasıl yapılır: bir nesne değişkeni olun herhangi bir örneğine Başvurmamasını sağlama](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
