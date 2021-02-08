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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="17d0f-103">Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17d0f-103">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="17d0f-104">Bu örnek, bir işleyiciyi bir Web hizmetinin zaman uyumsuz işleyici olayına iliştirir, böylece zaman uyumsuz bir yöntem çağrısının sonucunu alabilir.</span><span class="sxs-lookup"><span data-stu-id="17d0f-104">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="17d0f-105">Bu örnek, adresinde DemoTemperatureService Web hizmetini kullandı `http://www.xmethods.net` .</span><span class="sxs-lookup"><span data-stu-id="17d0f-105">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="17d0f-106">Visual Studio tümleşik geliştirme ortamında (IDE) projenizdeki bir Web hizmetine başvurduğunuzda, `My.WebServices` nesnesine eklenir ve IDE belirtilen Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur</span><span class="sxs-lookup"><span data-stu-id="17d0f-106">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="17d0f-107">Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği zaman uyumlu Web hizmeti yöntemlerini aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d0f-107">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="17d0f-108">Ayrıca, proxy, yöntemi zaman uyumsuz olarak çağırmaya yardımcı olmak için ek Üyeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17d0f-108">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="17d0f-109">Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy bir *NameOfWebServiceFunction* alt `Async` yordamı, *NameOfWebServiceFunction* `Completed` olayı ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17d0f-109">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="17d0f-110">Bu örnek, `getTemp` DemoTemperatureService Web hizmetinin işlevine erişmek için zaman uyumsuz üyelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d0f-110">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="17d0f-111">ASP.NET nesneyi desteklemediğinden, bu kod Web uygulamalarında çalışmaz `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="17d0f-111">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="17d0f-112">Bir Web hizmetini zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="17d0f-112">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="17d0f-113">Adresindeki DemoTemperatureService Web hizmetine başvurun `http://www.xmethods.net` .</span><span class="sxs-lookup"><span data-stu-id="17d0f-113">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="17d0f-114">Adres</span><span class="sxs-lookup"><span data-stu-id="17d0f-114">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="17d0f-115">Olay için bir olay işleyicisi ekleyin `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="17d0f-115">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="17d0f-116">`Handles`Bir olay işleyicisini nesnenin olaylarıyla ilişkilendirmek için ifadesini kullanamazsınız `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="17d0f-116">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="17d0f-117">Olay işleyicisinin olaya eklendiğini izlemek için bir alan ekleyin `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="17d0f-117">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="17d0f-118">Gerekirse olaya olay işleyicisini eklemek ve yöntemi çağırmak için bir yöntem ekleyin `getTempCompleted` `getTempAsync` :</span><span class="sxs-lookup"><span data-stu-id="17d0f-118">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="17d0f-119">`getTemp`Web yöntemini zaman uyumsuz olarak çağırmak için yöntemini çağırın `CallGetTempAsync` .</span><span class="sxs-lookup"><span data-stu-id="17d0f-119">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="17d0f-120">Web yöntemi bittiğinde, dönüş değeri `getTempCompletedHandler` olay işleyicisine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="17d0f-120">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="17d0f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17d0f-121">See also</span></span>

- [<span data-ttu-id="17d0f-122">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="17d0f-122">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="17d0f-123">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="17d0f-123">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
