---
title: Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: cfeefcd29dc05ed5e325950194d9f0775b1fa9fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions"></a>Özel Durumlar
İş akışları kullanabilirsiniz <xref:System.Activities.Statements.TryCatch> bir iş akışı yürütme sırasında başlatılan özel durumları işleme etkinlik. Bu özel durumlar işlenebilir veya bunlar kullanarak yeniden atılabilen <xref:System.Activities.Statements.Rethrow> etkinlik. Etkinlikler <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü olan yürütülmesi ya da <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm veya <xref:System.Activities.Statements.TryCatch.Catches%2A> bölüm tamamlar. İş akışları tarafından barındırılan bir <xref:System.Activities.WorkflowApplication> örneği de kullanabilir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> tarafından işlenmemiş özel durumları işlemek için olay işleyicisi bir <xref:System.Activities.Statements.TryCatch> etkinlik.  
  
## <a name="causes-of-exceptions"></a>Özel durumlar nedenleri  
 Bir iş akışında, özel durumlar aşağıdaki yollarla oluşturulabilir:  
  
-   Bir zaman aşımı işlemlerinde <xref:System.Activities.Statements.TransactionScope>.  
  
-   İş akışını kullanarak oluşturulan bir açık özel <xref:System.Activities.Statements.Throw> etkinlik.  
  
-   A [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bir etkinlikten özel durum oluştu.  
  
-   Kitaplıklar, bileşenleri veya iş akışında kullanılan hizmetleri gibi dış koddan bir özel durum oluştu.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Bir özel durum etkinlik tarafından oluşturulan ve işlenmeyen ise, varsayılan iş akışı örneği sonlandırılacak davranıştır. Özel bir varsa <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici varsa, bu varsayılan davranışı geçersiz kılabilirsiniz. Bu işleyici, iş akışı ana Yazar özel günlüğü, iş akışı iptal etme, iş akışı iptal etme veya iş akışının sonlandırma gibi uygun işleme sağlamak için fırsatı sunar.  Bir iş akışı işlenmiyor, bir özel durum geçirirse <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağrılır. Döndürülen üç olası eylemler vardır <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> iş akışının nihai sonucu belirleyin.  
  
-   **İptal** -normal çıkış şube yürütme iptal edilen iş akışı örneğidir. (Örneğin, bir CancellationScope etkinliğini kullanarak) için İptali davranışı model oluşturabilirsiniz. İptal işlemi tamamlandığında tamamlanan işleyici çağrılır. İptal edilen bir iş akışı iptal edildi durumda değil.  
  
-   **Sonlandırma** -Sonlandırılan İş akışı örneği yeniden veya sürdürülemez.  Bu, özel bir durum sona erdirildi neden olarak sağlayabilir tamamlanan olay tetiklenir. Sonlandırma işlemi tamamlandığında kesildi işleyici çağrılır. Sonlandırılmış bir iş akışı Faulted durumda değil.  
  
-   **Abort** -yalnızca onu kalıcı olması için yapılandırılmışsa, durdurulan iş akışı örnekleri sürdürüldü.  Kalıcı bir iş akışı devam ettirilemez.  Bir noktada bir iş akışı son Kalıcılık noktası kaybolacak bu yana (bellekte) tüm işleri iptal edilir. Durdurulan iş akışı için İptal işlemi tamamlandığında kullanarak özel durum neden iptal edildi işleyici çağrılır. Ancak, iptal edildi ve kesildi aksine, tamamlandı işleyici çağrılır. İptal edilen bir iş akışı bir iptal edildi durumda.  
  
 Aşağıdaki örnek aykırı bir iş akışını çağırır. Özel iş akışı tarafından işlenmeyen ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağrılır. <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Özel durum hakkında bilgi sağlamak için denetlenir ve iş akışı sonlandırılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>TryCatch aktivitesiyle özel durumları işleme  
 Bir iş akışı içinde özel durumları işleme ile gerçekleştirilir <xref:System.Activities.Statements.TryCatch> etkinlik. <xref:System.Activities.Statements.TryCatch> Etkinliği olan bir <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonu <xref:System.Activities.Statements.Catch> her etkinlikleri ile belirli bir ilişkili <xref:System.Exception> türü. Varsa bulunan bir etkinlik tarafından oluşturulan özel durum <xref:System.Activities.Statements.TryCatch.Try%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> etkinlik özel durumu ile eşleşen bir <xref:System.Activities.Statements.Catch%601> etkinliğinde <xref:System.Activities.Statements.TryCatch.Catches%2A> koleksiyonu sonra özel durumu ele alınır. Özel durum açık olarak yeniden oluşturulur veya yeni bir özel durum oluşturulduktan sonra bu özel durum üst etkinliğe geçirir. Aşağıdaki örnekte gösterildiği kod bir <xref:System.Activities.Statements.TryCatch> işler etkinliği bir <xref:System.ApplicationException> oluşturulan <xref:System.Activities.Statements.TryCatch.Try%2A> tarafından bölümünde bir <xref:System.Activities.Statements.Throw> etkinlik. Özel durum iletisi Konsolu tarafından yazılan <xref:System.Activities.Statements.Catch%601> etkinliği ve bir ileti yazılır konsolda <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Etkinlikler <xref:System.Activities.Statements.TryCatch.Finally%2A> bölümü olan yürütülmesi ya da <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm veya <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümü başarıyla tamamlanır. <xref:System.Activities.Statements.TryCatch.Try%2A> Bölümü başarıyla tamamlanırsa hiçbir ondan, özel durumlar varsa ve <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümü başarıyla tamamlandığında durum ya da ondan işlenemezse hiçbir özel durum. Bir özel durum, <xref:System.Activities.Statements.TryCatch.Try%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> ve ya da tarafından işlenmez bir <xref:System.Activities.Statements.Catch%601> içinde <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünde veya gelen işlenemezse <xref:System.Activities.Statements.TryCatch.Catches%2A>, etkinlikler <xref:System.Activities.Statements.TryCatch.Finally%2A> sürece çalıştırılmayacak aşağıdakilerden biri gerçekleşir.  
  
-   Daha yüksek bir düzeye göre özel durum yakalandı <xref:System.Activities.Statements.TryCatch> olup, daha yüksek bir düzeyinden işlenemezse bağımsız olarak iş akışında etkinlik <xref:System.Activities.Statements.TryCatch>.  
  
-   Özel durum tarafından daha yüksek bir düzeye işlenmemiş <xref:System.Activities.Statements.TryCatch>, çıkışları iş akışı ve iş akışı kökündeki Sonlandır yerine iptal edin veya iptal etmek üzere yapılandırılmış. İş akışlarını kullanarak barındırılan <xref:System.Activities.WorkflowApplication> işleyerek yapılandırabilirsiniz <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ve döndürme <xref:System.Activities.UnhandledExceptionAction.Cancel>. İşleme örneği <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> bu konuda daha önce sağlanan. İş akışı Hizmetleri bu kullanarak konusunda yapılandırabilir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve belirterek <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Yapılandırma örneği için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Özel durum işleme maaş  
 Özel durum işleme ve Dengeleme arasındaki farkı özel durum işleme sırasında bir etkinlik yürütülmesini gerçekleşir. Bir etkinliği başarıyla tamamlandıktan sonra maaş oluşur. Özel durum işleme etkinlik özel durumu tetikler sonra maaş tarafından önceden tamamlanmış bir etkinliğin başarıyla tamamlanan iş alınabilecek bir mekanizma sağlar ancak temizleme fırsatı sağlar. Daha fazla bilgi için bkz: [maaş](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.TryCatch>  
 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>  
 <xref:System.Activities.Statements.CompensableActivity>
