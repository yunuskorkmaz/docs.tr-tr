---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="5018a-102">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="5018a-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="5018a-103">Bu örnek çözümleme izleme Windows Communication Foundation (WCF) olayları, olay izleme için Windows (ETW) yayma için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5018a-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="5018a-104">Analitik izlemeleri, WCF hizmetleri üretim ortamında sorun giderme sağlayan anahtar noktalarda WCF yığınında gösterilen olaylardır.</span><span class="sxs-lookup"><span data-stu-id="5018a-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>  
  
 <span data-ttu-id="5018a-105">WCF hizmetlerinde çözümleme izleme, izleme bir üretim ortamında performansı üzerinde en az etkiyle açılabilir.</span><span class="sxs-lookup"><span data-stu-id="5018a-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="5018a-106">Bu izlemeler olayları ETW oturumuna olarak gösterilen.</span><span class="sxs-lookup"><span data-stu-id="5018a-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="5018a-107">Bu örnek, olayları Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için hizmetinden yayılan temel bir WCF hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="5018a-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="5018a-108">WCF hizmetinden gelen olayları dinler adanmış bir ETW oturumu başlatmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5018a-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="5018a-109">Örnek olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolar adanmış bir ETW oturum oluşturmak için bir komut dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="5018a-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5018a-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5018a-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="5018a-111">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EtwAnalyticTraceSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5018a-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5018a-112">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5018a-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5018a-113">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5018a-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="5018a-114">Web tarayıcısında tıklatın **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="5018a-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="5018a-115">Hizmet için WSDL belgenin URI tarayıcıda görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5018a-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="5018a-116">Bu URI kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5018a-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="5018a-117">Varsayılan olarak, hizmet başlatır bağlantı 1378 isteklerini dinleme (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="5018a-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="5018a-118">WCF test istemcisi (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5018a-118">Run the WCF test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="5018a-119">WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini > \Common7\IDE\ WcfTestClient.exe (varsayılan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini olan C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="5018a-119">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="5018a-120">WCF test istemcisi içinde hizmet seçerek eklemek **dosya**ve ardından **Hizmet Ekle**.</span><span class="sxs-lookup"><span data-stu-id="5018a-120">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="5018a-121">Uç nokta adresi giriş kutusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5018a-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="5018a-122">Varsayılan, http://localhost:1378/Calculator.svc değeridir.</span><span class="sxs-lookup"><span data-stu-id="5018a-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="5018a-123">Olay Görüntüleyicisi'ni uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="5018a-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="5018a-124">Hizmet çağrılırken önce Olay Görüntüleyicisi'ni başlatın ve WCF hizmetinden gösterilen olayları izlemek için olay günlüğüne dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5018a-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>  
  
7.  <span data-ttu-id="5018a-125">Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="5018a-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="5018a-126">Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.</span><span class="sxs-lookup"><span data-stu-id="5018a-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="5018a-127">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="5018a-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="5018a-128">Sağ **uygulama uygulamalarının**seçin **Görünüm**ve ardından **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="5018a-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="5018a-129">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="5018a-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="5018a-130">Etkinleştirme **analitik** günlük.</span><span class="sxs-lookup"><span data-stu-id="5018a-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="5018a-131">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="5018a-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="5018a-132">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="5018a-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="5018a-133">Hizmeti sınamak için</span><span class="sxs-lookup"><span data-stu-id="5018a-133">To test the service</span></span>  
  
1.  <span data-ttu-id="5018a-134">Çift tıklayın ve geçiş WCF test istemcisi geri `Divide` ve Payda 0 belirtin varsayılan değerleri koruyun.</span><span class="sxs-lookup"><span data-stu-id="5018a-134">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="5018a-135">Paydanın 0 ise, hizmet bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5018a-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="5018a-136">Hizmetinden gösterilen olayları gözlemektir.</span><span class="sxs-lookup"><span data-stu-id="5018a-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="5018a-137">Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="5018a-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="5018a-138">Sağ **analitik** seçip **yenileme**.</span><span class="sxs-lookup"><span data-stu-id="5018a-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="5018a-139">WCF analiz izleme olayları Olay Görüntüleyicisi'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5018a-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="5018a-140">Bir arıza tarafından oluşturulan olduğundan hizmet bir hata izleme olayı olduğundan Olay Görüntüleyicisi görüntülenen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5018a-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="5018a-141">1 ve 2, ancak geçerli giriş ile.</span><span class="sxs-lookup"><span data-stu-id="5018a-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="5018a-142">Değeri `N2` parametresi, 0 dışında herhangi bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5018a-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="5018a-143">WCF görüntülemek için analitik kanal yenileme olayları hata olaylarını içermez.</span><span class="sxs-lookup"><span data-stu-id="5018a-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="5018a-144">Örnek bir WCF hizmetinden yayılan analitik izleme olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5018a-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="5018a-145">Temizleme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5018a-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="5018a-146">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="5018a-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="5018a-147">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="5018a-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="5018a-148">Sağ **analitik** seçip **günlüğü devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="5018a-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="5018a-149">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="5018a-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="5018a-150">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="5018a-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="5018a-151">Seçin **temizleyin** olayları temizlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5018a-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5018a-152">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="5018a-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5018a-153">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5018a-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5018a-154">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5018a-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5018a-155">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5018a-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="5018a-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5018a-156">See Also</span></span>  
 [<span data-ttu-id="5018a-157">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="5018a-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
