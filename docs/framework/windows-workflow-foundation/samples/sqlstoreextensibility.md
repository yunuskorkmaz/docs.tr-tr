---
title: SQLStoreExtensibility
ms.date: 03/30/2017
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
ms.openlocfilehash: 37c83a9c1062fe074e41ec5db211fd513355c045
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518492"
---
# <a name="sqlstoreextensibility"></a><span data-ttu-id="6c5fa-102">SQLStoreExtensibility</span><span class="sxs-lookup"><span data-stu-id="6c5fa-102">SQLStoreExtensibility</span></span>
<span data-ttu-id="6c5fa-103">Bu örnek kullanım ve SQL iş akışı örneği deposundaki yükseltilen özellikleri yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-103">This sample demonstrates the use and configuration of promoted properties in the SQL workflow instance store.</span></span> <span data-ttu-id="6c5fa-104">SQL iş akışı örneği deposuna bir SQL tabanlı bir örnek deposuna uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="6c5fa-105">Durumu kaydedin ve durumunu bir SQL Server veya SQL Server Express veritabanı gelen ve giden yüklemek bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-105">It allows an instance to save its state and load its state to and from a SQL Server or SQL Server Express database.</span></span> <span data-ttu-id="6c5fa-106">Depolama genişletilebilirlik özelliği örneği deposunda saklanır özelliklerini tanımlamak kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-106">The store extensibility feature allows the user to define properties that are stored in the instance store.</span></span> <span data-ttu-id="6c5fa-107">Bu özellikler için sorgu kullanıcıya veren bir yükseltilen özellikleri görünümü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-107">These properties are displayed in a promoted properties view that allows the user to query for them.</span></span>  
  
 <span data-ttu-id="6c5fa-108">Bu örnek bir sayım hizmeti uygulayan bir iş akışı oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-108">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="6c5fa-109">Hizmetin başlangıç yöntemi çağrıldıktan sonra hizmet 29 için 0'dan sayar.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-109">Once the service's start method is invoked, the service counts from 0 to 29.</span></span> <span data-ttu-id="6c5fa-110">2 saniyede sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-110">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="6c5fa-111">Her sayısı sonra iş akışı devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-111">After each count, the workflow persists.</span></span> <span data-ttu-id="6c5fa-112">Geçerli sayaç değeri örnek deposunda yükseltilen bir özellik olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-112">The current counter value is stored in the instance store as a promoted property.</span></span>  
  
 <span data-ttu-id="6c5fa-113">Sayım iş akışını bir iş akışı hizmeti ana bilgisayar tarafından kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-113">The Counting Workflow is self-hosted by a Workflow Service Host.</span></span> <span data-ttu-id="6c5fa-114">Programın `Main` yöntemi aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6c5fa-114">The program's `Main` method performs the following actions:</span></span>  
  
-   <span data-ttu-id="6c5fa-115">Sayım iş akışı barındıran ve altında sayım iş akışı ulaşılabilen uç noktalarını tanımlayan iş akışı hizmeti konak örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-115">Creates an instance of the Workflow Service Host that hosts the Counting Workflow and defines the endpoints under which the Counting Workflow can be reached.</span></span>  
  
-   <span data-ttu-id="6c5fa-116">SQL iş akışı örneği deposunu yapılandırmak için kullanılan bir SQL iş akışı örneği deposu davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-116">Defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="6c5fa-117">Mağaza işlemek için talimat `CountStatus` yükseltilen bir özellik olarak.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-117">The store is instructed to treat `CountStatus` as a promoted property.</span></span>  
  
-   <span data-ttu-id="6c5fa-118">Sayım bir iş akışı başlatma yöntemini çağıran bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-118">Creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="6c5fa-119">Program başladıktan sonra sayaç sayım otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-119">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="6c5fa-120">Örneği yüklemek ve SQL iş akışı örneği deposunu yapılandırmak için birkaç saniye sürebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-120">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span>  
  
 <span data-ttu-id="6c5fa-121">Sayaç değeri özel bir özellik olarak yükseltmek için aşağıdaki adımlar izlenmelidir:</span><span class="sxs-lookup"><span data-stu-id="6c5fa-121">To promote the counter value as a custom property, the following steps must be taken:</span></span>  
  
1.  <span data-ttu-id="6c5fa-122">Sınıf `CounterStatus` türünün bir örneği uzantısını tanımlayan <xref:System.Activities.Persistence.PersistenceParticipant>, etkinlikler tarafından durumu değişkenleri sağlamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-122">The class `CounterStatus` defines an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span> <span data-ttu-id="6c5fa-123">`Count` bir salt değer olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-123">`Count` is defined as a write-only value.</span></span> <span data-ttu-id="6c5fa-124">Bir iş akışı örneği Kalıcılık noktasına geldiğinde, örnek uzantısı kaydeder `Count` özelliği Kalıcılık veri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-124">When a workflow instance comes to a persistence point, the instance extension saves the `Count` property into the persistence data collection.</span></span>  
  
2.  <span data-ttu-id="6c5fa-125">Örnek deposu, yeni bir özellik oluştururken `CountStatus`, aracılığıyla tanımlanan `store.Promote()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-125">When creating the instance store, a new property, `CountStatus`, is defined through the `store.Promote()` method.</span></span>  
  
3.  <span data-ttu-id="6c5fa-126">İş akışı `SaveCounter` Etkinlik geçerli sayaç değeri atar `Count` durum alanı.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-126">The workflow's `SaveCounter` activity assigns the current counter value to the `Count` status field.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="6c5fa-127">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6c5fa-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="6c5fa-128">Örnek deposu veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-128">Create the instance store database.</span></span>  
  
    1.  <span data-ttu-id="6c5fa-129">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="6c5fa-130">Örnek dizine (\WF\Basic\Persistence\SqlStoreExtensibility\CS) gidin ve CreateInstanceStore.cmd çalıştırmadan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-130">Navigate to the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility\CS) and run CreateInstanceStore.cmd in the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="6c5fa-131">CreateInstanceStore.cmd komut dosyası, SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma dener.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-131">The CreateInstanceStore.cmd script attempts to create the database on the default instance of SQL Server 2008 Express.</span></span> <span data-ttu-id="6c5fa-132">Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-132">If you want to install the database on a different instance, modify the script to do so.</span></span>  
  
2.  <span data-ttu-id="6c5fa-133">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] SqlStoreExtensibility.sln çözüm yük ve CTRL + SHIFT + B tuşuna basarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-133">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and load the SqlStoreExtensibility.sln solution and build it by pressing CTRL+SHIFT+B.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="6c5fa-134">Varsayılan olmayan SQL Server örneğinde veritabanı yüklü değilse, bağlantı dizesi çözümü oluşturma önce kodda güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-134">If you installed the database on a non-default instance of SQL Server, update the connection string in the code prior to building the solution.</span></span>  
  
3.  <span data-ttu-id="6c5fa-135">Örnek, projenin bin dizinine (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) giderek yönetici ayrıcalıklarıyla çalıştırın [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], SqlStoreExtensibility.exe sağ tıklayıp seçerek **farklı çalıştır Yönetici**.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-135">Run the sample with administrator privileges by navigating to the project’s bin directory (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], right-clicking SqlStoreExtensibility.exe and selecting **Run as Administrator**.</span></span>  
  
### <a name="to-verify-the-sample-is-working-correctly"></a><span data-ttu-id="6c5fa-136">Örnek doğru şekilde çalıştığını doğrulama</span><span class="sxs-lookup"><span data-stu-id="6c5fa-136">To verify the sample is working correctly</span></span>  
  
1.  <span data-ttu-id="6c5fa-137">Seçerek örneği tablosunun içeriğini görüntülemek için SQL Server Management Studio kullanın **veritabanları**, **InstanceStore**ve ardından  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** nesne Gezgini'nde sağ **System.ServiceModel.Activities.DurableInstancing.InstanceTable** ve seçin **İlk 1000 satırı Seç**.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-137">Use SQL Server Management Studio to view the contents of the instance table by selecting **Databases**, **InstanceStore**, and then **System.ServiceModel.Activities.DurableInstancing.InstanceTable** in the Object Explorer, right-click **System.ServiceModel.Activities.DurableInstancing.InstanceTable** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="6c5fa-138">SQL Server Management Studio hakkında daha fazla bilgi için bkz: [SQL Server Management Studio Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=165645)</span><span class="sxs-lookup"><span data-stu-id="6c5fa-138">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span></span>  
  
2.  <span data-ttu-id="6c5fa-139">Listelenen iş akışı örnekleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-139">Observe the workflow instances listed.</span></span>  
  
3.  <span data-ttu-id="6c5fa-140">İçinde bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan QueryInstanceStore.cmd komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-140">In a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run the QueryInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
4.  <span data-ttu-id="6c5fa-141">Sayaç değeri görüntülenen altındaki gözlemlemek **CountStatus**.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-141">Observe the counter value displayed under **CountStatus**.</span></span>  
  
5.  <span data-ttu-id="6c5fa-142">Birkaç kez komut dosyasını çalıştırmak görmek için **CountStats** değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-142">Run the script a few times to see the **CountStats** value change.</span></span>  
  
6.  <span data-ttu-id="6c5fa-143">İş akışı sonlandırmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-143">Press ENTER to terminate the workflow application.</span></span>  
  
### <a name="to-uninstall-the-sample"></a><span data-ttu-id="6c5fa-144">Örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="6c5fa-144">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="6c5fa-145">Örnek deposu veritabanı (\WF\Basic\Persistence\SqlStoreExtensibility) örnek dizininde bulunan RemoveInstanceStore.cmd komut dosyası çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-145">Remove the instance store database by running the RemoveInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c5fa-146">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-146">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c5fa-147">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-147">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c5fa-148">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c5fa-149">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-149">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a><span data-ttu-id="6c5fa-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c5fa-150">See Also</span></span>  
 [<span data-ttu-id="6c5fa-151">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="6c5fa-151">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="6c5fa-152">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6c5fa-152">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="6c5fa-153">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="6c5fa-153">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
