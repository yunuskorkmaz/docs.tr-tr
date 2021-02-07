---
description: Hakkında daha fazla bilgi için bkz. Windows için WCF Hizmetleri ve olay Izleme
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ba2d323322a2d3481f1414ac58fbf0b44508bb03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755687"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="9a754-103">Windows için WCF Hizmetleri ve Etkinlik İzleme</span><span class="sxs-lookup"><span data-stu-id="9a754-103">WCF Services and Event Tracing for Windows</span></span>

<span data-ttu-id="9a754-104">Bu örnek, Windows için olay Izleme (ETW) içindeki olayları göstermek için Windows Communication Foundation (WCF) ' de analitik izlemenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a754-104">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="9a754-105">Analitik izlemeler, WCF yığınında, üretim ortamındaki WCF hizmetlerinde sorun gidermeye izin veren önemli noktalara yayılan olaylardır.</span><span class="sxs-lookup"><span data-stu-id="9a754-105">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="9a754-106">WCF Hizmetlerinde analitik izleme, performans üzerinde en az etkisi olan bir üretim ortamında açılıp açılbiliyordu.</span><span class="sxs-lookup"><span data-stu-id="9a754-106">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="9a754-107">Bu izlemeler bir ETW oturumuna olay olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="9a754-107">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="9a754-108">Bu örnek, olayların hizmetten, Olay Görüntüleyicisi kullanılarak görüntülenebilen olay günlüğüne oluşturulduğu temel bir WCF hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="9a754-108">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="9a754-109">WCF hizmetinden olayları dinleyen özel bir ETW oturumu başlatmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9a754-109">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="9a754-110">Örnek, Olay Görüntüleyicisi kullanılarak okunabilen bir ikili dosyada olayları depolayan adanmış bir ETW oturumu oluşturmak için bir komut dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="9a754-110">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="9a754-111">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9a754-111">To use this sample</span></span>

1. <span data-ttu-id="9a754-112">Visual Studio 2012 kullanarak, Etwanaltictracesample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9a754-112">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="9a754-113">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="9a754-113">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="9a754-114">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="9a754-114">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="9a754-115">Web tarayıcısında, **Hesaplayıcı. svc**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9a754-115">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="9a754-116">Hizmet için WSDL belgesinin URI 'SI tarayıcıda görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="9a754-116">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="9a754-117">Bu URI 'yi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9a754-117">Copy that URI.</span></span>

     <span data-ttu-id="9a754-118">Varsayılan olarak, hizmet bağlantı noktası 1378 ' deki istekleri dinlemeye başlar `http://localhost:1378/Calculator.svc` .</span><span class="sxs-lookup"><span data-stu-id="9a754-118">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="9a754-119">WCF test istemcisini çalıştırın (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="9a754-119">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="9a754-120">WCF Test istemcisi (WcfTestClient.exe) konumunda bulunur `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` .</span><span class="sxs-lookup"><span data-stu-id="9a754-120">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="9a754-121">Varsayılan Visual Studio 2012 install dir `C:\Program Files\Microsoft Visual Studio 10.0` .</span><span class="sxs-lookup"><span data-stu-id="9a754-121">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="9a754-122">WCF Test istemcisi içinde **Dosya**' yı ve ardından **Hizmet Ekle**' yi seçerek hizmeti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a754-122">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="9a754-123">Giriş kutusuna uç nokta adresini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a754-123">Add the endpoint address in the input box.</span></span> <span data-ttu-id="9a754-124">Varsayılan değer: `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="9a754-124">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="9a754-125">Olay Görüntüleyicisi uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="9a754-125">Open the Event Viewer application.</span></span>

     <span data-ttu-id="9a754-126">Hizmeti çağırmadan önce Olay Görüntüleyicisi başlatın ve olay günlüğünün WCF hizmetinden yayılan izleme olaylarını dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a754-126">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="9a754-127">**Başlat** menüsünde, **Yönetim Araçları**' nı seçin ve ardından **Olay Görüntüleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="9a754-127">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="9a754-128">**Analitik** ve **hata ayıklama** günlüklerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9a754-128">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="9a754-129">Olay Görüntüleyicisi ' deki ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows** ve ardından **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="9a754-129">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9a754-130">**Uygulama sunucusu-uygulamalar**' a sağ tıklayın, **Görünüm**' ü seçin ve ardından **analitik ve hata ayıklama günlüklerini görüntüleyin**.</span><span class="sxs-lookup"><span data-stu-id="9a754-130">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="9a754-131">**Analitik ve hata ayıklama günlüklerini göster** seçeneğinin işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a754-131">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="9a754-132">**Analitik** günlüğü etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9a754-132">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="9a754-133">Olay Görüntüleyicisi ' deki ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows** ve ardından **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="9a754-133">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9a754-134">**Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9a754-134">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="9a754-135">Hizmeti test etmek için</span><span class="sxs-lookup"><span data-stu-id="9a754-135">To test the service</span></span>

1. <span data-ttu-id="9a754-136">WCF test istemcisine geri dönün ve çift tıklayın `Divide` ve 0 paydasını belirten varsayılan değerleri tutun.</span><span class="sxs-lookup"><span data-stu-id="9a754-136">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="9a754-137">Payda 0 ise, hizmet bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a754-137">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="9a754-138">Hizmetten yayılan olayları gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="9a754-138">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="9a754-139">Olay Görüntüleyicisi dönün ve **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows** ve **uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="9a754-139">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9a754-140">**Analitik** ' e sağ tıklayın ve **Yenile**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a754-140">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="9a754-141">WCF analitik izleme olayları Olay Görüntüleyicisi 'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9a754-141">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="9a754-142">Olay görüntüleyicisindeki bir hata izleme olayı tarafından bir hata oluşturulduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9a754-142">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="9a754-143">1 ve 2. adımları, ancak geçerli girişlerle tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a754-143">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="9a754-144">`N2`Parametresinin değeri 0 dışında herhangi bir sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a754-144">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="9a754-145">WCF olaylarını görüntülemek için analitik kanalı yenileme herhangi bir hata olayı içermez.</span><span class="sxs-lookup"><span data-stu-id="9a754-145">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="9a754-146">Örnek, bir WCF hizmetinden yayılan analitik izleme olaylarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a754-146">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="9a754-147">Temizlemek için (Isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9a754-147">To cleanup (Optional)</span></span>

1. <span data-ttu-id="9a754-148">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="9a754-148">Open Event Viewer.</span></span>

2. <span data-ttu-id="9a754-149">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows** ve sonra **uygulama-sunucu uygulamaları**' na gidin.</span><span class="sxs-lookup"><span data-stu-id="9a754-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="9a754-150">**Analitik** öğesine sağ tıklayın ve **günlüğü devre dışı bırak**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a754-150">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="9a754-151">**Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows** ve sonra **uygulama-sunucu uygulamaları**' na gidin.</span><span class="sxs-lookup"><span data-stu-id="9a754-151">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="9a754-152">**Analitik** öğesine sağ tıklayın ve **Günlüğü Temizle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a754-152">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="9a754-153">Olayları temizlemek için **Temizle** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="9a754-153">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a754-154">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a754-154">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9a754-155">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9a754-155">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9a754-156">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9a754-156">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a754-157">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9a754-157">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="9a754-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a754-158">See also</span></span>

- <span data-ttu-id="9a754-159">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9a754-159">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
