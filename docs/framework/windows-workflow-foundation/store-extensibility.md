---
title: "Depolama genişletilebilirliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12204ebe9720fb8f894046622d6bb81b1c7d5706
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="store-extensibility"></a>Depolama genişletilebilirliği
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>kullanılabilir, uygulamaya özgü özel özellikleri yükseltmek kullanıcılara sorgulamak için Kalıcılık veritabanı örneği. Bir özellik yükseltme eylemi değeri veritabanındaki özel bir görünüm içinde kullanılabilir olacak şekilde neden olur. Bu yükseltilen özelliklerini (kullanıcı sorgularda kullanılan) Int64, GUID, dize ve tarih/saat gibi basit türler veya seri hale getirilmiş ikili türde (byte[]). olabilir  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Sınıfına sahip <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> sorgularında kullanılabilir bir özellik olarak bir özellik yükseltmek için kullanabileceğiniz yöntemi. Aşağıdaki örnek uçtan uca deposu genişletilebilirlik örneğidir.  
  
1.  Bu örnek senaryoda, her biri özel etkinlikler için belge işleme kullanan iş akışları, bir belge (DP) uygulama işleme sahiptir. Bu iş akışları son kullanıcıya görünür yapılması gereken durumu değişkenleri kümesine sahiptir. Bunu başarmak için DP uygulama türünün bir örneği uzantısını sağlar <xref:System.Activities.Persistence.PersistenceParticipant>, etkinlikler tarafından durumu değişkenleri sağlamak için kullanılan.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  Yeni uzantıyı daha sonra ana bilgisayara eklenir.  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     Özel Kalıcılık katılımcı ekleme hakkında daha fazla ayrıntı için bkz: [Kalıcılık katılımcıları](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) örnek.  
  
3.  Özel etkinlikler DP uygulamasında çeşitli durum alanları doldurmak **yürütme** yöntemi.  
  
    ```  
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
  
4.  Bir iş akışı örneği bir Kalıcılık noktasına ulaştığında **CollectValues** yöntemi **DocumentStatusExtension** Kalıcılık katılımcı Kalıcılık verileri bu özellikleri kaydeder koleksiyonu.  
  
    ```  
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
    >  Bu özellikleri geçirilecek **SqlWorkflowInstanceStore** Kalıcılık framework tarafından **SaveWorkflowCommand.InstanceData** koleksiyonu.  
  
5.  DP uygulama SQL iş akışı örneği deposuna başlatır ve çağırır **Yükselt** bu verileri yükseltmek için yöntem.  
  
    ```  
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
  
     Bu yükseltme bilgilere göre **SqlWorkflowInstanceStore** veri özelliklerini sütunlarında yerleştirir [InstancePromotedProperties](#InstancePromotedProperties) görünümü.
  
6.  Bir yükseltme tablodan veri alt kümesini sorgulamak için özelleştirilmiş görünüm yükseltme görünümü üstünde DP uygulama ekler.  
  
    ```  
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
  
##  <a name="InstancePromotedProperties"></a>[System.Activities.DurableInstancing.InstancePromotedProperties] görünümü  
  
|Sütun adı|Sütun türü|Açıklama|  
|-----------------|-----------------|-----------------|  
|örnek kimliği|GUID|Bu yükseltme ait iş akışı örneği.|  
|PromotionName|nvarchar(400)|Yükseltme adı.|  
|Value1, Value2, Value3,.., Value32|sql_variant|Yükseltilen özellik değeri. İkili BLOB'ların ve üzerinde 8000 bayt uzunluğundadır dizeleri dışında çoğu SQL temel veri türleri sql_variant uygun olamaz.|  
|Value33, Value34, Value35,..., Value64|varbinary(max)|Açıkça varbinary(max) olarak bildirilen yükseltilen özellikleri değeri.|
