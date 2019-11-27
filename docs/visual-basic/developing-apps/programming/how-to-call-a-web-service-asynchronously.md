---
title: 'Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 0eeb358ba38836ba6302f98f9e3e0314b83510f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352130"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)

Bu örnek, bir işleyiciyi bir Web hizmetinin zaman uyumsuz işleyici olayına iliştirir, böylece zaman uyumsuz bir yöntem çağrısının sonucunu alabilir. Bu örnek `http://www.xmethods.net`adresindeki DemoTemperatureService Web hizmetini kullandı.

Visual Studio tümleşik geliştirme ortamında (IDE) projenizdeki bir Web hizmetine başvurduğunuzda, `My.WebServices` nesnesine eklenir ve IDE belirtilen Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur

Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği zaman uyumlu Web hizmeti yöntemlerini aramanızı sağlar. Ayrıca, proxy, yöntemi zaman uyumsuz olarak çağırmaya yardımcı olmak için ek Üyeler oluşturur. Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy, bir *nameofwebservicefunction*`Async` altyordam, bir *NameOfWebServiceFunction*`Completed` event ve *NameOfWebServiceFunction*`CompletedEventArgs` sınıfı oluşturur. Bu örnek, DemoTemperatureService Web hizmetinin `getTemp` işlevine erişmek için zaman uyumsuz üyelerin nasıl kullanılacağını gösterir.

> [!NOTE]
> Bu kod Web uygulamalarında çalışmaz, çünkü ASP.NET `My.WebServices` nesnesini desteklemez.

### <a name="to-call-a-web-service-asynchronously"></a>Bir Web hizmetini zaman uyumsuz olarak çağırmak için

1. `http://www.xmethods.net`adresindeki DemoTemperatureService Web hizmetine başvurun. Adres

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. `getTempCompleted` olayı için bir olay işleyicisi ekleyin:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Bir olay işleyicisini `My.WebServices` nesnesinin olaylarıyla ilişkilendirmek için `Handles` ifadesini kullanamazsınız.

3. Olay işleyicisinin `getTempCompleted` olayına eklendiğini izlemek için bir alan ekleyin:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Gerekirse `getTempCompleted` olayına olay işleyicisini eklemek ve `getTempAsync` yöntemini çağırmak için bir yöntem ekleyin:

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

    `getTemp` Web yöntemini zaman uyumsuz olarak çağırmak için `CallGetTempAsync` yöntemini çağırın. Web yöntemi bittiğinde, dönüş değeri `getTempCompletedHandler` olay işleyicisine geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
