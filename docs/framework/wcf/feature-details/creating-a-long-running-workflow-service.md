---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: e6206babdb728b6ce38c94441f775e1fdffe7d79
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040410"
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="2aaf0-102">Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2aaf0-102">Creating a Long-running Workflow Service</span></span>

<span data-ttu-id="2aaf0-103">Bu konuda, uzun süre çalışan bir iş akışı hizmetinin nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="2aaf0-104">Uzun süre çalışan iş akışı hizmetleri uzun süreler için çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="2aaf0-105">Bazı bir noktada iş akışı, bazı ek bilgiler için bekleyen boşta kalabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="2aaf0-106">Bu gerçekleştiğinde, iş akışı bir SQL veritabanında kalıcı hale getirilir ve bellekten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="2aaf0-107">Ek bilgiler kullanılabilir hale geldiğinde, iş akışı örneği belleğe geri yüklenir ve yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="2aaf0-108">Bu senaryoda, çok basitleştirilmiş bir sıralama sistemi uygulıyız.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="2aaf0-109">İstemci sıraya başlamak için iş akışı hizmetine bir başlangıç iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="2aaf0-110">İstemciye bir sıra KIMLIĞI döndürür.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-110">It returns an order ID to the client.</span></span> <span data-ttu-id="2aaf0-111">Bu noktada, iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna geçiyor ve bir SQL Server veritabanına kalıcı hale getirildi.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="2aaf0-112">İstemci bir öğeyi sipariş etmek için bir sonraki iletiyi gönderdiğinde, iş akışı hizmeti belleğe geri yüklenir ve siparişi işlemeyi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="2aaf0-113">Kod örneğinde, öğenin sıraya eklendiğini belirten bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="2aaf0-114">Kod örneği, teknolojinin gerçek bir dünya uygulaması değil, uzun süre çalışan iş akışı hizmetlerini gösteren basit bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="2aaf0-115">Bu konu başlığı altında, Visual Studio 2012 projeleri ve çözümleri oluşturmayı bildiğiniz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-115">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2aaf0-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2aaf0-116">Prerequisites</span></span>

<span data-ttu-id="2aaf0-117">Bu yönergeyi kullanabilmeniz için aşağıdaki yazılımların yüklü olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-117">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="2aaf0-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2aaf0-118">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="2aaf0-119">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="2aaf0-119">Visual Studio 2012</span></span>

3. <span data-ttu-id="2aaf0-120">MICROSOFT[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aaf0-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="2aaf0-121">WCF ve Visual Studio 2012 hakkında bilgi sahibisiniz ve proje/çözüm oluşturma hakkında bilgi sahibi olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-121">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

### <a name="to-setup-the-sql-database"></a><span data-ttu-id="2aaf0-122">SQL veritabanını ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2aaf0-122">To Setup the SQL Database</span></span>

1. <span data-ttu-id="2aaf0-123">İş akışı hizmeti örneklerinin kalıcı olabilmesi için Microsoft SQL Server yüklü olmalıdır ve kalıcı iş akışı örneklerini depolamak için bir veritabanı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-123">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="2aaf0-124">**Başlat** düğmesine tıklayarak, **tüm programlar**, **Microsoft SQL Server 2008**ve **MICROSOFT sql Management Studio**' nı seçerek Microsoft SQL Management Studio 'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-124">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="2aaf0-125">SQL Server örneğine oturum açmak için **Bağlan** düğmesine tıklayın</span><span class="sxs-lookup"><span data-stu-id="2aaf0-125">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="2aaf0-126">Ağaç görünümünde **veritabanları** ' na sağ tıklayın ve **Yeni veritabanı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-126">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="2aaf0-127">adlı `SQLPersistenceStore`yeni bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-127">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="2aaf0-128">Gerekli veritabanı şemalarını ayarlamak için Sqlpersistenınstancestore veritabanındaki C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema. SQL komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-128">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="2aaf0-129">Gerekli veritabanı mantığını ayarlamak için Sqlpersistenınstancestore veritabanındaki C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan Sqlworkflowcestorelogic. SQL komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-129">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="2aaf0-130">Web 'de barındırılan Iş akışı hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2aaf0-130">To Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="2aaf0-131">Boş bir Visual Studio 2012 çözümü oluşturun, adlandırın `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-131">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="2aaf0-132">Çözüme adlı `OrderService` yeni bir WCF iş akışı hizmeti uygulama projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-132">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="2aaf0-133">Proje Özellikleri iletişim kutusunda **Web** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-133">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="2aaf0-134">**Başlatma eylemi** altında **belirli sayfa** ' yı seçin `Service1.xamlx`ve belirtin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-134">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="2aaf0-135">![Iş akışı hizmeti projesi Web özellikleri](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Web 'de barındırılan iş akışı hizmeti 'Ne özgü sayfa seçeneğini oluşturma")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-135">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="2aaf0-136">**Sunucular** altında **yerel IIS Web sunucusu kullan**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-136">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="2aaf0-137">![Yerel Web sunucusu ayarları](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Web 'de barındırılan iş akışı hizmetini oluşturma-Yerel IIS Web sunucusu seçeneğini kullanın")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-137">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="2aaf0-138">Bu ayarı yapmak için, Visual Studio 2012 ' i yönetici modunda çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-138">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="2aaf0-139">Bu iki adım, iş akışı hizmeti projesini IIS tarafından barındırılacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-139">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="2aaf0-140">Henüz `Service1.xamlx` açık değilse açın ve var olan **ReceiveRequest** ve **SendResponse** etkinliklerini silin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-140">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="2aaf0-141">**Sıralı hizmet** etkinliğini seçin ve **değişkenler** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-141">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="2aaf0-142">Bunu yapmak, daha sonra iş akışı hizmetinde kullanılacak bazı değişkenleri ekler.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-142">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2aaf0-143">CorrelationHandle, değişken türü açılan kutusunda değilse, açılan listeden **türler Için araştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-143">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="2aaf0-144">**Tür adı** kutusuna CorrelationHandle yazın, ListBox ' dan CorrelationHandle ' ı seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-144">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="2aaf0-145">![Değişken Ekle](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Sıralı hizmet etkinliğine değişken ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-145">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="2aaf0-146">Bir **ReceiveAndSendReply** etkinlik şablonunu sürükleyip **sıralı hizmet** etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-146">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="2aaf0-147">Bu etkinlik kümesi bir istemciden bir ileti alır ve tekrar yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-147">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="2aaf0-148">**Alma** etkinliğini seçin ve aşağıdaki çizimde vurgulanan özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-148">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="2aaf0-149">![Alma etkinliği özelliklerini ayarla](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Alma etkinliği özelliklerini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-149">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="2aaf0-150">DisplayName özelliği, tasarımcıda alma etkinliği için görünen adı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-150">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="2aaf0-151">ServiceContractName ve OperationName özellikleri, alma etkinliği tarafından uygulanan hizmet sözleşmesinin ve işlemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-151">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="2aaf0-152">Iş akışı hizmetlerinde sözleşmelerin nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [Iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="2aaf0-152">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="2aaf0-153">**ReceiveStartOrder** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-153">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="2aaf0-154">**Parametreler** radyo düğmesinin seçili olduğuna, adlı `p_customerName` parametrenin `customerName` değişkenine bağlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-154">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="2aaf0-155">Bu, **alma** etkinliğini bazı verileri alacak şekilde yapılandırır ve bu verileri yerel değişkenlere bağlar.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-155">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="2aaf0-156">![Alma etkinliği tarafından alınan verileri ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Alma etkinliği tarafından alınan veriler için özellikleri ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-156">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="2aaf0-157">**SendReplyToReceive** etkinliğini seçin ve aşağıdaki çizimde gösterilen vurgulanan özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-157">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="2aaf0-158">![SendReply etkinliğinin özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "Setreplyproperties")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-158">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="2aaf0-159">**SendReplyToStartOrder** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-159">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="2aaf0-160">**Parametreler** radyo düğmesinin seçili olduğuna dikkat edin; adlı `p_orderId` bir parametre `orderId` değişkenine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-160">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="2aaf0-161">Bu ayar, SendReplyToStartOrder etkinliğinin çağırana String türünde bir değer döndürmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-161">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="2aaf0-162">![SendReply etkinlik içerik verilerini yapılandırma](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "SetReplyToStartOrder etkinliğinin ayarını yapılandırın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-162">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="2aaf0-163">**Receive** ve **SendReply** etkinlikleri arasında bir atama etkinliği sürükleyip bırakın ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-163">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="2aaf0-164">![Atama etkinliği ekleme](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Atama etkinliği ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-164">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="2aaf0-165">Bu, yeni bir sipariş KIMLIĞI oluşturur ve değeri OrderID değişkenine koyar.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-165">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="2aaf0-166">**ReplyToStartOrder** etkinliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-166">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="2aaf0-167">Özellikler penceresinde, **Correlationbaşlatıcıları**için üç nokta düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-167">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="2aaf0-168">**Başlatıcı Ekle** bağlantısını seçin, başlatıcı metin `orderIdHandle` kutusunda girin, bağıntı türü için sorgu bağıntı Başlatıcısı ' nı seçin ve XPath sorguları açılan kutusu altında p_orderId ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-168">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="2aaf0-169">Bu ayarlar aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-169">These settings are shown in the following illustration.</span></span> <span data-ttu-id="2aaf0-170">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-170">Click **OK**.</span></span>  <span data-ttu-id="2aaf0-171">Bu, istemci ile iş akışı hizmetinin bu örneği arasında bir bağıntı başlatır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-171">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="2aaf0-172">Bu sipariş KIMLIĞINI içeren bir ileti alındığında, iş akışı hizmetinin bu örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-172">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="2aaf0-173">![Bağıntı başlatıcısı ekleme](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Bağıntı başlatıcısı ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-173">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="2aaf0-174">Başka bir **ReceiveAndSendReply** etkinliğini, iş akışının sonuna sürükleyin ve bırakın (ilk **Receive** ve **SendReply** etkinliklerini içeren **sıra** dışında).</span><span class="sxs-lookup"><span data-stu-id="2aaf0-174">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="2aaf0-175">Bu, istemci tarafından gönderilen ikinci iletiyi alır ve buna yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-175">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="2aaf0-176">Yeni eklenen **Receive** ve **SendReply** etkinliklerini Içeren **diziyi** seçin ve **değişkenler** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-176">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="2aaf0-177">Aşağıdaki çizimde vurgulanan değişkeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-177">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="2aaf0-178">![Yeni değişkenler ekleme](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "ItemId değişkenini ekleyin.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-178">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="2aaf0-179">Ayrıca, `orderResult` kapsama`Sequence` **dize** olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-179">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="2aaf0-180">**Alma** etkinliğini seçin ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-180">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="2aaf0-181">![Alma etkinliği özelliklerini ayarla](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Alma etkinlikleri özelliklerini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-181">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="2aaf0-182">**ServiceContractName** alanını ile `../IAddItem`değiştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-182">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="2aaf0-183">**ReceiveAddItem** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterilen parametreleri ekleyin: Bu, Receive etkinliğini iki parametreyi kabul edecek şekılde yapılandırır, sipariş KIMLIĞI ve sıralanan öğenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-183">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="2aaf0-184">![İkinci alım için parametreleri belirtme](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Alma etkinliğini iki parametre alacak şekilde yapılandırın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-184">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="2aaf0-185">**CorrelateOn** üç nokta düğmesine tıklayın ve girin `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-185">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="2aaf0-186">**XPath sorguları**altında aşağı açılan oka tıklayın ve öğesini seçin `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-186">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="2aaf0-187">Bu, ikinci alma etkinliğinde bağıntıyı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-187">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="2aaf0-188">Bağıntı hakkında daha fazla bilgi için bkz. [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="2aaf0-188">For more information about correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>

        <span data-ttu-id="2aaf0-189">![CorrelatesOn özelliğini ayarlama](./media/creating-a-long-running-workflow-service/correlateson-setting.png "CorrelatesOn özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-189">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="2aaf0-190">Bir **IF** etkinliğini **receiveaddidıtem** etkinliğinden hemen sonra sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-190">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="2aaf0-191">Bu etkinlik tıpkı bir if bildirisi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-191">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="2aaf0-192">**Koşul** özelliğini olarak ayarlayın`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="2aaf0-192">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="2aaf0-193">' A bir **atama** etkinliğini sürükleyip **daha sonra** , aşağıdaki çizimde gösterildiği gibi, başka bir şekilde **atama** etkinliklerinin özelliklerini ayarla bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-193">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="2aaf0-194">![Hizmet çağrısının sonucunu atama](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Hizmet çağrısının sonucunu atayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-194">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="2aaf0-195">Koşul ise `true` , Bölüm yürütülür .</span><span class="sxs-lookup"><span data-stu-id="2aaf0-195">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="2aaf0-196">Koşul `false` **Else** bölümü yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-196">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="2aaf0-197">**SendReplyToReceive** etkinliğini seçin ve aşağıdaki çizimde gösterilen **DisplayName** özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-197">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="2aaf0-198">![SendReply etkinlik özelliklerini ayarlama](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "SendReply etkinlik özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-198">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="2aaf0-199">**Setreplytoaddidıtem** etkinliğinde **define...** bağlantısına tıklayın ve aşağıdaki çizimde gösterildiği gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-199">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="2aaf0-200">Bu, `orderResult` değişkende değeri döndürecek **SendReplyToAddItem** etkinliğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-200">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="2aaf0-201">![SendReply etkinliği için veri bağlamayı ayarlama](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Sendreplytoaddidıtem etkinliğinin özelliğini ayarlayın.")</span><span class="sxs-lookup"><span data-stu-id="2aaf0-201">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="2aaf0-202">Web. config dosyasını açın ve iş akışı kalıcılığını etkinleştirmek için \<davranış > bölümüne aşağıdaki öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-202">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="2aaf0-203">Önceki kod parçacığında ana bilgisayarınızı ve SQL Server örnek adınızı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-203">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="2aaf0-204">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-204">Build the solution.</span></span>

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="2aaf0-205">Iş akışı hizmetini çağırmak üzere bir Istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2aaf0-205">To Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="2aaf0-206">Çözüme adlı `OrderClient` yeni bir konsol uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-206">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="2aaf0-207">`OrderClient` Projeye aşağıdaki derlemelere başvurular ekleyin</span><span class="sxs-lookup"><span data-stu-id="2aaf0-207">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="2aaf0-208">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="2aaf0-208">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="2aaf0-209">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="2aaf0-209">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="2aaf0-210">İş akışı hizmetine bir hizmet başvurusu ekleyin ve ad alanı `OrderService` olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-210">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="2aaf0-211">İstemci projesi `Main()` yönteminde aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-211">In the `Main()` method of the client project add the following code:</span></span>

    ```csharp
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

5. <span data-ttu-id="2aaf0-212">Çözümü derleyin ve `OrderClient` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-212">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="2aaf0-213">İstemci aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-213">The client will display the following text:</span></span>

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="2aaf0-214">İş akışı hizmetinin kalıcı olduğunu doğrulamak için, **Başlat** menüsüne gidip **tüm programlar**' a, **Microsoft SQL Server 2008** **SQL Server Management Studio**' i seçerek SQL Server Management Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-214">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="2aaf0-215">Sol taraftaki bölmede, **veritabanları**, **sqlpersistenınstancestore**, **Görünümler** ' i genişletin ve **System. Activities. durableörnek oluşturma. örnekler** ' i seçin ve **en üstteki 1000 satırları Seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-215">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="2aaf0-216">**Sonuçlar** bölmesinde, listelenen en az bir örnek olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-216">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="2aaf0-217">Çalıştırılırken bir özel durum oluşursa, önceki çalıştırmaların başka örnekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-217">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="2aaf0-218">**System. Activities. Durableörnek oluşturma. Instances** ' a sağ tıklayıp, **en üstteki 200 satırları Düzenle**' yi seçerek **yürütme** düğmesine basarak, sonuçlar bölmesinde tüm satırları seçip **Sil**' i seçerek mevcut satırları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-218">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="2aaf0-219">Veritabanında görüntülenmekte olan örneği uygulamanızın oluşturduğu örnek olduğunu doğrulamak için, istemci çalıştırılmadan önce örnekler görünümünün boş olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-219">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="2aaf0-220">İstemci çalışmaya başladıktan sonra sorguyu yeniden çalıştırın (en üstteki 1000 satırları seçin) ve yeni bir örnek eklendiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-220">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="2aaf0-221">Öğe Ekle iletisini iş akışı hizmetine göndermek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-221">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="2aaf0-222">İstemci aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2aaf0-222">The client will display the following text:</span></span>

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="2aaf0-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2aaf0-223">See also</span></span>

- [<span data-ttu-id="2aaf0-224">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2aaf0-224">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
