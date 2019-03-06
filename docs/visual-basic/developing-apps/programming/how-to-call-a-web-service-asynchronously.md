---
title: 'Nasıl yapılır: Bir Web hizmetini zaman uyumsuz çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376214"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="1f8db-102">Nasıl yapılır: Bir Web hizmetini zaman uyumsuz çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f8db-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="1f8db-103">Bu örnek, zaman uyumsuz yöntem çağrısı sonucu alabilmeleri Web hizmetinin zaman uyumsuz işleyicisi olaya bir işleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="1f8db-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="1f8db-104">Bu örnekte kullanılan DemoTemperatureService Web hizmeti `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="1f8db-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="1f8db-105">Bir Web hizmeti projenizde, Visual Studio tümleşik geliştirme ortamı (IDE) başvuruda bulunduğunuzda eklendiği `My.WebServices` nesne ve IDE, belirtilen bir Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur</span><span class="sxs-lookup"><span data-stu-id="1f8db-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="1f8db-106">Proxy sınıfı zaman uyumlu olarak, Web hizmeti yöntemlerini çağırmanızı sağlar. Burada, uygulamanızın işlevi için bekler.</span><span class="sxs-lookup"><span data-stu-id="1f8db-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="1f8db-107">Ayrıca, zaman uyumsuz yöntem çağırma yardımcı olmak için ek üyeler proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f8db-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="1f8db-108">Her Web hizmeti işlev için *NameOfWebServiceFunction*, proxy oluşturur bir *NameOfWebServiceFunction* `Async` alt yordam, bir *NameOfWebServiceFunction* `Completed` olay ve *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f8db-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="1f8db-109">Bu örnek, zaman uyumsuz üyeler erişmek için nasıl kullanılacağını gösterir `getTemp` işlevi DemoTemperatureService Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="1f8db-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="1f8db-110">ASP.NET desteklemediğinden Web uygulamalarında, bu kod işe yaramazsa `My.WebServices` nesne.</span><span class="sxs-lookup"><span data-stu-id="1f8db-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="1f8db-111">Zaman uyumsuz olarak bir Web hizmetini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="1f8db-111">To call a Web service asynchronously</span></span>

1. <span data-ttu-id="1f8db-112">DemoTemperatureService Web hizmeti başvurusu `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="1f8db-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="1f8db-113">Adres</span><span class="sxs-lookup"><span data-stu-id="1f8db-113">The address is</span></span>

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="1f8db-114">İçin bir olay işleyicisi ekleme `getTempCompleted` olay:</span><span class="sxs-lookup"><span data-stu-id="1f8db-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="1f8db-115">Kullanamazsınız `Handles` deyimi bir olay işleyicisi ile ilişkilendirilecek `My.WebServices` nesnenin olayları.</span><span class="sxs-lookup"><span data-stu-id="1f8db-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="1f8db-116">Olay işleyicisi için eklenmişse izlemek için alan ekleme `getTempCompleted` olay:</span><span class="sxs-lookup"><span data-stu-id="1f8db-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="1f8db-117">Olay işleyicisi eklemek için bir yöntem ekleyin `getTempCompleted` gerekirse, olay ve çağrılacak `getTempAsync` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1f8db-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="1f8db-118">Çağrılacak `getTemp` yöntemi zaman uyumsuz olarak Web, çağrı `CallGetTempAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f8db-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="1f8db-119">Web yöntemi sona erdiğinde, dönüş değerinin geçirilen `getTempCompletedHandler` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1f8db-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f8db-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f8db-120">See also</span></span>

- [<span data-ttu-id="1f8db-121">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="1f8db-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [<span data-ttu-id="1f8db-122">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="1f8db-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
