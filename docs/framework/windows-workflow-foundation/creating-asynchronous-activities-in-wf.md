---
title: WF içinde zaman uyumsuz etkinlikler oluşturma
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: b990631d6efdb4644274c8a4606af07495b1979c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592965"
---
# <a name="creating-asynchronous-activities-in-wf"></a>WF içinde zaman uyumsuz etkinlikler oluşturma
<xref:System.Activities.AsyncCodeActivity> Etkinlik yazarlar etkinleştirir ve zaman uyumsuz yürütme mantığı uygulamak için etkinlikleri türetilmiş kullanmak için bir temel sınıf sağlar. Bu, zaman uyumsuz işler, iş akışı Zamanlayıcı iş parçacığı bulunduran ve paralel olarak çalıştırmak için herhangi bir etkinlik engelleme olmadan gerçekleştirmelidir özel etkinlikler için kullanışlıdır. Bu konu, kullanarak özel bir zaman uyumsuz etkinlikler oluşturma genel bir bakış sağlar. <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>AsyncCodeActivity kullanma  
 <xref:System.Activities?displayProperty=nameWithType> Özel Etkinlik yazarları ile farklı temel sınıflar için farklı bir etkinlik yazma gereksinimlerini sağlar. Her biri, belirli bir anlam taşır ve bir iş akışı yazar (ve etkinlik çalışma zamanı) karşılık gelen bir sözleşme sağlar. Bir <xref:System.Activities.AsyncCodeActivity> göre etkinlik dışı bir iş Zamanlayıcı göreli zaman uyumsuz olarak gerçekleştirdiği etkinlik yönetilen kodda iş parçacığı ve, yürütme mantığı ifade edilir. Zaman uyumsuz, giden sonucunda bir <xref:System.Activities.AsyncCodeActivity> boşta noktanız yürütme sırasında anlamına. Zaman uyumsuz işler geçici niteliği nedeniyle bir <xref:System.Activities.AsyncCodeActivity> her zaman Etkinlik yürütme süresi boyunca hiç kalıcı bir blok oluşturur. Bu iş akışı çalışma zamanı zaman uyumsuz iş ortasında iş akışı örneği kalıcı ve ayrıca kaldırma sırada'den zaman uyumsuz kodu yürüten iş akışı örneği engeller.  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity yöntemleri  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.AsyncCodeActivity> zaman uyumsuz yürütme mantığı geçersiz kılarak oluşturabilirsiniz <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> özel kodla yöntemleri. Çalışma zamanı tarafından çağrıldığında, bu yöntemlere geçirilen bir <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext> Paylaşılan duruma sağlamak etkinlik yazarın sağlar <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> bağlamı'nın içinde <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> özelliği. Aşağıdaki örnekte, bir `GenerateRandom` etkinlik rastgele bir sayı zaman uyumsuz olarak oluşturur.  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Önceki örnek etkinlik türetildiği <xref:System.Activities.AsyncCodeActivity%601>, ve yükseltilmiş `OutArgument<int>` adlı `Result`. Tarafından döndürülen değer `GetRandom` yöntemi ayıklanır ve tarafından döndürülen <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılma ve bu değeri olarak ayarlanır `Result` değeri. Bir sonuç döndürmediği zaman uyumsuz etkinlikler türetilmelidir <xref:System.Activities.AsyncCodeActivity>. Aşağıdaki örnekte, bir `DisplayRandom` etkinlik öğesinden türetilen tanımlanan <xref:System.Activities.AsyncCodeActivity>. Bu etkinlik benzer `GetRandom` etkinlik ancak bir sonuç döndürmek yerine, bir iletiyi konsola görüntüler.  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Dönüş değeri olduğundan `DisplayRandom` kullanan bir <xref:System.Action> yerine bir <xref:System.Func%602> , temsilci ve temsilci çağırmak için herhangi bir değer döndürür.  
  
 <xref:System.Activities.AsyncCodeActivity> Ayrıca sağlar bir <xref:System.Activities.AsyncCodeActivity.Cancel%2A> geçersiz kılar. Sırada <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> gerekli geçersiz kılmalar olan <xref:System.Activities.AsyncCodeActivity.Cancel%2A> isteğe bağlıdır ve onu edilirken etkinliği bekleyen zaman uyumsuz durumunu temizleyebilirsiniz için geçersiz kılınabilir iptal edildi veya iptal edildi. Temizleme mümkün olup olmadığını ve `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` olduğu `true`, etkinlik çağırmalıdır <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Bu yöntemden atılan özel durumların iş akışı örneği için önemli.  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Bir sınıfı zaman uyumsuz yöntemleri çağırma  
 .NET Framework'teki sınıfların çoğu zaman uyumsuz işlevleri sağlar ve bu işlevi kullanarak zaman uyumsuz olarak çağrılabilir bir <xref:System.Activities.AsyncCodeActivity> etkinlik tabanlı. Aşağıdaki örnekte, zaman uyumsuz olarak kullanarak bir dosya oluşturur, bir etkinlik oluşturulur <xref:System.IO.FileStream> sınıfı.  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>BeginExecute ve EndExecute yöntemleri arasında durum paylaşma  
 Önceki örnekte, <xref:System.IO.FileStream> oluşturulan nesne <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> içinde erişilmiş olan <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Bu mümkün olur çünkü `file` değişken geçirildi <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> özelliğinde <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Arasında durum paylaşımı için doğru yöntem budur <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Türetilen bir sınıfta bir üye değişkenini kullanmak için yanlış (`FileWriter` bu durumda) arasında durum paylaşma için <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> etkinlik nesnesi birden fazla etkinlik örneği tarafından başvurulabilir olduğundan. Üye değişkeni, durumu paylaşmak için kullanılmaya çalışılıyor sonuçlanabilir değerlerinden biri <xref:System.Activities.ActivityInstance> üzerine yazmaya veya başka bir değer tüketen <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Bağımsız değişken değerlerine erişim  
 Ortamının bir <xref:System.Activities.AsyncCodeActivity> etkinlikte tanımlanmış değişkenlerin oluşur. Bu bağımsız değişkenler erişilebilir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> kullanarak geçersiz kılar <xref:System.Activities.AsyncCodeActivityContext> parametresi. Bağımsız değişkenler temsilci, ancak bağımsız değişken değerlerini erişilemez veya istenen herhangi bir veri parametrelerini kullanarak temsilci geçirilebilir. Aşağıdaki örnekte, kapsamlı bir üst sınır gelen alan bir rastgele sayı oluşturma etkinliği tanımlanan kendi `Max` bağımsız değişken. Temsilci çağrıldığında bağımsız değişkenin değeri için zaman uyumsuz kod geçirilir.  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Eylemler ya da çocuk etkinliklerinin AsyncCodeActivity kullanarak zamanlama  
 <xref:System.Activities.AsyncCodeActivity> türetilmiş özel etkinlikler iş akışı iş parçacığı zaman uyumsuz olarak onaylamaz işlemi gerçekleştirmek için bir yöntem sağlar, ancak alt etkinlikler veya Eylemler zamanlama olanağı sağlamaz. Ancak, zaman uyumsuz davranış alt etkinlik oluşturma yoluyla zamanlama ile birleştirilebilir. Zaman uyumsuz bir etkinlik oluşturulabilir ve ardından ile oluşan bir <xref:System.Activities.Activity> veya <xref:System.Activities.NativeActivity> zaman uyumsuz davranış ve alt etkinlikler veya Eylemler zamanlama sağlamak için etkinlik türetilmiş. Örneğin, bir etkinlik öğesinden türetilen oluşturulabilir <xref:System.Activities.Activity>ve uygulaması bir <xref:System.Activities.Statements.Sequence> etkinliğin mantığını de diğer etkinlikler olarak zaman uyumsuz etkinliğini içeren. Etkinlikleri kullanarak oluşturma hakkında daha fazla örnekleri için <xref:System.Activities.Activity> ve <xref:System.Activities.NativeActivity>, bkz: [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) ve [etkinlik yazma seçenekleri](activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Action>
- <xref:System.Func%602>
