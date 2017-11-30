---
title: "Zaman uyumsuz etkinlikleri WF içinde oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2fd247348050b8335f4f6354c88664d497dbbf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-asynchronous-activities-in-wf"></a>Zaman uyumsuz etkinlikleri WF içinde oluşturma
<xref:System.Activities.AsyncCodeActivity>Etkinlik yazarlar etkinleştirir ve zaman uyumsuz yürütme mantığını uygulamak için etkinlikler türetilmiş kullanmak için bir temel sınıf sağlar. Bu, zaman uyumsuz iş akışı Zamanlayıcı iş parçacığı tutan ve paralel olarak çalıştırılabilmesi için hiç etkinlik engelleme olmadan gerçekleştirmelisiniz özel etkinlikler için kullanışlıdır. Bu konu kullanarak zaman uyumsuz özel etkinlikler oluşturmak nasıl bir bakış sunar <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>AsyncCodeActivity kullanma  
 <xref:System.Activities?displayProperty=nameWithType>Özel Etkinlik yazarlar farklı temel sınıflarının farklı etkinlik yazma gereksinimlerini sağlar. Her biri belirli bir anlam taşır ve iş akışı yazarı (ve etkinlik çalışma zamanı) karşılık gelen bir sözleşme sağlar. Bir <xref:System.Activities.AsyncCodeActivity> tabanlı etkinliktir iş Zamanlayıcı göre zaman uyumsuz olarak gerçekleştirdiği etkinlik yönetilen kodda iş parçacığı ve, yürütme mantığını cinsinden ifade edilir. Zaman uyumsuz, giden sonucunda bir <xref:System.Activities.AsyncCodeActivity> boşta noktanız yürütme sırasında anlamına. Zaman uyumsuz iş volatile doğası nedeniyle bir <xref:System.Activities.AsyncCodeActivity> her zaman etkinliğin yürütme süresi için hiçbir kalan bloğu oluşturur. Bu iş akışı çalışma zamanı iş akışı örneği zaman uyumsuz iş ortasında kalıcı ve ayrıca kaldırma sırada'den zaman uyumsuz kod yürütme iş akışı örneği engeller.  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity yöntemleri  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.AsyncCodeActivity> zaman uyumsuz yürütme mantığını kılarak oluşturabilirsiniz <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> özel kod yöntemleriyle. Çalışma zamanı tarafından çağrıldığında, bu yöntemleri geçirilen bir <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext>Paylaşılan durum arasında sağlamak üzere etkinlik Yazar verir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> bağlamın içinde <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> özelliği. Aşağıdaki örnekte, bir `GenerateRandom` etkinlik rastgele bir sayı zaman uyumsuz olarak oluşturur.  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Önceki örnek etkinlik türetilen <xref:System.Activities.AsyncCodeActivity%601>, ve yükseltilmiş `OutArgument<int>` adlı `Result`. Tarafından döndürülen değer `GetRandom` yöntemi ayıklanır ve tarafından döndürülen <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılma ve bu değer olarak ayarlanır `Result` değeri. Bir sonuç döndürmeyen zaman uyumsuz etkinlikleri türetilen <xref:System.Activities.AsyncCodeActivity>. Aşağıdaki örnekte, bir `DisplayRandom` etkinlik öğesinden türetilen tanımlanmış <xref:System.Activities.AsyncCodeActivity>. Bu etkinlik benzer `GetRandom` etkinlik ancak sonucu döndürerek yerine bir ileti konsola gösterir.  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Hiçbir değer döndürmeyen olduğundan unutmayın `DisplayRandom` kullanan bir <xref:System.Action> yerine bir <xref:System.Func%602> kendi temsilci ve temsilci çağırmak için herhangi bir değer döndürür.  
  
 <xref:System.Activities.AsyncCodeActivity>Ayrıca sağlayan bir <xref:System.Activities.AsyncCodeActivity.Cancel%2A> geçersiz kılar. Sırada <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> gerekli geçersiz kılmalar olan <xref:System.Activities.AsyncCodeActivity.Cancel%2A> isteğe bağlıdır ve onu yüklenirken etkinliği bekleyen zaman uyumsuz durumuna temizleyebilirsiniz şekilde kılınabilir iptal edildi veya iptal edildi. Temizleme mümkün olup olmadığını ve `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` olan `true`, etkinlik çağırmalıdır <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Bu yöntemle karşılaşılan özel durumlar için iş akışı örneği önemli.  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Bir sınıfı zaman uyumsuz yöntemleri çağırma  
 Sınıflarda birçoğu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz işlevselliği sağlamak ve bu işlevselliği kullanarak zaman uyumsuz olarak çağrılabilir bir <xref:System.Activities.AsyncCodeActivity> etkinlik tabanlı. Aşağıdaki örnekte [kullanarak AsyncOperationContext bir etkinlikte](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md), bir etkinlik zaman uyumsuz olarak kullanarak bir dosyayı oluşturan oluşturulur <xref:System.IO.FileStream> sınıfı.  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Durum BeginExecute ve EndExecute yöntemleri arasında paylaşma  
 Önceki örnekte, <xref:System.IO.FileStream> oluşturulan nesne <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> içinde eriştiğiniz <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Bu olasıdır çünkü `file` değişken olarak geçirilen <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> özelliğinde <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Bu, durumu arasında paylaşmak için doğru yöntemdir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Türetilen sınıfta bir üye değişkenine kullanmak için geçersiz (`FileWriter` bu durumda) durumu arasında paylaşmak için <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> etkinliği nesnesi birden çok etkinlik örnekleri tarafından başvurulabilir olduğundan. Durum paylaşmak için bir üye değişkenine kullanılmaya çalışılıyor birinden değerlerde sonuçlanabilir <xref:System.Activities.ActivityInstance> üzerine yazmaya veya başka bir değer tüketen <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Bağımsız değişken değerleri erişme  
 Ortamının bir <xref:System.Activities.AsyncCodeActivity> faaliyete tanımlı değişkenlerin oluşur. Bu bağımsız değişkenler erişilebilen <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> kullanarak geçersiz kılar <xref:System.Activities.AsyncCodeActivityContext> parametresi. Bağımsız değişkenler temsilci, ancak bağımsız değişken değerleri erişilemiyor veya istenen herhangi bir veri parametrelerini kullanarak temsilci geçirilebilir. Aşağıdaki örnekte, rastgele bir sayı oluştururken etkinlik (bunlar dahil) bir üst sınır gelen edindiği tanımlanır kendi `Max` bağımsız değişkeni. Temsilci çağrıldığında bağımsız değişkeninin değeri için zaman uyumsuz koduna geçirilen.  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Zamanlama eylemler veya alt etkinlikleri AsyncCodeActivity kullanma  
 <xref:System.Activities.AsyncCodeActivity>türetilen özel etkinlikler iş akışı iş parçacığı açısından zaman uyumsuz olarak gerçekleştirmek için bir yöntem sağlar, ancak alt etkinlikler veya Eylemler zamanlama yeteneği sağlamaz. Ancak, zaman uyumsuz davranışı alt etkinliklerin birleşim aracılığıyla zamanlama ile birleştirilebilir. Zaman uyumsuz bir etkinlik oluşturulabilir ve ardından ile oluşan bir <xref:System.Activities.Activity> veya <xref:System.Activities.NativeActivity> zaman uyumsuz davranışı ve alt etkinlikler veya Eylemler zamanlama sağlamak üzere etkinlik türetilmiş. Örneğin, bir etkinlik öğesinden türetilen oluşturulamadı <xref:System.Activities.Activity>ve kendi uygulamanızda bir <xref:System.Activities.Statements.Sequence> etkinliğin mantığını uygulayan iyi diğer etkinlikler olarak zaman uyumsuz etkinliğini içeren. Kullanarak etkinlikleri oluşturma hakkında daha fazla örnekleri için <xref:System.Activities.Activity> ve <xref:System.Activities.NativeActivity>, bkz: [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md), [etkinlik yazma seçenekleri](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)ve [bileşik](../../../docs/framework/windows-workflow-foundation/samples/composite.md) etkinlik örnekleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Action>  
 <xref:System.Func%602>  
 [AsyncOperationContext bir etkinlikte kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)
