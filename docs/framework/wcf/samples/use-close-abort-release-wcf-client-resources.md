---
title: Kapat ve Durdur seçeneklerini kullanarak WCF istemci kaynaklarını serbest bırakma
description: Dispose başarısız olabilir ve ağ başarısız olduğunda özel durum oluşturabilir. Bu, istenmeyen davranışa neden olabilir. Bunun yerine, ağ başarısız olduğunda istemci kaynaklarını serbest bırakmak için Kapat ve Iptal ' i kullanın.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599925"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="12e79-105">Ağ bağlantıları kesildiğinde yayın kaynaklarını güvenli bir şekilde kapat ve Iptal et</span><span class="sxs-lookup"><span data-stu-id="12e79-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="12e79-106">Bu örnek, `Close` `Abort` türü belirlenmiş bir istemci kullanılırken kaynakları temizlemek için ve yöntemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12e79-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="12e79-107">`using`Ağ bağlantısı sağlam olmadığında, ifade özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="12e79-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="12e79-108">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="12e79-108">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="12e79-109">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="12e79-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="12e79-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="12e79-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="12e79-111">Bu örnek, C# "Using" ifadesinin yazılı istemcilerle birlikte kullanılması durumunda ortaya çıkan ve özel durumların ardından doğru şekilde temizliği olan kodun yanı sıra oluşan yaygın sorunlardan ikisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12e79-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="12e79-112">C# "Using" deyimleri () çağrısı ile sonuçlanır `Dispose` .</span><span class="sxs-lookup"><span data-stu-id="12e79-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="12e79-113">Bu, `Close` () ile aynıdır ve bir ağ hatası oluştuğunda özel durumlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="12e79-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="12e79-114">() Çağrısı, `Dispose` "Using" bloğunun kapatma küme ayracı içinde örtük olarak yapıldığından, bu özel durum kaynağının, kodu yazan ve kodu okuyan kişilerin fark etmeme olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="12e79-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="12e79-115">Bu, olası bir uygulama hataları kaynağını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12e79-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="12e79-116">Yönteminde gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` , kapatma küme ayracı bir özel durum yaratmakta ve kapatma küme ayracından sonraki kodun yürütülmemelidir:</span><span class="sxs-lookup"><span data-stu-id="12e79-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="12e79-117">Using bloğunun içindeki hiçbir şey bir özel durum oluşturursa veya using bloğunun içindeki tüm özel durumlar yakalansa bile, `Console.WriteLine` `Dispose` Kapanış küme ayracı içindeki örtük () çağrısı bir özel durum oluşturabileceğinden, bu durum gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="12e79-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="12e79-118">Yönteminde gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` , kapanış küme ayracı bir özel durum oluşturan başka bir sorundur:</span><span class="sxs-lookup"><span data-stu-id="12e79-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="12e79-119">`Dispose`() Bir "Finally" bloğunda gerçekleştiğinden, `ApplicationException` () başarısız olursa,, (), using bloğunun dışında hiçbir şekilde görülmez `Dispose` .</span><span class="sxs-lookup"><span data-stu-id="12e79-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="12e79-120">Dış kodun gerçekleştiği zaman hakkında bilmeleri gerekiyorsa `ApplicationException` , "Using" yapısı bu özel durumu maskeleyerek soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="12e79-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="12e79-121">Son olarak, örnek, içinde özel durumlar oluştuğunda nasıl doğru şekilde temizleyeceğinizi gösterir `DemonstrateCleanupWithExceptions` .</span><span class="sxs-lookup"><span data-stu-id="12e79-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="12e79-122">Bu, hataları raporlamak ve çağırmak için bir try/catch bloğu kullanır `Abort` .</span><span class="sxs-lookup"><span data-stu-id="12e79-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="12e79-123">İstemci çağrılarından özel durumları yakalama hakkında daha fazla ayrıntı için [Beklenen özel durumlar](expected-exceptions.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="12e79-123">See the [Expected Exceptions](expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

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
> <span data-ttu-id="12e79-124">Using deyimleri ve ServiceHost: birçok Self-barındırma uygulaması bir hizmeti barındırmakla çok daha fazla yapılır ve ServiceHost. Close nadiren bir özel durum oluşturur, bu nedenle bu uygulamalar, using ifadesini ServiceHost ile güvenli bir şekilde kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="12e79-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="12e79-125">Ancak ServiceHost. Close 'un bir oluşturup oluşturmadığını unutmayın. bu `CommunicationException` nedenle, uygulamanız ServiceHost kapatıldıktan sonra devam ederse, using deyiminden kaçınmalı ve daha önce verilen kalıbı izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="12e79-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="12e79-126">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="12e79-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="12e79-127">İstemci işlemi her biri çağrı yapmaya çalışan üç senaryo çalıştırır `Divide` .</span><span class="sxs-lookup"><span data-stu-id="12e79-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="12e79-128">İlk senaryo, () öğesinden bir özel durum nedeniyle atlanan kodu gösterir `Dispose` .</span><span class="sxs-lookup"><span data-stu-id="12e79-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="12e79-129">İkinci senaryo, () öğesinden bir özel durum nedeniyle maskelenecek önemli bir özel durum gösterir `Dispose` .</span><span class="sxs-lookup"><span data-stu-id="12e79-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="12e79-130">Üçüncü senaryoda doğru temizleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12e79-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="12e79-131">İstemci işlemindeki beklenen çıkış:</span><span class="sxs-lookup"><span data-stu-id="12e79-131">The expected output from the client process is:</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12e79-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="12e79-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="12e79-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="12e79-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="12e79-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="12e79-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="12e79-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="12e79-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12e79-136">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="12e79-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="12e79-137">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="12e79-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="12e79-138">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="12e79-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12e79-139">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="12e79-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
