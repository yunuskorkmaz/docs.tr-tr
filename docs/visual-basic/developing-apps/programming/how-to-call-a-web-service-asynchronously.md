---
title: 'Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76794558"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)

Bu örnek, bir işleyiciyi bir Web hizmetinin zaman uyumsuz işleyici olayına iliştirir, böylece zaman uyumsuz bir yöntem çağrısının sonucunu alabilir. Bu örnek, adresinde `http://www.xmethods.net`DemoTemperatureService Web hizmetini kullandı.

Visual Studio tümleşik geliştirme ortamında (IDE) projenizdeki bir Web hizmetine başvurduğunuzda, `My.WebServices` nesnesine EKLENIR ve IDE belirtilen Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur

Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği zaman uyumlu Web hizmeti yöntemlerini aramanızı sağlar. Ayrıca, proxy, yöntemi zaman uyumsuz olarak çağırmaya yardımcı olmak için ek Üyeler oluşturur. Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy bir *NameOfWebServiceFunction* `Async` alt yordamı, *NameOfWebServiceFunction* `Completed` olayı ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı oluşturur. Bu örnek, DemoTemperatureService Web hizmetinin `getTemp` işlevine erişmek için zaman uyumsuz üyelerin nasıl kullanılacağını gösterir.

> [!NOTE]
> ASP.NET `My.WebServices` nesneyi desteklemediğinden, bu kod Web uygulamalarında çalışmaz.

## <a name="call-a-web-service-asynchronously"></a>Bir Web hizmetini zaman uyumsuz olarak çağırma

1. Adresindeki `http://www.xmethods.net`DemoTemperatureService Web hizmetine başvurun. Adres

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. `getTempCompleted` Olay için bir olay işleyicisi ekleyin:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Bir olay işleyicisini `My.WebServices` nesnenin `Handles` olaylarıyla ilişkilendirmek için ifadesini kullanamazsınız.

3. Olay işleyicisinin `getTempCompleted` olaya eklendiğini izlemek için bir alan ekleyin:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Gerekirse olaya olay işleyicisini `getTempCompleted` eklemek ve `getTempAsync` yöntemi çağırmak için bir yöntem ekleyin:

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

- [Uygulama Web Hizmetlerine Erişme](accessing-application-web-services.md)
- [My.WebServices Nesnesi](../../language-reference/objects/my-webservices-object.md)
