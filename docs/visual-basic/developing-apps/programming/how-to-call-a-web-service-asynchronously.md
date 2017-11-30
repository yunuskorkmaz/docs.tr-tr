---
title: "Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6410ef93a706c047047aa24b3d47f8915e928015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="05098-102">Nasıl Yapılır: Web Hizmetini Zaman Uyumsuz Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05098-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="05098-103">Bir zaman uyumsuz yöntem çağrısının sonucunu alabilmeleri Bu örnek bir Web Service'in zaman uyumsuz işleyicisi olaya işleyici iliştirir.</span><span class="sxs-lookup"><span data-stu-id="05098-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="05098-104">Bu örnek http://www.xmethods.net DemoTemperatureService Web hizmeti kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05098-104">This example used the DemoTemperatureService Web service at http://www.xmethods.net.</span></span>  
  
 <span data-ttu-id="05098-105">Başvuru yaptığınızda bir Web hizmeti projenizde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE) eklenir `My.WebServices` nesne ve IDE oluşturur belirtilen bir Web hizmetine erişmek için bir istemci proxy sınıfı</span><span class="sxs-lookup"><span data-stu-id="05098-105">When you reference a Web service in your project in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="05098-106">Proxy sınıfı eşzamanlı olarak, Web hizmeti yöntemlerini çağırın sayesinde Burada, uygulamanızın işlevi için bekler.</span><span class="sxs-lookup"><span data-stu-id="05098-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="05098-107">Ayrıca, zaman uyumsuz yöntem çağırma yardımcı olmak için ek üyeleri proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05098-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="05098-108">Her Web hizmeti işlevi için *NameOfWebServiceFunction*, proxy oluşturur bir *NameOfWebServiceFunction* `Async` alt yordam, bir *NameOfWebServiceFunction* `Completed` olayı ve bir *NameOfWebServiceFunction* `CompletedEventArgs` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05098-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="05098-109">Örnek zaman uyumsuz üyeleri erişmek için nasıl kullanılacağını gösterir `getTemp` DemoTemperatureService Web hizmetinin işlevi.</span><span class="sxs-lookup"><span data-stu-id="05098-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05098-110">ASP.NET desteklemediğinden bu kodu Web uygulamalarında çalışmıyor `My.WebServices` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="05098-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="05098-111">Zaman uyumsuz olarak bir Web hizmetini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="05098-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="05098-112">Başvuru http://www.xmethods.net DemoTemperatureService Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="05098-112">Reference the DemoTemperatureService Web service at http://www.xmethods.net.</span></span> <span data-ttu-id="05098-113">Adresidir</span><span class="sxs-lookup"><span data-stu-id="05098-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="05098-114">Bir olay işleyicisi ekleme `getTempCompleted` olay:</span><span class="sxs-lookup"><span data-stu-id="05098-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="05098-115">Kullanamazsınız `Handles` olay işleyicisi ile ilişkilendirmek için deyimi `My.WebServices` nesnenin olaylar.</span><span class="sxs-lookup"><span data-stu-id="05098-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="05098-116">Olay işleyicisi için eklenmişse izlemek için bir alan ekleyebilmek `getTempCompleted` olay:</span><span class="sxs-lookup"><span data-stu-id="05098-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="05098-117">Olay işleyicisi eklemek için bir yöntem ekleyin `getTempCompleted` olay, gerekirse ve çağırmak için `getTempAsynch` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="05098-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
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
  
     <span data-ttu-id="05098-118">Çağrılacak `getTemp` yöntemi zaman uyumsuz olarak Web, çağrı `CallGetTempAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05098-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="05098-119">Web yöntemi sona erdiğinde, dönüş değeri için geçirilen `getTempCompletedHandler` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="05098-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05098-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05098-120">See Also</span></span>  
 [<span data-ttu-id="05098-121">Uygulama Web hizmetlerine erişme</span><span class="sxs-lookup"><span data-stu-id="05098-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [<span data-ttu-id="05098-122">My.WebServices nesnesi</span><span class="sxs-lookup"><span data-stu-id="05098-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
