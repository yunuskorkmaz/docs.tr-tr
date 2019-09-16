---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: a874b291202cb8c3c8752c13b357679c7fd5a556
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989971"
---
# <a name="expected-exceptions"></a><span data-ttu-id="5f15c-102">Beklenen Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="5f15c-102">Expected Exceptions</span></span>
<span data-ttu-id="5f15c-103">Bu örnek, yazılan bir istemci kullanılırken beklenen özel durumların nasıl yakalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="5f15c-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="5f15c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5f15c-105">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="5f15c-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f15c-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5f15c-107">Bu örnek, doğru programların işlemesi gereken iki beklenen özel durum türünü yakalama ve işlemeyi gösterir: `TimeoutException` ve `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="5f15c-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="5f15c-108">Windows Communication Foundation (WCF) istemcisinde iletişim yöntemlerinden oluşturulan özel durumlar bekleniyor veya beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5f15c-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="5f15c-109">Beklenmeyen özel durumlar, veya `OutOfMemoryException` `InvalidOperationException`gibi `ArgumentNullException` programlama hataları gibi çok zararlı hatalar içerir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="5f15c-110">Genellikle beklenmeyen hataları işlemenin yararlı bir yolu yoktur, bu nedenle genellikle WCF istemci iletişim yöntemini çağırırken bunları yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="5f15c-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="5f15c-111">Bir WCF istemcisinde iletişim yöntemlerinden beklenen özel durumlar, `TimeoutException` `CommunicationException` `CommunicationException`ve tüm türetilmiş sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="5f15c-112">Bu, WCF istemcisini iptal ederek ve bir iletişim hatası bildirerek güvenli bir şekilde işlenebilen iletişim sırasında bir sorun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="5f15c-113">Dış faktörler herhangi bir uygulamada bu hatalara neden olabileceğinden, doğru uygulamalar bu özel durumları yakalamalı ve oluştuğunda kurtarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f15c-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="5f15c-114">Bir istemcinin oluşturbileceği birkaç türetilmiş `CommunicationException` sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="5f15c-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="5f15c-115">Bazı durumlarda, uygulamalar özel işlem yapmak için bunlardan bazılarını da yakalar, ancak diğerlerinin bir `CommunicationException`olarak işlenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="5f15c-116">Bu, önce daha özel bir özel durum türü yakalayıp daha sonra `CommunicationException` bir catch yan tümcesinde yakalanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="5f15c-117">İstemci iletişim yöntemini çağıran kodun `TimeoutException` ve ' i `CommunicationException`yakalamalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="5f15c-118">Bu tür hataları işlemenin bir yolu, istemciyi durdurmak ve iletişim başarısızlığını raporlamak olur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="5f15c-119">Beklenen bir özel durum oluşursa, istemci daha sonra kullanılabilir olmayabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="5f15c-120">İstemcinin hala kullanılabilir olup olmadığını anlamak için, `State` özelliğinin olduğunu `CommunicationState`kontrol edin. Makta.</span><span class="sxs-lookup"><span data-stu-id="5f15c-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="5f15c-121">Hala açılırsa, hala kullanılabilir olur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="5f15c-122">Aksi takdirde, istemciyi iptal etmeniz ve tüm başvurularını serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5f15c-123">Bir oturumun bulunduğu istemciler genellikle özel bir durum sonrasında artık kullanılamaz ve bir oturumu olmayan istemciler genellikle bir özel durumla sonra hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="5f15c-124">Ancak, bunlardan hiçbiri garanti edilmez, bu nedenle istemciyi kullanmaya devam etmeyi denemek istiyorsanız, uygulamanızın hala açık olduğunu doğrulamak için `State` özelliği denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="5f15c-125">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="5f15c-126">İstemci süreci iki senaryo çalıştırır, her biri ' ın her birini çağırma `Add` `Divide`girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="5f15c-127">İlk senaryo, çağrısını `Divide`yapmadan önce istemciyi iptal ederek bir ağ sorununun benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="5f15c-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="5f15c-128">İkinci senaryo, yöntemin tamamlanabilmesi için çok kısa süre sonu ayarlayarak zaman aşımı koşuluna neden olur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="5f15c-129">İstemci işlemindeki beklenen çıkış:</span><span class="sxs-lookup"><span data-stu-id="5f15c-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f15c-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5f15c-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f15c-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5f15c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5f15c-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5f15c-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5f15c-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5f15c-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5f15c-134">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f15c-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f15c-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5f15c-135">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5f15c-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="5f15c-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f15c-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f15c-137">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
