---
title: Using Deyimi Sorunlarını Önleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="669ae-102">Using Deyimi Sorunlarını Önleme</span><span class="sxs-lookup"><span data-stu-id="669ae-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="669ae-103">Bu örnek nasıl, C# "türü belirlenmiş istemci kullanırken kaynakları otomatik olarak temizlemek için using deyimi" kullanmamanız gösterir.</span><span class="sxs-lookup"><span data-stu-id="669ae-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="669ae-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="669ae-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="669ae-105">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="669ae-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="669ae-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="669ae-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="669ae-107">Bu örnek iki C# "deyimi yazılan istemcileri gibi özel durumlar sonra doğru bir şekilde temizler kodu kullanarak" kullanırken oluşan genel sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="669ae-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="669ae-108">C# "deyimi kullanarak" sonuçları çağrıda `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="669ae-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="669ae-109">Bu aynı sonucu verir `Close`bir ağ hatası oluştuğunda, özel durumlar oluşturma ().</span><span class="sxs-lookup"><span data-stu-id="669ae-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="669ae-110">Çünkü çağrısı `Dispose`() olur dolaylı olarak "kullanarak" blok kapanış ayracı, bu özel durumlar olasılıkla Git bilgisi dışında her ikisi için de kod yazma ve kodu okuyan kişilerin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="669ae-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="669ae-111">Bu uygulama hatalarının olası bir kaynağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="669ae-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="669ae-112">Gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` yöntemidir kapanış ayracı değil yürüttükten sonra kapanış ayracı bir özel durum ve kod oluşturur:</span><span class="sxs-lookup"><span data-stu-id="669ae-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="669ae-113">Nothing using içinde engelleme olsa bile bir özel durum ya da kullanarak içindeki tüm özel durumları blok yakalandı, `Console.Writeline` nedeniyle gerçekleşebilir değil örtük `Dispose`kapanış ayracı () çağrısı bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="669ae-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="669ae-114">Gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` yöntemidir, bir özel durum atma kapanış ayracı, başka bir uygulanır:</span><span class="sxs-lookup"><span data-stu-id="669ae-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="669ae-115">Çünkü `Dispose`() oluşur bir "son" bloğunun içine, `ApplicationException` kullanarak dışında hiçbir zaman görülür bloke `Dispose`() başarısız.</span><span class="sxs-lookup"><span data-stu-id="669ae-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="669ae-116">Kod dışında ne zaman hakkında bilmeniz gerekir, `ApplicationException` oluşur, bu özel durumun maskeleyerek "kullanarak" yapı sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="669ae-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="669ae-117">Son olarak, örnek doğru olduğunda özel durumlar ortaya yukarı temizlemeyi gösteren `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="669ae-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="669ae-118">Bu rapor hataları ve arama için bir try/catch bloğu kullanır `Abort`.</span><span class="sxs-lookup"><span data-stu-id="669ae-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="669ae-119">Bkz: [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) istemci aramalardan özel durumları yakalama hakkında daha fazla ayrıntı için örnek.</span><span class="sxs-lookup"><span data-stu-id="669ae-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="669ae-120">Deyimi ve ServiceHost kullanarak: birçok kendi kendine barındırma uygulama biraz birden fazla hizmet barındırma ve ServiceHost.Close kullanarak bu tür uygulamalar güvenli bir şekilde kullanabilmeniz için bir özel durum nadiren oluşturur ServiceHost deyimiyle.</span><span class="sxs-lookup"><span data-stu-id="669ae-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="669ae-121">Ancak, ServiceHost.Close atabilirsiniz unutmayın bir `CommunicationException`, uygulamanızın ServiceHost kapattıktan sonra devam ederse, yapmaktan kaçınmalısınız deyimi ve daha önce verilen desenle izleyin.</span><span class="sxs-lookup"><span data-stu-id="669ae-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="669ae-122">Örneği çalıştırdığınızda, özel durumlar ve işlem yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="669ae-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="669ae-123">Üç senaryo, istemci işlemini çalıştıran her hangi aranır `Divide`.</span><span class="sxs-lookup"><span data-stu-id="669ae-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="669ae-124">İlk senaryoda özel durumu nedeniyle geçiliyor kodu gösterir `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="669ae-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="669ae-125">İkinci senaryo özel durumu nedeniyle maskelenen önemli bir özel durum gösterir `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="669ae-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="669ae-126">Üçüncü senaryo temizleme doğru gösterir.</span><span class="sxs-lookup"><span data-stu-id="669ae-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="669ae-127">İstemci işlemi beklenen çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="669ae-127">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="669ae-128">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="669ae-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="669ae-129">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="669ae-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="669ae-130">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="669ae-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="669ae-131">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="669ae-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="669ae-132">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="669ae-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="669ae-133">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="669ae-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="669ae-134">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="669ae-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="669ae-135">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="669ae-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="669ae-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="669ae-136">See Also</span></span>
