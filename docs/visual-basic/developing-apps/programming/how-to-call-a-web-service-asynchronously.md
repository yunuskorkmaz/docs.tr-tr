---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Web hizmetini zaman uyumsuz olarak çağırma (Visual Basic)'
title: 'Nasıl yapılır: Web Hizmetini Zaman Uyumsuz Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: a702177f60ac598f624676072116bd3ce78da0bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775259"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)

Bu örnek, bir işleyiciyi bir Web hizmetinin zaman uyumsuz işleyici olayına iliştirir, böylece zaman uyumsuz bir yöntem çağrısının sonucunu alabilir. Bu örnek, adresinde DemoTemperatureService Web hizmetini kullandı `http://www.xmethods.net` .

Visual Studio tümleşik geliştirme ortamında (IDE) projenizdeki bir Web hizmetine başvurduğunuzda, `My.WebServices` nesnesine eklenir ve IDE belirtilen Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur

Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği zaman uyumlu Web hizmeti yöntemlerini aramanızı sağlar. Ayrıca, proxy, yöntemi zaman uyumsuz olarak çağırmaya yardımcı olmak için ek Üyeler oluşturur. Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy bir *NameOfWebServiceFunction* alt `Async` yordamı, *NameOfWebServiceFunction* `Completed` olayı ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı oluşturur. Bu örnek, `getTemp` DemoTemperatureService Web hizmetinin işlevine erişmek için zaman uyumsuz üyelerin nasıl kullanılacağını gösterir.

> [!NOTE]
> ASP.NET nesneyi desteklemediğinden, bu kod Web uygulamalarında çalışmaz `My.WebServices` .

## <a name="call-a-web-service-asynchronously"></a>Bir Web hizmetini zaman uyumsuz olarak çağırma

1. Adresindeki DemoTemperatureService Web hizmetine başvurun `http://www.xmethods.net` . Adres

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Olay için bir olay işleyicisi ekleyin `getTempCompleted` :

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > `Handles`Bir olay işleyicisini nesnenin olaylarıyla ilişkilendirmek için ifadesini kullanamazsınız `My.WebServices` .

3. Olay işleyicisinin olaya eklendiğini izlemek için bir alan ekleyin `getTempCompleted` :

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Gerekirse olaya olay işleyicisini eklemek ve yöntemi çağırmak için bir yöntem ekleyin `getTempCompleted` `getTempAsync` :

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

    `getTemp`Web yöntemini zaman uyumsuz olarak çağırmak için yöntemini çağırın `CallGetTempAsync` . Web yöntemi bittiğinde, dönüş değeri `getTempCompletedHandler` olay işleyicisine geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Web Hizmetlerine Erişme](accessing-application-web-services.md)
- [My.WebServices Nesnesi](../../language-reference/objects/my-webservices-object.md)
