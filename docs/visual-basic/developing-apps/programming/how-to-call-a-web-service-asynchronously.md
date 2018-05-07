---
title: 'Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 8968eaa8edd8dee177906a6c801f2f46c2a740d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)
Bir zaman uyumsuz yöntem çağrısının sonucunu alabilmeleri Bu örnek bir Web Service'in zaman uyumsuz işleyicisi olaya işleyici iliştirir. Bu örnek DemoTemperatureService Web hizmeti kullanılan http://www.xmethods.net.  
  
 Projenizdeki, Visual Studio tümleşik geliştirme ortamı (IDE) bir Web hizmeti başvurduğunuzda eklendiğinden `My.WebServices` nesne ve IDE oluşturur belirtilen bir Web hizmetine erişmek için bir istemci proxy sınıfı  
  
 Proxy sınıfı eşzamanlı olarak, Web hizmeti yöntemlerini çağırın sayesinde Burada, uygulamanızın işlevi için bekler. Ayrıca, zaman uyumsuz yöntem çağırma yardımcı olmak için ek üyeleri proxy oluşturur. Her Web hizmeti işlevi için *NameOfWebServiceFunction*, proxy oluşturur bir *NameOfWebServiceFunction* `Async` alt yordam, bir *NameOfWebServiceFunction* `Completed` olayı ve bir *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı. Örnek zaman uyumsuz üyeleri erişmek için nasıl kullanılacağını gösterir `getTemp` DemoTemperatureService Web hizmetinin işlevi.  
  
> [!NOTE]
>  ASP.NET desteklemediğinden bu kodu Web uygulamalarında çalışmıyor `My.WebServices` nesnesi.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Zaman uyumsuz olarak bir Web hizmetini çağırmak için  
  
1.  DemoTemperatureService Web hizmeti başvuru http://www.xmethods.net. Adresidir  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Bir olay işleyicisi ekleme `getTempCompleted` olay:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Kullanamazsınız `Handles` olay işleyicisi ile ilişkilendirmek için deyimi `My.WebServices` nesnenin olaylar.  
  
3.  Olay işleyicisi için eklenmişse izlemek için bir alan ekleyebilmek `getTempCompleted` olay:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Olay işleyicisi eklemek için bir yöntem ekleyin `getTempCompleted` olay, gerekirse ve çağırmak için `getTempAsynch` yöntemi:  
  
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
  
     Çağrılacak `getTemp` yöntemi zaman uyumsuz olarak Web, çağrı `CallGetTempAsync` yöntemi. Web yöntemi sona erdiğinde, dönüş değeri için geçirilen `getTempCompletedHandler` olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
