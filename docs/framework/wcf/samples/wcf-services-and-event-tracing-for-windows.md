---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183207"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="6d407-102">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="6d407-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="6d407-103">Bu örnek, Windows İletişim Vakfı'ndaki (WCF) analitik izlemenin, Windows için Olay İzleme (ETW) etkinliklerini yalamak için nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6d407-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="6d407-104">Analitik izlemeler, WCF yığınının kilit noktalarında yayılan ve WCF hizmetlerinin üretim ortamında sorun gidermesine olanak tanıyan olaylardır.</span><span class="sxs-lookup"><span data-stu-id="6d407-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="6d407-105">WCF hizmetlerinde analitik izleme, performans üzerinde en az etkiye sahip bir üretim ortamında açılabilir izleme.</span><span class="sxs-lookup"><span data-stu-id="6d407-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="6d407-106">Bu izlemeler bir ETW oturumuna olay olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="6d407-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="6d407-107">Bu örnek, olayların hizmetten olay günlüğüne yayıldığı ve Olay Görüntüleyicisi kullanılarak görüntülenebilen temel bir WCF hizmetini içerir.</span><span class="sxs-lookup"><span data-stu-id="6d407-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="6d407-108">Ayrıca, WCF hizmetindeki etkinlikleri dinleyen özel bir ETW oturumu başlatmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6d407-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="6d407-109">Örnek, olayları Olay Görüntüleyicisi kullanılarak okunabilen ikili bir dosyada depolayan özel bir ETW oturumu oluşturmak için bir komut dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="6d407-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6d407-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6d407-110">To use this sample</span></span>

1. <span data-ttu-id="6d407-111">Visual Studio 2012'yi kullanarak EtwAnalyticTraceSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6d407-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="6d407-112">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d407-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="6d407-113">Çözümü çalıştırmak için CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d407-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="6d407-114">Web tarayıcısında, **Calculator.svc'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6d407-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="6d407-115">Hizmet için WSDL belgesinin URI tarayıcıda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="6d407-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="6d407-116">Uri'yi kopyala.</span><span class="sxs-lookup"><span data-stu-id="6d407-116">Copy that URI.</span></span>

     <span data-ttu-id="6d407-117">Varsayılan olarak, hizmet bağlantı noktası 1378 `http://localhost:1378/Calculator.svc`isteklerini dinlemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="6d407-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="6d407-118">WCF test istemcisini çalıştırın (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="6d407-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="6d407-119">WCF test istemcisi (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`adresinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="6d407-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="6d407-120">Varsayılan Visual Studio 2012 `C:\Program Files\Microsoft Visual Studio 10.0`yüklemek dir .</span><span class="sxs-lookup"><span data-stu-id="6d407-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="6d407-121">WCF test istemcisi içinde, **Dosya**seçerek hizmet ekleyin ve sonra **Hizmet ekle**.</span><span class="sxs-lookup"><span data-stu-id="6d407-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="6d407-122">Giriş kutusuna bitiş noktası adresini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d407-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="6d407-123">Varsayılan değer: `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="6d407-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="6d407-124">Olay Görüntüleyicisi uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="6d407-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="6d407-125">Hizmeti başlatmadan önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğünün WCF hizmetinden yayılan olayları izlemek için dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d407-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="6d407-126">**Başlat** menüsünden **Yönetim Araçları'nı**ve ardından **Olay Görüntüleyicisi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="6d407-127">**Analitik** ve **Hata Ayıklama** günlüklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d407-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="6d407-128">Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6d407-129">**Uygulama Sunucusu Uygulamaları'nı**sağ tıklatın, **Görünüm'i**seçin ve ardından Analitik ve **Hata Ayıklama Günlüklerini Göster'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="6d407-130">**Analitik ve Hata Ayıklama Günlükleri'ni göster** seçeneğinin işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d407-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="6d407-131">**Analitik** günlüğünü etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6d407-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="6d407-132">Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6d407-133">**Analytic'e** sağ tıklayın ve **Günlüğü Etkinleştir'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="6d407-134">Hizmeti test etmek için</span><span class="sxs-lookup"><span data-stu-id="6d407-134">To test the service</span></span>

1. <span data-ttu-id="6d407-135">WCF test istemcisine geri dön `Divide` ve çift tıklatın ve 0 paydasını belirten varsayılan değerleri koruyun.</span><span class="sxs-lookup"><span data-stu-id="6d407-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="6d407-136">Payda 0 ise, servis bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="6d407-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="6d407-137">Hizmetten yayılan olayları gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="6d407-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="6d407-138">Olay Görüntüleyici'ye geri dön ve **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6d407-139">**Analytic'e** sağ tıklayın ve **Yenile'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="6d407-140">WCF analitik izleme olayları olay görüntüleyicisinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6d407-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="6d407-141">Hizmet tarafından bir hata atıldığı için olay görüntüleyicisinde bir hata izleme olayının görüntülendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6d407-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="6d407-142">1 ve 2 adımlarını, ancak geçerli girişlerle yineleyin.</span><span class="sxs-lookup"><span data-stu-id="6d407-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="6d407-143">Parametrenin `N2` değeri 0'dan başka herhangi bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d407-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="6d407-144">WCF olaylarını görüntülemek için analitik kanalı yenileyin herhangi bir hata olayı içermez.</span><span class="sxs-lookup"><span data-stu-id="6d407-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="6d407-145">Örnek, bir WCF hizmetinden yayılan analitik izleme olaylarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d407-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="6d407-146">Temizlemek için (İsteğe Bağlı)</span><span class="sxs-lookup"><span data-stu-id="6d407-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="6d407-147">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="6d407-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="6d407-148">Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama-Sunucu Uygulamaları**gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6d407-149">**Analytic'e** sağ tıklayın ve **Günlük'ünü Devre Dışı Nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="6d407-150">Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama-Sunucu Uygulamaları**gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6d407-151">**Analytic'e** sağ tıklayın ve **Günlük'u temizle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="6d407-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="6d407-152">Olayları temizlemek için **Temizle** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="6d407-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d407-153">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d407-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6d407-154">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6d407-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6d407-155">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="6d407-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d407-156">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d407-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="6d407-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d407-157">See also</span></span>

- <span data-ttu-id="6d407-158">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6d407-158">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
