---
title: Ne&#39;s Windows Workflow Foundation'deki yenilikler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: d45c16d4f16c239d1c1c8116b4b41dd41f8a953d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="what39s-new-in-windows-workflow-foundation"></a>Ne&#39;s Windows Workflow Foundation'deki yenilikler
Windows Workflow Foundation (WF) [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] önceki sürümlerden birkaç geliştirme örneklerinde değiştirir. İş akışları oluşturmak, yürütme ve korumak ve yeni işlevsellik ana bilgisayarını uygulamak daha kolay. En son sürümü kullanmak için .NET 3.0 ve .NET 3.5 iş akışı uygulamalarını geçirme hakkında daha fazla bilgi için bkz: [Geçiş Kılavuzu](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>İş akışı etkinlik modeli  
 Şimdi kullanmak yerine bir iş akışı oluşturmanın temel birimidir etkinliktir <xref:System.Workflow.Activities.SequentialWorkflowActivity> veya <xref:System.Workflow.Activities.StateMachineWorkflowActivity> sınıfları. <xref:System.Activities.Activity> Sınıfı, temel Özet akışı davranış sağlar. Etkinlik yazarlar ardından uygulayabilirsiniz ya da <xref:System.Activities.CodeActivity> temel özel etkinlik işlevsellik için veya <xref:System.Activities.NativeActivity> çalışma zamanı derecesini kullanan özel etkinlik işlevleri için. <xref:System.Activities.Activity> Yeni davranışları diğer bakımından bildirimli olarak ifade etmek için etkinlik yazarlar tarafından kullanılan bir sınıftır <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.DynamicActivity> nesneleri özel geliştirilmiş ya da dahil olup [yerleşik etkinliği Kitaplık](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Zengin bileşik etkinlik seçenekleri  
 <xref:System.Activities.Statements.Flowchart> model rasgele döngüler ve koşullu dallanma yazarların bir güçlü yeni denetim akışı etkinliği var. <xref:System.Activities.Statements.Flowchart> ile uygulanması daha önce yalnızca mümkün olan bir olay kaynaklı programlama modelidir <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Yordam iş akışları fayda geleneksel akış denetimi yapıları gibi model yeni akış denetimi etkinliklerden <xref:System.Activities.Statements.TryCatch> ve <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Genişletilmiş yerleşik etkinlik kitaplığı  
 Etkinlik kitaplığı yeni özellikleri şunlardır:  
  
-   Yeni akışını denetlemek etkinlikleri gibi <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, ve <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Üye verileri işlemek için kullanılan, gibi etkinlikler <xref:System.Activities.Statements.Assign> ve koleksiyon etkinlikleri gibi <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   İşlemleri gibi denetleme etkinlikleri <xref:System.Activities.Statements.TransactionScope> ve <xref:System.Activities.Statements.Compensate>.  
  
-   Yeni etkinlikler gibi Mesajlaşma <xref:System.ServiceModel.Activities.SendContent> ve <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Açık etkinliği veri modeli  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] depolama ve veri taşıma yeni seçenekleri içerir. Bir etkinlik kullanarak veri depolanabilir <xref:System.Activities.Variable>. Bir etkinlik ve dışındaki veri taşırken, özelleştirilmiş bağımsız değişken türleri yönü veri taşıma olduğunu belirlemek için kullanılır. Bu türleri <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, ve <xref:System.Activities.OutArgument>. Daha fazla bilgi için bkz: [Windows Workflow Foundation veri modeli](../../../docs/framework/windows-workflow-foundation/data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Gelişmiş, Kalıcılık, barındırma ve izleme seçenekleri  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] aşağıdaki gibi Kalıcılık geliştirmeleri içerir:  
  
-   İş akışları dahil olmak üzere, çalıştırmak için daha fazla seçenek <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, ve <xref:System.Activities.WorkflowInvoker>.  
  
-   İş akışı durumu verileri açıkça kalıcı hale kullanarak <xref:System.Activities.Statements.Persist> etkinlik.  
  
-   Bir konak kalıcı bir <xref:System.Activities.ActivityInstance> , eklentiyi olmadan.  
  
-   Bir iş akışı belirtebilirsiniz no-bölgeleri kalıcılığı no-persist bölge çıkar kadar ertelenir böylece kalıcı yapılamıyor, verilerle çalışırken kalır.  
  
-   Bir iş akışı kullanarak işlemleri geçirilebilir <xref:System.Activities.Statements.TransactionScope>.  
  
-   İzleme, kullanarak daha kolay gerçekleştirilir <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   Sistem olay günlüğünü izleme kullanılarak sağlanır <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Bekleyen bir iş akışını sürdürme yönetilen kullanarak bir <xref:System.Activities.Bookmark> nesnesi.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>WF Tasarımcısı deneyimi genişletmek için daha kolay özelliği  
 Yeni WF Tasarımcısı'nı Windows Presentation Foundation (WPF) oluşturulur ve Visual Studio dışında WF Tasarımcısı'nı yeniden barındırılmasını sırasında kullanmak için daha kolay bir modeli sağlar ve ayrıca özel etkinlik tasarımcıları oluşturmak için daha kolay mekanizmaları sağlar. Daha fazla bilgi için bkz: [iş akışı tasarım deneyimini özelleştirme](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).
