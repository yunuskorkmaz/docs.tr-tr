---
title: Store genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 0c6f67469db04705a9ac7827ef301ff226ea3bdb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465736"
---
# <a name="store-extensibility"></a><span data-ttu-id="e2a96-102">Store genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="e2a96-102">Store Extensibility</span></span>

<span data-ttu-id="e2a96-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kullanılabilir, uygulamaya özgü özel özellikleri yükseltmek kullanıcılara sorgulamak için Kalıcılık veritabanı örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e2a96-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="e2a96-104">Bir özellik yükseltme işlemi veritabanı'nda bir özel görünümde kullanılabilir olması değeri neden olur.</span><span class="sxs-lookup"><span data-stu-id="e2a96-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="e2a96-105">Bu yükseltilen özelliklerini (kullanıcı sorgularında kullanılan), Int64, Guid, dize ve DateTime gibi basit türler veya seri hale getirilmiş ikili tür (byte[]). olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2a96-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>

<span data-ttu-id="e2a96-106"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Sınıfında <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> sorgularında kullanılabilir bir özellik olarak bir özellik yükseltmek için kullanabileceğiniz yöntem.</span><span class="sxs-lookup"><span data-stu-id="e2a96-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="e2a96-107">Aşağıdaki örnek bir depo genişletilebilirliği uçtan uca örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e2a96-107">The following example is an end-to-end example of store extensibility.</span></span>

1. <span data-ttu-id="e2a96-108">Bu örnek senaryoda, her biri için belge işleme özel etkinlikler kullanan iş akışları, bir belge (DP) uygulama işleme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e2a96-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="e2a96-109">Bu iş akışları, son kullanıcıya görünür yapılması gereken durumu değişkenler kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e2a96-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="e2a96-110">Bunu başarmak için DP uygulama türünün bir örneği uzantısını sağlar <xref:System.Activities.Persistence.PersistenceParticipant>, durumu değişkenleri sağlamak için etkinlikleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2a96-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. <span data-ttu-id="e2a96-111">Yeni uzantıyı daha sonra ana bilgisayara eklenir.</span><span class="sxs-lookup"><span data-stu-id="e2a96-111">The new extension is then added to the host.</span></span>

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     <span data-ttu-id="e2a96-112">Özel Kalıcılık Katılımcısı ekleme hakkında daha fazla ayrıntı için bkz. [Kalıcılık katılımcıları](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e2a96-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>

3. <span data-ttu-id="e2a96-113">Özel etkinlikler DP uygulamada çeşitli durumu alanları doldurmak **yürütme** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2a96-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>

    ```csharp
    public override void Execute(CodeActivityContext context)
    {
        // ...
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();
        // ...
    }
    ```

4. <span data-ttu-id="e2a96-114">Bir iş akışı örneği bir Kalıcılık noktasına ulaştığında **CollectValues** yöntemi **DocumentStatusExtension** Kalıcılık Katılımcısı, bu özellikleri Kalıcılık verilerini kaydeder koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e2a96-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");

        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)
        {
            readWriteValues = new Dictionary<XName, object>();
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);

            writeOnlyValues = null;
        }
        // ...
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="e2a96-115">Tüm bu özellikler geçirilen **SqlWorkflowInstanceStore** Kalıcılık framework tarafından **SaveWorkflowCommand.InstanceData** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e2a96-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>

5. <span data-ttu-id="e2a96-116">DP uygulama SQL iş akışı örneği Store başlatır ve çağıran **Yükselt** bu verileri yükseltmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2a96-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);

    List<XName> variantProperties = new List<XName>()
    {
        xNS.GetName("UserName"),
        xNS.GetName("ApprovalStatus"),
        xNS.GetName("DocumentId"),
        xNS.GetName("LastModifiedTime")
    };

    store.Promote("DocumentStatus", variantProperties, null);
    ```

    <span data-ttu-id="e2a96-117">Bu promosyon bilgilere göre **SqlWorkflowInstanceStore** veri özellikleri, sütunlarında yerleştirir [InstancePromotedProperties](#InstancePromotedProperties) görünümü.</span><span class="sxs-lookup"><span data-stu-id="e2a96-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>

6. <span data-ttu-id="e2a96-118">Bir alt kümesini yükseltme tablodaki verileri sorgulamak için özelleştirilmiş bir görünümü yükseltme görünümü üzerinde DP uygulama ekler.</span><span class="sxs-lookup"><span data-stu-id="e2a96-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>

    ```sql
    create view [dbo].[DocumentStatus] with schemabinding
    as
        select  P.[InstanceId] as [InstanceId],
            P.Value1 as [UserName],
            P.Value2 as [ApprovalStatus],
            P.Value3 as [DocumentId],
            P.Value4 as [LastUpdatedTime]
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P
    where P.PromotionName = N'DocumentStatus'
    go
    ```

## <a name="InstancePromotedProperties"></a> <span data-ttu-id="e2a96-119">[System.Activities.DurableInstancing.InstancePromotedProperties] görünümü</span><span class="sxs-lookup"><span data-stu-id="e2a96-119">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>

|<span data-ttu-id="e2a96-120">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="e2a96-120">Column Name</span></span>|<span data-ttu-id="e2a96-121">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="e2a96-121">Column Type</span></span>|<span data-ttu-id="e2a96-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2a96-122">Description</span></span>|
|-----------------|-----------------|-----------------|
|<span data-ttu-id="e2a96-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e2a96-123">InstanceId</span></span>|<span data-ttu-id="e2a96-124">GUID</span><span class="sxs-lookup"><span data-stu-id="e2a96-124">GUID</span></span>|<span data-ttu-id="e2a96-125">Bu promosyon ait iş akışı örneği.</span><span class="sxs-lookup"><span data-stu-id="e2a96-125">The workflow instance that this promotion belongs to.</span></span>|
|<span data-ttu-id="e2a96-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="e2a96-126">PromotionName</span></span>|<span data-ttu-id="e2a96-127">Nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="e2a96-127">nvarchar(400)</span></span>|<span data-ttu-id="e2a96-128">Yükseltme adı.</span><span class="sxs-lookup"><span data-stu-id="e2a96-128">The name of the promotion itself.</span></span>|
|<span data-ttu-id="e2a96-129">Value1, Value2, Value3,.., Value32</span><span class="sxs-lookup"><span data-stu-id="e2a96-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="e2a96-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="e2a96-130">sql_variant</span></span>|<span data-ttu-id="e2a96-131">Yükseltilen özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="e2a96-131">The value of the promoted property itself.</span></span> <span data-ttu-id="e2a96-132">İkili, blobları ve üzerinde 8000 bayt uzunluğunda dizeleri dışında çoğu SQL ilkel veri türleri sql_variant uygun olamaz.</span><span class="sxs-lookup"><span data-stu-id="e2a96-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|
|<span data-ttu-id="e2a96-133">Value33, Value34, Value35,..., Value64</span><span class="sxs-lookup"><span data-stu-id="e2a96-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="e2a96-134">VARBINARY(max)</span><span class="sxs-lookup"><span data-stu-id="e2a96-134">varbinary(max)</span></span>|<span data-ttu-id="e2a96-135">Açıkça VARBINARY(max) bildirilen yükseltilen özellik değeri.</span><span class="sxs-lookup"><span data-stu-id="e2a96-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
