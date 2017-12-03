---
title: "Windows için WCF Hizmetleri ve Etkinlik İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3b7b370ed6b1d9a900579ff0e6f1b0a22290c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="031c3-102">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="031c3-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="031c3-103">Bu örnek analitik izlemede kullanmak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] olayları, olay izleme için Windows (ETW) verebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="031c3-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="031c3-104">Analitik izlemeleri anahtar noktalarında yayılan olaylardır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , sorun giderme izin yığın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] üretim ortamında Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="031c3-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="031c3-105">Analitik izlemede [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, izleme açılabilir bir üretim ortamında performansı üzerinde en az etkiyle.</span><span class="sxs-lookup"><span data-stu-id="031c3-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="031c3-106">Bu izlemeler olayları ETW oturumuna olarak gösterilen.</span><span class="sxs-lookup"><span data-stu-id="031c3-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="031c3-107">Bu örnek temel içeren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hangi olayların hizmetinden Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için gösterilen hizmeti.</span><span class="sxs-lookup"><span data-stu-id="031c3-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="031c3-108">Olayları dinler adanmış bir ETW oturumu başlatmak mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="031c3-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="031c3-109">Örnek olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolar adanmış bir ETW oturum oluşturmak için bir komut dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="031c3-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="031c3-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="031c3-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="031c3-111">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EtwAnalyticTraceSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="031c3-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="031c3-112">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="031c3-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="031c3-113">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="031c3-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="031c3-114">Web tarayıcısında tıklatın **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="031c3-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="031c3-115">Hizmet için WSDL belgenin URI tarayıcıda görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="031c3-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="031c3-116">Bu URI kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="031c3-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="031c3-117">Varsayılan olarak, bağlantı noktası 1378 (http://localhost:1378/Calculator.svc) isteklerini dinleme hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="031c3-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="031c3-118">Çalıştırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemcisi (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="031c3-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="031c3-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Test istemcisi (WcfTestClient.exe) bulunduğu \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini > \Common7\IDE\ WcfTestClient.exe (varsayılan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini olan C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="031c3-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="031c3-120">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemci, hizmet seçerek eklemek **dosya**ve ardından **Hizmet Ekle**.</span><span class="sxs-lookup"><span data-stu-id="031c3-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="031c3-121">Uç nokta adresi giriş kutusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="031c3-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="031c3-122">Http://localhost:1378/Calculator.svc varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="031c3-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="031c3-123">Olay Görüntüleyicisi'ni uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="031c3-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="031c3-124">Hizmet çağrılırken önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğü olaylarını izleme alanından yayınlaması için dinleme yaptığından emin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="031c3-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="031c3-125">Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="031c3-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="031c3-126">Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.</span><span class="sxs-lookup"><span data-stu-id="031c3-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="031c3-127">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="031c3-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="031c3-128">Sağ **uygulama uygulamalarının**seçin **Görünüm**ve ardından **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="031c3-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="031c3-129">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="031c3-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="031c3-130">Etkinleştirme **analitik** günlük.</span><span class="sxs-lookup"><span data-stu-id="031c3-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="031c3-131">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="031c3-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="031c3-132">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="031c3-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="031c3-133">Hizmeti sınamak için</span><span class="sxs-lookup"><span data-stu-id="031c3-133">To test the service</span></span>  
  
1.  <span data-ttu-id="031c3-134">Dönmek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift tıklayın ve test istemcisi `Divide` ve Payda 0 belirtin varsayılan değerleri koruyun.</span><span class="sxs-lookup"><span data-stu-id="031c3-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="031c3-135">Paydanın 0 ise, hizmet bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="031c3-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="031c3-136">Hizmetinden gösterilen olayları gözlemektir.</span><span class="sxs-lookup"><span data-stu-id="031c3-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="031c3-137">Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="031c3-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="031c3-138">Sağ **analitik** seçip **yenileme**.</span><span class="sxs-lookup"><span data-stu-id="031c3-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="031c3-139">WCF analiz izleme olayları Olay Görüntüleyicisi'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="031c3-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="031c3-140">Bir arıza tarafından oluşturulan olduğundan hizmet bir hata izleme olayı olduğundan Olay Görüntüleyicisi görüntülenen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="031c3-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="031c3-141">1 ve 2, ancak geçerli giriş ile.</span><span class="sxs-lookup"><span data-stu-id="031c3-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="031c3-142">Değeri `N2` parametresi, 0 dışında herhangi bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="031c3-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="031c3-143">WCF görüntülemek için analitik kanal yenileme olayları hata olaylarını içermez.</span><span class="sxs-lookup"><span data-stu-id="031c3-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="031c3-144">Örnek bir WCF hizmetinden yayılan analitik izleme olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="031c3-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="031c3-145">Temizleme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="031c3-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="031c3-146">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="031c3-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="031c3-147">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="031c3-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="031c3-148">Sağ **analitik** seçip **günlüğü devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="031c3-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="031c3-149">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="031c3-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="031c3-150">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="031c3-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="031c3-151">Seçin **temizleyin** olayları temizlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="031c3-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="031c3-152">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="031c3-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="031c3-153">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="031c3-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="031c3-154">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="031c3-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="031c3-155">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="031c3-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="031c3-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="031c3-156">See Also</span></span>  
 [<span data-ttu-id="031c3-157">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="031c3-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
