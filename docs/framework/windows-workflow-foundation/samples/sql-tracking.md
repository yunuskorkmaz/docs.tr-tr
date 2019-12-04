---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: c1bb4492695df3ff803dff893de24453d7c03dfb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715561"
---
# <a name="sql-tracking"></a><span data-ttu-id="18eaa-102">SQL İzleme</span><span class="sxs-lookup"><span data-stu-id="18eaa-102">SQL Tracking</span></span>
<span data-ttu-id="18eaa-103">Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısının nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="18eaa-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="18eaa-104">Windows Workflow Foundation (WF), bir iş akışı örneğinin yürütülmesi için görünürlük elde etmek üzere iş akışı izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="18eaa-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="18eaa-105">İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="18eaa-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="18eaa-106">İş akışı izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="18eaa-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="18eaa-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="18eaa-107">To use this sample</span></span>

1. <span data-ttu-id="18eaa-108">SQL Server 2008, SQL Server 2008 Express veya daha yeni bir sürümün yüklü olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="18eaa-109">Örnekle paketlenmiş betikler, yerel bilgisayarınızda bir SQL Express örneği kullanımını varsayar.</span><span class="sxs-lookup"><span data-stu-id="18eaa-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="18eaa-110">Farklı bir örneğiniz varsa, örneği çalıştırmadan önce lütfen veritabanıyla ilgili betikleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="18eaa-111">Betikler dizinindeki Trackingsetup. cmd ' i çalıştırarak SQL Server izleme veritabanını oluşturun (\Wf\basic\izlemedosyası \ KomutDosyaları).</span><span class="sxs-lookup"><span data-stu-id="18eaa-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="18eaa-112">Bu, TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18eaa-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="18eaa-113">Betik, SQL Express 'in varsayılan örneğinde veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18eaa-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="18eaa-114">Farklı bir veritabanı örneğine yüklemek isterseniz, Trackingsetup. cmd betiğini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="18eaa-115">Visual Studio 2010 ' de SqlTrackingSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="18eaa-116">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-116">Press CTRL+SHIFT+B to build the solution.</span></span>

5. <span data-ttu-id="18eaa-117">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-117">Press F5 to run the application.</span></span>

     <span data-ttu-id="18eaa-118">Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="18eaa-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="18eaa-119">Tarayıcıda, StockPriceService. xamlx ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="18eaa-120">Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18eaa-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="18eaa-121">Bu adresi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-121">Copy this address.</span></span>

     <span data-ttu-id="18eaa-122">Yerel hizmet WSDL adresine bir örnek `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="18eaa-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="18eaa-123">Dosya Gezgini 'ni kullanarak WCF test istemcisini (WcfTestClient. exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="18eaa-124">Microsoft Visual Studio 10.0 \ Common7\ıde dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18eaa-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>

9. <span data-ttu-id="18eaa-125">WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="18eaa-126">Yerel hizmet adresini metin kutusuna yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="18eaa-127">İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="18eaa-128">WCF test istemcisinde **GetStockPrice**' ye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="18eaa-129">Bu, tek bir parametre alan `GetStockPrice` işlemini açar, `Contoso` değeri yazın ve **çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="18eaa-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="18eaa-130">Yayınlanan izleme kayıtları bir SQL veritabanına yazılır.</span><span class="sxs-lookup"><span data-stu-id="18eaa-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="18eaa-131">İzleme kayıtlarını görüntülemek için, SQL Management Studio 'de TrackingSample veritabanını açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="18eaa-132">SQL Server Management Studio hakkında daha fazla bilgi için bkz. [SQL Server Management Studio tanıtımı](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="18eaa-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="18eaa-133">SQL Server 2008 Management Studio Express [buradan](https://go.microsoft.com/fwlink/?LinkId=180520)indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="18eaa-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="18eaa-134">Tablolarda bir SELECT sorgusu çalıştırmak, ilgili tablolarda depolanan izleme kayıtları içindeki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18eaa-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="18eaa-135">Örneği kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="18eaa-135">To uninstall the sample</span></span>

1. <span data-ttu-id="18eaa-136">Örnek dizininde theTrackingcleanup. cmd betiğini çalıştırın (\Wf\basic\izlemesqltracking).</span><span class="sxs-lookup"><span data-stu-id="18eaa-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>

    > [!NOTE]
    > <span data-ttu-id="18eaa-137">Trackingcleanup. cmd yerel bilgisayarınızdaki SQL Express veritabanını silmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="18eaa-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="18eaa-138">Başka bir SQL Server örneği kullanıyorsanız, Trackingcleanup. cmd ' yi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18eaa-139">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="18eaa-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="18eaa-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="18eaa-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="18eaa-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18eaa-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18eaa-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="18eaa-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18eaa-143">See also</span></span>

- [<span data-ttu-id="18eaa-144">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="18eaa-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
