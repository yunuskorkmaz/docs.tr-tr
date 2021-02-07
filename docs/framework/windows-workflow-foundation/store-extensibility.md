---
description: 'Daha fazla bilgi edinin: depolama genişletilebilirliği'
title: Depo Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: f04c466224aacd1c8f755e7aa60b18846d0c7180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755232"
---
# <a name="store-extensibility"></a><span data-ttu-id="fcdae-103">Depo Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="fcdae-103">Store Extensibility</span></span>

<span data-ttu-id="fcdae-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kullanıcıların kalıcılık veritabanındaki örnekleri sorgulamak için kullanılabilecek özel, uygulamaya özgü özellikleri yükselmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcdae-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="fcdae-105">Bir özelliği yükseltme eylemi, değerin veritabanındaki özel bir görünüm içinde kullanılabilir olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fcdae-105">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="fcdae-106">Bu yükseltilen Özellikler (Kullanıcı sorgularında kullanılabilen özellikler), Int64, Guid, dize ve Tarih ve seri hale getirilmiş ikili tür (Byte []) gibi basit türlerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcdae-106">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>

<span data-ttu-id="fcdae-107"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>Sınıfında, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> bir özelliği sorgularda kullanılabilecek bir özellik olarak yükseltmek için kullanabileceğiniz yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="fcdae-107">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="fcdae-108">Aşağıdaki örnek, depo genişletilebilirliği için uçtan uca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="fcdae-108">The following example is an end-to-end example of store extensibility.</span></span>

1. <span data-ttu-id="fcdae-109">Bu örnek senaryoda bir belge işleme (DP) uygulamasında, her biri belge işleme için özel etkinlikler kullanan iş akışları vardır.</span><span class="sxs-lookup"><span data-stu-id="fcdae-109">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="fcdae-110">Bu iş akışlarının, son kullanıcıya görünür olması gereken bir durum değişkenleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="fcdae-110">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="fcdae-111">Bu işlemi gerçekleştirmek için, DP uygulaması <xref:System.Activities.Persistence.PersistenceParticipant> , durum değişkenlerini sağlamak üzere etkinlikler tarafından kullanılan türünde bir örnek uzantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcdae-111">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. <span data-ttu-id="fcdae-112">Yeni uzantı daha sonra konağa eklenir.</span><span class="sxs-lookup"><span data-stu-id="fcdae-112">The new extension is then added to the host.</span></span>

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     <span data-ttu-id="fcdae-113">Özel bir Kalıcılık Katılımcısı ekleme hakkında daha fazla bilgi için bkz. [Kalıcılık katılımcıları](persistence-participants.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="fcdae-113">For more details about adding a custom persistence participant, see the [Persistence Participants](persistence-participants.md) sample.</span></span>

3. <span data-ttu-id="fcdae-114">DP uygulamasındaki özel etkinlikler **yürütme** yöntemindeki çeşitli durum alanlarını doldurur.</span><span class="sxs-lookup"><span data-stu-id="fcdae-114">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>

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

4. <span data-ttu-id="fcdae-115">Bir iş akışı örneği bir kalıcılık noktasına ulaştığında, **Documentkara sextenbir** Kalıcılık Katılımcısı 'Nın **CollectValues** yöntemi bu özellikleri Kalıcılık verileri koleksiyonuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fcdae-115">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>

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
    > <span data-ttu-id="fcdae-116">Bu özelliklerin tümü, **SaveWorkflowCommand. InstanceData** koleksiyonu aracılığıyla Kalıcılık çerçevesi tarafından **SqlWorkflowInstanceStore** 'a geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fcdae-116">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>

5. <span data-ttu-id="fcdae-117">DP uygulaması, SQL Iş akışı örnek deposunu başlatır ve bu verileri yükseltmek için **Yükselt** yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fcdae-117">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>

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

    <span data-ttu-id="fcdae-118">**SqlWorkflowInstanceStore** , bu promosyon bilgilerine göre veri özelliklerini [InstancePromotedProperties](#InstancePromotedProperties) görünümünün sütunlarına koyar.</span><span class="sxs-lookup"><span data-stu-id="fcdae-118">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>

6. <span data-ttu-id="fcdae-119">Yükseltme tablosundan verilerin bir alt kümesini sorgulamak için, DP uygulaması promosyon görünümünün üzerine özelleştirilmiş bir görünüm ekler.</span><span class="sxs-lookup"><span data-stu-id="fcdae-119">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>

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

## <a name="systemactivitiesdurableinstancinginstancepromotedproperties-view"></a><a name="InstancePromotedProperties"></a> <span data-ttu-id="fcdae-120">[System. Activities. Durableörnek_adı. InstancePromotedProperties] görünümü</span><span class="sxs-lookup"><span data-stu-id="fcdae-120">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>

|<span data-ttu-id="fcdae-121">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="fcdae-121">Column Name</span></span>|<span data-ttu-id="fcdae-122">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="fcdae-122">Column Type</span></span>|<span data-ttu-id="fcdae-123">Description</span><span class="sxs-lookup"><span data-stu-id="fcdae-123">Description</span></span>|
|-----------------|-----------------|-----------------|
|<span data-ttu-id="fcdae-124">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fcdae-124">InstanceId</span></span>|<span data-ttu-id="fcdae-125">GUID</span><span class="sxs-lookup"><span data-stu-id="fcdae-125">GUID</span></span>|<span data-ttu-id="fcdae-126">Bu yükseltmenin ait olduğu iş akışı örneği.</span><span class="sxs-lookup"><span data-stu-id="fcdae-126">The workflow instance that this promotion belongs to.</span></span>|
|<span data-ttu-id="fcdae-127">PromotionName</span><span class="sxs-lookup"><span data-stu-id="fcdae-127">PromotionName</span></span>|<span data-ttu-id="fcdae-128">nvarchar (400)</span><span class="sxs-lookup"><span data-stu-id="fcdae-128">nvarchar(400)</span></span>|<span data-ttu-id="fcdae-129">Yükseltmenin kendisi adı.</span><span class="sxs-lookup"><span data-stu-id="fcdae-129">The name of the promotion itself.</span></span>|
|<span data-ttu-id="fcdae-130">Değer1, değer2, Value3,.., Value32</span><span class="sxs-lookup"><span data-stu-id="fcdae-130">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="fcdae-131">sql_variant</span><span class="sxs-lookup"><span data-stu-id="fcdae-131">sql_variant</span></span>|<span data-ttu-id="fcdae-132">Yükseltilen özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="fcdae-132">The value of the promoted property itself.</span></span> <span data-ttu-id="fcdae-133">İkili blob 'lar ve 8000 bayt uzunluğundaki dizeler hariç en çok SQL temel veri türleri sql_variant 'e uyabilirler.</span><span class="sxs-lookup"><span data-stu-id="fcdae-133">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|
|<span data-ttu-id="fcdae-134">Value33, Value34, Value35, ..., Value64</span><span class="sxs-lookup"><span data-stu-id="fcdae-134">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="fcdae-135">varbinary (max)</span><span class="sxs-lookup"><span data-stu-id="fcdae-135">varbinary(max)</span></span>|<span data-ttu-id="fcdae-136">Açıkça varbinary (max) olarak belirtilen yükseltilen özelliklerin değeri.</span><span class="sxs-lookup"><span data-stu-id="fcdae-136">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
