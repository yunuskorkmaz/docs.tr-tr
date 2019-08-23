---
title: Iş akışlarında modelleme Iptali davranışı
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: ec0cf810693e2eda01a4c489b6eb938538719228
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965944"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Iş akışlarında modelleme Iptali davranışı
Etkinlikler, bir iş akışı içinde iptal edilebilir. Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinlik <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> , bir işlem tarafından `true`, ya değerlendirildiğinde ya da iş akışının dışından, ana bilgisayar çağırırsa <xref:System.Activities.WorkflowApplication.Cancel%2A>. İş akışı yazarları <xref:System.Activities.Statements.CancellationScope> iptal işleme sağlamak için etkinliği <xref:System.Activities.Statements.CompensableActivity> , etkinliği veya iptal mantığı sağlayan özel etkinlikler oluşturabilir. Bu konuda, iş akışlarında iptale bir genel bakış sunulmaktadır.  
  
## <a name="cancellation-compensation-and-transactions"></a>İptal, Dengeleme ve Işlemler  
 İşlemler, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlem içinde yürütülen tüm değişiklikleri (geri alma) sağlar. Bununla birlikte, iptal edilmesi veya geri yüklenmesi gerekebilecek tüm işler, uzun süreli çalışma veya işlem kaynakları içermeyen iş gibi işlemler için uygundur. Dengeleme, iş akışında sonraki bir hata varsa, daha önce tamamlanmış işlem dışı çalışmayı geri almak için bir model sağlar. İptal işlemi, tamamlanmamış çalışmayı işlemek için iş akışı ve etkinlik yazarları için bir model sağlar. Bir etkinlik yürütmesini tamamlamamışsa ve iptal edilirse, varsa iptal mantığı çağrılır.  
  
> [!NOTE]
> İşlemler ve dengeleme hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md) ve [Dengeleme](compensation.md).  
  
## <a name="using-cancellationscope"></a>CancellationScope kullanma  
 Etkinliğin alt etkinlikleri içerebilen iki bölümü vardır: <xref:System.Activities.Statements.CancellationScope.Body%2A> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope> , <xref:System.Activities.Statements.CancellationScope.Body%2A> Etkinliğin mantığını oluşturan etkinliklerin yerleştirildiği <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> ve etkinlik için iptal mantığı sağlayan etkinliklerin yerleştirildiği yer olduğu yerdir. Bir etkinlik yalnızca tamamlanmayan iptal edilebilir. <xref:System.Activities.Statements.CancellationScope> Etkinlik durumunda, tamamlama <xref:System.Activities.Statements.CancellationScope.Body%2A>içindeki etkinliklerin tamamlanmasını ifade eder. Bir <xref:System.Activities.Statements.CancellationScope.Body%2A> iptal isteği zamanlanırsa ve içindeki etkinlikler tamamlanmamışsa <xref:System.Activities.Statements.CancellationScope> , olarak <xref:System.Activities.ActivityInstanceState.Canceled> işaretlenir ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinlikler yürütülür.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Konaktan bir Iş akışını iptal etme  
 Bir konak, iş akışını barındıran <xref:System.Activities.WorkflowApplication.Cancel%2A> <xref:System.Activities.WorkflowApplication> örneğin yöntemini çağırarak bir iş akışını iptal edebilir. Aşağıdaki örnekte, <xref:System.Activities.Statements.CancellationScope>içeren bir iş akışı oluşturulur. İş akışı çağrılır, sonra ana bilgisayar öğesine <xref:System.Activities.WorkflowApplication.Cancel%2A>bir çağrı yapar. İş akışının ana yürütmesi durdurulur, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> öğesinin çağrılır ve sonra iş akışı durumu ile <xref:System.Activities.ActivityInstanceState.Canceled>tamamlanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**CancellationHandler çağrıldı.**    
**İş akışı b30ebb30-df46-4d90-A211-e31c38d8db3c Iptal edildi.**    
> [!NOTE]
> Bir <xref:System.Activities.Statements.CancellationScope> etkinlik iptal edildiğinde <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> ve çağrıldığında, iptal edilen etkinliğin uygun iptal mantığını sağlamak üzere iptal edilmeden önce yaptığı ilerlemeyi belirlemede iş akışı yazarının sorumluluğundadır. , <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> İptal edilen etkinliğin ilerlemesi hakkında herhangi bir bilgi sağlamaz.  
  
 İşlenmemiş bir özel durum kabarcıkları, iş akışının kökünü aşıp <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicinin döndürdüğü <xref:System.Activities.UnhandledExceptionAction.Cancel>takdirde, bir iş akışı konaktan de iptal edilebilir. Bu örnekte, iş akışı başlar ve sonra bir <xref:System.ApplicationException>oluşturur. Bu özel durum iş akışı <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> tarafından işlenmemiş olduğundan işleyicinin çağrılması. İşleyici, çalışma zamanına iş akışını iptal eder ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Şu anda yürütülmekte <xref:System.Activities.Statements.CancellationScope> olan etkinliğin çağırılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**Iş akışında OnUnhandledException, 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**   
**ApplicationException oluşturuldu.**    
**CancellationHandler çağrıldı.**    
**Workflow 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 Iptal edildi.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Iş akışının Içinden etkinlik iptal ediliyor  
 Etkinlik, üst öğesi tarafından da iptal edilebilir. Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinliğin birden fazla çalışan dalı varsa ve bu `true` durumda <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> , onun eksik dalları iptal edilir. Bu örnekte, iki <xref:System.Activities.Statements.Parallel> dalı olan bir etkinlik oluşturulur. , Dallarından herhangi `true` biri tamamlandıktan <xref:System.Activities.Statements.Parallel> hemen sonra tamamlanmasını sağlayacak şekilde ayarlanmıştır. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Bu örnekte 2. dal tamamlandığında, 1. dal iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Şube 1 başlatılıyor.**  
**2. dal tamam.**    
**Şube 1 iptal edildi.**    
**İş akışı e0685e24-18ef-4A47-acf3-5c638732f3be tamamlandı.**  Etkinlik, etkinliğin kökünün ötesinde, ancak iş akışında daha yüksek bir düzeyde işlenirse etkinlikler de iptal edilir. Bu örnekte, iş akışının ana mantığı bir <xref:System.Activities.Statements.Sequence> etkinlikten oluşur. , <xref:System.Activities.Statements.Sequence> Bir <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope> etkinliğin içerdiğibiretkinliğin'iolarakbelirtilir.<xref:System.Activities.Statements.TryCatch> Öğesinin <xref:System.Activities.Statements.Sequence>gövdesinden bir özel durum oluşturulur, üst <xref:System.Activities.Statements.TryCatch> etkinlik tarafından işlenir ve <xref:System.Activities.Statements.Sequence> iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Sıra başlatılıyor.**  
**Sıra iptal edildi.**    
**Özel durum yakalandı.**    
**İş akışı e3c18939-121E-4c43-af1c-ba1ce977ce55 tamamlandı.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>CancellationHandler 'dan özel durumlar oluşturma  
 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Kaynağından<xref:System.Activities.Statements.CancellationScope> oluşan tüm özel durumlar iş akışı için önemli değildir. Bir <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> için özel durum kaçış olasılığı varsa, bu özel durumları yakalamak ve <xref:System.Activities.Statements.TryCatch> işlemek için içinde bir kullanın.  
  
### <a name="cancellation-using-compensableactivity"></a>CompensableActivity kullanarak iptal etme  
 Etkinlik gibi, öğesine <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>sahiptir. <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CancellationScope> Bir <xref:System.Activities.Statements.CompensableActivity> iptal edilirse, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> içindeki herhangi bir etkinlik çağrılır. Bu, kısmen tamamlanmış dengelenebilir çalışmayı geri almak için yararlı olabilir. Dengeleme ve iptal için kullanma <xref:System.Activities.Statements.CompensableActivity> hakkında daha fazla bilgi için bkz. [Dengeleme](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Özel etkinlikleri kullanarak iptal etme  
 Özel etkinlik yazarları, özel etkinliklerine birkaç farklı şekilde iptal mantığı uygulayabilir. Öğesinden <xref:System.Activities.Activity> türetilen özel etkinlikler, etkinliğin gövdesinde iptal mantığı içeren bir veya <xref:System.Activities.Statements.CancellationScope> başka bir özel etkinlik yerleştirerek iptal mantığını uygulayabilir. <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity> türetilmiş etkinlikler ilgili <xref:System.Activities.NativeActivity.Cancel%2A> yöntemini geçersiz kılabilir ve burada iptal mantığı sağlayabilir. <xref:System.Activities.CodeActivity>çalışma zamanı <xref:System.Activities.CodeActivity.Execute%2A> yöntemi çağırdığında, tüm işleri tek bir yürütme veri bloğu içinde gerçekleştirildiğinden, türetilmiş etkinlikler iptal için herhangi bir sağlama sağlamaz. Execute yöntemi henüz çağrılmadıysa ve bir <xref:System.Activities.CodeActivity> tabanlı etkinlik iptal edilirse, etkinlik <xref:System.Activities.ActivityInstanceState.Canceled> durumu ile kapanır ve <xref:System.Activities.CodeActivity.Execute%2A> yöntemi çağrılmaz.  
  
### <a name="cancellation-using-nativeactivity"></a>NativeActivity kullanarak iptal etme  
 <xref:System.Activities.NativeActivity>türetilmiş etkinlikler özel iptal mantığı <xref:System.Activities.NativeActivity.Cancel%2A> sağlamak için yöntemini geçersiz kılabilir. Bu yöntem geçersiz kılınmamışsa, varsayılan iş akışı iptali mantığı uygulanır. Varsayılan iptal, <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi geçersiz kılmayan veya <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi <xref:System.Activities.NativeActivity> temel <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi çağıran bir için gerçekleşen işlemdir. Bir etkinlik iptal edildiğinde, çalışma zamanı iptal için etkinliği işaretler ve belirli temizleme işlemini otomatik olarak işler. Etkinliğin yalnızca bekleyen yer işaretleri varsa, yer işaretleri kaldırılır ve etkinlik olarak <xref:System.Activities.ActivityInstanceState.Canceled>işaretlenir. İptal edilen etkinliğin bekleyen tüm alt etkinlikleri iptal edilecek. Ek alt etkinliklerin planlanmasına yönelik herhangi bir girişim, denenmesine ve etkinliğin olarak <xref:System.Activities.ActivityInstanceState.Canceled>işaretlenmesine neden olur. <xref:System.Activities.ActivityInstanceState.Canceled> <xref:System.Activities.ActivityInstanceState.Canceled>Veya durumundaherhangibirbekleyenaltetkinliktamamlanırsa,etkinlikolarakişaretlenir.<xref:System.Activities.ActivityInstanceState.Faulted> İptal isteğinin yoksayılıp yoksayılmadığını unutmayın. Bir etkinlik bekleyen yer işaretlerine sahip değilse veya alt etkinlikleri yürütüp, iptal için işaretlendikten sonra ek iş öğeleri zamanlayamaz, işlem başarıyla tamamlanır. Bu varsayılan iptal, birçok senaryo için yeterli olacaktır, ancak ek iptal mantığı gerekliyse, yerleşik iptal etkinlikleri veya özel etkinlikler kullanılabilir.  
  
 Aşağıdaki örnekte, <xref:System.Activities.NativeActivity.Cancel%2A> bir <xref:System.Activities.NativeActivity> tabanlı özel `ParallelForEach` etkinliğin geçersiz kılınması tanımlanmıştır. Etkinlik iptal edildiğinde, bu geçersiz kılma etkinliğin iptal mantığını işler. Bu örnek, [genel olmayan ParallelForEach](./samples/non-generic-parallelforeach.md) örneğinin bir parçasıdır.  
  
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
  
 <xref:System.Activities.NativeActivity>türetilmiş etkinlikler, <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> özelliği inceleyerek iptal edilip edilmediğini tespit edebilir ve yöntemi çağırarak, <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> iptal edildi olarak işaretleyebilir. Çağırma <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> etkinliği hemen tamamlamaz. Her zamanki gibi, çalışma zamanı daha fazla bekleyen iş olmadığında etkinliği tamamlar, ancak eğer <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> çağrılırsa son durum <xref:System.Activities.ActivityInstanceState.Canceled> yerine <xref:System.Activities.ActivityInstanceState.Closed>gelir.  
  
### <a name="cancellation-using-asynccodeactivity"></a>AsyncCodeActivity kullanarak iptal etme  
 <xref:System.Activities.AsyncCodeActivity>tabanlı etkinlikler, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> yöntemi geçersiz kılarak özel iptal mantığı da sağlayabilir. Bu yöntem geçersiz kılınmamışsa, etkinlik iptal edildiğinde iptal işlemi gerçekleştirilmez. Aşağıdaki örnekte, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> bir <xref:System.Activities.AsyncCodeActivity> tabanlı özel `ExecutePowerShell` etkinliğin geçersiz kılınması tanımlanmıştır. Etkinlik iptal edildiğinde, istenen iptal davranışını gerçekleştirir.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>türetilmiş etkinlikler, <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> özelliği inceleyerek iptal edilip edilmediğini tespit edebilir ve yöntemi çağırarak, <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> iptal edildi olarak işaretleyebilir.
