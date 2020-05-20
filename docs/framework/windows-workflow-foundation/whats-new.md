---
title: Windows Workflow Foundation’daki Yenilikler
description: .NET Framework 4 ' teki Windows Workflow Foundation değişiklikler hakkında bilgi edinin. İş akışlarının oluşturulması, yürütülmesi ve bakımının daha kolay olması.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: b25b71a61f8a96d59c79e780d9fe5cd03abfa299
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419349"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Windows Workflow Foundation’daki Yenilikler

.NET Framework 4 ' te Windows Workflow Foundation (WF), önceki sürümlerden birkaç geliştirme paradigmalarına değiştirir. İş akışları artık yeni işlevlerin oluşturulması, yürütülmesi ve bakımını yapmak ve bir ana bilgisayarı uygulamak daha kolay. .NET 3,0 ve .NET 3,5 iş akışı uygulamalarını en son sürümü kullanacak şekilde geçirme hakkında daha fazla bilgi için bkz. [Geçiş Kılavuzu](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>İş akışı etkinlik modeli  
 Etkinlik artık, veya sınıflarını kullanmak yerine iş akışı oluşturma temel birimidir <xref:System.Workflow.Activities.SequentialWorkflowActivity> <xref:System.Workflow.Activities.StateMachineWorkflowActivity> . <xref:System.Activities.Activity>Sınıfı, iş akışı davranışının temel soyutlamasını sağlar. Etkinlik yazarları daha sonra <xref:System.Activities.CodeActivity> temel özel etkinlik işlevselliği için ya da <xref:System.Activities.NativeActivity> çalışma zamanının kapsamını kullanan özel etkinlik işlevselliği için uygulayabilir. <xref:System.Activities.Activity>, <xref:System.Activities.NativeActivity> <xref:System.Activities.CodeActivity> özel olarak <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.DynamicActivity> geliştirilmiş veya [yerleşik etkinlik kitaplığına](net-framework-4-5-built-in-activity-library.md)dahil olmak üzere, etkinlik yazarları tarafından, başka,, veya nesneler açısından bildirimli olarak yeni davranışlar ifade etmek için kullanılan bir sınıftır.  
  
## <a name="rich-composite-activity-options"></a>Zengin bileşik etkinlik seçenekleri  
 <xref:System.Activities.Statements.Flowchart>, yazarların rastgele döngüleri ve koşullu dallanmayı modeletmesine olanak tanıyan güçlü bir yeni denetim akışı etkinliğidir. <xref:System.Activities.Statements.Flowchart>daha önce yalnızca ile uygulanabilir olan olay odaklı bir programlama modeli sağlar <xref:System.Workflow.Activities.StateMachineWorkflowActivity> . Yordamsal iş akışları, ve gibi geleneksel akış denetimi yapılarını modeleden yeni akış denetimi etkinliklerinden yararlanır <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.Switch%601> .  
  
## <a name="expanded-built-in-activity-library"></a>Genişletilmiş yerleşik etkinlik kitaplığı  
 Etkinlik kitaplığının yeni özellikleri şunlardır:  
  
- ,,,,, Ve gibi yeni akış denetimi etkinlikleri <xref:System.Activities.Statements.DoWhile> <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.Switch%601> <xref:System.Activities.Statements.ParallelForEach%601> .  
  
- Gibi üye verilerini düzenleme etkinlikleri <xref:System.Activities.Statements.Assign> ve gibi koleksiyon etkinlikleri <xref:System.Activities.Statements.AddToCollection%601> .  
  
- Ve gibi işlemleri denetlemeye yönelik etkinlikler <xref:System.Activities.Statements.TransactionScope> <xref:System.Activities.Statements.Compensate> .  
  
- Ve gibi yeni mesajlaşma etkinlikleri <xref:System.ServiceModel.Activities.SendContent> <xref:System.ServiceModel.Activities.ReceiveReply> .  
  
## <a name="explicit-activity-data-model"></a>Açık etkinlik veri modeli  
 .NET Framework 4, verileri depolamaya veya taşımaya yönelik yeni seçenekler içerir. Veriler, kullanarak bir etkinlikte depolanabilir <xref:System.Activities.Variable> . Verileri bir etkinliğin içine ve dışına taşırken, hangi yön verilerinin taşınmakta olduğunu belirlemede özelleştirilmiş bağımsız değişken türleri kullanılır. Bu türler <xref:System.Activities.InArgument> , <xref:System.Activities.InOutArgument> ve ' dir <xref:System.Activities.OutArgument> . Daha fazla bilgi için bkz. [veri modeli Windows Workflow Foundation](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Gelişmiş barındırma, kalıcılık ve Izleme seçenekleri  
 .NET Framework 4, aşağıdakiler gibi Kalıcılık geliştirmeleri içerir:  
  
- , Ve dahil iş akışlarını çalıştırmaya yönelik daha fazla seçenek vardır <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowInvoker> .  
  
- İş akışı durum verileri, etkinlik kullanılarak açık bir şekilde kalıcı hale getirilir <xref:System.Activities.Statements.Persist> .  
  
- Bir konak, yüklemesini kaldırmadan kalıcı hale getirebilirler <xref:System.Activities.ActivityInstance> .  
  
- Bir iş akışı kalıcı olmayacak verilerle çalışırken kalıcı olmayan bölgeler belirtebilir, böylece kalıcı olmayan bölge kalana kadar Kalıcılık ertelenir.  
  
- İşlemler, kullanarak bir iş akışına akışda eklenebilir <xref:System.Activities.Statements.TransactionScope> .  
  
- İzleme daha kolay kullanılarak yapılır <xref:System.Activities.Tracking.TrackingParticipant> .  
  
- Sistem olay günlüğüne izleme kullanılarak sağlanır <xref:System.Activities.Tracking.EtwTrackingParticipant> .  
  
- Bekleyen bir iş akışını sürdürmek artık bir nesne kullanılarak yönetilir <xref:System.Activities.Bookmark> .  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>WF Tasarımcısı deneyimini genişletmek daha kolay olur  
 Yeni WF Tasarımcısı Windows Presentation Foundation (WPF) üzerine kurulmuştur ve Visual Studio dışında WF tasarımcısını yeniden barındırırken kullanılacak daha kolay bir model sağlar ve ayrıca özel etkinlik tasarımcıları oluşturmak için daha kolay mekanizmalar sağlar. Daha fazla bilgi için bkz. [Iş akışı tasarım deneyimini özelleştirme](customizing-the-workflow-design-experience.md).
