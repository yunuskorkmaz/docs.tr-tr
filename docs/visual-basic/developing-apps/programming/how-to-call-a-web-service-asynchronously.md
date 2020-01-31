---
title: 'Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794558"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="2f1d7-102">Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f1d7-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="2f1d7-103">Bu örnek, bir işleyiciyi bir Web hizmetinin zaman uyumsuz işleyici olayına iliştirir, böylece zaman uyumsuz bir yöntem çağrısının sonucunu alabilir.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="2f1d7-104">Bu örnek `http://www.xmethods.net`adresindeki DemoTemperatureService Web hizmetini kullandı.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="2f1d7-105">Visual Studio tümleşik geliştirme ortamında (IDE) projenizdeki bir Web hizmetine başvurduğunuzda, `My.WebServices` nesnesine eklenir ve IDE belirtilen Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur</span><span class="sxs-lookup"><span data-stu-id="2f1d7-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="2f1d7-106">Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği zaman uyumlu Web hizmeti yöntemlerini aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="2f1d7-107">Ayrıca, proxy, yöntemi zaman uyumsuz olarak çağırmaya yardımcı olmak için ek Üyeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="2f1d7-108">Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy, bir *nameofwebservicefunction*`Async` altyordam, bir *NameOfWebServiceFunction*`Completed` event ve *NameOfWebServiceFunction*`CompletedEventArgs` sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="2f1d7-109">Bu örnek, DemoTemperatureService Web hizmetinin `getTemp` işlevine erişmek için zaman uyumsuz üyelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="2f1d7-110">Bu kod Web uygulamalarında çalışmaz, çünkü ASP.NET `My.WebServices` nesnesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="2f1d7-111">Bir Web hizmetini zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="2f1d7-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="2f1d7-112">`http://www.xmethods.net`adresindeki DemoTemperatureService Web hizmetine başvurun.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="2f1d7-113">Adres</span><span class="sxs-lookup"><span data-stu-id="2f1d7-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="2f1d7-114">`getTempCompleted` olayı için bir olay işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f1d7-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="2f1d7-115">Bir olay işleyicisini `My.WebServices` nesnesinin olaylarıyla ilişkilendirmek için `Handles` ifadesini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="2f1d7-116">Olay işleyicisinin `getTempCompleted` olayına eklendiğini izlemek için bir alan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f1d7-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="2f1d7-117">Gerekirse `getTempCompleted` olayına olay işleyicisini eklemek ve `getTempAsync` yöntemini çağırmak için bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2f1d7-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="2f1d7-118">`getTemp` Web yöntemini zaman uyumsuz olarak çağırmak için `CallGetTempAsync` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="2f1d7-119">Web yöntemi bittiğinde, dönüş değeri `getTempCompletedHandler` olay işleyicisine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f1d7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f1d7-120">See also</span></span>

- [<span data-ttu-id="2f1d7-121">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="2f1d7-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="2f1d7-122">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="2f1d7-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
