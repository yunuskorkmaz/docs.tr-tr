---
title: Windows Workflow Foundation'daki yenilikler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: 5ab1419a29dd77ac276681bb49dc529fc05d5b15
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711830"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Windows Workflow Foundation'daki yenilikler
Windows Workflow Foundation (WF) [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] birkaç geliştirme paradigmalarını önceki sürümlerden değiştirir. İş akışları oluşturup, yürütme, korumak ve çok sayıda yeni işlevler uygulamak daha kolaydır. En son sürümü kullanmak için .NET 3.0 ve .NET 3.5 iş akışı uygulamalarını geçirme hakkında daha fazla bilgi için bkz. [geçiş kılavuzuna](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>İş akışı etkinlik modeli  
 Etkinlik artık kullanmak yerine bir iş akışı oluşturulurken, temel birimidir <xref:System.Workflow.Activities.SequentialWorkflowActivity> veya <xref:System.Workflow.Activities.StateMachineWorkflowActivity> sınıfları. <xref:System.Activities.Activity> Sınıfı, temel iş akışı davranışını özetini sağlar. Etkinlik yazarlar ardından uygulayabilirsiniz ya da <xref:System.Activities.CodeActivity> temel özel etkinlik işlevselliği veya <xref:System.Activities.NativeActivity> avantajlarına çalışma zamanı kullanan özel etkinlik işlevleri için. <xref:System.Activities.Activity> Yeni davranışlar diğer açısından bildirimli olarak ifade etmek için etkinlik yazarları tarafından kullanılan bir sınıftır <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.DynamicActivity> nesneleri özel olarak geliştirilmiş veya dahil olup [yerleşik etkinlik Kitaplık](net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Zengin bileşik etkinlik seçenekleri  
 <xref:System.Activities.Statements.Flowchart> model rastgele döngü ve koşullu dallanmayı yazarların bir güçlü yeni denetim akışı etkinliği var. <xref:System.Activities.Statements.Flowchart> Olay temelli ve ile uygulanan daha önce yalnızca gönderebildiğini bir programlama modeli sağlar <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Yordam iş akışları gibi geleneksel akış denetimi yapıları, model yeni akış denetimi etkinlikleri fayda <xref:System.Activities.Statements.TryCatch> ve <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Genişletilmiş yerleşik etkinlik kitaplığı  
 Etkinlik Kitaplığı'nın yeni özellikler içerir:  
  
-   Yeni akış denetimi etkinlikleri gibi <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, ve <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Üye verileri gibi düzenlemek için etkinlikleri <xref:System.Activities.Statements.Assign> ve koleksiyon etkinlikleri gibi <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   Etkinlikleri gibi işlemleri, denetleme <xref:System.Activities.Statements.TransactionScope> ve <xref:System.Activities.Statements.Compensate>.  
  
-   Yeni etkinlikler gibi Mesajlaşma <xref:System.ServiceModel.Activities.SendContent> ve <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Açık etkinlik veri modeli  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] Depolama veya veri taşıma için yeni seçenekler içerir. Bir etkinliği kullanarak verileri depolanabilir <xref:System.Activities.Variable>. Bir etkinlik içine ve dışına veri taşıma, özelleştirilmiş bir bağımsız değişken türleri hangi yönde veri taşıma olduğunu belirlemek için kullanılır. Bu türler <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, ve <xref:System.Activities.OutArgument>. Daha fazla bilgi için [Windows Workflow Foundation veri modeli](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Gelişmiş, Kalıcılık, barındırma ve izleme seçenekleri  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] aşağıdaki gibi Kalıcılık geliştirmeleri içerir:  
  
-   İş akışları dahil olmak üzere, çalıştırmak için daha fazla seçenek <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, ve <xref:System.Activities.WorkflowInvoker>.  
  
-   İş akışı durumu açıkça kalıcı verileri kullanarak <xref:System.Activities.Statements.Persist> etkinlik.  
  
-   Bir konak kalıcı bir <xref:System.Activities.ActivityInstance> bu eklentiyi olmadan.  
  
-   Bir iş akışı belirtebilirsiniz no-bölgeleri Kalıcılık no-persist bölge çıkana kadar ertelenir böylece kalıcı yapılamıyor, verilerle çalışırken kalıcı.  
  
-   Akışı yapılan işlemler bir iş akışı kullanarak <xref:System.Activities.Statements.TransactionScope>.  
  
-   İzleme, kullanarak daha kolay gerçekleştirilir <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   Sistem olay günlüğüne izleme kullanarak sağlanan <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Bekleyen bir iş akışını sürdürme yönetilen kullanarak bir <xref:System.Activities.Bookmark> nesne.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Daha kolay WF Tasarımcısı deneyimini genişleten olanağı  
 Yeni WF Tasarımcısı, Windows Presentation Foundation (WPF) üzerinde oluşturulmuş ve Visual Studio dışında WF tasarımcısını yeniden barındırma sırasında kullanmak için daha kolay bir modeli sağlar ve ayrıca özel etkinlik tasarımcıları oluşturmak için daha kolay mekanizmaları sağlar. Daha fazla bilgi için [iş akışı tasarım deneyimini özelleştirme](customizing-the-workflow-design-experience.md).
