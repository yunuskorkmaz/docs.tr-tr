---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 10a2c568f14c3f3c1818fd8b3240279b798777b8
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063807"
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="7cae6-102">Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7cae6-102">Creating a Long-running Workflow Service</span></span>
<span data-ttu-id="7cae6-103">Bu konuda, uzun süre çalışan iş akışı hizmeti oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7cae6-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="7cae6-104">İş akışı hizmetleri uzun süre çalışan uzun süreler için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cae6-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="7cae6-105">İş akışını belirli bir noktada bazı ek bilgiler için bekleyen boşta gidebilir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="7cae6-106">Bu meydana geldiğinde iş akışını bir SQL veritabanı'na kalıcı ve bellekten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="7cae6-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="7cae6-107">Ek bilgilerin kullanıma sunulduğunda iş akışı örneği belleğe geri yüklenir ve yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="7cae6-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="7cae6-108">Bu senaryoda, oldukça basitleştirilmiş bir sipariş sistemi uyguluyor.</span><span class="sxs-lookup"><span data-stu-id="7cae6-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="7cae6-109">İstemci sırasını başlatmak için iş akışı hizmeti için bir Başlangıç iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="7cae6-110">İstemciye bir sipariş kimliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cae6-110">It returns an order ID to the client.</span></span> <span data-ttu-id="7cae6-111">Bu noktada iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna girer ve bir SQL Server veritabanına kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="7cae6-112">İstemci bir öğe sıralamak için sonraki iletiyi gönderdiğinde, iş akışı hizmeti belleğe geri yüklenir ve sırasını işlemeyi tamamladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="7cae6-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="7cae6-113">Kod örneğinde öğe sırasını eklenmiş belirten bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cae6-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="7cae6-114">Kod örneği, teknoloji, ancak bunun yerine uzun süre çalışan iş akışı hizmetleri gösteren basit örnek bir gerçek dünya uygulaması olarak hazırlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="7cae6-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="7cae6-115">Bu konu Visual Studio 2012 projeler ve çözümler oluşturulacağını bildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="7cae6-115">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7cae6-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7cae6-116">Prerequisites</span></span>
 <span data-ttu-id="7cae6-117">Bu anlatımda kullanmak için aşağıdaki yazılımlar olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7cae6-117">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="7cae6-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="7cae6-118">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="7cae6-119">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="7cae6-119">Visual Studio 2012</span></span>

3. <span data-ttu-id="7cae6-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cae6-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="7cae6-121">WCF ve Visual Studio 2012 ile ilgili bilgi sahibi olduğunuz ve proje/çözüm oluşturmayı biliyorsanız.</span><span class="sxs-lookup"><span data-stu-id="7cae6-121">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

### <a name="to-setup-the-sql-database"></a><span data-ttu-id="7cae6-122">SQL veritabanı kurulumu için</span><span class="sxs-lookup"><span data-stu-id="7cae6-122">To Setup the SQL Database</span></span>

1. <span data-ttu-id="7cae6-123">Kalıcı için iş akışı hizmet örneklerine yönelik, Microsoft SQL Server'ın yüklü olması gerekir ve kalıcı iş akışı örnekleri depolamak için bir veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-123">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="7cae6-124">Microsoft SQL Management Studio tıklayarak çalıştırın **Başlat** düğmesi, seçerek **tüm programlar**, **Microsoft SQL Server 2008**, ve **Microsoft SQL Management Studio'yu**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-124">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="7cae6-125">Tıklayın **Connect** için SQL Server örneği oturum açma düğmesi</span><span class="sxs-lookup"><span data-stu-id="7cae6-125">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="7cae6-126">Sağ tıklayın **veritabanları** ağaç görünümü seçip **yeni veritabanı...**</span><span class="sxs-lookup"><span data-stu-id="7cae6-126">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="7cae6-127">adlı yeni bir veritabanı oluşturmak için `SQLPersistenceStore`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-127">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="7cae6-128">Gerekli veritabanı şemaları ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema.sql komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-128">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="7cae6-129">SQLPersistenceStore veritabanında gerekli veritabanı mantığı oluşturma ayarlanacak C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreLogic.sql komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-129">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="7cae6-130">İş akışı hizmeti barındırılan Web oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7cae6-130">To Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="7cae6-131">Boş bir Visual Studio 2012 çözümü oluşturmak için adlandırın `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-131">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="7cae6-132">Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `OrderService` çözüm.</span><span class="sxs-lookup"><span data-stu-id="7cae6-132">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="7cae6-133">Proje Özellikleri iletişim kutusunda, seçmek **Web** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="7cae6-133">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="7cae6-134">Altında **başlatma eylemi** seçin **belirli sayfa** belirtin `Service1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-134">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

         <span data-ttu-id="7cae6-135">![İş akışı hizmeti proje Web özellikleri](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "- belirli bir sayfaya seçeneği barındırılan web iş akışı hizmeti oluşturma")</span><span class="sxs-lookup"><span data-stu-id="7cae6-135">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="7cae6-136">Altında **sunucuları** seçin **yerel IIS Web sunucusunu kullan**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-136">Under **Servers** select **Use Local IIS Web server**.</span></span>

         <span data-ttu-id="7cae6-137">![Yerel Web sunucusu ayarlarını](./media/creating-a-long-running-workflow-service/use-local-web-server.png "- yerel IIS Web sunucusu kullan seçeneği barındırılan web iş akışı hizmeti oluşturma")</span><span class="sxs-lookup"><span data-stu-id="7cae6-137">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        >  <span data-ttu-id="7cae6-138">Bu ayar yapmak için Yönetici modunda Visual Studio 2012 çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-138">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

         <span data-ttu-id="7cae6-139">Bu iki adımı, IIS tarafından barındırılan iş akışı hizmeti projenin yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-139">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="7cae6-140">Açık `Service1.xamlx` açık ve mevcut değil ise **ReceiveRequest** ve **SendResponse** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="7cae6-140">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="7cae6-141">Seçin **sıralı hizmeti** etkinliği ve tıklatın **değişkenleri** bağlamak ve aşağıdaki çizimde gösterilen değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7cae6-141">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="7cae6-142">Bunun yapılması kullanılacak olan bazı değişkenler daha sonra iş akışı hizmetinde ekler.</span><span class="sxs-lookup"><span data-stu-id="7cae6-142">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="7cae6-143">Değişken türü açılan menü CorrelationHandle değilse seçin **vyhledat Typy** açılır listeden.</span><span class="sxs-lookup"><span data-stu-id="7cae6-143">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="7cae6-144">Türü içinde CorrelationHandle **tür adı** kutusunda, liste kutusundan CorrelationHandle seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-144">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

     <span data-ttu-id="7cae6-145">![Değişkenleri ekleyin](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "değişkenleri için sıralı hizmeti etkinliği ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-145">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="7cae6-146">Sürükle ve bırak bir **ReceiveAndSendReply** etkinlik şablona **sıralı hizmeti** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7cae6-146">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="7cae6-147">Bu etkinlikler kümesi, bir istemciden bir ileti alırsınız ve bir yanıtı geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-147">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="7cae6-148">Seçin **alma** etkinliği ve özellikleri aşağıdaki çizimde vurgulanan kümesi.</span><span class="sxs-lookup"><span data-stu-id="7cae6-148">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

         <span data-ttu-id="7cae6-149">![Etkinlik özellikleri alma](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Receive etkinlik özelliklerini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-149">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

         <span data-ttu-id="7cae6-150">DisplayName özelliği için Receive etkinlik Tasarımcısı'nda görüntülenen adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7cae6-150">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="7cae6-151">ServiceContractName ve OperationName özellikleri hizmet sözleşmesini ve Al etkinliği tarafından uygulanan işlem adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="7cae6-151">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="7cae6-152">Sözleşme iş akışı hizmetleri nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="7cae6-152">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="7cae6-153">Tıklayın **tanımlayın...**  bağlantısını **ReceiveStartOrder** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-153">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="7cae6-154">Dikkat **parametreleri** radyo düğmesi seçilirse, adlı bir parametre `p_customerName` bağlı `customerName` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7cae6-154">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="7cae6-155">Bu yapılandırır **alma** bazı veri almak ve yerel değişkenlere, veri bağlama için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7cae6-155">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

         <span data-ttu-id="7cae6-156">![Receive etkinlik tarafından alınan veri ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Al etkinliği tarafından alınan veriler için özelliklerini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-156">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="7cae6-157">Seçin **SendReplyToReceive** etkinliği ve aşağıdaki çizimde gösterilen vurgulanan özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-157">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

         <span data-ttu-id="7cae6-158">![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="7cae6-158">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="7cae6-159">Tıklayın **tanımlayın...**  bağlantısını **SendReplyToStartOrder** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-159">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="7cae6-160">Dikkat **parametreleri** radyo düğmesi seçili; adlı bir parametre `p_orderId` bağlı `orderId` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7cae6-160">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="7cae6-161">Bu ayar, SendReplyToStartOrder etkinlik dize türünde bir değer çağırana döndürmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-161">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

         <span data-ttu-id="7cae6-162">![İçerik verileri SendReply etkinliği yapılandırma](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "SetReplyToStartOrder etkinlik ayarını yapılandırın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-162">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="7cae6-163">Bir Ata etkinlik arasında sürükleyip **alma** ve **SendReply** etkinlikleri ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="7cae6-163">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

         <span data-ttu-id="7cae6-164">![Ata etkinlik ekleme](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Ata etkinliği ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-164">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

         <span data-ttu-id="7cae6-165">Bu, yeni bir sipariş kimliği oluşturur ve değer OrderID değişkene yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-165">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="7cae6-166">Seçin **ReplyToStartOrder** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7cae6-166">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="7cae6-167">Özellikler penceresinde için üç nokta düğmesine **Correlationınitializer**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-167">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="7cae6-168">Seçin **Başlatıcı Ekle** bağlantı, girin `orderIdHandle` Başlatıcı metin kutusunda, bağıntı türü için sorgu bağıntı başlatıcı seçin ve XPATH sorgularını açılan kutunun altında p_orderId seçin.</span><span class="sxs-lookup"><span data-stu-id="7cae6-168">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="7cae6-169">Bu ayarlar aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-169">These settings are shown in the following illustration.</span></span> <span data-ttu-id="7cae6-170">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-170">Click **OK**.</span></span>  <span data-ttu-id="7cae6-171">Bu, istemci ile bu iş akışı hizmeti örneği arasında bir bağıntı başlatır.</span><span class="sxs-lookup"><span data-stu-id="7cae6-171">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="7cae6-172">Kimliği bu sırayı içeren bir ileti alındığında, bu iş akışı hizmeti örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-172">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

         <span data-ttu-id="7cae6-173">![Bağıntı başlatıcı ekleme](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "bağıntı başlatıcısını ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-173">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="7cae6-174">Sürükle ve bırak başka **ReceiveAndSendReply** etkinlik iş akışı sonuna (dışında **dizisi** ilk içeren **alma** ve  **SendReply** etkinlikler).</span><span class="sxs-lookup"><span data-stu-id="7cae6-174">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="7cae6-175">İstemci tarafından gönderilen ikinci bir ileti alırsınız ve yanıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cae6-175">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="7cae6-176">Seçin **dizisi** yeni eklenen içeren **alma** ve **SendReply** etkinlikleri ve tıklatın **değişkenleri** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7cae6-176">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="7cae6-177">Aşağıdaki çizimde vurgulanan değişkeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7cae6-177">Add the variable highlighted in the following illustration:</span></span>

         <span data-ttu-id="7cae6-178">![Yeni değişkenleri ekleme](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId değişkenini ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-178">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>
         
         <span data-ttu-id="7cae6-179">Ayrıca `orderResult` olarak **dize** içinde `Sequence` kapsam.</span><span class="sxs-lookup"><span data-stu-id="7cae6-179">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="7cae6-180">Seçin **alma** etkinlik ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="7cae6-180">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

         <span data-ttu-id="7cae6-181">![Receive etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "alma etkinlikleri özelliklerini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-181">![Set the Receive acitivity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>
         
         > [!NOTE]
         >  <span data-ttu-id="7cae6-182">Değiştirmeyi unutmayın **ServiceContractName** alanına `../IAddItem`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-182">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="7cae6-183">Tıklayın **tanımlayın...**  bağlantısını **ReceiveAddItem** etkinlik ve aşağıdaki çizimde gösterilen parametreler Ekle: Bu alma etkinliğini sipariş kimliği ve sıralanan öğenin kimliği iki parametre kabul edecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7cae6-183">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

         <span data-ttu-id="7cae6-184">![İkinci alan için parametrelerini belirtme](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "iki parametre almak için Al etkinliği yapılandırın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-184">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="7cae6-185">Tıklayın **CorrelateOn** üç nokta düğmesine tıklayın ve girin `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-185">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="7cae6-186">Altında **XPath sorguları**, aşağı açılan oku tıklatın ve seçin `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="7cae6-186">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="7cae6-187">Bu ikinci bağıntı yapılandırır etkinlik alırsınız.</span><span class="sxs-lookup"><span data-stu-id="7cae6-187">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="7cae6-188">Bağıntı hakkında daha fazla bilgi için bkz. [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="7cae6-188">For more information about correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>

         <span data-ttu-id="7cae6-189">![CorrelatesOn özelliğini ayarlayarak](./media/creating-a-long-running-workflow-service/correlateson-setting.png "CorrelatesOn özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-189">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="7cae6-190">Sürükle ve bırak bir **varsa** etkinlik hemen sonra **ReceiveAddItem** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7cae6-190">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="7cae6-191">Bu etkinlik bir IF gibi davranan deyimi.</span><span class="sxs-lookup"><span data-stu-id="7cae6-191">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="7cae6-192">Ayarlama **koşul** özelliği `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="7cae6-192">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="7cae6-193">Sürükle ve bırak bir **atama** etkinlik için **ardından** bölümü ve başka bir **Else** bölümü özelliklerini ayarlayın **atama** Aşağıdaki çizimde gösterildiği gibi etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="7cae6-193">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

             <span data-ttu-id="7cae6-194">![Hizmet çağrısı sonucunu atama](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "hizmet çağrısı sonucunu atayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-194">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

             <span data-ttu-id="7cae6-195">Koşul ise `true` **ardından** bölüm yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7cae6-195">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="7cae6-196">Koşul ise `false` **Else** bölüm yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7cae6-196">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="7cae6-197">Seçin **SendReplyToReceive** etkinliği ve kümesi **DisplayName** aşağıdaki çizimde gösterilen özelliği.</span><span class="sxs-lookup"><span data-stu-id="7cae6-197">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

             <span data-ttu-id="7cae6-198">![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "SendReply etkinlik özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-198">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="7cae6-199">Tıklayın **tanımlayın...**  bağlantısını **SetReplyToAddItem** etkinlik ve aşağıdaki çizimde gösterildiği gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-199">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="7cae6-200">Bu yapılandırır **SendReplyToAddItem** değeri döndürmek için etkinliği `orderResult` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7cae6-200">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

             <span data-ttu-id="7cae6-201">![Veri bağlama SendReply etkinliğinin ayarlama](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "SendReplyToAddItem etkinliğinin özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="7cae6-201">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="7cae6-202">Web.config dosyasını açın ve aşağıdaki öğeleri ekleyin \<davranışı > bölümü iş akışı kalıcılığı etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-202">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  <span data-ttu-id="7cae6-203">Konak ve SQL server örneği adı önceki kod parçacığında değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7cae6-203">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="7cae6-204">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7cae6-204">Build the solution.</span></span>

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="7cae6-205">İş akışı hizmeti çağırmak için bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7cae6-205">To Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="7cae6-206">Adlı yeni bir konsol uygulama projesi Ekle `OrderClient` çözüm.</span><span class="sxs-lookup"><span data-stu-id="7cae6-206">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="7cae6-207">Aşağıdaki derlemelere başvurular ekleyin `OrderClient` proje</span><span class="sxs-lookup"><span data-stu-id="7cae6-207">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="7cae6-208">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="7cae6-208">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="7cae6-209">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="7cae6-209">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="7cae6-210">Bir iş akışı hizmetine hizmet başvurusu eklemek ve belirtmek `OrderService` ad alanı olarak.</span><span class="sxs-lookup"><span data-stu-id="7cae6-210">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="7cae6-211">İçinde `Main()` istemci projesinin bir yöntem aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7cae6-211">In the `Main()` method of the client project add the following code:</span></span>

    ```
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. <span data-ttu-id="7cae6-212">Çözümü derleyin ve çalıştırın `OrderClient` uygulama.</span><span class="sxs-lookup"><span data-stu-id="7cae6-212">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="7cae6-213">İstemci, aşağıdaki metni görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="7cae6-213">The client will display the following text:</span></span>

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="7cae6-214">İş akışı hizmeti kalıcı olduğunu doğrulamak için SQL Server Management Studio adresine giderek başlatın **Başlat** menüsünde seçme **tüm programlar**, **Microsoft SQL Server 2008**, **SQL Server Management Studio'yu**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-214">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="7cae6-215">Sol taraftaki bölmede genişletin, **veritabanları**, **SQLPersistenceStore**, **görünümleri** ve sağ tıklatma **System.Activities.DurableInstancing.Instances**  seçip **ilk 1000 satırı Seç**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-215">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="7cae6-216">İçinde **sonuçları** bölmesinde doğrulayın listelenen en az bir örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-216">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="7cae6-217">Çalıştırılırken bir özel durum oluştuysa diğer örnekleri önceki çalıştırmalardan olabilir.</span><span class="sxs-lookup"><span data-stu-id="7cae6-217">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="7cae6-218">Sağ tıklayarak var olan satır silebilirsiniz **System.Activities.DurableInstancing.Instances** seçerek **Düzenle üst 200 satırı**, ENTER tuşuna basın **yürütme** düğmesi Sonuçlar bölmesinde tüm satırları ve seçerek **Sil**.</span><span class="sxs-lookup"><span data-stu-id="7cae6-218">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="7cae6-219">Veritabanında görüntülenen örnek doğrulamak için örneği oluşturulmuş uygulamanızı, örnekler görünümü istemci çalıştırılmadan önce boş olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7cae6-219">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="7cae6-220">İstemci (ilk 1000 satırı Seç) sorgu olan çalışan yeniden çalıştırın ve doğrulayın, sonra yeni bir örneği eklendi.</span><span class="sxs-lookup"><span data-stu-id="7cae6-220">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="7cae6-221">İş akışı hizmeti için add öğesi ileti göndermek için enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7cae6-221">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="7cae6-222">İstemci, aşağıdaki metni görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="7cae6-222">The client will display the following text:</span></span>

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="7cae6-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cae6-223">See also</span></span>

- [<span data-ttu-id="7cae6-224">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7cae6-224">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
