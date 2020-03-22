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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="f1b30-102">Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b30-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="f1b30-103">Bu örnek, bir Web hizmetinin eşsenkronize işleyicisi olayına bir işleyici bağlar, böylece eşzamanlı yöntem çağrısının sonucunu alabilir.</span><span class="sxs-lookup"><span data-stu-id="f1b30-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="f1b30-104">Bu örnekte DemoTemperatureService Web `http://www.xmethods.net`hizmeti kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1b30-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="f1b30-105">Visual Studio Tümleşik Geliştirme Ortamı'ndaki (IDE) projenizde bir Web `My.WebServices` hizmetine başvururken, bu hizmet nesneye eklenir ve IDE belirli bir Web hizmetine erişmek için bir istemci proxy sınıfı oluşturur</span><span class="sxs-lookup"><span data-stu-id="f1b30-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="f1b30-106">Proxy sınıfı, uygulamanızın işlevin tamamlanmasını beklediği Web hizmeti yöntemlerini eşzamanlı olarak aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1b30-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="f1b30-107">Buna ek olarak, proxy yöntem eşit olarak aramanıza yardımcı olmak için ek üyeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1b30-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="f1b30-108">Her Web hizmeti işlevi için, *NameOfWebServiceFunction*, proxy bir *NameOfWebServiceFunction* `Async` alt yordamı, bir *NameOfWebServiceFunction* `Completed` olay ve bir *NameOfWebServiceFunction* `CompletedEventArgs` sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1b30-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="f1b30-109">Bu örnek, DemoTemperatureService Web hizmetinin işlevine `getTemp` erişmek için eşzamanlı üyelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1b30-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="f1b30-110">ASP.NET `My.WebServices` nesneyi desteklemediği için bu kod Web uygulamalarında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f1b30-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="f1b30-111">Bir Web hizmetini eşzamanlı olarak arama</span><span class="sxs-lookup"><span data-stu-id="f1b30-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="f1b30-112">DemoTemperatureService Web hizmetine `http://www.xmethods.net`başvurun.</span><span class="sxs-lookup"><span data-stu-id="f1b30-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="f1b30-113">Adres,</span><span class="sxs-lookup"><span data-stu-id="f1b30-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="f1b30-114">Olay için bir olay `getTempCompleted` işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f1b30-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="f1b30-115">Bir olay `Handles` işleyicisini nesnenin `My.WebServices` olaylarıyla ilişkilendirmek için deyimi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f1b30-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="f1b30-116">`getTempCompleted` Olay işleyicisi olaya eklendiğini izlemek için bir alan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f1b30-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="f1b30-117">Olay işleyicisini gerekirse `getTempCompleted` olaya eklemek ve `getTempAsync` yöntemi çağırmak için bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f1b30-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="f1b30-118">Web yöntemini `getTemp` eşzamanlı olarak çağırmak için `CallGetTempAsync` yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="f1b30-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="f1b30-119">Web yöntemi bittiğinde, iade değeri olay işleyicisine `getTempCompletedHandler` aktarılır.</span><span class="sxs-lookup"><span data-stu-id="f1b30-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1b30-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1b30-120">See also</span></span>

- [<span data-ttu-id="f1b30-121">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="f1b30-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="f1b30-122">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="f1b30-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
