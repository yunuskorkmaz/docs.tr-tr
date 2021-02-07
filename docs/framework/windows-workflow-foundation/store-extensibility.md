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
# <a name="store-extensibility"></a>Depo Genişletilebilirliği

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kullanıcıların kalıcılık veritabanındaki örnekleri sorgulamak için kullanılabilecek özel, uygulamaya özgü özellikleri yükselmesini sağlar. Bir özelliği yükseltme eylemi, değerin veritabanındaki özel bir görünüm içinde kullanılabilir olmasına neden olur. Bu yükseltilen Özellikler (Kullanıcı sorgularında kullanılabilen özellikler), Int64, Guid, dize ve Tarih ve seri hale getirilmiş ikili tür (Byte []) gibi basit türlerde olabilir.

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>Sınıfında, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> bir özelliği sorgularda kullanılabilecek bir özellik olarak yükseltmek için kullanabileceğiniz yöntemi vardır. Aşağıdaki örnek, depo genişletilebilirliği için uçtan uca bir örnektir.

1. Bu örnek senaryoda bir belge işleme (DP) uygulamasında, her biri belge işleme için özel etkinlikler kullanan iş akışları vardır. Bu iş akışlarının, son kullanıcıya görünür olması gereken bir durum değişkenleri kümesi vardır. Bu işlemi gerçekleştirmek için, DP uygulaması <xref:System.Activities.Persistence.PersistenceParticipant> , durum değişkenlerini sağlamak üzere etkinlikler tarafından kullanılan türünde bir örnek uzantısı sağlar.

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. Yeni uzantı daha sonra konağa eklenir.

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     Özel bir Kalıcılık Katılımcısı ekleme hakkında daha fazla bilgi için bkz. [Kalıcılık katılımcıları](persistence-participants.md) örneği.

3. DP uygulamasındaki özel etkinlikler **yürütme** yöntemindeki çeşitli durum alanlarını doldurur.

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

4. Bir iş akışı örneği bir kalıcılık noktasına ulaştığında, **Documentkara sextenbir** Kalıcılık Katılımcısı 'Nın **CollectValues** yöntemi bu özellikleri Kalıcılık verileri koleksiyonuna kaydeder.

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
    > Bu özelliklerin tümü, **SaveWorkflowCommand. InstanceData** koleksiyonu aracılığıyla Kalıcılık çerçevesi tarafından **SqlWorkflowInstanceStore** 'a geçirilir.

5. DP uygulaması, SQL Iş akışı örnek deposunu başlatır ve bu verileri yükseltmek için **Yükselt** yöntemini çağırır.

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

    **SqlWorkflowInstanceStore** , bu promosyon bilgilerine göre veri özelliklerini [InstancePromotedProperties](#InstancePromotedProperties) görünümünün sütunlarına koyar.

6. Yükseltme tablosundan verilerin bir alt kümesini sorgulamak için, DP uygulaması promosyon görünümünün üzerine özelleştirilmiş bir görünüm ekler.

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

## <a name="systemactivitiesdurableinstancinginstancepromotedproperties-view"></a><a name="InstancePromotedProperties"></a> [System. Activities. Durableörnek_adı. InstancePromotedProperties] görünümü

|Sütun adı|Sütun türü|Description|
|-----------------|-----------------|-----------------|
|InstanceId|GUID|Bu yükseltmenin ait olduğu iş akışı örneği.|
|PromotionName|nvarchar (400)|Yükseltmenin kendisi adı.|
|Değer1, değer2, Value3,.., Value32|sql_variant|Yükseltilen özelliğin değeri. İkili blob 'lar ve 8000 bayt uzunluğundaki dizeler hariç en çok SQL temel veri türleri sql_variant 'e uyabilirler.|
|Value33, Value34, Value35, ..., Value64|varbinary (max)|Açıkça varbinary (max) olarak belirtilen yükseltilen özelliklerin değeri.|
