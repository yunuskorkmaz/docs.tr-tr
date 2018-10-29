---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 100f9c0ce71eedaa4061fc894521597074b21b00
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198295"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="49bb0-102">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="49bb0-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="49bb0-103">Bu örnek, çözümleme izleme Windows Communication Foundation (WCF), olay izleme için Windows (ETW) olayları yaymak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="49bb0-104">Analitik izlemeleri, WCF hizmetleri üretim ortamında giderme sağlayan anahtar WCF yığın noktalarında yayılan olaylardır.</span><span class="sxs-lookup"><span data-stu-id="49bb0-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="49bb0-105">WCF hizmetlerinde analitik izleme, izleme performans üzerinde en az etki ile bir üretim ortamında açılabilir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="49bb0-106">Bu izlemeler, olaylar bir ETW oturumu için olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="49bb0-107">Bu örnek, olayları Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için hizmetten gönderilir, temel bir WCF hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="49bb0-108">WCF hizmetinden gelen olayları dinler adanmış bir ETW oturumu başlatmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="49bb0-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="49bb0-109">Örnek, olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolayan ayrılmış bir ETW oturumu oluşturmak için bir betik içerir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="49bb0-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="49bb0-110">To use this sample</span></span>

1.  <span data-ttu-id="49bb0-111">Visual Studio 2012 kullanarak EtwAnalyticTraceSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2.  <span data-ttu-id="49bb0-112">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="49bb0-113">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="49bb0-114">Web tarayıcısında tıklayın **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="49bb0-115">WSDL belgesinde hizmet URI'si tarayıcı içinde görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="49bb0-116">Bu URI'yi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-116">Copy that URI.</span></span>

     <span data-ttu-id="49bb0-117">Varsayılan olarak, hizmet başlatılır 1378 bağlantı noktası isteklerini dinlemeye `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="49bb0-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4.  <span data-ttu-id="49bb0-118">WCF test istemcisi (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="49bb0-119">WCF test istemcisi (WcfTestClient.exe) şu konumdadır `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="49bb0-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="49bb0-120">Varsayılan Visual Studio 2012 yükleme dizini olan `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="49bb0-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5.  <span data-ttu-id="49bb0-121">WCF test istemcisi içinde hizmet seçerek ekleyin **dosya**, ardından **Hizmet Ekle**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="49bb0-122">Uç nokta adresi giriş kutusuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="49bb0-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="49bb0-123">Varsayılan, `http://localhost:1378/Calculator.svc` değeridir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6.  <span data-ttu-id="49bb0-124">Olay Görüntüleyici uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="49bb0-125">Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğüne olayları WCF hizmetinden yayılan izleme dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="49bb0-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7.  <span data-ttu-id="49bb0-126">Gelen **Başlat** menüsünde **Yönetimsel Araçlar**, ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="49bb0-127">Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.</span><span class="sxs-lookup"><span data-stu-id="49bb0-127">Enable the **Analytic** and **Debug** logs.</span></span>

8.  <span data-ttu-id="49bb0-128">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="49bb0-129">Sağ **uygulama uygulamalarının**seçin **görünümü**, ardından **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="49bb0-130">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="49bb0-131">Etkinleştirme **analitik** günlük.</span><span class="sxs-lookup"><span data-stu-id="49bb0-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="49bb0-132">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="49bb0-133">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="49bb0-134">Hizmeti test etmek için</span><span class="sxs-lookup"><span data-stu-id="49bb0-134">To test the service</span></span>

1.  <span data-ttu-id="49bb0-135">WCF test istemcisi geri geçiş yapmak ve çift `Divide` ve bir Payda 0 belirtin varsayılan değerleri koruyun.</span><span class="sxs-lookup"><span data-stu-id="49bb0-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="49bb0-136">Payda 0 ise, hizmet bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49bb0-136">If the denominator is 0, then the service throws a fault.</span></span>

2.  <span data-ttu-id="49bb0-137">Hizmetten yayılan olayları gözlemektir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="49bb0-138">Olay Görüntüleyicisi'ne geçin ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="49bb0-139">Sağ **analitik** seçip **Yenile**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="49bb0-140">WCF analiz izleme olayları Olay Görüntüleyicisi'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="49bb0-141">Tarafından bir hata oluştuğundan bir hata izleme olayı service Olay Görüntüleyicisi görüntülenen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="49bb0-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3.  <span data-ttu-id="49bb0-142">1 ve 2, ancak geçerli girişler.</span><span class="sxs-lookup"><span data-stu-id="49bb0-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="49bb0-143">Değerini `N2` parametresi 0 dışındaki herhangi bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="49bb0-144">WCF görüntülemek için analitik kanal Yenile olayları hata olaylarını dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="49bb0-145">Örnek, bir WCF hizmetinden yayılan analitik izleme olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="49bb0-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="49bb0-146">(İsteğe bağlı) temizlemek için</span><span class="sxs-lookup"><span data-stu-id="49bb0-146">To cleanup (Optional)</span></span>

1.  <span data-ttu-id="49bb0-147">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="49bb0-147">Open Event Viewer.</span></span>

2.  <span data-ttu-id="49bb0-148">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="49bb0-149">Sağ **analitik** seçip **devre dışı günlük**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3.  <span data-ttu-id="49bb0-150">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, ardından  **Uygulama sunucusu uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="49bb0-151">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="49bb0-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4.  <span data-ttu-id="49bb0-152">Seçin **Temizle** olayları silmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="49bb0-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="49bb0-153">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="49bb0-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="49bb0-154">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="49bb0-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49bb0-155">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="49bb0-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49bb0-156">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="49bb0-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="49bb0-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49bb0-157">See Also</span></span>  
 [<span data-ttu-id="49bb0-158">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="49bb0-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
