---
title: İş Akışlarında İptal Davranışını Modelleme
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8738afa838f1d0ca36b7fd6def00f0794bcf47ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143050"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>İş Akışlarında İptal Davranışını Modelleme
<xref:System.Activities.Statements.Parallel> Etkinlikler, örneğin, ev sahibi aradığında <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> `true` <xref:System.Activities.WorkflowApplication.Cancel%2A>iş akışı dışında veya dolduğunda eksik dalları iptal eden bir etkinlik tarafından bir iş akışı içinde iptal edilebilir. İptal işleme sağlamak için, iş <xref:System.Activities.Statements.CancellationScope> akışı yazarları <xref:System.Activities.Statements.CompensableActivity> etkinliği, etkinliği kullanabilir veya iptal mantığı sağlayan özel etkinlikler oluşturabilir. Bu konu, iş akışlarındaki iptale genel bir bakış sağlar.  
  
## <a name="cancellation-compensation-and-transactions"></a>İptal, Tazminat ve İşlemler  
 Hareketler, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanız için yapılan tüm değişiklikleri iptal etme (geri alma) olanağı sağlar. Ancak, iptal edilmesi veya geri alınması gereken tüm işler, uzun süren çalışma veya işlem kaynaklarını içermeyen çalışma gibi hareketler için uygun değildir. İş akışında sonraki bir hata varsa, daha önce tamamlanmış işlem dışı çalışmayı geri alamak için bir model sağlar. İptal, tamamlanmamış işlem dışı işleri işlemek için iş akışı ve etkinlik yazarları için bir model sağlar. Bir etkinlik yürütmesini tamamlamadıysa ve iptal edilirse, varsa iptal mantığı çağrılır.  
  
> [!NOTE]
> İşlemler ve tazminatlar hakkında daha fazla bilgi [için, Bkz. İşlemler](workflow-transactions.md) ve [Tazminatlar.](compensation.md)  
  
## <a name="using-cancellationscope"></a>CancellationScope Kullanma  
 Etkinlik, <xref:System.Activities.Statements.CancellationScope> alt etkinlikleri içerebilecek iki <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>bölümden oluşur: ve. Etkinlik <xref:System.Activities.Statements.CancellationScope.Body%2A> mantığını oluşturan etkinliklerin yerleştirildiği <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> yer, etkinlik için iptal mantığı sağlayan etkinliklerin yerleştirildiği yerdir. Bir etkinlik yalnızca tamamlanmadıysa iptal edilebilir. <xref:System.Activities.Statements.CancellationScope> Etkinlik söz konusu olduğunda, tamamlanma, faaliyetlerin tamamlanması anlamına <xref:System.Activities.Statements.CancellationScope.Body%2A>gelir. İptal isteği zamanlanmış sayılsa ve etkinlikler <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope> tamamlanmamışsa, bu durum işaretlenir <xref:System.Activities.ActivityInstanceState.Canceled> ve <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> etkinlikler yürütülür.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Ana Bilgisayar'dan İş Akışını İptal Etme  
 Ana bilgisayar, iş akışını barındıran <xref:System.Activities.WorkflowApplication.Cancel%2A> <xref:System.Activities.WorkflowApplication> örneğin yöntemini çağırarak iş akışını iptal edebilir. Aşağıdaki örnekte bir iş akışı oluşturulur. <xref:System.Activities.Statements.CancellationScope> İş akışı çağrılır ve sonra ana bilgisayar <xref:System.Activities.WorkflowApplication.Cancel%2A>' dan ' ' İş akışının ana yürütülmesi durdurulur, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> çağrılan ve daha sonra iş akışı bir durum <xref:System.Activities.ActivityInstanceState.Canceled>ile tamamlar .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **İş akışını başlatılır.**  
**İptalHandler çağrıldı.** 
 **İş akışı b30ebb30-df46-4d90-a211-e31c38d8db3c İptal edildi.**
> [!NOTE]
> Bir <xref:System.Activities.Statements.CancellationScope> etkinlik iptal edildiğinde <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> ve çağrıldığında, uygun iptal mantığını sağlamak için iptal edilen etkinliğin iptal edilmeden önce yaptığı ilerlemeyi belirlemek iş akışı yazarının sorumluluğundadır. İptal <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> edilen etkinliğin ilerlemesi hakkında herhangi bir bilgi sağlamaz.  
  
 İşlenmemiş bir özel durum iş akışının kökünü aşar ve <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işleyici döndürürse, <xref:System.Activities.UnhandledExceptionAction.Cancel>iş akışı ana bilgisayardan da iptal edilebilir. Bu örnekte iş akışı başlar ve <xref:System.ApplicationException>sonra bir. Bu özel durum iş akışı tarafından <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> işlenmemiş ve bu nedenle işleyici çağrılır. İşleyici çalışma saatini iş akışını iptal etmek için <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> bildirir ve <xref:System.Activities.Statements.CancellationScope> şu anda çalıştırılatan etkinliğin çağrılması çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **İş akışını başlatılır.**  
**OnUnhandledException in Workflow 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**
**Bir UygulamaException atıldı.** 
 **İptalHandler çağrıldı.** 
 **İş Akışı 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 İptal edildi.**
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Bir İş Akışı İçinden Bir Etkinliği İptal Etme  
 Bir etkinlik, üst öğesi tarafından da iptal edilebilir. Örneğin, bir <xref:System.Activities.Statements.Parallel> etkinliğin birden çok yürütme <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> dalı varsa `true` ve onun değerlendirmeleri sonra eksik dalları iptal edilir. Bu örnekte <xref:System.Activities.Statements.Parallel> iki dalı olan bir etkinlik oluşturulur. Herhangi <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> bir `true` şubesi <xref:System.Activities.Statements.Parallel> tamamlanır tamamlanmaz tamamlanacak şekilde ayarlanır. Bu örnekte şube 2 tamamlanır ve böylece şube 1 iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **Şube 1 başlıyor.**  
**Şube 2 tamamlandı.** 
 **Şube 1 iptal edildi.** 
 **İş Akışı e0685e24-18ef-4a47-acf3-5c638732f3be Tamamlandı.**  Bir özel durum, etkinliğin kökünü aşar ancak iş akışında daha yüksek bir düzeyde işlenirse etkinlikler de iptal edilir. Bu örnekte, iş akışının ana mantığı <xref:System.Activities.Statements.Sequence> bir etkinlikten oluşur. Bir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.TryCatch> etkinlik tarafından <xref:System.Activities.Statements.CancellationScope.Body%2A> bulunan <xref:System.Activities.Statements.CancellationScope> bir etkinliğin olarak belirtilir. Bir özel durum gövdesinden <xref:System.Activities.Statements.Sequence>atılır , üst <xref:System.Activities.Statements.TryCatch> etkinlik tarafından <xref:System.Activities.Statements.Sequence> işlenir ve iptal edilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **Dizi başlangıç.**  
**Sıra iptal edildi.** 
 **İstisna yakalandı.** 
 **İş Akışı e3c18939-121e-4c43-af1c-ba1ce977ce55 Tamamlandı.**
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>İptalHandler'dan İstisnaları Atma  
 A'dan <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> atılan tüm özel durumlar iş akışı için ölümcüldür. Bir özel durum dan kaçan bir <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>olasılık varsa, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> bu özel durumları yakalamak ve işlemek için a <xref:System.Activities.Statements.TryCatch> kullanın.  
  
### <a name="cancellation-using-compensableactivity"></a>Telafi Etkinliği kullanarak iptal  
 <xref:System.Activities.Statements.CancellationScope> Etkinlik gibi, <xref:System.Activities.Statements.CompensableActivity> bir <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. A <xref:System.Activities.Statements.CompensableActivity> iptal edilirse, içinde <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> herhangi bir etkinlik çağrılır. Bu kısmen tamamlanmış telafi edilebilir iş geri getirmek için yararlı olabilir. Tazminat ve iptal <xref:System.Activities.Statements.CompensableActivity> için nasıl kullanılacağı hakkında bilgi için [Tazminat'a](compensation.md)bakın.  
  
## <a name="cancellation-using-custom-activities"></a>Özel Etkinlikler kullanılarak İptal  
 Özel etkinlik yazarları, özel etkinliklerine iptal mantığını birkaç farklı şekilde uygulayabilir. Türeyen <xref:System.Activities.Activity> özel etkinlikler, etkinliğin gövdesine <xref:System.Activities.Statements.CancellationScope> iptal mantığı içeren bir veya başka bir özel etkinlik yerleştirerek iptal mantığını uygulayabilir. <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity> türetilen faaliyetler kendi <xref:System.Activities.NativeActivity.Cancel%2A> yöntemini geçersiz kılabilir ve burada iptal mantığı sağlayabilir. <xref:System.Activities.CodeActivity>türetilen faaliyetler iptal için herhangi bir hüküm sağlamaz, çünkü çalışma zamanı <xref:System.Activities.CodeActivity.Execute%2A> yöntemi aradığında tüm çalışmaları tek bir yürütme patlamasında gerçekleştirilir. Yürütme yöntemi henüz çağrılmazsa ve <xref:System.Activities.CodeActivity> tabanlı bir etkinlik iptal edilirse, etkinlik <xref:System.Activities.ActivityInstanceState.Canceled> bir <xref:System.Activities.CodeActivity.Execute%2A> durumla kapanır ve yöntem çağrılmaz.  
  
### <a name="cancellation-using-nativeactivity"></a>NativeActivity kullanarak iptal  
 <xref:System.Activities.NativeActivity>türetilen etkinlikler özel <xref:System.Activities.NativeActivity.Cancel%2A> iptal mantığı sağlamak için yöntemi geçersiz kılabilir. Bu yöntem geçersiz kılınmazsa, varsayılan iş akışı iptali mantığı uygulanır. Varsayılan iptal yöntemi geçersiz kılmayan <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> veya <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi temel <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> yöntemi çağıran bir işlemdir. Bir etkinlik iptal edildiğinde, çalışma zamanı iptal için etkinliği işaretler ve belirli temizlemeleri otomatik olarak işler. Etkinlik yalnızca bekleyen yer imleri varsa, yer imleri kaldırılır ve <xref:System.Activities.ActivityInstanceState.Canceled>etkinlik . İptal edilen etkinliğin olağanüstü alt etkinlikleri de iptal edilecektir. Ek alt etkinlikler zamanlamaya yönelik herhangi bir girişim, girişimin yoksayılmasına neden olur ve etkinlik <xref:System.Activities.ActivityInstanceState.Canceled>. Olağanüstü alt etkinlik veya <xref:System.Activities.ActivityInstanceState.Canceled> <xref:System.Activities.ActivityInstanceState.Faulted> durumda tamamlanırsa, etkinlik . <xref:System.Activities.ActivityInstanceState.Canceled> İptal isteğinin yoksayılmasına dikkat edin. Bir etkinlikte bekleyen yer imleri veya yürütme alt etkinlikleri yoksa ve iptal için işaretlendikten sonra ek iş öğeleri zamanlamazsa, başarıyla tamamlanır. Bu varsayılan iptal birçok senaryo için yeterlidir, ancak ek iptal mantığı gerekiyorsa, yerleşik iptal etkinlikleri veya özel etkinlikler kullanılabilir.  
  
 Aşağıdaki örnekte, <xref:System.Activities.NativeActivity.Cancel%2A> tabanlı bir <xref:System.Activities.NativeActivity> özel `ParallelForEach` etkinliğin geçersiz kılınmı tanımlanır. Etkinlik iptal edildiğinde, bu geçersiz kılma, etkinliğin iptal mantığını işler. Bu örnek, [Genel Olmayan ParallelForEach](./samples/non-generic-parallelforeach.md) örneğinin bir parçasıdır.  
  
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
  
 <xref:System.Activities.NativeActivity>türemiş faaliyetler, <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> mülkü inceleyerek iptal talebinde bulunulup bulunulan olmadığını belirleyebilir ve <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> yöntemi arayarak kendilerini iptal edilmiş olarak işaretleyebilir. Arama <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> hemen etkinliği tamamlamaz. Her zamanki gibi, çalışma zamanı artık bekleyen iş olduğunda etkinliği <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> tamamlar, ancak <xref:System.Activities.ActivityInstanceState.Canceled> son <xref:System.Activities.ActivityInstanceState.Closed>durum yerine '' olarak adlandırılırsa.  
  
### <a name="cancellation-using-asynccodeactivity"></a>AsyncCodeActivity kullanarak iptal  
 <xref:System.Activities.AsyncCodeActivity>tabanlı etkinlikler de <xref:System.Activities.AsyncCodeActivity.Cancel%2A> yöntemi geçersiz kılarak özel iptal mantığı sağlayabilir. Bu yöntem geçersiz kılınmazsa, etkinlik iptal edilirse iptal işlemi yapılmaz. Aşağıdaki örnekte, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> tabanlı bir <xref:System.Activities.AsyncCodeActivity> özel `ExecutePowerShell` etkinliğin geçersiz kılınmı tanımlanır. Etkinlik iptal edildiğinde, istenen iptal davranışını gerçekleştirir.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>türemiş faaliyetler, <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> mülkü inceleyerek iptal talebinde bulunulup bulunulan olmadığını belirleyebilir ve <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> yöntemi arayarak kendilerini iptal edilmiş olarak işaretleyebilir.
