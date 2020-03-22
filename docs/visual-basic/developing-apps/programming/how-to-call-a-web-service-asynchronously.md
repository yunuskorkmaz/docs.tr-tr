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

Bu örnek, bir Web hizmetinin eşsenkronize işleyicisi olayına bir işleyici bağlar, böylece eşzamanlı yöntem çağrısının sonucunu alabilir. Bu örnekte DemoTemperatureService Web `http://www.xmethods.net`hizmeti kullanılır.

Visual Studio Tümleşik Geliştirme Ortamı'ndaki (IDE) projenizde bir Web `My.WebServices` hizmetine başvururken, bu hizmet nesneye eklenir ve IDE belirli bir Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur

Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği Web hizmeti yöntemlerini eşzamanlı olarak aramanızı sağlar. Buna ek olarak, proxy yöntem eşit olarak aramanıza yardımcı olmak için ek üyeler oluşturur. Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy bir *NameOfWebServiceFunction* `Async` alt yordamı, bir *NameOfWebServiceFunction* `Completed` olay ve bir *NameOfWebServiceFunction* `CompletedEventArgs` sınıf oluşturur. Bu örnek, DemoTemperatureService Web hizmetinin işlevine `getTemp` erişmek için eşzamanlı üyelerin nasıl kullanılacağını gösterir.

> [!NOTE]
> ASP.NET `My.WebServices` nesneyi desteklemediği için bu kod Web uygulamalarında çalışmaz.

## <a name="call-a-web-service-asynchronously"></a>Bir Web hizmetini eşzamanlı olarak arama

1. DemoTemperatureService Web hizmetine `http://www.xmethods.net`başvurun. Adres,

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Olay için bir olay `getTempCompleted` işleyicisi ekleyin:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Bir olay `Handles` işleyicisini nesnenin `My.WebServices` olaylarıyla ilişkilendirmek için deyimi kullanamazsınız.

3. `getTempCompleted` Olay işleyicisi olaya eklendiğini izlemek için bir alan ekleyin:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Olay işleyicisini gerekirse `getTempCompleted` olaya eklemek ve `getTempAsync` yöntemi çağırmak için bir yöntem ekleyin:

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

    Web yöntemini `getTemp` eşzamanlı olarak çağırmak için `CallGetTempAsync` yöntemi arayın. Web yöntemi bittiğinde, iade değeri olay işleyicisine `getTempCompletedHandler` aktarılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Web Hizmetlerine Erişme](accessing-application-web-services.md)
- [My.WebServices Nesnesi](../../language-reference/objects/my-webservices-object.md)
