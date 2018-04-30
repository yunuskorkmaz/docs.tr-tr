---
title: İş akışlarında iptal davranışı modelleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e455bf4d74f77c6cd87301dc9a21f56117777ecf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>İş akışlarında iptal davranışı modelleme
Etkinlikler iptal edilemez bir iş akışı içinde örneğin tarafından bir <xref:System.Activities.Statements.Parallel> tamamlanmamış dalları iptal etme Etkinlik zaman kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> değerlendiren `true`, veya konak çağırırsa iş akışını dışında <xref:System.Activities.WorkflowApplication.Cancel%2A>. İptalleri işleme sağlamak için iş akışı yazarları kullanabilirsiniz <xref:System.Activities.Statements.CancellationScope> etkinliği <xref:System.Activities.Statements.CompensableActivity> etkinliği veya iptal mantığın özel etkinlikler oluşturun. Bu konu, iş akışlarında iptal genel bir bakış sağlar.  
  
## <a name="cancellation-compensation-and-transactions"></a>İptal, maaş ve işlemleri  
 İşlemler, uygulamanızın (geri dön) işlem işleminin herhangi bir bölümü sırasında herhangi bir hata oluşursa işlem içinde yürütülen tüm değişiklikleri iptal etmek için kabiliyeti sağlar. Ancak, iptal edildi veya geri gerekebilir tüm iş uzun süre çalışan iş veya işlem kaynakları içermeyen çalışma gibi işlemler için uygundur. İş akışında bir sonraki hata olduğunda maaş geri alma önceden tamamlanmış işlemsel olmayan iş için bir model sağlar. İptali iş akışı için bir model sağlar ve işlemsel olmayan işlemek için etkinlik yazarlar, tamamlanmadığını çalışır. Varsa, iptal mantığını bir etkinlik yürütülmesinin tamamlanmadı ve iptal edilir, çağrılır.  
  
> [!NOTE]
>  İşlemler ve Dengeleme hakkında daha fazla bilgi için bkz: [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) ve [maaş](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="using-cancellationscope"></a>CancellationScope kullanma  
 <xref:System.Activities.Statements.CancellationScope> Etkinlik alt etkinlikler içeren iki bölümü vardır: <xref:System.Activities.Statements.CancellationScope.Body%2A> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Etkinlik mantığı oluşturan etkinlikler yerleştirildiği olduğu ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinliğini iptal mantığın etkinlikleri yerleştirildiği olduğu. Tamamlanmadı yalnızca, bir etkinlik iptal edilebilir. Durumunda <xref:System.Activities.Statements.CancellationScope> etkinliği tamamlama etkinlikler tamamlandığında başvurduğu <xref:System.Activities.Statements.CancellationScope.Body%2A>. İptal isteği zamanlanırsa ve etkinlikleri <xref:System.Activities.Statements.CancellationScope.Body%2A> tamamlamadıysanız, sonra <xref:System.Activities.Statements.CancellationScope> olarak işaretlenmiş <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinlikleri yürütülür.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Ana bilgisayardan bir iş akışı iptal etme  
 Bir ana iş akışı çağırarak iptal edebilirsiniz <xref:System.Activities.WorkflowApplication.Cancel%2A> yöntemi <xref:System.Activities.WorkflowApplication> iş akışı barındırma örneği. Sahip bir iş akışı oluşturulur aşağıdaki örnekte bir <xref:System.Activities.Statements.CancellationScope>. İş akışı çağrılır ve ardından ana bilgisayar için bir çağrı yapar <xref:System.Activities.WorkflowApplication.Cancel%2A>. İş akışı ana yürütülmesi durdurulduğunda, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , <xref:System.Activities.Statements.CancellationScope> çağrılır, ve ardından iş akışını durumuyla tamamlandığında <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**CancellationHandler çağrılır.**   
**İş akışı b30ebb30-df46-4d90-a211-e31c38d8db3c iptal edildi.**    
> [!NOTE]
>  Zaman bir <xref:System.Activities.Statements.CancellationScope> etkinliği iptal edilir ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> çağrılır, bunu uygun iptal mantığı sağlamak için daha önce yaptığınız iptal edilmiş etkinliği iptal edildi ilerlemesini belirlemek için iş akışı yazarı sorumluluğundadır. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> İptal edilmiş etkinliğin ilerleme durumu ile ilgili herhangi bir bilgi sağlamaz.  
  
 İşlenmeyen bir özel durum iş akışı kök köpürür, bir iş akışı ana bilgisayardan iptal edilebilir ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyicisini döndürür <xref:System.Activities.UnhandledExceptionAction.Cancel>. Bu örnekte, iş akışı başlatıldığında'ı ve ardından oluşturur bir <xref:System.ApplicationException>. Bu özel iş akışı tarafından işlenmeyen ve böylece <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici çağrılır. İş akışı iptal etmek için çalışma zamanı işleyici bildirir ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> şu anda yürütülmekte olan <xref:System.Activities.Statements.CancellationScope> etkinlik çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **İş akışı başlatılıyor.**  
**İş akışı 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 OnUnhandledException**   
**Bir ApplicationException bir durum oluştu.**   
**CancellationHandler çağrılır.**   
**İş akışı 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 iptal edildi.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Bir iş akışı içinde bir etkinlikten iptal etme  
 Bir etkinlik üst tarafından iptal edilebilir. Örneğin, varsa bir <xref:System.Activities.Statements.Parallel> etkinlik sahip birden çok yürütme dalları ve kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> değerlendiren `true` tamamlanmamış dalları iptal edilecek sonra. Bu örnekte bir <xref:System.Activities.Statements.Parallel> etkinlik iki dalı olan oluşturulur. Kendi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ayarlanır `true` böylece <xref:System.Activities.Statements.Parallel> onun dallandırır herhangi biri tamamlandıktan hemen sonra tamamlar. Bu örnekte, şube 2 tamamlandıktan ve bu nedenle şube 1 iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **1 başlangıç dal.**  
**Dal 2 tamamlandı.**   
**Dal 1 iptal edildi.**   
**İş akışı e0685e24-18ef-4a47-acf3-5c638732f3be tamamlandı.**  Bir özel durum yukarı etkinlik kök köpürür ancak iş akışı içinde daha yüksek düzeyde ele etkinlikleri de iptal edilir. Bu örnekte, iş akışı ana mantığını oluşan bir <xref:System.Activities.Statements.Sequence> etkinlik. <xref:System.Activities.Statements.Sequence> Olarak belirtilen <xref:System.Activities.Statements.CancellationScope.Body%2A> , bir <xref:System.Activities.Statements.CancellationScope> tarafından bulunan etkinliği bir <xref:System.Activities.Statements.TryCatch> etkinlik. Gövdesinden bir özel durum <xref:System.Activities.Statements.Sequence>, üst öğe tarafından işlenen <xref:System.Activities.Statements.TryCatch> etkinliği ve <xref:System.Activities.Statements.Sequence> iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **Başlangıç dizisi.**  
**Sıra iptal edildi.**   
**Özel durum oluştu.**   
**İş akışı e3c18939-121e-4c43-af1c-ba1ce977ce55 tamamlandı.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Bir CancellationHandler özel durumları atma  
 Gelen karşılaşılan özel durumlar <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> , bir <xref:System.Activities.Statements.CancellationScope> iş akışı için önemli olan. Gelen kaçış özel durumlar olasılığını ise bir <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, kullanan bir <xref:System.Activities.Statements.TryCatch> içinde <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> yakalamak ve bu özel durumları işlemek için.  
  
### <a name="cancellation-using-compensableactivity"></a>İptal CompensableActivity kullanma  
 Gibi <xref:System.Activities.Statements.CancellationScope> etkinliği <xref:System.Activities.Statements.CompensableActivity> sahip bir <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Varsa bir <xref:System.Activities.Statements.CompensableActivity> iptal edilir, hiç etkinlik kendi <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır. Kısmen tamamlanan geri alma compensable iş için yararlı olabilir. Nasıl kullanılacağı hakkında bilgi için <xref:System.Activities.Statements.CompensableActivity> maaş ve iptal için bkz: [maaş](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Özel etkinlikleri kullanarak iptal  
 Özel Etkinlik yazarlar, kendi özel etkinliklerine birkaç farklı şekillerde iptal mantığı uygulayabilirsiniz. Öğesinden türetilen özel etkinlikler <xref:System.Activities.Activity> koyarak iptal mantığı uygulayabilirsiniz bir <xref:System.Activities.Statements.CancellationScope> veya iptal mantığını etkinliği gövdesinde içeren diğer özel etkinlik. <xref:System.Activities.AsyncCodeActivity> ve <xref:System.Activities.NativeActivity> türetilmiş etkinlikleri kendi ilgili kılabilirsiniz <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi ve iptal mantığı sağlar. <xref:System.Activities.CodeActivity> türetilen etkinlikleri herhangi sağlamak için İptali çalışma zamanı aradığında, iş yürütme tek olarak veri bloğu içinde yapıldığından sağlamaz <xref:System.Activities.CodeActivity.Execute%2A> yöntemi. Execute yöntemi henüz çağrılmadıysa varsa ve <xref:System.Activities.CodeActivity> göre etkinlik iptal edilir, etkinlik durumu olan kapatır <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.CodeActivity.Execute%2A> yöntemi çağrılmaz.  
  
### <a name="cancellation-using-nativeactivity"></a>İptal NativeActivity kullanma  
 <xref:System.Activities.NativeActivity> türetilen etkinlikleri kılabilirsiniz <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi özel iptal mantığı sağlar. Bu yöntem geçersiz değil, varsayılan iş akışı iptal mantığı uygulanır. Varsayılan iptal işlemidir için oluşan bir <xref:System.Activities.NativeActivity> , geçersiz <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi veya özelliği <xref:System.Activities.NativeActivity.Cancel%2A> yöntemini çağırır temel <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi. Bir etkinlik iptal ettiğinizde, çalışma zamanı iptal etkinliğini bayraklar ve belirli temizleme otomatik olarak işler. Etkinlik bekleyen yer işaretleri yalnızca sahip yer işaretleri kaldırılacak ve etkinlik olarak işaretlenmiş <xref:System.Activities.ActivityInstanceState.Canceled>. İptal edilen etkinliğin tüm bekleyen alt etkinlikleri sırayla iptal edilir. Ek alt etkinlikler zamanlamak için her türlü girişim yoksayılıyor denemesi neden olur ve etkinlik olarak işaretlenmiş <xref:System.Activities.ActivityInstanceState.Canceled>. Herhangi bir bekleyen alt etkinliği tamamlarsa <xref:System.Activities.ActivityInstanceState.Canceled> veya <xref:System.Activities.ActivityInstanceState.Faulted> durum etkinlik olarak işaretlenmiş sonra <xref:System.Activities.ActivityInstanceState.Canceled>. İptal isteği yoksayılabilir unutmayın. Bir etkinlik herhangi bir bekleyen yer işaretleri veya yürütülen alt etkinlikler yok ve herhangi bir ek iş öğesini iptalleri işaretlenen sonra zamanlayamazsınız, başarıyla tamamlanır. Bu varsayılan iptal birçok senaryoları için son eklerini, ancak ek iptal mantığı gerekiyorsa, daha sonra yerleşik iptal etkinlikleri veya özel etkinlikler kullanılabilir.  
  
 Aşağıdaki örnekte, <xref:System.Activities.NativeActivity.Cancel%2A> , geçersiz bir <xref:System.Activities.NativeActivity> özel dayalı `ParallelForEach` etkinlik tanımlanır. Etkinlik iptal ettiğinizde, bu geçersiz kılma iptal mantığını etkinliği işler. Bu örneğin parçasıdır [olmayan genel ParallelForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md) örnek.  
  
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
  
 <xref:System.Activities.NativeActivity> türetilen etkinlikleri inceleyerek iptal istedi olmadığını belirleyebilir <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> özelliği ve kendilerini çağırarak iptal olarak işaretle <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> yöntemi. Çağırma <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> hemen etkinlik tamamlanmazsa. Her zamanki gibi çalışma zamanı etkinliği artık bekleyen iş olduğunda ancak tamamlayacak <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> son adlı durumu olacaktır <xref:System.Activities.ActivityInstanceState.Canceled> yerine <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>İptal AsyncCodeActivity kullanma  
 <xref:System.Activities.AsyncCodeActivity> bağlı etkinlikler de sağlayabilir özel iptal mantığı kılarak <xref:System.Activities.AsyncCodeActivity.Cancel%2A> yöntemi. Bu yöntem kılınmayan, etkinlik iptal edilirse hiçbir iptalleri işleme gerçekleştirilir. Aşağıdaki örnekte, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> , geçersiz bir <xref:System.Activities.AsyncCodeActivity> özel dayalı `ExecutePowerShell` etkinlik tanımlanır. Etkinlik iptal ettiğinizde, istenen iptal davranışı gerçekleştirir. Bu örneğin parçasıdır [InvokePowerShell etkinliğini kullanarak](../../../docs/framework/windows-workflow-foundation/samples/using-the-invokepowershell-activity.md) örnek.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> türetilen etkinlikleri inceleyerek iptal istedi olmadığını belirleyebilir <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> özelliği ve kendilerini çağırarak iptal olarak işaretle <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> yöntemi.
