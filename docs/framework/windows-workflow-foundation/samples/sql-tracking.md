---
title: SQL izleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bd8fbe1a29793778d93eeca64b185079d706f3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-tracking"></a><span data-ttu-id="a798d-102">SQL izleme</span><span class="sxs-lookup"><span data-stu-id="a798d-102">SQL Tracking</span></span>
<span data-ttu-id="a798d-103">Bu örnek, bir özel SQL izleme katılımcı yazma gösterilmiştir, bir SQL veritabanına izleme kayıtları yazar.</span><span class="sxs-lookup"><span data-stu-id="a798d-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="a798d-104">İş akışı iş akışı örneğini yürütmeyi görünürlük elde etmek için izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="a798d-104"> provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="a798d-105">İzleme çalışma zamanı iş akışı iş akışı yürütme sırasında kayıtları izleme yayar.</span><span class="sxs-lookup"><span data-stu-id="a798d-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a798d-106">İzleme, iş akışı bkz [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="a798d-106"> workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a798d-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a798d-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="a798d-108">SQL Server 2008, SQL Server 2008 Express veya daha yeni yüklü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a798d-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="a798d-109">SQL Express örneği, yerel bilgisayarınızda kullanımını örnekle paketlenmiş betikleri varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a798d-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="a798d-110">Veritabanı ile ilgili betikleri örneği çalıştırmadan önce lütfen değiştirin farklı bir örnek varsa.</span><span class="sxs-lookup"><span data-stu-id="a798d-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="a798d-111">SQL Server veritabanı izleme betikleri dizininde (\WF\Basic\Tracking\SqlTracking\CS\Scripts) Trackingsetup.cmd çalıştırarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a798d-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="a798d-112">Bu TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a798d-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a798d-113">Komut dosyası, SQL Express varsayılan örneğinde veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a798d-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="a798d-114">Farklı bir veritabanı örneği üzerinde yüklemek istiyorsanız, Trackingsetup.cmd betiğini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="a798d-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="a798d-115">İçinde SqlTrackingSample.sln açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a798d-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="a798d-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a798d-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="a798d-117">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a798d-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="a798d-118">Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a798d-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="a798d-119">Tarayıcıda StockPriceService.xamlx'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a798d-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="a798d-120">Tarayıcı yerel hizmet WSDL adresi içeren StockPriceService sayfa görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a798d-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="a798d-121">Bu adresini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a798d-121">Copy this address.</span></span>  
  
     <span data-ttu-id="a798d-122">Yerel Hizmet WSDL adresi http://localhost:65193/StockPriceService.xamlx?wsdl örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a798d-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="a798d-123">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test istemcisi (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a798d-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="a798d-124">Microsoft Visual Studio 10.0\Common7\IDE dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a798d-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="a798d-125">WCF test İstemcisi'ni tıklatın **dosya** menü ve select **Hizmet Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a798d-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="a798d-126">Yerel hizmet adresi metin kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a798d-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="a798d-127">Tıklatın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="a798d-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="a798d-128">WCF test istemcisi çift tıklayarak **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="a798d-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="a798d-129">Bu açılır `GetStockPrice` bir parametre değeri türü alan işlemi `Contoso` tıklatıp **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="a798d-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="a798d-130">Verilmiş izleme kayıtları bir SQL veritabanına yazılır.</span><span class="sxs-lookup"><span data-stu-id="a798d-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="a798d-131">İzleme kayıtları görüntülemek için SQL Management Studio'da TrackingSample veritabanı açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="a798d-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a798d-132">SQL Server Management Studio bkz [SQL Server Management Studio Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="a798d-132"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="a798d-133">SQL Server 2008 Management Studio Express indirilebilir [burada](http://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="a798d-133">SQL Server 2008 Management Studio Express can be downloaded [here](http://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="a798d-134">Tabloları seçme sorgusu çalıştıran ilgili tablolarda depolanan izleme kayıtları içinde verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a798d-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="a798d-135">Örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a798d-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="a798d-136">TheTrackingcleanup.cmd betik örnek dizininde (\WF\Basic\Tracking\SqlTracking) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a798d-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a798d-137">Yerel bilgisayarınızda SQL Express veritabanını silmek Trackingcleanup.cmd çalışır.</span><span class="sxs-lookup"><span data-stu-id="a798d-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="a798d-138">Başka bir SQL server örneği kullanıyorsanız, Trackingcleanup.cmd düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="a798d-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a798d-139">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="a798d-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a798d-140">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a798d-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a798d-141">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a798d-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a798d-142">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a798d-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="a798d-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a798d-143">See Also</span></span>  
 [<span data-ttu-id="a798d-144">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="a798d-144">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
