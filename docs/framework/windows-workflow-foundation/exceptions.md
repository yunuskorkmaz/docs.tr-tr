---
title: Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 64a8338133c265ee1b4c7acbd9b4d168318b66a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145996"
---
# <a name="exceptions"></a>Özel Durumlar
İş akışları kullanabilirsiniz <xref:System.Activities.Statements.TryCatch> bir iş akışı yürütme sırasında başlatılan özel durumları işlemek için etkinlik. Bu özel durumlar işlenebilen veya bunlar kullanarak yeniden oluşturulan <xref:System.Activities.Statements.Rethrow> etkinlik. Etkinlikler <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü olan yürütülmesi ya da <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm veya <xref:System.Activities.Statements.TryCatch.Catches%2A> bölüm tamamlar. İş akışları tarafından barındırılan bir <xref:System.Activities.WorkflowApplication> örneği de kullanabilirsiniz <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> olay işleyici tarafından işlenmeyen özel durumları işlemek için bir <xref:System.Activities.Statements.TryCatch> etkinlik.  
  
## <a name="causes-of-exceptions"></a>Özel durumların nedenlerini  
 Bir iş akışında özel durumları, aşağıdaki yollarla oluşturulabilir:  
  
-   İşlem zaman aşımı <xref:System.Activities.Statements.TransactionScope>.  
  
-   İş akışı kullanarak bir açık durum <xref:System.Activities.Statements.Throw> etkinlik.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] etkinliği özel durum oluştu.  
  
-   Kitaplıklar, bileşenleri veya iş akışında kullanılan hizmetler gibi dış kod özel bir durum oluştu.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Bir etkinlik tarafından oluşturulan ve işlenmeyen özel durum, varsayılan iş akışı örneği sonlandırmaya davranışıdır. Özel durumunda <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici varsa, bu varsayılan davranışı geçersiz kılabilirsiniz. Bu işleyici, iş akışı konak yazarı özel günlüğü, iş akışı iptal etme, iş akışı iptal etme veya iş akışı sonlandırılıyor gibi uygun işleme sağlamak için bir fırsat sağlar.  Bir iş akışı işlenmiyor, bir özel durum harekete geçirirse <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicisi çağrılır. Öğesinden döndürülen üç olası eylemler vardır <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> iş akışının son sonucunu belirlemek.  
  
-   **İptal** -normal bir çıkış bir dal yürütme iptal edilen iş akışı örneğidir. İptal davranışını (örneğin, bir CancellationScope etkinlik kullanarak) modelleyebilirsiniz. İptal işlemi tamamlandığında tamamlanan işleyicisi çağrılır. İptal edilen bir iş akışı başlatılırken iptal edildi durumdadır.  
  
-   **Sonlandırma** -sonlandırılan bir iş akışı örneği yeniden başlatıldı veya sürdürülemez.  Bu, bir özel durum sona erdirildi nedeni olarak sağlamak tamamlandı olay tetiklenir. Sonlandırma işlemi tamamlandığında kesildi işleyicisi çağrılır. Sonlandırılan bir iş akışı hatalı durumda.  
  
-   **Abort** -yalnızca bunu kalıcı olması için yapılandırılmış olması halinde bir iptal edilen iş akışı örnekleri devam ettirilebilir.  Kalıcılık, bir iş akışı devam ettirilemez.  Bir noktada bir iş akışı (bellekte) son Kalıcılık noktası kaybolacak bu yana gerçekleştirilen tüm işleri iptal edilir. İptal edilen bir iş akışı için Aborted durdurma işlemi tamamlandıktan sonra özel durumun nedeni kullanarak çağrılır. Ancak, iptal edildi ve kesildi aksine, tamamlanan işleyici çağrılmaz. İptal edilen bir iş akışı bir iptal edildi durumda.  
  
 Aşağıdaki örnek bir özel durum oluşturur, bir iş akışı çağırır. Özel durum, iş akışı tarafından işlenmeyen ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağrılır. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Özel durum hakkında bilgi sağlamak için incelenir ve iş akışı sonlandırılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>TryCatch etkinlik ile özel durumları işleme  
 Bir iş akışı içinde özel durum işleme ile gerçekleştirilir <xref:System.Activities.Statements.TryCatch> etkinlik. <xref:System.Activities.Statements.TryCatch> Etkinliğinde bir <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonunu <xref:System.Activities.Statements.Catch> her etkinlikleri ile belirli bir ilişkili <xref:System.Exception> türü. Varsa bulunan bir etkinlik tarafından oluşturulan özel durum <xref:System.Activities.Statements.TryCatch.Try%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> etkinlik özel durumu, eşleşen bir <xref:System.Activities.Statements.Catch%601> etkinliğinde <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonu ve ardından özel durumu ele alınır. Özel durum açıkça yeniden oluşturulmuş veya yeni bir özel durum, ardından bu özel durum üst etkinliğine geçirir. Aşağıdaki kod örnekte gösterildiği bir <xref:System.Activities.Statements.TryCatch> işleyen etkinliği bir <xref:System.ApplicationException> oluşturulan <xref:System.Activities.Statements.TryCatch.Try%2A> tarafından bölümünde bir <xref:System.Activities.Statements.Throw> etkinlik. Özel durumun iletisi Konsolu tarafından yazılan <xref:System.Activities.Statements.Catch%601> konsolda etkinliği ve bir ileti yazılır <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Etkinlikler, <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü olan yürütülmesi ya da <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm veya <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümü başarıyla tamamlar. <xref:System.Activities.Statements.TryCatch.Try%2A> Bölümü başarıyla tamamlandığında kendisinden özel hiçbir özel durum oluşursa ve <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümü başarıyla tamamlandığında hiçbir özel durum oluşturulur veya ondan yeniden atılır. Bir özel durum oluşturulursa <xref:System.Activities.Statements.TryCatch.Try%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> ve ya da tarafından işlenmiyor bir <xref:System.Activities.Statements.Catch%601> içinde <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünde veya gelen fırlatılan <xref:System.Activities.Statements.TryCatch.Catches%2A>, etkinlikler, <xref:System.Activities.Statements.TryCatch.Finally%2A> sürece yürütülmez aşağıdakilerden biri gerçekleşir.  
  
-   Daha yüksek bir düzeye göre özel durum yakalandı <xref:System.Activities.Statements.TryCatch> olup, daha yüksek bir düzeyinden fırlatılan bağımsız olarak iş akışında etkinlik <xref:System.Activities.Statements.TryCatch>.  
  
-   Özel durum daha yüksek düzeyde tarafından işlenmiyor <xref:System.Activities.Statements.TryCatch>, iş akışını ve iş akışı kök yerine sonlandırma iptal veya iptal etmek için yapılandırılmış çıkar. İş akışlarını kullanarak barındırılan <xref:System.Activities.WorkflowApplication> işleyerek yapılandırabilirsiniz <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ve döndürerek <xref:System.Activities.UnhandledExceptionAction.Cancel>. İşleme örneği <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> bu konuda daha önce sağlanır. İş akışı Hizmetleri bu kullanarak konusunda yapılandırabilir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> belirterek <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Yapılandırma örneği için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Özel durum işleme maaş  
 Özel durum işleme ve maaş arasındaki fark özel durum işleme bir etkinliği yürütülmesi sırasında gerçekleşir. Bir etkinlik başarıyla tamamlandıktan sonra maaş gerçekleşir. Özel durum işleme maaş tarafından başarıyla tamamlanan iş önceden tamamlanmış bir etkinliğin Al. geri alınabilecek bir mekanizma sağlar. etkinlik özel durumu oluşturur sonra temizleme fırsatı sağlar. Daha fazla bilgi için [maaş](compensation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>
