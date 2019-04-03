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
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840282"
---
# <a name="object-variable-assignment-visual-basic"></a>Nesne Değişkeni Ataması (Visual Basic)
Bir nesne bir nesne değişkenine atamak için bir normal atama ifadesi kullanın. Bir nesne ifadesi atayabilirsiniz veya [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) anahtar sözcüğü, aşağıdaki örnek gösterir.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` şu anda değişkenine atanan nesnesi yok anlamına gelir.  
  
## <a name="initialization"></a>Başlatma  
 Kodunuzu çalıştırmak, nesnenizin değişkenleri başlatıldığı başladığı `Nothing`. Bu başlatma, bildirimleri içeren bildirim deyimleri yürütüldüğünde, belirttiğiniz değerleri yeniden başlatılır.  
  
 Başlatma kullanarak, bildiriminde dahil edebilirsiniz [yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü. Aşağıdaki bildirim deyimleri nesne değişkenlerini bildirme `testUri` ve `ver` ve belirli nesneleri atayabilirsiniz. Her bir uygun sınıf aşırı yüklü oluşturucular nesneyi başlatmak için kullanır.  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>İlişkisi kaldırma  
 Bir nesne değişkeninin ayarını `Nothing` herhangi belirli bir nesne değişkeninin ilişkilendirmesini sona erdirir. Bu, yanlışlıkla nesne değişkeni değiştirerek değiştirmesini engeller. Ayrıca, nesne değişkenini aşağıdaki örnekte gösterildiği gibi geçerli bir nesneye işaret olup olmadığını sınamak sağlar.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Değişkenin başvurduğu nesneyi başka bir uygulamada ise, bu test, uygulamanın sahip sonlandırıldı veya yalnızca nesne geçersiz kılınan belirlenemiyor.  
  
 Bir nesne değişkeninin değerini `Nothing` olarak da adlandırılan bir *null başvuru*.  
  
## <a name="current-instance"></a>Geçerli örnek  
 *Geçerli örneğin* nesnenin hangi kod şu anda Yürütülüyor sertifikadır. Tüm kod yürüten bir yordam içinde olduğundan, geçerli Örneğin, yordamı çağrıldı olur.  
  
 `Me` Anahtar sözcüğü bir nesne değişkeninin geçerli örneğine başvurma olarak görev yapar. Bir yordam değilse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), bunu `Me` geçerli örneğine bir işaretçi alma için anahtar sözcüğü. Paylaşılan yordamlar, bir sınıfın belirli bir örneği ile ilişkilendirilemez.  
  
 Kullanarak `Me` geçerli örneğin başka bir modül bir yordamda geçirmek özellikle yararlıdır. Örneğin, XML belgelerinin sahiptir ve bunların tümüne bazı standart metin eklemek istediğiniz varsayalım. Aşağıdaki örnek bunu yapma yordamı tanımlar.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Her XML belge nesnesi, bir yordamı çağırma ve kendi geçerli örneğini bağımsız değişken geçirin. Aşağıdaki örnekte bu gösterir.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Nasıl yapılır: Bir nesnenin değişken sağlamak için herhangi bir örneğine Başvurmamasını](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
