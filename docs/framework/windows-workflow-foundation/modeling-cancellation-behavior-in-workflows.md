---
title: Iş akışlarında modelleme Iptali davranışı
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 157bff0d24b00f293fd551dd52fe693d36dfad61
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242064"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Iş akışlarında modelleme Iptali davranışı

Etkinlikler, bir iş akışı içinde iptal edilebilir. Örneğin, bir etkinlik, bir işlem tarafından <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> `true` , ya değerlendirildiğinde ya da iş akışının dışından, ana bilgisayar çağırırsa <xref:System.Activities.WorkflowApplication.Cancel%2A> . İş akışı yazarları iptal işleme sağlamak için <xref:System.Activities.Statements.CancellationScope> etkinliği, <xref:System.Activities.Statements.CompensableActivity> etkinliği veya iptal mantığı sağlayan özel etkinlikler oluşturabilir. Bu konuda, iş akışlarında iptale bir genel bakış sunulmaktadır.  
  
## <a name="cancellation-compensation-and-transactions"></a>İptal, Dengeleme ve Işlemler  

 İşlemler, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlem içinde yürütülen tüm değişiklikleri (geri alma) sağlar. Bununla birlikte, iptal edilmesi veya geri yüklenmesi gerekebilecek tüm işler, uzun süreli çalışma veya işlem kaynakları içermeyen iş gibi işlemler için uygundur. Dengeleme, iş akışında sonraki bir hata varsa, daha önce tamamlanmış işlem dışı çalışmayı geri almak için bir model sağlar. İptal işlemi, tamamlanmamış çalışmayı işlemek için iş akışı ve etkinlik yazarları için bir model sağlar. Bir etkinlik yürütmesini tamamlamamışsa ve iptal edilirse, varsa iptal mantığı çağrılır.  
  
> [!NOTE]
> İşlemler ve dengeleme hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md) ve [Dengeleme](compensation.md).  
  
## <a name="using-cancellationscope"></a>CancellationScope Kullanma  

 <xref:System.Activities.Statements.CancellationScope>Etkinliğin alt etkinlikleri içerebilen iki bölümü vardır: <xref:System.Activities.Statements.CancellationScope.Body%2A> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> . , <xref:System.Activities.Statements.CancellationScope.Body%2A> Etkinliğin mantığını oluşturan etkinliklerin yerleştirildiği ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinlik için iptal mantığı sağlayan etkinliklerin yerleştirildiği yer olduğu yerdir. Bir etkinlik yalnızca tamamlanmayan iptal edilebilir. Etkinlik durumunda, <xref:System.Activities.Statements.CancellationScope> tamamlama içindeki etkinliklerin tamamlanmasını ifade eder <xref:System.Activities.Statements.CancellationScope.Body%2A> . Bir iptal isteği zamanlanırsa ve içindeki etkinlikler <xref:System.Activities.Statements.CancellationScope.Body%2A> tamamlanmamışsa, <xref:System.Activities.Statements.CancellationScope> olarak işaretlenir <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Etkinlikler yürütülür.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Konaktan bir Iş akışını iptal etme  

 Bir konak <xref:System.Activities.WorkflowApplication.Cancel%2A> , iş akışını barındıran örneğin yöntemini çağırarak bir iş akışını iptal edebilir <xref:System.Activities.WorkflowApplication> . Aşağıdaki örnekte, içeren bir iş akışı oluşturulur <xref:System.Activities.Statements.CancellationScope> . İş akışı çağrılır, sonra ana bilgisayar öğesine bir çağrı yapar <xref:System.Activities.WorkflowApplication.Cancel%2A> . İş akışının ana yürütmesi durdurulur, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> öğesinin <xref:System.Activities.Statements.CancellationScope> çağrılır ve sonra iş akışı durumu ile tamamlanır <xref:System.Activities.ActivityInstanceState.Canceled> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**CancellationHandler çağrıldı.** 
 **Iş akışı B30ebb30-df46-4d90-A211-e31c38d8db3c Iptal edildi.**
> [!NOTE]
> Bir <xref:System.Activities.Statements.CancellationScope> etkinlik iptal edildiğinde ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> çağrıldığında, iptal edilen etkinliğin uygun iptal mantığını sağlamak üzere iptal edilmeden önce yaptığı ilerlemeyi belirlemede iş akışı yazarının sorumluluğundadır. , <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> İptal edilen etkinliğin ilerlemesi hakkında herhangi bir bilgi sağlamaz.  
  
 İşlenmemiş bir özel durum kabarcıkları, iş akışının kökünü aşıp işleyicinin döndürdüğü takdirde, bir iş akışı konaktan de iptal edilebilir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> <xref:System.Activities.UnhandledExceptionAction.Cancel> . Bu örnekte, iş akışı başlar ve sonra bir oluşturur <xref:System.ApplicationException> . Bu özel durum iş akışı tarafından işlenmemiş olduğundan <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicinin çağrılması. İşleyici, çalışma zamanına iş akışını iptal eder ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Şu anda yürütülmekte olan <xref:System.Activities.Statements.CancellationScope> etkinliğin çağırılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**Iş akışında OnUnhandledException, 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9** 
 **ApplicationException oluşturuldu.** 
 **CancellationHandler çağrıldı.** 
 **Workflow 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 Iptal edildi.**

### <a name="canceling-an-activity-from-inside-a-workflow"></a>Iş akışının Içinden etkinlik iptal ediliyor  

 Etkinlik, üst öğesi tarafından da iptal edilebilir. Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinliğin birden fazla çalışan dalı varsa ve bu <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> durumda, onun `true` eksik dalları iptal edilir. Bu örnekte <xref:System.Activities.Statements.Parallel> , iki dalı olan bir etkinlik oluşturulur. , <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> `true` <xref:System.Activities.Statements.Parallel> Dallarından herhangi biri tamamlandıktan hemen sonra tamamlanmasını sağlayacak şekilde ayarlanmıştır. Bu örnekte 2. dal tamamlandığında, 1. dal iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Şube 1 başlatılıyor.**  
**2. dal tamam.** 
 **Şube 1 iptal edildi.** 
 **Iş akışı E0685e24-18ef-4A47-acf3-5c638732f3be tamamlandı.**  Etkinlik, etkinliğin kökünün ötesinde, ancak iş akışında daha yüksek bir düzeyde işlenirse etkinlikler de iptal edilir. Bu örnekte, iş akışının ana mantığı bir <xref:System.Activities.Statements.Sequence> etkinlikten oluşur. , <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope> Bir etkinliğin içerdiği bir etkinliğin ' i olarak belirtilir <xref:System.Activities.Statements.TryCatch> . Öğesinin gövdesinden bir özel durum oluşturulur, <xref:System.Activities.Statements.Sequence> üst etkinlik tarafından işlenir <xref:System.Activities.Statements.TryCatch> ve <xref:System.Activities.Statements.Sequence> iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Sıra başlatılıyor.**  
**Sıra iptal edildi.** 
 **Özel durum yakalandı.** 
 **Iş akışı E3c18939-121E-4c43-af1c-ba1ce977ce55 tamamlandı.**

### <a name="throwing-exceptions-from-a-cancellationhandler"></a>CancellationHandler 'dan özel durumlar oluşturma  

 Kaynağından oluşan tüm özel durumlar <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> iş akışı için önemli değildir. Bir için özel durum kaçış olasılığı varsa, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Bu özel durumları yakalamak ve işlemek için içinde bir kullanın.  
  
### <a name="cancellation-using-compensableactivity"></a>CompensableActivity kullanarak iptal etme  

 Etkinlik gibi, öğesine <xref:System.Activities.Statements.CancellationScope> <xref:System.Activities.Statements.CompensableActivity> sahiptir <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> . Bir <xref:System.Activities.Statements.CompensableActivity> iptal edilirse, içindeki herhangi bir etkinlik <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır. Bu, kısmen tamamlanmış dengelenebilir çalışmayı geri almak için yararlı olabilir. Dengeleme ve iptal için kullanma hakkında daha fazla bilgi için <xref:System.Activities.Statements.CompensableActivity> bkz. [Dengeleme](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Özel etkinlikleri kullanarak iptal etme  

 Özel etkinlik yazarları, özel etkinliklerine birkaç farklı şekilde iptal mantığı uygulayabilir. Öğesinden türetilen özel etkinlikler, <xref:System.Activities.Activity> <xref:System.Activities.Statements.CancellationScope> etkinliğin gövdesinde iptal mantığı içeren bir veya başka bir özel etkinlik yerleştirerek iptal mantığını uygulayabilir. <xref:System.Activities.AsyncCodeActivity> ve <xref:System.Activities.NativeActivity> türetilmiş etkinlikler ilgili yöntemini geçersiz kılabilir <xref:System.Activities.NativeActivity.Cancel%2A> ve burada iptal mantığı sağlayabilir. <xref:System.Activities.CodeActivity> çalışma zamanı yöntemi çağırdığında, tüm işleri tek bir yürütme veri bloğu içinde gerçekleştirildiğinden, türetilmiş etkinlikler iptal için herhangi bir sağlama sağlamaz <xref:System.Activities.CodeActivity.Execute%2A> . Execute yöntemi henüz çağrılmadıysa ve bir <xref:System.Activities.CodeActivity> tabanlı etkinlik iptal edilirse, etkinlik durumu ile kapanır <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.CodeActivity.Execute%2A> yöntemi çağrılmaz.  
  
### <a name="cancellation-using-nativeactivity"></a>NativeActivity kullanarak iptal etme  

 <xref:System.Activities.NativeActivity> türetilmiş etkinlikler <xref:System.Activities.NativeActivity.Cancel%2A> özel iptal mantığı sağlamak için yöntemini geçersiz kılabilir. Bu yöntem geçersiz kılınmamışsa, varsayılan iş akışı iptali mantığı uygulanır. Varsayılan iptal, <xref:System.Activities.NativeActivity> yöntemi geçersiz kılmayan <xref:System.Activities.NativeActivity.Cancel%2A> veya <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi temel yöntemi çağıran bir <xref:System.Activities.NativeActivity> için gerçekleşen işlemdir <xref:System.Activities.NativeActivity.Cancel%2A> . Bir etkinlik iptal edildiğinde, çalışma zamanı iptal için etkinliği işaretler ve belirli temizleme işlemini otomatik olarak işler. Etkinliğin yalnızca bekleyen yer işaretleri varsa, yer işaretleri kaldırılır ve etkinlik olarak işaretlenir <xref:System.Activities.ActivityInstanceState.Canceled> . İptal edilen etkinliğin bekleyen tüm alt etkinlikleri iptal edilecek. Ek alt etkinliklerin planlanmasına yönelik herhangi bir girişim, denenmesine ve etkinliğin olarak işaretlenmesine neden olur <xref:System.Activities.ActivityInstanceState.Canceled> . Veya durumunda herhangi bir bekleyen alt etkinlik tamamlanırsa <xref:System.Activities.ActivityInstanceState.Canceled> <xref:System.Activities.ActivityInstanceState.Faulted> , etkinlik olarak işaretlenir <xref:System.Activities.ActivityInstanceState.Canceled> . İptal isteğinin yoksayılıp yoksayılmadığını unutmayın. Bir etkinlik bekleyen yer işaretlerine sahip değilse veya alt etkinlikleri yürütüp, iptal için işaretlendikten sonra ek iş öğeleri zamanlayamaz, işlem başarıyla tamamlanır. Bu varsayılan iptal, birçok senaryo için yeterli olacaktır, ancak ek iptal mantığı gerekliyse, yerleşik iptal etkinlikleri veya özel etkinlikler kullanılabilir.  
  
 Aşağıdaki örnekte, <xref:System.Activities.NativeActivity.Cancel%2A> bir <xref:System.Activities.NativeActivity> tabanlı özel etkinliğin geçersiz kılınması `ParallelForEach` tanımlanmıştır. Etkinlik iptal edildiğinde, bu geçersiz kılma etkinliğin iptal mantığını işler. Bu örnek, [genel olmayan ParallelForEach](./samples/non-generic-parallelforeach.md) örneğinin bir parçasıdır.  
  
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
  
 <xref:System.Activities.NativeActivity> türetilmiş etkinlikler, özelliği inceleyerek iptal edilip edilmediğini tespit edebilir <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> ve yöntemi çağırarak, iptal edildi olarak işaretleyebilir <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> . Çağırma <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> etkinliği hemen tamamlamaz. Her zamanki gibi, çalışma zamanı daha fazla bekleyen iş olmadığında etkinliği tamamlar, ancak eğer <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> çağrılırsa son durum <xref:System.Activities.ActivityInstanceState.Canceled> yerine gelir <xref:System.Activities.ActivityInstanceState.Closed> .  
  
### <a name="cancellation-using-asynccodeactivity"></a>AsyncCodeActivity kullanarak iptal etme  

 <xref:System.Activities.AsyncCodeActivity> tabanlı etkinlikler, yöntemi geçersiz kılarak özel iptal mantığı da sağlayabilir <xref:System.Activities.AsyncCodeActivity.Cancel%2A> . Bu yöntem geçersiz kılınmamışsa, etkinlik iptal edildiğinde iptal işlemi gerçekleştirilmez. Aşağıdaki örnekte, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> bir <xref:System.Activities.AsyncCodeActivity> tabanlı özel etkinliğin geçersiz kılınması `ExecutePowerShell` tanımlanmıştır. Etkinlik iptal edildiğinde, istenen iptal davranışını gerçekleştirir.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlikler, özelliği inceleyerek iptal edilip edilmediğini tespit edebilir <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> ve yöntemi çağırarak, iptal edildi olarak işaretleyebilir <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> .
