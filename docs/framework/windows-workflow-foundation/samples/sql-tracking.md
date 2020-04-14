---
title: SQL İzleme
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 72bfcaac2903b3e7fa5679422ad4feaa79e93211
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243186"
---
# <a name="sql-tracking"></a><span data-ttu-id="72e1a-102">SQL izleme</span><span class="sxs-lookup"><span data-stu-id="72e1a-102">SQL tracking</span></span>

<span data-ttu-id="72e1a-103">Bu örnek, izleme kayıtlarını bir SQL veritabanına yazan özel bir SQL izleme katılımcısı nasıl yazılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72e1a-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="72e1a-104">Windows İş Akışı Temeli (WF), iş akışı örneğinin yürütülmesinde görünürlük elde etmek için iş akışı izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="72e1a-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="72e1a-105">İzleme çalışma zamanı, iş akışının yürütülmesi sırasında iş akışı izleme kayıtlarını yayar.</span><span class="sxs-lookup"><span data-stu-id="72e1a-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="72e1a-106">İş akışı izleme hakkında daha fazla bilgi için [bkz.](../workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="72e1a-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="72e1a-107">Örneği kullanma</span><span class="sxs-lookup"><span data-stu-id="72e1a-107">Use the sample</span></span>

1. <span data-ttu-id="72e1a-108">SQL Server 2008, SQL Server 2008 Express veya yeni yüklü olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="72e1a-109">Örnekle birlikte paketlenmiş komut dosyaları, yerel bilgisayarınızda bir SQL Express örneğinin kullanıldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="72e1a-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="72e1a-110">Farklı bir örneğinvarsa, lütfen örneği çalıştırmadan önce veritabanıyla ilgili komut dosyalarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="72e1a-111">Komut dosyaları dizininde Trackingsetup.cmd (\WF\Basic\Tracking\SqlTracking\CS\Scripts) çalıştırarak SQL Server izleme veritabanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72e1a-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="72e1a-112">Bu, TrackingSample adlı bir veritabanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72e1a-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="72e1a-113">Komut dosyası, SQL Express'in varsayılan örneğinde veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72e1a-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="72e1a-114">Farklı bir veritabanı örneğine yüklemek istiyorsanız, Trackingsetup.cmd komut dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="72e1a-115">Visual Studio 2010'da SqlTrackingSample.sln'yi açın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="72e1a-116">Çözümü oluşturmak için **Ctrl**+**Shift**+**B** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="72e1a-117">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="72e1a-118">Tarayıcı penceresi açılır ve uygulamanın dizin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72e1a-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="72e1a-119">Tarayıcıda StockPriceService.xamlx'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="72e1a-120">Tarayıcı, yerel hizmet WSDL adresini içeren StockPriceService sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72e1a-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="72e1a-121">Bu adresi kopyala.</span><span class="sxs-lookup"><span data-stu-id="72e1a-121">Copy this address.</span></span>

   <span data-ttu-id="72e1a-122">Yerel hizmet WSDL adresibir `http://localhost:65193/StockPriceService.xamlx?wsdl`örnektir.</span><span class="sxs-lookup"><span data-stu-id="72e1a-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="72e1a-123">Dosya Gezgini'ni kullanarak WCF test istemcisini (WcfTestClient.exe) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="72e1a-124">*Microsoft Visual Studio 10.0\Common7\IDE dizininde*yer alır.</span><span class="sxs-lookup"><span data-stu-id="72e1a-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="72e1a-125">WCF test istemcisinde **Dosya** menüsüne tıklayın ve **Hizmet Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="72e1a-126">Yerel servis adresini textbox'a yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="72e1a-127">İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="72e1a-128">WCF test istemcisinde **GetStockPrice'ı**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="72e1a-129">Bu, `GetStockPrice` bir parametre alan işlemi açar, `Contoso` değeri yazın ve **Çağır'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="72e1a-130">Yayılan izleme kayıtları bir SQL veritabanına yazılır.</span><span class="sxs-lookup"><span data-stu-id="72e1a-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="72e1a-131">İzleme kayıtlarını görüntülemek için SQL Management Studio'da TrackingSample veritabanını açın ve tablolara gidin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="72e1a-132">Tablolarda seçili bir sorgunun çalıştırılsa, ilgili tablolarda depolanan izleme kayıtlarıiçindeki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72e1a-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="72e1a-133">SQL Server Management Studio hakkında daha fazla bilgi için SQL [Server Management Studio tanıtımına](/sql/ssms/sql-server-management-studio-ssms)bakın.</span><span class="sxs-lookup"><span data-stu-id="72e1a-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="72e1a-134">SQL Server Management [Studio'u buradan](https://aka.ms/ssmsfullsetup)indirin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="72e1a-135">Örneği kaldırma</span><span class="sxs-lookup"><span data-stu-id="72e1a-135">Uninstall the sample</span></span>

1. <span data-ttu-id="72e1a-136">Örnek dizindeki Trackingcleanup.cmd komut dosyasını çalıştırın (*\WF\Basic\Tracking\SqlTracking*).</span><span class="sxs-lookup"><span data-stu-id="72e1a-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="72e1a-137">Trackingcleanup.cmd, yerel bilgisayarınız SQL Express'teki veritabanını silmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="72e1a-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="72e1a-138">Başka bir SQL sunucu örneği kullanıyorsanız, Trackingcleanup.cmd'yi düzenlemeyi edin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72e1a-139">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="72e1a-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="72e1a-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="72e1a-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="72e1a-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72e1a-142">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="72e1a-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="72e1a-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e1a-143">See also</span></span>

- <span data-ttu-id="72e1a-144">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="72e1a-144">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
