---
title: Store genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 46c1ea40925a5c79180171da9a705d7e6b7c8b89
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703295"
---
# <a name="store-extensibility"></a>Store genişletilebilirliği

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kullanılabilir, uygulamaya özgü özel özellikleri yükseltmek kullanıcılara sorgulamak için Kalıcılık veritabanı örnekleri. Bir özellik yükseltme işlemi veritabanı'nda bir özel görünümde kullanılabilir olması değeri neden olur. Bu yükseltilen özelliklerini (kullanıcı sorgularında kullanılan), Int64, Guid, dize ve DateTime gibi basit türler veya seri hale getirilmiş ikili tür (byte[]). olabilir.

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Sınıfında <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> sorgularında kullanılabilir bir özellik olarak bir özellik yükseltmek için kullanabileceğiniz yöntem. Aşağıdaki örnek bir depo genişletilebilirliği uçtan uca örneğidir.

1. Bu örnek senaryoda, her biri için belge işleme özel etkinlikler kullanan iş akışları, bir belge (DP) uygulama işleme sahiptir. Bu iş akışları, son kullanıcıya görünür yapılması gereken durumu değişkenler kümesine sahiptir. Bunu başarmak için DP uygulama türünün bir örneği uzantısını sağlar <xref:System.Activities.Persistence.PersistenceParticipant>, durumu değişkenleri sağlamak için etkinlikleri tarafından kullanılır.

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. Yeni uzantıyı daha sonra ana bilgisayara eklenir.

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     Özel Kalıcılık Katılımcısı ekleme hakkında daha fazla ayrıntı için bkz. [Kalıcılık katılımcıları](persistence-participants.md) örnek.

3. Özel etkinlikler DP uygulamada çeşitli durumu alanları doldurmak **yürütme** yöntemi.

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

4. Bir iş akışı örneği bir Kalıcılık noktasına ulaştığında **CollectValues** yöntemi **DocumentStatusExtension** Kalıcılık Katılımcısı, bu özellikleri Kalıcılık verilerini kaydeder koleksiyonu.

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
    > Tüm bu özellikler geçirilen **SqlWorkflowInstanceStore** Kalıcılık framework tarafından **SaveWorkflowCommand.InstanceData** koleksiyonu.

5. DP uygulama SQL iş akışı örneği Store başlatır ve çağıran **Yükselt** bu verileri yükseltmek için yöntemi.

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

    Bu promosyon bilgilere göre **SqlWorkflowInstanceStore** veri özellikleri, sütunlarında yerleştirir [InstancePromotedProperties](#InstancePromotedProperties) görünümü.

6. Bir alt kümesini yükseltme tablodaki verileri sorgulamak için özelleştirilmiş bir görünümü yükseltme görünümü üzerinde DP uygulama ekler.

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

## <a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] görünümü

|Sütun adı|Sütun türü|Açıklama|
|-----------------|-----------------|-----------------|
|InstanceId|GUID|Bu promosyon ait iş akışı örneği.|
|PromotionName|Nvarchar(400)|Yükseltme adı.|
|Value1, Value2, Value3,.., Value32|sql_variant|Yükseltilen özellik değeri. İkili, blobları ve üzerinde 8000 bayt uzunluğunda dizeleri dışında çoğu SQL ilkel veri türleri sql_variant uygun olamaz.|
|Value33, Value34, Value35,..., Value64|VARBINARY(max)|Açıkça VARBINARY(max) bildirilen yükseltilen özellik değeri.|
