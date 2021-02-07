---
description: 'Daha fazla bilgi edinin: SQL izleme'
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 2b336839b9c63c0b7bde8b6451add00cb353fec6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741750"
---
# <a name="sql-tracking"></a><span data-ttu-id="e4edd-103">SQL izleme</span><span class="sxs-lookup"><span data-stu-id="e4edd-103">SQL tracking</span></span>

<span data-ttu-id="e4edd-104">Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısının nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4edd-104">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="e4edd-105">Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesi için görünürlük elde etmek üzere iş akışı izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4edd-105">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="e4edd-106">İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="e4edd-106">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="e4edd-107">İş akışı izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="e4edd-107">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="e4edd-108">Örneği kullanın</span><span class="sxs-lookup"><span data-stu-id="e4edd-108">Use the sample</span></span>

1. <span data-ttu-id="e4edd-109">SQL Server 2008, SQL Server 2008 Express veya daha yeni bir sürümün yüklü olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-109">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="e4edd-110">Örnekle paketlenmiş betikler, yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayar.</span><span class="sxs-lookup"><span data-stu-id="e4edd-110">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="e4edd-111">Farklı bir örneğiniz varsa, örneği çalıştırmadan önce lütfen veritabanıyla ilgili betikleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-111">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="e4edd-112">Betikler dizinindeki Trackingsetup. cmd ' i çalıştırarak SQL Server izleme veritabanını oluşturun (\Wf\basic\izlemedosyası \ KomutDosyaları).</span><span class="sxs-lookup"><span data-stu-id="e4edd-112">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="e4edd-113">Bu, TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4edd-113">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e4edd-114">Betik, SQL Express 'in varsayılan örneğinde veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4edd-114">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="e4edd-115">Farklı bir veritabanı örneğine yüklemek isterseniz, Trackingsetup. cmd betiğini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-115">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="e4edd-116">Visual Studio 2010 ' de SqlTrackingSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-116">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="e4edd-117"> +  + Çözümü derlemek için CTRL SHIFT **B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-117">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="e4edd-118">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-118">Press **F5** to run the application.</span></span>

   <span data-ttu-id="e4edd-119">Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4edd-119">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="e4edd-120">Tarayıcıda, StockPriceService. xamlx ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-120">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="e4edd-121">Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e4edd-121">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="e4edd-122">Bu adresi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-122">Copy this address.</span></span>

   <span data-ttu-id="e4edd-123">Yerel hizmet WSDL adresi örneği `http://localhost:65193/StockPriceService.xamlx?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="e4edd-123">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="e4edd-124">Dosya Gezgini 'ni kullanarak WCF test istemcisini (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-124">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="e4edd-125">*Microsoft Visual Studio 10.0 \ Common7\IDE dizininde* bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4edd-125">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="e4edd-126">WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-126">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="e4edd-127">Yerel hizmet adresini metin kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-127">Paste the local service address in the textbox.</span></span> <span data-ttu-id="e4edd-128">İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-128">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="e4edd-129">WCF test istemcisinde **GetStockPrice**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-129">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="e4edd-130">Bu `GetStockPrice` işlem bir parametre alan işlemi açar, değeri yazın `Contoso` ve **çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4edd-130">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="e4edd-131">Yayınlanan izleme kayıtları bir SQL veritabanına yazılır.</span><span class="sxs-lookup"><span data-stu-id="e4edd-131">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="e4edd-132">İzleme kayıtlarını görüntülemek için, SQL Management Studio 'de TrackingSample veritabanını açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-132">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="e4edd-133">Tablolarda bir SELECT sorgusu çalıştırmak, ilgili tablolarda depolanan izleme kayıtları içindeki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e4edd-133">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="e4edd-134">SQL Server Management Studio hakkında daha fazla bilgi için bkz. [SQL Server Management Studio tanıtımı](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="e4edd-134">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="e4edd-135">SQL Server Management Studio [buradan](https://aka.ms/ssmsfullsetup)indirin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-135">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="e4edd-136">Örneği kaldırma</span><span class="sxs-lookup"><span data-stu-id="e4edd-136">Uninstall the sample</span></span>

1. <span data-ttu-id="e4edd-137">Örnek dizininde theTrackingcleanup. cmd betiğini çalıştırın (*\Wf\basic\izlemesqltracking*).</span><span class="sxs-lookup"><span data-stu-id="e4edd-137">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e4edd-138">Trackingcleanup. cmd yerel bilgisayarınızdaki SQL Express veritabanını silmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="e4edd-138">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="e4edd-139">Başka bir SQL Server örneği kullanıyorsanız, Trackingcleanup. cmd ' yi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-139">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4edd-140">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4edd-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e4edd-141">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e4edd-141">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e4edd-142">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e4edd-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4edd-143">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4edd-143">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="e4edd-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4edd-144">See also</span></span>

- <span data-ttu-id="e4edd-145">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e4edd-145">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
