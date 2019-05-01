---
title: İptal davranışını iş akışlarında modelleme
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8bbd746d40e9114eacd5a752481d5316c3f30e57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934712"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>İptal davranışını iş akışlarında modelleme
Etkinlikler iptal edilemez bir iş akışı içinde örneğin tarafından bir <xref:System.Activities.Statements.Parallel> tamamlanmamış dalları iptal etkinlik zaman kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> değerlendiren `true`, veya konak çağırırsa iş akışının dışında <xref:System.Activities.WorkflowApplication.Cancel%2A>. İptal işleme sağlamak için iş akışı yazarları kullanabilirsiniz <xref:System.Activities.Statements.CancellationScope> etkinliği <xref:System.Activities.Statements.CompensableActivity> etkinliği veya iptal etme mantığı sağlayan özel etkinlikler oluşturur. Bu konu, iş akışlarında iptal genel bir bakış sağlar.  
  
## <a name="cancellation-compensation-and-transactions"></a>İptal ve telafi işlemleri  
 İşlem, uygulamanızı (geri alma) işlem işlemi sırasında herhangi bir bölümü herhangi bir hata meydana gelirse işlem içinde yürütülen tüm değişiklikleri iptal etmek için olanağı sunar. Ancak, iptal ya da geri gerekebilir tüm çalışma, uzun süre çalışan iş ya da işlem kaynakları içermeyen çalışma gibi işlemler için uygundur. İş akışında bir sonraki hata olursa maaş alma daha önce Tamamlanan işlem olmayan işler için bir model sağlar. İptal, iş akışı için bir modeli sağlar ve işlem olmayan işlemek için etkinlik yazarlar, tamamlanmadı çalışır. Varsa bir etkinlik yürütmesi tamamlanmadı ve iptal edildi, kendi iptal mantığına çağrılır.  
  
> [!NOTE]
>  İşlemler ve Dengeleme hakkında daha fazla bilgi için bkz: [işlemleri](workflow-transactions.md) ve [maaş](compensation.md).  
  
## <a name="using-cancellationscope"></a>CancellationScope kullanma  
 <xref:System.Activities.Statements.CancellationScope> Etkinlik alt etkinlikleri içeren iki bölüm içerir: <xref:System.Activities.Statements.CancellationScope.Body%2A> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Etkinlik mantığı oluşturma etkinliklerinin yerleştirildiği olduğu ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> için etkinlik iptal etme mantığı sağlayan etkinlikler yerleştirildiği olduğu. Tamamlanmadı yalnızca, bir etkinlik iptal edilebilir. Durumunda, <xref:System.Activities.Statements.CancellationScope> etkinliği tamamlama etkinliklerin tamamlanmasını başvurduğu <xref:System.Activities.Statements.CancellationScope.Body%2A>. Bir iptal isteğine zamanlanırsa ve etkinlikleri <xref:System.Activities.Statements.CancellationScope.Body%2A> tamamlamadıysanız, ardından <xref:System.Activities.Statements.CancellationScope> olarak işaretlenecek <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinlikleri yürütülür.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Bir iş akışı ana bilgisayarından iptal ediliyor  
 Bir konağa bir iş akışı çağırarak iptal edebilirsiniz <xref:System.Activities.WorkflowApplication.Cancel%2A> yöntemi <xref:System.Activities.WorkflowApplication> iş akışı barındırma örneği. Sahip bir iş akışı oluşturulur aşağıdaki örnekte bir <xref:System.Activities.Statements.CancellationScope>. İş akışı çağrılır ve ardından konak çağrıda <xref:System.Activities.WorkflowApplication.Cancel%2A>. Ana iş akışlarının yürütülmesini durdurulmuş, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , <xref:System.Activities.Statements.CancellationScope> çağrılır, ve ardından durumuyla iş akışının tamamlanmasının <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**CancellationHandler çağrılır.**   
**İş akışı b30ebb30-df46-4d90-a211-e31c38d8db3c iptal edildi.**    
> [!NOTE]
>  Olduğunda bir <xref:System.Activities.Statements.CancellationScope> etkinlik iptal edilir ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> çağrılır, uygun iptal etme mantığı sağlamak için daha önce yapılan iptal edilen etkinlik iptal edildi ilerleme durumunu belirlemek için iş akışı Yazar sorumluluğundadır. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> İptal edilen etkinlik ilerleme durumu ile ilgili herhangi bir bilgi sağlamaz.  
  
 İşlenmeyen bir özel durum oluşturan iş akışı kök Balonlar, bir iş akışı ana bilgisayarından iptal edilebilir ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicisini döndürür <xref:System.Activities.UnhandledExceptionAction.Cancel>. Bu örnekte, iş akışı başlatır ve ardından oluşturur bir <xref:System.ApplicationException>. Bu durum, iş akışı tarafından işlenmeyen ve böylece <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicisi çağrılır. Çalışma zamanının iş akışını iptal işleyicisi bildirir ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> şu anda yürütmenin <xref:System.Activities.Statements.CancellationScope> etkinlik çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**OnUnhandledException içinde iş akışı 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**   
**ApplicationException bir durum oluştu.**   
**CancellationHandler çağrılır.**   
**İş akışı 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 iptal edildi.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>İçinde bir iş akışı etkinliği iptal ediliyor  
 Bir etkinliğin üst öğesi tarafından iptal edilebilir. Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinliğinde birden çok yürütme dalları ve kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> değerlendiren `true` tamamlanmamış dalların iptal edilecek sonra. Bu örnekte bir <xref:System.Activities.Statements.Parallel> etkinlik sahip iki dal oluşturulur. Kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ayarlanır `true` böylece <xref:System.Activities.Statements.Parallel> dalların herhangi biri tamamlandıktan hemen sonra tamamlar. Bu örnekte dal 2 tamamlanır ve bu nedenle şube 1 iptal edildi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **Dal 1 başlatılıyor.**  
**Dal 2 tamamlandı.**   
**1 dal iptal edildi.**   
**İş akışı e0685e24-18ef-4a47-acf3-5c638732f3be tamamlandı.**  Bir özel durum oluşturan etkinliğin kök Balonlar ancak iş akışındaki daha yüksek düzeyde işlenen etkinlikleri de iptal edilir. Bu örnekte, iş akışı ana mantığını oluşan bir <xref:System.Activities.Statements.Sequence> etkinlik. <xref:System.Activities.Statements.Sequence> Olarak belirtilen <xref:System.Activities.Statements.CancellationScope.Body%2A> , bir <xref:System.Activities.Statements.CancellationScope> tarafından bulunan bir etkinlik bir <xref:System.Activities.Statements.TryCatch> etkinlik. Gövdesinden bir özel durum <xref:System.Activities.Statements.Sequence>, üst öğe tarafından işlenen <xref:System.Activities.Statements.TryCatch> etkinliği ve <xref:System.Activities.Statements.Sequence> iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **Başlangıç dizisi.**  
**Dizisi iptal edildi.**   
**Özel durum yakalandı.**   
**İş akışı e3c18939-121e-4c43-af1c-ba1ce977ce55 tamamlandı.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Bir CancellationHandler özel durumları atma  
 Şuradan oluşturulduğu özel durumların <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , bir <xref:System.Activities.Statements.CancellationScope> iş akışı için önemli olan. Gelen kaçış özel durumların olasılığı varsa bir <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, kullanan bir <xref:System.Activities.Statements.TryCatch> içinde <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> catch ve bu özel durumları işlemek için.  
  
### <a name="cancellation-using-compensableactivity"></a>CompensableActivity kullanarak iptal  
 Gibi <xref:System.Activities.Statements.CancellationScope> etkinliği <xref:System.Activities.Statements.CompensableActivity> sahip bir <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Varsa bir <xref:System.Activities.Statements.CompensableActivity> iptal edilen herhangi bir etkinlik kendi <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır. Kısmen tamamlanan geri alma compensable işler için yararlı olabilir. Nasıl kullanılacağı hakkında daha fazla bilgi için <xref:System.Activities.Statements.CompensableActivity> maaş ve iptal için bkz: [maaş](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>İptal özel etkinlikler kullanma  
 Özel Etkinlik yazarlar, kendi özel etkinliklerine birkaç farklı yolla iptal etme mantığı uygulayabilir. Öğesinden türetilen özel etkinlikler <xref:System.Activities.Activity> yerleştirerek iptal etme mantığı uygulayabilir bir <xref:System.Activities.Statements.CancellationScope> veya etkinlik gövdesinde iptal etme mantığı içeren başka bir özel etkinliği. <xref:System.Activities.AsyncCodeActivity> ve <xref:System.Activities.NativeActivity> türetilmiş etkinlikleri, ilgili kılabilir <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi ve iptal etme mantığı sağlar. <xref:System.Activities.CodeActivity> türetilmiş etkinlik herhangi sağlama iptal için çalışma zamanı çağırdığında, tüm çalışmasını tek bir yürütme veri bloğunda yapıldığından sağlamaz <xref:System.Activities.CodeActivity.Execute%2A> yöntemi. Yürütme yönteminin henüz çağrılmadıysa gerekiyorsa ve bir <xref:System.Activities.CodeActivity> göre etkinlik iptal edildi, etkinlik durumu olan kapatır <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.CodeActivity.Execute%2A> yöntemi çağrılmadı.  
  
### <a name="cancellation-using-nativeactivity"></a>NativeActivity kullanarak iptal  
 <xref:System.Activities.NativeActivity> türetilmiş etkinlik geçersiz kılma <xref:System.Activities.NativeActivity.Cancel%2A> özel iptal etme mantığı sağlamaya yöntemi. Bu yöntem kılınmazsa, ardından varsayılan iş akışı iptal etme mantığı uygulanır. Varsayılan iptal işlemdir için oluşan bir <xref:System.Activities.NativeActivity> , Geçersiz Kılmıyor <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi veya özelliği <xref:System.Activities.NativeActivity.Cancel%2A> taban yöntemini çağırır <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi. Bir etkinlik iptal edildiğinde, çalışma zamanı etkinlik iptal bayraklar ve belirli temizleme otomatik olarak işler. Bekleyen yer işaretleri etkinliğinde yalnızca yer işaretleri kaldırılacak ve etkinlik olarak işaretlenmiş <xref:System.Activities.ActivityInstanceState.Canceled>. Tüm bekleyen alt etkinlik iptal edilmiş etkinliğin sırayla iptal edilir. Ek alt etkinlikler zamanlamak için her türlü girişim yoksayılıyor denemede neden olur ve etkinlik olarak işaretlenmiş <xref:System.Activities.ActivityInstanceState.Canceled>. Tüm bekleyen bir alt etkinlik tamamlanırsa <xref:System.Activities.ActivityInstanceState.Canceled> veya <xref:System.Activities.ActivityInstanceState.Faulted> etkinlik olarak işaretlenmiş sonra durum <xref:System.Activities.ActivityInstanceState.Canceled>. Bir iptal isteğine yoksayılabilir unutmayın. Bir etkinlik herhangi bir bekleyen yer işaretleri veya yürütme çocuk etkinliklerinin yok ve herhangi bir ek çalışma öğesi iptal için işaretlenmiş sonra zamanlayamazsınız, başarıyla tamamlanır. Birçok senaryo için bu varsayılan iptal soneklerini belirttiniz, ancak ek iptal etme mantığı gerekli olursa, daha sonra iptal yerleşik etkinlikler veya özel etkinlikler kullanılabilir.  
  
 Aşağıdaki örnekte, <xref:System.Activities.NativeActivity.Cancel%2A> , geçersiz bir <xref:System.Activities.NativeActivity> özel tabanlı `ParallelForEach` etkinlik tanımlanır. Etkinlik iptal edildiğinde bu geçersiz kılma etkinliğinin iptal etme mantığı işler. Bu örneğin parçasıdır [genel olmayan ParallelForEach](./samples/non-generic-parallelforeach.md) örnek.  
  
```csharp  
protected override void Cancel(NativeActivityContext context)  
{  
    // If we do not have a completion condition then we can just  
    // use default logic.  
    if (this.CompletionCondition == null)  
    {  
        base.Cancel(context);  
    }  
    else  
    {  
        context.CancelChildren();  
    }  
}  
```  
  
 <xref:System.Activities.NativeActivity> türetilmiş etkinlikleri belirleyebilir inceleyerek iptal isteğinde varsa <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> özelliği ve kendilerini çağırarak iptal edildi olarak işaretle <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> yöntemi. Çağırma <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> hemen etkinlik tamamlanmazsa. Her zamanki şekilde çalışma zamanı etkinlik artık bekleyen iş olduğunda ancak tamamlayacak <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> en son çağrılır durumu olacaktır <xref:System.Activities.ActivityInstanceState.Canceled> yerine <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>İptal AsyncCodeActivity kullanma  
 <xref:System.Activities.AsyncCodeActivity> tabanlı etkinlikler de sağlayabilir özel iptal etme mantığı geçersiz kılarak <xref:System.Activities.AsyncCodeActivity.Cancel%2A> yöntemi. Bu yöntem kılınmazsa, etkinlik iptal edildiğinde İptal hiçbir işleme gerçekleştirilir. Aşağıdaki örnekte, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> , geçersiz bir <xref:System.Activities.AsyncCodeActivity> özel tabanlı `ExecutePowerShell` etkinlik tanımlanır. Etkinlik iptal edildiğinde, istenen iptal davranışını gerçekleştirir.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlikleri belirleyebilir inceleyerek iptal isteğinde varsa <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> özelliği ve kendilerini çağırarak iptal edildi olarak işaretle <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> yöntemi.
