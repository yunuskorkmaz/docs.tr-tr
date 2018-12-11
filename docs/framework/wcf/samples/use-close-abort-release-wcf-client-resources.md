---
title: WCF istemci kaynakları serbest bırakmak için iptal etmek ve kapatmak kullanın
description: Dispose, başarısız ve ağ başarısız olduğunda özel durumlar. Bu, istenmeyen davranışlara neden olabilir. Bunun yerine, yakın kullanın ve ağ başarısız olduğunda istemci kaynakları serbest bırakmak için İptal.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: d37ad9d2277fea2656311a5a1f57d51343d10d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147222"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="b6ce7-105">Kapat ve ağ bağlantıları güvenli bir şekilde bırakılan iptal yayın kaynakları</span><span class="sxs-lookup"><span data-stu-id="b6ce7-105">Close and Abort release resources safely when network connections have dropped</span></span>
<span data-ttu-id="b6ce7-106">Bu örnek, kullanarak gösterir `Close` ve `Abort` türü belirlenmiş istemci kullanırken kaynakları temizlemek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="b6ce7-107">`using` Deyimi ağ bağlantısı sağlam olmadığında özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="b6ce7-108">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="b6ce7-109">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ce7-110">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b6ce7-111">Bu örnek iki C# "özel durumları sonra doğru şekilde temizler kod yanı sıra, belirlenmiş istemcileri ile using deyimi" kullanırken oluşan genel sorunları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="b6ce7-112">C# "using deyimi" sonuçları bir çağrıda `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b6ce7-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="b6ce7-113">Bu, aynı `Close`bir ağ hatası oluştuğunda, özel durumlar oluşturabilir ().</span><span class="sxs-lookup"><span data-stu-id="b6ce7-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="b6ce7-114">Çünkü çağrısı `Dispose`() "kullanma" blok kapanış ayracı örtük olarak olur, bu özel durum büyük olasılıkla Git bilgisi dışında kod yazmak ve kodunuzu okuyan kişi tarafından kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="b6ce7-115">Bu uygulama hatalarının olası bir kaynağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-115">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="b6ce7-116">Gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` yöntemi olduğundan kapanış ayracı değil yürüttükten sonra kapanış küme ayracı ve kod özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b6ce7-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="b6ce7-117">Kullanarak içinde hiçbir şey engelleyecek bir özel durum veya içeriden kullanarak tüm özel durumları bile blok yakalanır, `Console.Writeline` nedeni aşağıdakiler olabilir değil örtük `Dispose`kapanış ayracı () çağrısında bir özel durum throw.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="b6ce7-118">Gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` yöntemi olduğundan, bir özel durum kapanış ayracı başka bir uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b6ce7-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="b6ce7-119">Çünkü `Dispose`() "finally" bloğun içinde gerçekleşir `ApplicationException` kullanarak dışında hiçbir zaman görülmedi bloke `Dispose`() başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="b6ce7-120">Kodun dışında ne zaman hakkında bilmeniz gerekir, `ApplicationException` ortaya "kullanarak" yapısı, bu özel durumun maskeleyerek sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="b6ce7-121">Son olarak, örnek doğru olduğunda özel durumlar ortaya yukarı temizlemek nasıl gösterir `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="b6ce7-122">Bu bir try/catch bloğu hatalarını raporlamak ve çağrı kullanır `Abort`.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="b6ce7-123">Bkz: [beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) istemci çağrılarının özel durumları yakalama hakkında daha fazla ayrıntı için örnek.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
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
>  <span data-ttu-id="b6ce7-124">Deyimi ile ServiceHost: Kendi kendine barındırma birçok uygulama biraz daha uzun bir hizmeti barındırma ve ServiceHost.Close söz konusu uygulamalar kullanarak güvenli bir şekilde kullanabilmeniz için bir özel durum nadiren oluşturur ServiceHost deyimiyle.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="b6ce7-125">Ancak ServiceHost.Close oluşturabilecek dikkat bir `CommunicationException`, uygulamanızın ServiceHost kapattıktan sonra devam ederse, kullanmaktan kaçınmanız gerekir böylece deyimi ve daha önce verilen desenle izleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="b6ce7-126">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="b6ce7-127">İstemci işlemi üç senaryo çalıştıran her çağırmak için hangi girişimleri `Divide`.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="b6ce7-128">İlk senaryoda adresinden bir özel durum nedeniyle atlandı kod gösterir `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b6ce7-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="b6ce7-129">İkinci senaryoda adresinden bir özel durum nedeniyle maskelenen önemli bir özel durum gösterir `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b6ce7-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="b6ce7-130">Üçüncü senaryo temizleme doğru gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-130">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="b6ce7-131">İstemci işlemi beklenen çıktısı bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b6ce7-131">The expected output from the client process is:</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b6ce7-132">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b6ce7-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b6ce7-133">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b6ce7-134">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b6ce7-135">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6ce7-136">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b6ce7-137">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b6ce7-138">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6ce7-139">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="b6ce7-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-140">See Also</span></span>
