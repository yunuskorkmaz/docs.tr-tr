---
title: Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 53cc8e3e27e131c5c2a9f8271851a0d8d7e0cbd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280214"
---
# <a name="exceptions"></a>Özel Durumlar

İş akışları, <xref:System.Activities.Statements.TryCatch> bir iş akışının yürütülmesi sırasında oluşturulan özel durumları işlemek için etkinliğini kullanabilir. Bu özel durumlar işlenebilir veya etkinlik kullanılarak yeniden oluşturulabilir <xref:System.Activities.Statements.Rethrow> . Bölümündeki etkinlikler <xref:System.Activities.Statements.TryCatch.Finally%2A> , <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm ya da <xref:System.Activities.Statements.TryCatch.Catches%2A> bölüm tamamlandığında yürütülür. Bir örnek tarafından barındırılan iş akışları <xref:System.Activities.WorkflowApplication> , <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> bir etkinlik tarafından işlenmeyen özel durumları işlemek için de olay işleyicisini de kullanabilir <xref:System.Activities.Statements.TryCatch> .  
  
## <a name="causes-of-exceptions"></a>Özel durumların nedenleri  

 Bir iş akışında, özel durumlar aşağıdaki yollarla oluşturulabilir:  
  
- İçindeki işlemlerin zaman aşımı <xref:System.Activities.Statements.TransactionScope> .  
  
- Etkinlik kullanılarak iş akışı tarafından oluşturulan açık bir özel durum <xref:System.Activities.Statements.Throw> .  
  
- [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]Etkinlikten özel durum oluşturuldu.  
  
- İş akışında kullanılan kitaplıklar, bileşenler veya hizmetler gibi harici koddan oluşturulan özel durum.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  

 Bir etkinlik tarafından bir özel durum oluşturulursa ve işlenmemiş ise, varsayılan davranış iş akışı örneğini sonlandırmak olur. Özel bir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici varsa, bu varsayılan davranışı geçersiz kılabilir. Bu işleyici, iş akışı ana bilgisayarına özel günlük kaydı, iş akışını iptal etme, iş akışını iptal etme veya iş akışını sonlandırma gibi uygun işleme sağlama fırsatı verir.  Bir iş akışı işlenmemiş bir özel durum harekete geçirirse, <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağrılır. <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>İş akışının nihai sonucunu belirleyen üç olası eylem döndürülür.  
  
- **İptal** -iptal edilen bir iş akışı örneği, bir dal yürütmesinin düzgün bir şekilde çıkışı. İptal davranışını modelleyebilirsiniz (örneğin, bir CancellationScope etkinliği kullanarak). Tamamlanan işleyici, iptal işlemi tamamlandığında çağrılır. İptal edilen bir iş akışı Iptal edildi durumunda.  
  
- **Sonlandır** -sonlandırılan bir iş akışı örneği sürdürülemez veya yeniden başlatılamaz.  Bu, sonlandırıldığı nedenden dolayı özel durum sağlayabilmeniz için tamamlanan olayı tetikler. Sonlandırma işlemi tamamlandığında sonlandırılmış işleyici çağrılır. Sonlandırılan bir iş akışı hatalı durumda.  
  
- **Abort** -durdurulan bir iş akışı örnekleri, yalnızca kalıcı olacak şekilde yapılandırıldıysa devam edebilir.  Kalıcı olmadan iş akışı devam ettirilemez.  Bir iş akışı iptal edilmediği zaman, son kalıcılık noktası bu yana gerçekleştirilen tüm işler (bellekte) kaybolacaktır. Durdurulan bir iş akışı için durdurulan işleyici, durdurma işleminin tamamlanması nedeniyle özel durum kullanılarak çağrılır. Ancak, Iptal edilen ve sonlandırılan aksine, tamamlanan işleyici çağrılmaz. Durdurulan bir iş akışı durdurulmuş durumda.  
  
 Aşağıdaki örnek bir özel durum oluşturan iş akışını çağırır. Özel durum iş akışı tarafından işlenmemiş ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağırılır. , <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> Özel durum hakkında bilgi sağlamak için denetlenir ve iş akışı sonlandırılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>TryCatch etkinliğiyle özel durumları işleme  

 Bir iş akışı içinde özel durumların işlenmesi etkinlikle gerçekleştirilir <xref:System.Activities.Statements.TryCatch> . <xref:System.Activities.Statements.TryCatch>Etkinlik, <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.Catch> her biri belirli bir türle ilişkili olan etkinliklerin bir koleksiyonunu içerir <xref:System.Exception> . Etkinliğin bölümünde yer alan bir etkinlik tarafından oluşturulan özel durum <xref:System.Activities.Statements.TryCatch.Try%2A> <xref:System.Activities.Statements.TryCatch> koleksiyondaki bir etkinliğin özel durumuyla eşleşiyorsa <xref:System.Activities.Statements.Catch%601> <xref:System.Activities.Statements.TryCatch.Catches%2A> , özel durum işlenir. Özel durum açıkça yeniden oluşturulursa veya yeni bir özel durum oluşturulursa, bu özel durum üst etkinliğe geçirilir. Aşağıdaki kod örneğinde, <xref:System.Activities.Statements.TryCatch> <xref:System.ApplicationException> <xref:System.Activities.Statements.TryCatch.Try%2A> bir etkinlik tarafından bölümünde oluşan bir etkinliği işleyen bir etkinlik gösterilmektedir <xref:System.Activities.Statements.Throw> . Özel durumun iletisi, etkinlik tarafından konsola yazılır <xref:System.Activities.Statements.Catch%601> ve ardından, bölümündeki konsola bir ileti yazılır <xref:System.Activities.Statements.TryCatch.Finally%2A> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Bölümündeki etkinlikler, <xref:System.Activities.Statements.TryCatch.Finally%2A> <xref:System.Activities.Statements.TryCatch.Try%2A> bölüm ya da <xref:System.Activities.Statements.TryCatch.Catches%2A> bölüm başarıyla tamamlandığında yürütülür. <xref:System.Activities.Statements.TryCatch.Try%2A>Bu bölüm, bundan hiçbir özel durum atılmadı ve bu bölüm, <xref:System.Activities.Statements.TryCatch.Catches%2A> herhangi bir özel durum atılmadı veya yeniden oluşturulursa bölüm başarıyla tamamlanır. Bir özel durum ' <xref:System.Activities.Statements.TryCatch.Try%2A> a bölümünde oluşturulursa <xref:System.Activities.Statements.TryCatch> ve bölümünde bir ile işlenmezse <xref:System.Activities.Statements.Catch%601> veya ' <xref:System.Activities.Statements.TryCatch.Catches%2A> den yeniden oluşturulursa, ' <xref:System.Activities.Statements.TryCatch.Catches%2A> deki etkinlikler, <xref:System.Activities.Statements.TryCatch.Finally%2A> aşağıdakilerden biri gerçekleşmediği takdirde yürütülmeyecektir.  
  
- Özel durum, <xref:System.Activities.Statements.TryCatch> Bu üst düzeyden yeniden oluşturulup oluşturulmayacağını bağımsız olarak iş akışında daha yüksek düzey bir etkinlik tarafından yakalanır <xref:System.Activities.Statements.TryCatch> .  
  
- Özel durum daha yüksek bir düzeyde işlenmez <xref:System.Activities.Statements.TryCatch> , iş akışının kökünü çıkar ve iş akışı Sonlandır veya Durdur yerine iptal etmek üzere yapılandırılır. Kullanılarak barındırılan iş akışları <xref:System.Activities.WorkflowApplication> , işleme <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ve döndürerek bunu yapılandırabilir <xref:System.Activities.UnhandledExceptionAction.Cancel> . <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>Bu konuda daha önce bir işleme örneği verilmiştir. İş akışı hizmetleri, kullanarak <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve belirterek bunu yapılandırabilir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> . Yapılandırma örneği için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](../wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Özel durum Işleme ve Dengeleme  

 Özel durum işleme ve dengeleme arasındaki fark, bir etkinliğin yürütülmesi sırasında özel durum işlemenin meydana geldi. Bir etkinlik başarıyla tamamlandıktan sonra Dengeleme oluşur. Özel durum işleme, etkinlik özel durumu harekete geçirdikten sonra temizlik için bir fırsat sağlar, ancak dengeleme, daha önce tamamlanmış bir etkinliğin başarıyla tamamlanmasıyla birlikte geri alınabilecek bir mekanizma sağlar. Daha fazla bilgi için bkz. [Dengeleme](compensation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>
