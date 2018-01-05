---
title: "WF izleme kullanarak veri ayıklamak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c269dc9c8b5a0050cfc3ffcefc3160b07c897
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="80876-102">WF izleme kullanarak veri ayıklamak</span><span class="sxs-lookup"><span data-stu-id="80876-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="80876-103">Bu örnek, iş akışı iş akışı değişkenleri ve bağımsız değişkenler etkinliklerden ayıklamak için izleme kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80876-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="80876-104">Ayrıca, kaydeder ve veri yükü özel izleme kayıtları içinde ayıklama izleme için ek açıklamalar eklenmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80876-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="80876-105">Örnek veri akışından ayıklamak için olay izleme için Windows (ETW) izleme katılımcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="80876-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="80876-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="80876-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="80876-107">bir iş akışı örneğini yürütmeyi görünürlük elde etmek için izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="80876-107"> provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="80876-108">İzleme çalışma zamanı iş akışı iş akışı yürütme sırasında kayıtları izleme yayar.</span><span class="sxs-lookup"><span data-stu-id="80876-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="80876-109">Kayıt iş akışı izleme yanı sıra, iş akışını iş akışı örneği verileri ayıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="80876-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="80876-110">Aşağıdaki listede kayıtları izleme ayıklanabilir veri türlerini Ayrıntılar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="80876-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="80876-111">Bir etkinlik ve etkinliği yürütülürken kayıtları izleme değişkenler iş akışı.</span><span class="sxs-lookup"><span data-stu-id="80876-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="80876-112">İş akışı değişkenleri ayıklamak için ayıklanacak değişkenleri, bir profilde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="80876-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="80876-113">Ayıklanacak değişkenleri yalnızca belirtilebilir ile `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="80876-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="80876-114">Aşağıdaki kod örneğinde etkinliği iş akışı değişkeni çıkarmak için kullanılan bir izleme profili gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80876-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="80876-115">Etkinlik bağımsız değişkenleri ve kayıtları izleme etkinlik durumu.</span><span class="sxs-lookup"><span data-stu-id="80876-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="80876-116">Bağımsız değişkenleri tanımlayın yolu veri akışları içinde veya dışında bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="80876-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="80876-117">Ayıklanacak bağımsız değişkenleri kullanılarak belirtilen bir <xref:System.Activities.Tracking.ActivityStateQuery>. Aşağıdaki kod örneğinde ayıklar bir izleme profilidir `Value` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="80876-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="80876-118">Ek açıklamalar yayılan tüm izleme kayıt eklenebilir anahtar/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="80876-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="80876-119">Ek açıklamalar kayıtları izleme için bir etiketleme mekanizması işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="80876-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="80876-120">Ek açıklamalar, bir izleme profili kayıtlarda izleme eklenir.</span><span class="sxs-lookup"><span data-stu-id="80876-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="80876-121">Ek açıklama herhangi bir türde bir iş akışı izleme sorgu eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="80876-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="80876-122">Aşağıdaki kod örneğinde açıklamanın bir izleme kaydına nasıl eklenebileceğini gösteren bir izleme profilidir.</span><span class="sxs-lookup"><span data-stu-id="80876-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="80876-123">Özel izleme kayıtları kullanıcı tanımlı etkinliklerden gösterilen.</span><span class="sxs-lookup"><span data-stu-id="80876-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="80876-124">Özel kayıtları izleme, bu etkinlik içinde tanımlanan yükü veri taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="80876-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="80876-125">İzleme profili özel izleme kayıtları için abone yükü izleme kaydı içinde ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="80876-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="80876-126">Özel izleme kayıtları özel ayıklanabilir bir <xref:System.Activities.Tracking.TrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="80876-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="80876-127">Aşağıdaki kod örneğinde özel izleme kaydı yük birlikte çıkaran bir izleme profilidir.</span><span class="sxs-lookup"><span data-stu-id="80876-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="80876-128">Örnek bağımsız değişkenler, özel kaydeder ve bir Web.config dosyasında belirtilen bir profili kullanarak ekleme ek açıklamaları değişkenleri ayıklama gösterir. İzleme etkin örnek iş akışı hizmeti ekleyerek bir `<etwTracking>` davranışı öğesi.</span><span class="sxs-lookup"><span data-stu-id="80876-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="80876-129">Aşağıdaki kod örnek etkinleştirir izleme `ExtractWorkflowVariables` profili izleme.</span><span class="sxs-lookup"><span data-stu-id="80876-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="80876-130">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="80876-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="80876-131">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="80876-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="80876-132">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80876-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="80876-133">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80876-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="80876-134">Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="80876-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="80876-135">Tarayıcıda StockPriceService.xamlx'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="80876-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="80876-136">Tarayıcı yerel hizmet WSDL adresi içeren StockPriceService sayfa görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80876-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="80876-137">Bu adresini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="80876-137">Copy this address.</span></span>  
  
     <span data-ttu-id="80876-138">Aşağıdaki örnek, bir yerel hizmet WSDL adresi gösterir.</span><span class="sxs-lookup"><span data-stu-id="80876-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="80876-139">Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve iş akışı hizmetinden gösterilen olayları izlemek için olay günlüğüne dinlediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="80876-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="80876-140">Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar** ve ardından **Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="80876-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="80876-141">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, ve **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="80876-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="80876-142">Sağ **Microsoft** seçip **Görünüm** ve ardından **Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="80876-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="80876-143">Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.</span><span class="sxs-lookup"><span data-stu-id="80876-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="80876-144">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="80876-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="80876-145">Sağ **analitik** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="80876-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="80876-146">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test İstemcisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="80876-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="80876-147">WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörü > \Common7\IDE\ klasör.</span><span class="sxs-lookup"><span data-stu-id="80876-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="80876-148">Varsayılan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükleme klasörüdür C:\Program Files\Microsoft Visual Studio 10.0.</span><span class="sxs-lookup"><span data-stu-id="80876-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="80876-149">WCF test istemcisi seçin **Hizmet Ekle** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="80876-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="80876-150">Yerel Hizmet giriş kutusuna daha önce kopyaladığınız WSDL adresi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="80876-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="80876-151">WCF test istemcisi `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="80876-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="80876-152">Bu açılır `GetStockPrice` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80876-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="80876-153">İstek bir parametre kabul eder.</span><span class="sxs-lookup"><span data-stu-id="80876-153">The request accepts one parameter.</span></span> <span data-ttu-id="80876-154">Değeri kullanmak **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="80876-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="80876-155">Tıklatın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="80876-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="80876-156">Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**.</span><span class="sxs-lookup"><span data-stu-id="80876-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="80876-157">Sağ **analitik** seçip **yenileme**.</span><span class="sxs-lookup"><span data-stu-id="80876-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="80876-158">İş akışı olayları olay kimliği 100-199 aralıktır.</span><span class="sxs-lookup"><span data-stu-id="80876-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="80876-159">Olayları içeren ek açıklamalar, değişkenleri, bağımsız değişkenler ve olabilir özel izleme kayıtları Olay Görüntüleyicisi'ni görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="80876-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="80876-160">Olay Görüntüleyicisi'ni temizleme</span><span class="sxs-lookup"><span data-stu-id="80876-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="80876-161">Analitik kanal olay günlüğündeki Olay Görüntüleyicisi'ni aşağıdakileri yaparak temizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="80876-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="80876-162">(İsteğe bağlı) temizlemek için</span><span class="sxs-lookup"><span data-stu-id="80876-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="80876-163">Olay Görüntüleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="80876-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="80876-164">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="80876-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="80876-165">Sağ **analitik** seçip **günlüğü devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="80876-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="80876-166">Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.</span><span class="sxs-lookup"><span data-stu-id="80876-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="80876-167">Sağ **analitik** seçip **Günlüğü Temizle**.</span><span class="sxs-lookup"><span data-stu-id="80876-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="80876-168">Seçin **temizleyin** olayları temizlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="80876-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="80876-169">Bilinen bir sorun</span><span class="sxs-lookup"><span data-stu-id="80876-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80876-170">Olay burada ETW olayları çözecek başlatılamayabilir Görüntüleyicisi'nde bilinen bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="80876-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="80876-171">Aşağıdakine benzer bir hata iletisi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80876-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="80876-172">Bu hatayla karşılaşırsanız, tıklatın **yenileme** Eylemler bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="80876-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="80876-173">Olay şimdi düzgün bir şekilde kod çözme.</span><span class="sxs-lookup"><span data-stu-id="80876-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="80876-174">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="80876-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="80876-175">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="80876-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="80876-176">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="80876-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80876-177">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="80876-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="80876-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80876-178">See Also</span></span>  
 [<span data-ttu-id="80876-179">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="80876-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
