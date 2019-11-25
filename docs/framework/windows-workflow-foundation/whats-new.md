---
title: Windows Workflow Foundation’daki Yenilikler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: 8f79c6d2a564571f8b753f322a79e91a01b1cf2f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142010"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Windows Workflow Foundation’daki Yenilikler

.NET Framework 4 ' te Windows Workflow Foundation (WF), önceki sürümlerden birkaç geliştirme paradigmalarına değiştirir. İş akışları artık yeni işlevlerin oluşturulması, yürütülmesi ve bakımını yapmak ve bir ana bilgisayarı uygulamak daha kolay. .NET 3,0 ve .NET 3,5 iş akışı uygulamalarını en son sürümü kullanacak şekilde geçirme hakkında daha fazla bilgi için bkz. [Geçiş Kılavuzu](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>İş akışı etkinlik modeli  
 Etkinlik artık <xref:System.Workflow.Activities.SequentialWorkflowActivity> veya <xref:System.Workflow.Activities.StateMachineWorkflowActivity> sınıfları kullanmak yerine iş akışı oluşturma temel birimidir. <xref:System.Activities.Activity> sınıfı, iş akışı davranışının temel soyutlamasını sağlar. Etkinlik yazarları daha sonra temel özel etkinlik işlevselliği için <xref:System.Activities.CodeActivity> ya da çalışma zamanının kapsamını kullanan özel etkinlik işlevselliği için <xref:System.Activities.NativeActivity> uygulayabilir. <xref:System.Activities.Activity>, etkinlik yazarları tarafından, özel olarak geliştirilmiş veya [yerleşik etkinlik kitaplığına](net-framework-4-5-built-in-activity-library.md)dahil olan diğer <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>veya <xref:System.Activities.DynamicActivity> nesneleri açısından bildirimli olarak ifade etmek için kullanılan bir sınıftır.  
  
## <a name="rich-composite-activity-options"></a>Zengin bileşik etkinlik seçenekleri  
 <xref:System.Activities.Statements.Flowchart>, yazarların rastgele döngüleri ve koşullu dallanmayı modeletmesine olanak tanıyan güçlü bir yeni denetim akışı etkinliğidir. <xref:System.Activities.Statements.Flowchart>, daha önce yalnızca <xref:System.Workflow.Activities.StateMachineWorkflowActivity>uygulanabilir olan olay odaklı bir programlama modeli sağlar. Yordamsal iş akışları, <xref:System.Activities.Statements.TryCatch> ve <xref:System.Activities.Statements.Switch%601>gibi geleneksel akış denetimi yapılarını modeleden yeni akış denetimi etkinliklerinden yararlanır.  
  
## <a name="expanded-built-in-activity-library"></a>Genişletilmiş yerleşik etkinlik kitaplığı  
 Etkinlik kitaplığının yeni özellikleri şunlardır:  
  
- <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>ve <xref:System.Activities.Statements.ParallelForEach%601>gibi yeni akış denetimi etkinlikleri.  
  
- <xref:System.Activities.Statements.Assign> gibi üye verilerini düzenleme etkinlikleri ve <xref:System.Activities.Statements.AddToCollection%601>gibi koleksiyon etkinlikleri.  
  
- <xref:System.Activities.Statements.TransactionScope> ve <xref:System.Activities.Statements.Compensate>gibi işlemleri denetlemeye yönelik etkinlikler.  
  
- <xref:System.ServiceModel.Activities.SendContent> ve <xref:System.ServiceModel.Activities.ReceiveReply>gibi yeni mesajlaşma etkinlikleri.  
  
## <a name="explicit-activity-data-model"></a>Açık etkinlik veri modeli  
 .NET Framework 4, verileri depolamaya veya taşımaya yönelik yeni seçenekler içerir. Veriler, <xref:System.Activities.Variable>kullanarak bir etkinlikte depolanabilir. Verileri bir etkinliğin içine ve dışına taşırken, hangi yön verilerinin taşınmakta olduğunu belirlemede özelleştirilmiş bağımsız değişken türleri kullanılır. Bu türler <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>ve <xref:System.Activities.OutArgument>. Daha fazla bilgi için bkz. [veri modeli Windows Workflow Foundation](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Gelişmiş barındırma, kalıcılık ve Izleme seçenekleri  
 .NET Framework 4, aşağıdakiler gibi Kalıcılık geliştirmeleri içerir:  
  
- <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>ve <xref:System.Activities.WorkflowInvoker>dahil iş akışlarını çalıştırmaya yönelik daha fazla seçenek vardır.  
  
- İş akışı durum verileri <xref:System.Activities.Statements.Persist> etkinliği kullanılarak açık bir şekilde kalıcı hale getirilir.  
  
- Bir konak, kaldırmadan <xref:System.Activities.ActivityInstance> kalıcı hale getirebilirler.  
  
- Bir iş akışı kalıcı olmayacak verilerle çalışırken kalıcı olmayan bölgeler belirtebilir, böylece kalıcı olmayan bölge kalana kadar Kalıcılık ertelenir.  
  
- İşlemler, <xref:System.Activities.Statements.TransactionScope>kullanarak bir iş akışına alınabilir.  
  
- İzleme <xref:System.Activities.Tracking.TrackingParticipant>kullanarak daha kolay bir şekilde gerçekleştirilir.  
  
- Sistem olay günlüğüne izleme <xref:System.Activities.Tracking.EtwTrackingParticipant>kullanılarak sağlanır.  
  
- Bekleyen bir iş akışını sürdürmek artık <xref:System.Activities.Bookmark> nesnesi kullanılarak yönetilir.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>WF Tasarımcısı deneyimini genişletmek daha kolay olur  
 Yeni WF Tasarımcısı Windows Presentation Foundation (WPF) üzerine kurulmuştur ve Visual Studio dışında WF tasarımcısını yeniden barındırırken kullanılacak daha kolay bir model sağlar ve ayrıca özel etkinlik tasarımcıları oluşturmak için daha kolay mekanizmalar sağlar. Daha fazla bilgi için bkz. [Iş akışı tasarım deneyimini özelleştirme](customizing-the-workflow-design-experience.md).
