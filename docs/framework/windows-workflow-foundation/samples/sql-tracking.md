---
title: SQL izleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: e2cb86a92e075d9117f2fe208f2044d4bc30dac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710023"
---
# <a name="sql-tracking"></a><span data-ttu-id="1ee23-102">SQL izleme</span><span class="sxs-lookup"><span data-stu-id="1ee23-102">SQL Tracking</span></span>
<span data-ttu-id="1ee23-103">Bu örnek nasıl yazılacağını özel SQL izleme katılımcı gösterir, bu bir SQL veritabanı'na izleme kayıtları yazar.</span><span class="sxs-lookup"><span data-stu-id="1ee23-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="1ee23-104">Windows Workflow Foundation (WF) iş akışı yürütme iş akışı örneğinin görünürlük elde etmek için izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ee23-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="1ee23-105">İzleme çalışma zamanı iş akışı iş akışı yürütülürken kayıtları izleme yayar.</span><span class="sxs-lookup"><span data-stu-id="1ee23-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="1ee23-106">İş akışı izleme hakkında daha fazla bilgi için bkz: [takip ve izleme iş akışı](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="1ee23-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="1ee23-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1ee23-107">To use this sample</span></span>

1.  <span data-ttu-id="1ee23-108">Bilgisayarınızda SQL Server 2008, SQL Server 2008 Express veya üzerinin yüklü doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="1ee23-109">Örnek ile paketlenmiş betikleri yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayılır.</span><span class="sxs-lookup"><span data-stu-id="1ee23-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="1ee23-110">Lütfen veritabanı ile ilgili betikleri örneği çalıştırmadan önce değiştirin. farklı bir örneğine sahipseniz.</span><span class="sxs-lookup"><span data-stu-id="1ee23-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2.  <span data-ttu-id="1ee23-111">SQL Server veritabanı izleme betikleri dizininde (\WF\Basic\Tracking\SqlTracking\CS\Scripts) Trackingsetup.cmd çalıştırarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ee23-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="1ee23-112">Bu TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ee23-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="1ee23-113">Betik, SQL Express varsayılan örnekte veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ee23-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="1ee23-114">Farklı bir veritabanı örneği üzerinde yüklemek istiyorsanız, Trackingsetup.cmd betiği düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee23-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="1ee23-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="1ee23-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>  
  
4.  <span data-ttu-id="1ee23-116">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="1ee23-117">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="1ee23-118">Tarayıcı penceresi açılır ve dizin için uygulama listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1ee23-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="1ee23-119">Tarayıcıda StockPriceService.xamlx tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="1ee23-120">Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ee23-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="1ee23-121">Bu adresini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-121">Copy this address.</span></span>  
  
     <span data-ttu-id="1ee23-122">Yerel Hizmet WSDL adresi örneğidir `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="1ee23-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>  
  
8.  <span data-ttu-id="1ee23-123">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], WCF test istemcisi (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="1ee23-124">Bunu yapmak için Microsoft Visual Studio 10.0\Common7\IDE dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ee23-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="1ee23-125">WCF test İstemcisi'nde tıklayın **dosya** menü ve select **Hizmet Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1ee23-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="1ee23-126">Yerel hizmet adresi metin kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="1ee23-127">Tıklayın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="1ee23-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="1ee23-128">WCF test İstemcisi'nde çift tıklayarak **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="1ee23-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="1ee23-129">Bu açılır `GetStockPrice` bir parametre, değer alan işlemi `Contoso` tıklatıp **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="1ee23-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="1ee23-130">Bir SQL veritabanına yayılan izleme kayıtları yazılır.</span><span class="sxs-lookup"><span data-stu-id="1ee23-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="1ee23-131">İzleme kayıtları görüntülemek için SQL Management Studio'da TrackingSample veritabanını açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="1ee23-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="1ee23-132">SQL Server Management Studio hakkında daha fazla bilgi için bkz: [Karşınızda SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="1ee23-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="1ee23-133">SQL Server 2008 Management Studio Express'i indirilebilir [burada](https://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="1ee23-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="1ee23-134">Tabloları seçme sorgusu çalıştıran izleme kayıtları ilgili tablolarında depolanan verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ee23-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="1ee23-135">Örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="1ee23-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="1ee23-136">Örnek dizini (\WF\Basic\Tracking\SqlTracking) theTrackingcleanup.cmd betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ee23-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ee23-137">Trackingcleanup.cmd, yerel bilgisayarınıza SQL Express veritabanında silmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="1ee23-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="1ee23-138">Başka bir SQL server örneği kullanıyorsanız, Trackingcleanup.cmd düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee23-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="1ee23-139">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1ee23-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1ee23-140">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee23-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1ee23-141">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1ee23-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ee23-142">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ee23-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="1ee23-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ee23-143">See also</span></span>
- [<span data-ttu-id="1ee23-144">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="1ee23-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
