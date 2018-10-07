---
title: 'Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: bf109780f26ce2fa4d5dbaa63832e765970b5cb4
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842703"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)
Bu örnek, zaman uyumsuz yöntem çağrısı sonucu alabilmeleri Web hizmetinin zaman uyumsuz işleyicisi olaya bir işleyici ekler. Bu örnekte kullanılan DemoTemperatureService Web hizmeti `http://www.xmethods.net`.  
  
 Bir Web hizmeti projenizde, Visual Studio tümleşik geliştirme ortamı (IDE) başvuruda bulunduğunuzda eklendiği `My.WebServices` nesne ve IDE, belirtilen bir Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur  
  
 Proxy sınıfı zaman uyumlu olarak, Web hizmeti yöntemlerini çağırmanızı sağlar. Burada, uygulamanızın işlevi için bekler. Ayrıca, zaman uyumsuz yöntem çağırma yardımcı olmak için ek üyeler proxy oluşturur. Her Web hizmeti işlev için *NameOfWebServiceFunction*, proxy oluşturur bir *NameOfWebServiceFunction* `Async` alt yordam, bir *NameOfWebServiceFunction* `Completed` olay ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı. Bu örnek, zaman uyumsuz üyeler erişmek için nasıl kullanılacağını gösterir `getTemp` işlevi DemoTemperatureService Web hizmeti.  
  
> [!NOTE]
>  ASP.NET desteklemediğinden Web uygulamalarında, bu kod işe yaramazsa `My.WebServices` nesne.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Zaman uyumsuz olarak bir Web hizmetini çağırmak için  
  
1.  DemoTemperatureService Web hizmeti başvurusu `http://www.xmethods.net`. Adres  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  İçin bir olay işleyicisi ekleme `getTempCompleted` olay:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Kullanamazsınız `Handles` deyimi bir olay işleyicisi ile ilişkilendirilecek `My.WebServices` nesnenin olayları.  
  
3.  Olay işleyicisi için eklenmişse izlemek için alan ekleme `getTempCompleted` olay:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Olay işleyicisi eklemek için bir yöntem ekleyin `getTempCompleted` gerekirse, olay ve çağrılacak `getTempAsynch` yöntemi:  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     Çağrılacak `getTemp` yöntemi zaman uyumsuz olarak Web, çağrı `CallGetTempAsync` yöntemi. Web yöntemi sona erdiğinde, dönüş değerinin geçirilen `getTempCompletedHandler` olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
