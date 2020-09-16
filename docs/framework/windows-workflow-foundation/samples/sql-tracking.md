---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559356"
---
# <a name="sql-tracking"></a><span data-ttu-id="23895-102">SQL izleme</span><span class="sxs-lookup"><span data-stu-id="23895-102">SQL tracking</span></span>

<span data-ttu-id="23895-103">Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısının nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23895-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="23895-104">Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesi için görünürlük elde etmek üzere iş akışı izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="23895-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="23895-105">İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="23895-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="23895-106">İş akışı izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="23895-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="23895-107">Örneği kullanın</span><span class="sxs-lookup"><span data-stu-id="23895-107">Use the sample</span></span>

1. <span data-ttu-id="23895-108">SQL Server 2008, SQL Server 2008 Express veya daha yeni bir sürümün yüklü olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="23895-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="23895-109">Örnekle paketlenmiş betikler, yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayar.</span><span class="sxs-lookup"><span data-stu-id="23895-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="23895-110">Farklı bir örneğiniz varsa, örneği çalıştırmadan önce lütfen veritabanıyla ilgili betikleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="23895-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="23895-111">Betikler dizinindeki Trackingsetup. cmd ' i çalıştırarak SQL Server izleme veritabanını oluşturun (\Wf\basic\izlemedosyası \ KomutDosyaları).</span><span class="sxs-lookup"><span data-stu-id="23895-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="23895-112">Bu, TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23895-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="23895-113">Betik, SQL Express 'in varsayılan örneğinde veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23895-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="23895-114">Farklı bir veritabanı örneğine yüklemek isterseniz, Trackingsetup. cmd betiğini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="23895-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="23895-115">Visual Studio 2010 ' de SqlTrackingSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="23895-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="23895-116">**Ctrl** + **Shift** + Çözümü derlemek için CTRL SHIFT**B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="23895-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="23895-117">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="23895-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="23895-118">Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23895-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="23895-119">Tarayıcıda, StockPriceService. xamlx ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23895-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="23895-120">Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="23895-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="23895-121">Bu adresi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="23895-121">Copy this address.</span></span>

   <span data-ttu-id="23895-122">Yerel hizmet WSDL adresi örneği `http://localhost:65193/StockPriceService.xamlx?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="23895-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="23895-123">Dosya Gezgini 'ni kullanarak WCF test istemcisini (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="23895-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="23895-124">*Microsoft Visual Studio 10.0 \ Common7\IDE dizininde*bulunur.</span><span class="sxs-lookup"><span data-stu-id="23895-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="23895-125">WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="23895-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="23895-126">Yerel hizmet adresini metin kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="23895-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="23895-127">İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="23895-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="23895-128">WCF test istemcisinde **GetStockPrice**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23895-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="23895-129">Bu `GetStockPrice` işlem bir parametre alan işlemi açar, değeri yazın `Contoso` ve **çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23895-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="23895-130">Yayınlanan izleme kayıtları bir SQL veritabanına yazılır.</span><span class="sxs-lookup"><span data-stu-id="23895-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="23895-131">İzleme kayıtlarını görüntülemek için, SQL Management Studio 'de TrackingSample veritabanını açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="23895-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="23895-132">Tablolarda bir SELECT sorgusu çalıştırmak, ilgili tablolarda depolanan izleme kayıtları içindeki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="23895-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="23895-133">SQL Server Management Studio hakkında daha fazla bilgi için bkz. [SQL Server Management Studio tanıtımı](/sql/ssms/sql-server-management-studio-ssms).</span><span class="sxs-lookup"><span data-stu-id="23895-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="23895-134">SQL Server Management Studio [buradan](https://aka.ms/ssmsfullsetup)indirin.</span><span class="sxs-lookup"><span data-stu-id="23895-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="23895-135">Örneği kaldırma</span><span class="sxs-lookup"><span data-stu-id="23895-135">Uninstall the sample</span></span>

1. <span data-ttu-id="23895-136">Örnek dizininde theTrackingcleanup. cmd betiğini çalıştırın (*\Wf\basic\izlemesqltracking*).</span><span class="sxs-lookup"><span data-stu-id="23895-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="23895-137">Trackingcleanup. cmd yerel bilgisayarınızdaki SQL Express veritabanını silmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="23895-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="23895-138">Başka bir SQL Server örneği kullanıyorsanız, Trackingcleanup. cmd ' yi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="23895-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23895-139">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="23895-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="23895-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="23895-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="23895-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="23895-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23895-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="23895-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="23895-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23895-143">See also</span></span>

- <span data-ttu-id="23895-144">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="23895-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
