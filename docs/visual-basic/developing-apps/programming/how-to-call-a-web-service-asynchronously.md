---
title: 'Nasıl yapılır: Bir Web hizmetini zaman uyumsuz çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943825"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl yapılır: Bir Web hizmetini zaman uyumsuz çağırma (Visual Basic)

Bu örnek, zaman uyumsuz yöntem çağrısı sonucu alabilmeleri Web hizmetinin zaman uyumsuz işleyicisi olaya bir işleyici ekler. Bu örnekte kullanılan DemoTemperatureService Web hizmeti `http://www.xmethods.net`.

Bir Web hizmeti projenizde, Visual Studio tümleşik geliştirme ortamı (IDE) başvuruda bulunduğunuzda eklendiği `My.WebServices` nesne ve IDE, belirtilen bir Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur

Proxy sınıfı zaman uyumlu olarak, Web hizmeti yöntemlerini çağırmanızı sağlar. Burada, uygulamanızın işlevi için bekler. Ayrıca, zaman uyumsuz yöntem çağırma yardımcı olmak için ek üyeler proxy oluşturur. Her Web hizmeti işlev için *NameOfWebServiceFunction*, proxy oluşturur bir *NameOfWebServiceFunction* `Async` alt yordam, bir *NameOfWebServiceFunction* `Completed` olay ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı. Bu örnek, zaman uyumsuz üyeler erişmek için nasıl kullanılacağını gösterir `getTemp` işlevi DemoTemperatureService Web hizmeti.

> [!NOTE]
> ASP.NET desteklemediğinden Web uygulamalarında, bu kod işe yaramazsa `My.WebServices` nesne.

### <a name="to-call-a-web-service-asynchronously"></a>Zaman uyumsuz olarak bir Web hizmetini çağırmak için

1. DemoTemperatureService Web hizmeti başvurusu `http://www.xmethods.net`. Adres

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. İçin bir olay işleyicisi ekleme `getTempCompleted` olay:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Kullanamazsınız `Handles` deyimi bir olay işleyicisi ile ilişkilendirilecek `My.WebServices` nesnenin olayları.

3. Olay işleyicisi için eklenmişse izlemek için alan ekleme `getTempCompleted` olay:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Olay işleyicisi eklemek için bir yöntem ekleyin `getTempCompleted` gerekirse, olay ve çağrılacak `getTempAsync` yöntemi:

    ```vb
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

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
