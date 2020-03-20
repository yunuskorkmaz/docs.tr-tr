---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144715"
---
# <a name="expected-exceptions"></a><span data-ttu-id="ad076-102">Beklenen Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ad076-102">Expected Exceptions</span></span>
<span data-ttu-id="ad076-103">Bu örnek, yazılı istemci kullanırken beklenen özel durumların nasıl yakaılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad076-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="ad076-104">Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="ad076-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="ad076-105">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="ad076-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad076-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ad076-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ad076-107">Bu örnek, doğru programların işlemesi gereken beklenen iki `TimeoutException` `CommunicationException`özel durum türünü yakalamayı ve işlemeyi gösterir: ve.</span><span class="sxs-lookup"><span data-stu-id="ad076-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="ad076-108">Windows Communication Foundation (WCF) istemcisindeki iletişim yöntemlerinden atılan özel durumlar beklenen veya beklenmeyen durumlardır.</span><span class="sxs-lookup"><span data-stu-id="ad076-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="ad076-109">Beklenmeyen özel durumlar gibi `OutOfMemoryException` felaket hataları ve `ArgumentNullException` `InvalidOperationException`programlama hataları içerir.</span><span class="sxs-lookup"><span data-stu-id="ad076-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="ad076-110">Genellikle beklenmeyen hataları işlemek için yararlı bir yol yoktur, bu nedenle genellikle bir WCF istemci iletişim yöntemi ni ararken bunları yakalamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="ad076-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="ad076-111">WCF istemcisindeki iletişim yöntemlerinden `TimeoutException` `CommunicationException`beklenen özel durumlar `CommunicationException`, ve türetilmiş herhangi bir sınıf .</span><span class="sxs-lookup"><span data-stu-id="ad076-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="ad076-112">Bunlar, WCF istemcisinin iptali ve bir iletişim hatası bildirilmesi yle güvenli bir şekilde işlenebilen iletişim sırasında ki bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad076-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="ad076-113">Dış etkenler herhangi bir uygulamada bu hatalara neden olabileceğinden, doğru uygulamaların bu özel durumları yakalaması ve oluştuğunda kurtarması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad076-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="ad076-114">Bir istemcinin `CommunicationException` atabileceği birkaç türemiş sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="ad076-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="ad076-115">Bazı durumlarda, uygulamalar da özel işleme yapmak için bunlardan bazılarını yakalamak, `CommunicationException`ancak diğerleri olarak ele alınmasını sağlar .</span><span class="sxs-lookup"><span data-stu-id="ad076-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="ad076-116">Bu, önce daha özel özel özel durum türünü `CommunicationException` yakalayarak ve daha sonra daha sonra catch-clause'da yakalayarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad076-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="ad076-117">İstemci iletişim yöntemiçağıran kod `TimeoutException` `CommunicationException`yakalamak gerekir ve .</span><span class="sxs-lookup"><span data-stu-id="ad076-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="ad076-118">Bu tür hataları işlemek için bir yolu istemci iptal etmek ve iletişim hatası rapor etmektir.</span><span class="sxs-lookup"><span data-stu-id="ad076-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="ad076-119">Beklenen bir özel durum oluşursa, istemci daha sonra kullanılabilir olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ad076-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="ad076-120">İstemcinin hala kullanılabilir olup olmadığını `State` belirlemek `CommunicationState`için özelliğin. Açıldı.</span><span class="sxs-lookup"><span data-stu-id="ad076-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="ad076-121">Hala açılırsa, o zaman hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ad076-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="ad076-122">Aksi takdirde istemciyi iptal etmeli ve tüm başvuruları serbest bırakmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ad076-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ad076-123">Oturumu olan istemcilerin genellikle bir özel durum sonrasında artık kullanılabilir olmadığını ve oturumu olmayan istemcilerin genellikle bir özel durum sonra da kullanılabilir olduğunu gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad076-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="ad076-124">Ancak, bunların hiçbiri garanti değildir, bu nedenle bir özel durum sonra istemci kullanmaya `State` devam etmek istiyorsanız, uygulamanız istemci hala açık olduğunu doğrulamak için özelliği kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="ad076-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="ad076-125">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ad076-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="ad076-126">İstem işlemi, her biri çağırılan `Add` iki `Divide`senaryo çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ad076-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="ad076-127">İlk senaryo, aramayı yapmadan önce istemciyi iptal ederek bir `Divide`ağ sorununu simüle eder.</span><span class="sxs-lookup"><span data-stu-id="ad076-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="ad076-128">İkinci senaryo, yöntemin tamamlanması için çok kısa zaman ayarı yaparak bir zaman ayarı durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="ad076-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="ad076-129">İstemci işleminden beklenen çıktı:</span><span class="sxs-lookup"><span data-stu-id="ad076-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad076-130">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ad076-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ad076-131">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad076-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ad076-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad076-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ad076-133">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad076-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad076-134">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad076-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ad076-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ad076-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ad076-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="ad076-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad076-137">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad076-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
