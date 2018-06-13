---
title: Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ddb995b849a15451c36d5d11c95a4904a3e0496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495713"
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="4ecaf-102">Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ecaf-102">Creating a Long-running Workflow Service</span></span>
<span data-ttu-id="4ecaf-103">Bu konu, uzun süre çalışan iş akışı hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="4ecaf-104">İş akışı hizmetleri uzun süre çalışan uzun bir süre için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="4ecaf-105">Belirli bir noktada iş akışı için bazı ek bilgiler bekleyen boşta gidebilir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="4ecaf-106">Bu meydana geldiğinde iş akışını bir SQL veritabanına kalıcı ve bellekten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="4ecaf-107">Ek bilgi kullanılabilir hale geldiğinde iş akışı örneği belleğe geri yüklenir ve yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="4ecaf-108">Bu senaryoda, oldukça basitleştirilmiş bir sıralama sistem uyguluyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="4ecaf-109">İstemci sırasını başlatmak için iş akışı hizmeti için bir Başlangıç iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="4ecaf-110">Bu, istemciye bir sipariş Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-110">It returns an order ID to the client.</span></span> <span data-ttu-id="4ecaf-111">Bu noktada iş akışı hizmeti istemciden başka bir ileti bekliyor ve boşta durumuna geçtiğinde ve SQL Server veritabanına kalıcı.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="4ecaf-112">İstemci öğeyi sıralamak için sonraki ileti gönderdiğinde, iş akışı hizmeti belleğe geri yüklenmez ve sipariş işleme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="4ecaf-113">Kod örneğinde öğe siparişe eklenmiş belirten bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="4ecaf-114">Kod örneği teknolojisi, ancak bunun yerine bir uzun süre çalışan iş akışı hizmetleri gösterilmektedir basit örnek gerçek dünya uygulamasının olması düşünülmemiştir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="4ecaf-115">Bu konu nasıl oluşturulacağını bilmeniz varsayar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projeler ve çözümler.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-115">This topic assumes you know how to create [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projects and solutions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4ecaf-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4ecaf-116">Prerequisites</span></span>  
 <span data-ttu-id="4ecaf-117">Bu anlatımda kullanmak için aşağıdaki yazılımlar olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-117">You must have the following software installed to use this walkthrough:</span></span>  
  
1.  <span data-ttu-id="4ecaf-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="4ecaf-118">Microsoft SQL Server 2008</span></span>  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  <span data-ttu-id="4ecaf-119">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ecaf-119">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>  
  
4.  <span data-ttu-id="4ecaf-120">WCF ile tanıdık ve [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeleri/çözümler oluşturmak nasıl biliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-120">You are familiar with WCF and [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and know how to create projects/solutions.</span></span>  
  
### <a name="to-setup-the-sql-database"></a><span data-ttu-id="4ecaf-121">SQL veritabanı kurulumu için</span><span class="sxs-lookup"><span data-stu-id="4ecaf-121">To Setup the SQL Database</span></span>  
  
1.  <span data-ttu-id="4ecaf-122">Kalıcı olmasını iş akışı hizmeti örnekleri için Microsoft SQL Server'ın yüklü olması gerekir ve kalıcı iş akışı örneklerini depolamak için bir veritabanı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-122">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="4ecaf-123">Microsoft SQL Management Studio'yu tıklayarak çalıştırın **Başlat** düğmesi, seçme **tüm programlar**, **Microsoft SQL Server 2008**, ve **Microsoft SQL Management Studio'yu**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-123">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>  
  
2.  <span data-ttu-id="4ecaf-124">Tıklatın **Bağlan** SQL Server örneğine oturum düğmesi</span><span class="sxs-lookup"><span data-stu-id="4ecaf-124">Click the **Connect** button to log on to the SQL Server instance</span></span>  
  
3.  <span data-ttu-id="4ecaf-125">Sağ tıklayın **veritabanları** ağaç görünümü seçip **yeni veritabanı...**</span><span class="sxs-lookup"><span data-stu-id="4ecaf-125">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="4ecaf-126">adlı yeni bir veritabanı oluşturmak için `SQLPersistenceStore`.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-126">to create a new database called `SQLPersistenceStore`.</span></span>  
  
4.  <span data-ttu-id="4ecaf-127">Gerekli veritabanı şemalarını ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreSchema.sql komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-127">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>  
  
5.  <span data-ttu-id="4ecaf-128">Gerekli veritabanı mantığı oluşturan ayarlamak için SQLPersistenceStore veritabanında C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dizininde bulunan SqlWorkflowInstanceStoreLogic.sql komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-128">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>  
  
### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="4ecaf-129">Web oluşturmak için iş akışı hizmeti barındırılan</span><span class="sxs-lookup"><span data-stu-id="4ecaf-129">To Create the Web Hosted Workflow Service</span></span>  
  
1.  <span data-ttu-id="4ecaf-130">Boş bir oluşturma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] çözümü adlandırın `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-130">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution, name it `OrderProcessing`.</span></span>  
  
2.  <span data-ttu-id="4ecaf-131">Adlı yeni bir WCF iş akışı hizmeti uygulaması projesi eklemek `OrderService` çözüme.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-131">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>  
  
3.  <span data-ttu-id="4ecaf-132">Proje Özellikleri iletişim kutusunda seçin **Web** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-132">In the project properties dialog, select the **Web** tab.</span></span>  
  
    1.  <span data-ttu-id="4ecaf-133">Altında **eylemi Başlat** seçin **belirli sayfa** ve belirtin `Service1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-133">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>  
  
         <span data-ttu-id="4ecaf-134">![İş akışı hizmeti proje Web özellikleri](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-134">![Workflow Service Project Web Properties](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span></span>  
  
    2.  <span data-ttu-id="4ecaf-135">Altında **sunucuları** seçin **yerel IIS Web sunucusunu kullan**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-135">Under **Servers** select **Use Local IIS Web server**.</span></span>  
  
         <span data-ttu-id="4ecaf-136">![Yerel Web sunucusu ayarları](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-136">![Local Web Server Settings](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="4ecaf-137">Çalıştırmalısınız [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bu ayarı yapmak için Yönetici modunda.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-137">You must run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] in administrator mode to make this setting.</span></span>  
  
         <span data-ttu-id="4ecaf-138">Bu iki adımı, IIS tarafından barındırılması için iş akışı hizmeti projesini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-138">These two steps configure the workflow service project to be hosted by IIS.</span></span>  
  
4.  <span data-ttu-id="4ecaf-139">Açık `Service1.xamlx` açık ve varolan silme ise **ReceiveRequest** ve **SendResponse** etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-139">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
5.  <span data-ttu-id="4ecaf-140">Seçin **sıralı hizmet** etkinliği ve tıklatın **değişkenleri** bağlamak ve aşağıdaki çizimde gösterilen değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-140">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="4ecaf-141">Bunun yapılması kullanılacak bazı değişkenler daha sonra iş akışı hizmetinde ekler.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-141">Doing this adds some variables that will be used later on in the workflow service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ecaf-142">CorrelationHandle değişken türü açılan değilse seçin **türleri için Gözat** gelen açılır.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-142">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="4ecaf-143">Yazın, CorrelationHandle **türü adı** kutusuna liste kutusundan CorrelationHandle seçin ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-143">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>  
  
     <span data-ttu-id="4ecaf-144">![Değişkenleri eklemek](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-144">![Add Variables](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span></span>  
  
6.  <span data-ttu-id="4ecaf-145">Sürükleme ve bırakma bir **ReceiveAndSendReply** etkinlik şablonuna **sıralı hizmet** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-145">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="4ecaf-146">Bu etkinlik kümesinin bir istemciden bir ileti alırsınız ve yanıt geri gönderin.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-146">This set of activities will receive a message from a client and send a reply back.</span></span>  
  
    1.  <span data-ttu-id="4ecaf-147">Seçin **alma** etkinliği ve özellikler aşağıdaki çizimde vurgulanan kümesi.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-147">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>  
  
         <span data-ttu-id="4ecaf-148">![Küme alacak etkinlik özellikleri](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-148">![Set Receive Activity Properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span></span>  
  
         <span data-ttu-id="4ecaf-149">DisplayName özelliğini Al etkinliğinin Tasarımcısı'nda görüntülenen adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-149">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="4ecaf-150">ServiceContractName ve OperationName özellikleri hizmet sözleşmesini ve Al etkinliği tarafından uygulanan işlem adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-150">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="4ecaf-151">İş akışı hizmetleri sözleşmeleri nasıl kullanıldığı konusunda daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="4ecaf-151">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  
  
    2.  <span data-ttu-id="4ecaf-152">Tıklatın **tanımlayın...**  bağlamak **ReceiveStartOrder** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-152">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="4ecaf-153">Dikkat **parametreleri** radyo düğmesi seçilirse, adlı bir parametre `p_customerName` bağlı `customerName` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-153">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="4ecaf-154">Bu yapılandırır **alma** bazı veri almasına ve bu verileri yerel değişkenlere bağlamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-154">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>  
  
         <span data-ttu-id="4ecaf-155">![Al etkinliği tarafından alınan veri ayarı](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-155">![Setting the data received by the Receive activity](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span></span>  
  
    3.  <span data-ttu-id="4ecaf-156">Seçin **SendReplyToReceive** etkinliği ve aşağıdaki çizimde gösterilen vurgulanan özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-156">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>  
  
         <span data-ttu-id="4ecaf-157">![SendReply etkinlik özelliklerini ayarlama](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-157">![Setting the properties of the SendReply activity](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span></span>  
  
    4.  <span data-ttu-id="4ecaf-158">Tıklatın **tanımlayın...**  bağlamak **SendReplyToStartOrder** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-158">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="4ecaf-159">Dikkat **parametreleri** radyo düğmesinin seçili; adlı bir parametre `p_orderId` bağlı `orderId` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-159">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="4ecaf-160">Bu ayar SendReplyToStartOrder etkinlik çağırana dize türünde değer döndürme belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-160">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>  
  
         <span data-ttu-id="4ecaf-161">![SendReply etkinlik içerik verileri yapılandırma](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-161">![Configuring the SendReply activity content data](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span></span>  
  
    5.  <span data-ttu-id="4ecaf-162">Ata aktivite arasında sürükleyip **alma** ve **SendReply** etkinlikleri ve aşağıdaki çizimde gösterildiği gibi özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-162">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>  
  
         <span data-ttu-id="4ecaf-163">![Ata etkinlik ekleme](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-163">![Adding an assign activity](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span></span>  
  
         <span data-ttu-id="4ecaf-164">Bu yeni bir sıra kimliği oluşturur ve OrderID değişken değeri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-164">This creates a new order ID and places the value in the orderId variable.</span></span>  
  
    6.  <span data-ttu-id="4ecaf-165">Seçin **ReplyToStartOrder** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-165">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="4ecaf-166">Üç nokta düğmesini Özellikler penceresinde **CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-166">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="4ecaf-167">Seçin **Başlatıcısı ekleme** bağlantı, girin `orderIdHandle` Başlatıcı metin kutusuna bağıntı türü için sorgu bağıntı başlatıcı seçin ve XPATH sorguları açılan kutusundan altında p_orderId seçin.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-167">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="4ecaf-168">Bu ayarlar aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-168">These settings are shown in the following illustration.</span></span> <span data-ttu-id="4ecaf-169">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-169">Click **OK**.</span></span>  <span data-ttu-id="4ecaf-170">Bu iş akışı hizmeti örneği ile istemci arasında bir ilişki başlatır.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-170">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="4ecaf-171">Kimliği alınan bu sırada içeren bir ileti olduğunda bu iş akışı hizmeti örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-171">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>  
  
         <span data-ttu-id="4ecaf-172">![Bağıntı başlatıcı ekleme](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-172">![Adding a correlation initializer](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span></span>  
  
7.  <span data-ttu-id="4ecaf-173">Sürükleme ve bırakma başka **ReceiveAndSendReply** etkinliği iş akışı sonuna (dışında **dizisi** ilk içeren **alma** ve  **SendReply** etkinlikleri).</span><span class="sxs-lookup"><span data-stu-id="4ecaf-173">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="4ecaf-174">Bu, istemci tarafından gönderilen ikinci bir ileti alırsınız ve yanıtlamak.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-174">This will receive the second message sent by the client and respond to it.</span></span>  
  
    1.  <span data-ttu-id="4ecaf-175">Seçin **dizisi** yeni eklenen içeren **alma** ve **SendReply** etkinlikleri ve tıklatın **değişkenleri** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-175">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="4ecaf-176">Aşağıdaki çizimde vurgulanan değişkeni ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-176">Add the variable highlighted in the following illustration:</span></span>  
  
         <span data-ttu-id="4ecaf-177">![Yeni değişkenleri ekleme](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-177">![Adding new variables](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span></span>  
  
    2.  <span data-ttu-id="4ecaf-178">Seçin **alma** etkinliği ve aşağıdaki çizimde gösterilen özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-178">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>  
  
         <span data-ttu-id="4ecaf-179">![Alma acitivity özelliklerini ayarlamak](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-179">![Set the Receive acitivity properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span></span>  
  
    3.  <span data-ttu-id="4ecaf-180">Tıklatın **tanımlayın...**  bağlamak **ReceiveAddItem** etkinliği ve aşağıdaki çizimde gösterilen parametreler ekleyin: Bu iki parametre, sipariş kimliği ve sipariş öğenin kimliği kabul etmek için alma etkinliğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-180">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>  
  
         <span data-ttu-id="4ecaf-181">![Alma için ikinci parametrelerini belirterek](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-181">![Specifying parameters for the second receive](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span></span>  
  
    4.  <span data-ttu-id="4ecaf-182">Tıklatın **CorrelateOn** üç nokta düğmesini tıklatın ve girin `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-182">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="4ecaf-183">Altında **XPath sorguları**, açılan oku tıklatın ve seçin `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-183">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="4ecaf-184">Bu ikinci bağıntı yapılandırır etkinlik alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-184">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="4ecaf-185">Bağıntı hakkında daha fazla bilgi için bkz: [bağıntı](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="4ecaf-185">For more information about correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>  
  
         <span data-ttu-id="4ecaf-186">![CorrelatesOn özelliğinin ayarlanması](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-186">![Setting the CorrelatesOn property](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span></span>  
  
    5.  <span data-ttu-id="4ecaf-187">Sürükleme ve bırakma bir **varsa** etkinlik hemen sonra **ReceiveAddItem** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-187">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="4ecaf-188">Bu etkinlik yalnızca bir if gibi davranan deyimi.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-188">This activity acts just like an if statement.</span></span>  
  
        1.  <span data-ttu-id="4ecaf-189">Ayarlama **koşulu** özelliği `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="4ecaf-189">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>  
  
        2.  <span data-ttu-id="4ecaf-190">Sürükleme ve bırakma bir **atamak** etkinliğinde için **sonra** bölümü ve başka bir dosyaya **Else** bölüm özelliklerini ayarlamak **atamak** Aşağıdaki çizimde gösterildiği gibi etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-190">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>  
  
             <span data-ttu-id="4ecaf-191">![Hizmet çağrının sonucu atama](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-191">![Assigning the result of the service call](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span></span>  
  
             <span data-ttu-id="4ecaf-192">Koşul ise `true` **sonra** bölüm yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-192">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="4ecaf-193">Koşul ise `false` **Else** bölüm gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-193">If the condition is `false` the **Else** section is executed.</span></span>  
  
        3.  <span data-ttu-id="4ecaf-194">Seçin **SendReplyToReceive** etkinliği ve kümesi **DisplayName** aşağıdaki çizimde gösterilen özelliği.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-194">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>  
  
             <span data-ttu-id="4ecaf-195">![SendReply etkinlik özelliklerini ayarlama](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-195">![Setting the SendReply activity properties](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span></span>  
  
        4.  <span data-ttu-id="4ecaf-196">Tıklatın **tanımlayın...**  bağlamak **SetReplyToAddItem** etkinliği ve aşağıdaki çizimde gösterildiği gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-196">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="4ecaf-197">Bu yapılandırır **SendReplyToAddItem** değeri döndürmek için etkinliği `orderResult` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-197">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>  
  
             <span data-ttu-id="4ecaf-198">![Veri bağlama SendReply aktivite için ayarı](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span><span class="sxs-lookup"><span data-stu-id="4ecaf-198">![Setting the data binding for the SendReply activit](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span></span>  
  
8.  <span data-ttu-id="4ecaf-199">Web.config dosyasını açın ve aşağıdaki öğeleri ekleyin \<davranışı > bölümü iş akışı kalıcılığı etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-199">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="4ecaf-200">Önceki kod parçacığında bulunan SQL server örneği adı ve ana bilgisayar değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-200">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>  
  
9. <span data-ttu-id="4ecaf-201">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-201">Build the solution.</span></span>  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="4ecaf-202">İş akışı hizmeti çağırmak için bir istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ecaf-202">To Create a Client Application to Call the Workflow Service</span></span>  
  
1.  <span data-ttu-id="4ecaf-203">Adlı yeni bir konsol uygulama projesi eklemek `OrderClient` çözüme.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-203">Add a new Console application project called `OrderClient` to the solution.</span></span>  
  
2.  <span data-ttu-id="4ecaf-204">Aşağıdaki derlemelerine başvurular ekleyin `OrderClient` proje</span><span class="sxs-lookup"><span data-stu-id="4ecaf-204">Add references to the following assemblies to the `OrderClient` project</span></span>  
  
    1.  <span data-ttu-id="4ecaf-205">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="4ecaf-205">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="4ecaf-206">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="4ecaf-206">System.ServiceModel.Activities.dll</span></span>  
  
3.  <span data-ttu-id="4ecaf-207">Bir iş akışı hizmetine hizmet başvurusu ekleyin ve belirtin `OrderService` ad alanı olarak.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-207">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>  
  
4.  <span data-ttu-id="4ecaf-208">İçinde `Main()` istemci projesinin yöntemi aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-208">In the `Main()` method of the client project add the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="4ecaf-209">Çözümü derleme ve çalıştırma `OrderClient` uygulama.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-209">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="4ecaf-210">İstemci aşağıdaki metni görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-210">The client will display the following text:</span></span>  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  <span data-ttu-id="4ecaf-211">İş akışı hizmeti kalıcı olduğunu doğrulamak için SQL Server Management Studio adresine giderek başlatın **Başlat** menüsünde seçme **tüm programlar**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-211">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>  
  
    1.  <span data-ttu-id="4ecaf-212">Sol bölmedeki'nı genişletin, **veritabanları**, **SQLPersistenceStore**, **görünümleri** ve sağ tıklatma **System.Activities.DurableInstancing.Instances**  seçip **ilk 1000 satırı Seç**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-212">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="4ecaf-213">İçinde **sonuçları** bölmesinde listelenen en az bir örnek görmek doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-213">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="4ecaf-214">Çalıştırılırken bir özel durum oluştu durumunda diğer önceki çalıştırır örneklerden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-214">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="4ecaf-215">Sağ tıklayarak var olan satırları silebilirsiniz **System.Activities.DurableInstancing.Instances** ve seçerek **Düzenle üst 200 satırı**, ENTER tuşuna basın **yürütme** düğmesi Sonuçlar bölmesinde tüm satırları ve seçerek **silmek**.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-215">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="4ecaf-216">Veritabanında görüntülenen örneği doğrulamak için örnek uygulamanızın oluşturulan, örnekleri görünüm istemci çalıştırılmadan önce boş olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-216">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="4ecaf-217">İstemci yeniden çalışan çalıştırın (ilk 1000 satırı Seç) sorgu ve doğrulama sonra yeni bir örneği eklendi.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-217">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>  
  
7.  <span data-ttu-id="4ecaf-218">İş akışı hizmeti Ekle öğesini ileti göndermek için enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-218">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="4ecaf-219">İstemci aşağıdaki metni görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="4ecaf-219">The client will display the following text:</span></span>  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ecaf-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ecaf-220">See Also</span></span>  
 [<span data-ttu-id="4ecaf-221">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4ecaf-221">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
