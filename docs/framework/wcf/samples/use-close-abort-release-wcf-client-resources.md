---
title: Kapat ve Durdur seçeneklerini kullanarak WCF istemci kaynaklarını serbest bırakma
description: Dispose başarısız olabilir ve ağ başarısız olduğunda özel durum oluşturabilir. Bu, istenmeyen davranışa neden olabilir. Bunun yerine, ağ başarısız olduğunda istemci kaynaklarını serbest bırakmak için Kapat ve Iptal ' i kullanın.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 38861252a470f71a6fa88554e289344e2918d710
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715328"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="a7366-105">Ağ bağlantıları kesildiğinde yayın kaynaklarını güvenli bir şekilde kapat ve Iptal et</span><span class="sxs-lookup"><span data-stu-id="a7366-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="a7366-106">Bu örnek, yazılan bir istemci kullanılırken kaynakları temizlemek için `Close` ve `Abort` yöntemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7366-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="a7366-107">`using` deyimleri, ağ bağlantısı sağlam olmadığında özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="a7366-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="a7366-108">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a7366-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a7366-109">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a7366-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="a7366-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a7366-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a7366-111">Bu örnek, yazılı istemcilerle C# "Using" ifadesinin yanı sıra özel durumların ardından doğru şekilde temizlem kodu kullanırken oluşan yaygın sorunlardan ikisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7366-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="a7366-112">C# "Using" ifadesinde `Dispose`() çağrısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="a7366-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="a7366-113">Bu, bir ağ hatası oluştuğunda özel durum oluşturabilecek `Close`() ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a7366-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="a7366-114">`Dispose`() çağrısı "Using" bloğunun kapatma küme ayracı içinde örtük olarak yapıldığından, bu özel durum kaynağının, kodu yazan ve kodu okuyan kişilerin fark etmeme olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="a7366-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="a7366-115">Bu, olası bir uygulama hataları kaynağını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7366-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="a7366-116">`DemonstrateProblemUsingCanThrow` yönteminde gösterilen ilk sorun, kapatma küme ayracı bir özel durum yaratmakta ve kapatma küme ayracından sonraki kodun yürütülmemelidir:</span><span class="sxs-lookup"><span data-stu-id="a7366-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="a7366-117">Using bloğunun içindeki hiçbir şey bir özel durum oluşturursa veya using bloğunun içindeki tüm özel durumlar yakalansa bile, kapatma küme ayracı içindeki örtük `Dispose`() çağrısı bir özel durum oluşturabileceğinden `Console.WriteLine` gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a7366-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="a7366-118">`DemonstrateProblemUsingCanThrowAndMask` yönteminde gösterilen ikinci sorun, kapanış küme ayracı bir özel durum oluşturan başka bir sorundur:</span><span class="sxs-lookup"><span data-stu-id="a7366-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="a7366-119">`Dispose`() bir "Finally" bloğunda gerçekleştiği için, `Dispose`() başarısız olursa, `ApplicationException`, using bloğunun dışında hiçbir şekilde görülmez.</span><span class="sxs-lookup"><span data-stu-id="a7366-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="a7366-120">Dış kodun `ApplicationException` gerçekleştiği zaman hakkında bilgi sahibi olması gerekiyorsa, "Using" yapısı bu özel durumu maskeleyerek soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7366-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="a7366-121">Son olarak, örnek, `DemonstrateCleanupWithExceptions`özel durumlar oluştuğunda doğru şekilde nasıl temizleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7366-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="a7366-122">Bu, hataları raporlamak ve `Abort`çağırmak için bir try/catch bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7366-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="a7366-123">İstemci çağrılarından özel durumları yakalama hakkında daha fazla ayrıntı için [Beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="a7366-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

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
> <span data-ttu-id="a7366-124">Using deyimleri ve ServiceHost: birçok Self-barındırma uygulaması bir hizmeti barındırmakla çok daha fazla yapılır ve ServiceHost. Close nadiren bir özel durum oluşturur, bu nedenle bu uygulamalar, using ifadesini ServiceHost ile güvenli bir şekilde kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a7366-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="a7366-125">Ancak ServiceHost. Close 'un bir `CommunicationException`oluşturabildiğini unutmayın. bu nedenle, uygulamanız ServiceHost kapatıldıktan sonra devam ederse, using deyiminden kaçınmalı ve daha önce verilen kalıbı izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a7366-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="a7366-126">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a7366-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="a7366-127">İstemci işlemi, her biri `Divide`çağırmayı deneyen üç senaryo çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a7366-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="a7366-128">İlk senaryo `Dispose`() öğesinden bir özel durum nedeniyle atlanan kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7366-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="a7366-129">İkinci senaryo, `Dispose`() ' den özel bir durum nedeniyle maskelenen önemli özel durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7366-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="a7366-130">Üçüncü senaryoda doğru temizleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7366-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="a7366-131">İstemci işlemindeki beklenen çıkış:</span><span class="sxs-lookup"><span data-stu-id="a7366-131">The expected output from the client process is:</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7366-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a7366-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a7366-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7366-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a7366-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a7366-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a7366-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a7366-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7366-136">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7366-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7366-137">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a7366-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a7366-138">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a7366-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7366-139">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a7366-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
