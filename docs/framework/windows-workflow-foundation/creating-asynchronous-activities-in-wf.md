---
title: WF 'de zaman uyumsuz etkinlikler oluşturma
description: AsyncCodeActivity kullanarak özel zaman uyumsuz etkinlikler oluşturmayı öğrenin ve bu da türetilmiş etkinliklerin zaman uyumsuz yürütme mantığını uygulamasına olanak sağlar.
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: f7ce0c0157791b34723feff185aed24bb56a4b3f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421533"
---
# <a name="creating-asynchronous-activities-in-wf"></a>WF 'de zaman uyumsuz etkinlikler oluşturma
<xref:System.Activities.AsyncCodeActivity>, türetilmiş etkinliklerin zaman uyumsuz yürütme mantığını uygulamasına olanak sağlayan bir temel sınıf olan etkinlik yazarlarına sahiptir. Bu, iş akışı Zamanlayıcı iş parçacığını tutmadan zaman uyumsuz çalışma gerçekleştirmesi gereken özel etkinlikler için yararlıdır ve paralel olarak çalıştırılabilecek etkinlikleri engeller. Bu konu, kullanarak özel zaman uyumsuz etkinliklerin nasıl oluşturulacağı hakkında genel bakış sağlar <xref:System.Activities.AsyncCodeActivity> .  
  
## <a name="using-asynccodeactivity"></a>AsyncCodeActivity kullanma  
 <xref:System.Activities?displayProperty=nameWithType>farklı etkinlik yazma gereksinimleri için farklı temel sınıflara sahip özel etkinlik yazarları sağlar. Her biri belirli bir anlam taşır ve ilgili sözleşmeye bir iş akışı yazarı (ve etkinlik çalışma zamanı) sağlar. <xref:System.Activities.AsyncCodeActivity>Tabanlı etkinlik, zamanlayıcı iş parçacığına göre zaman uyumsuz olarak iş yapan ve yürütme mantığı yönetilen kodda ifade edilen bir etkinliktir. Zaman uyumsuz olarak geçecek bir sonuç olarak, <xref:System.Activities.AsyncCodeActivity> yürütme sırasında boşta bir nokta alabilir. Zaman uyumsuz çalışmanın geçici doğası nedeniyle, <xref:System.Activities.AsyncCodeActivity> Etkinlik yürütme süresi boyunca her zaman kalıcı olmayan bir blok oluşturur. Bu, iş akışı çalışma zamanının zaman uyumsuz çalışmanın ortasındaki iş akışı örneğini kalıcı hale getirme ve ayrıca zaman uyumsuz kod yürütülürken iş akışı örneğinin kaldırılmasını önler.  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity yöntemleri  
 Öğesinden türetilen etkinlikler <xref:System.Activities.AsyncCodeActivity> , <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve yöntemlerini özel kodla geçersiz kılarak zaman uyumsuz yürütme mantığı oluşturabilir <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . Çalışma zamanı tarafından çağrıldığında, bu yöntemler geçirilir <xref:System.Activities.AsyncCodeActivityContext> . <xref:System.Activities.AsyncCodeActivityContext>Etkinlik yazarının <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> bağlam özelliğinde paylaşılan durum sağlamasına izin verir <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> . Aşağıdaki örnekte, bir `GenerateRandom` etkinlik zaman uyumsuz olarak rastgele bir sayı üretir.  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Önceki örnek etkinlik öğesinden türetilir <xref:System.Activities.AsyncCodeActivity%601> ve yükseltilmiş bir `OutArgument<int>` ada sahiptir `Result` . Yöntemi tarafından döndürülen değer `GetRandom` ayıklanır ve <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılma tarafından döndürülür ve bu değer değer olarak ayarlanır `Result` . Sonuç döndürmeyen zaman uyumsuz etkinlikler öğesinden türetilmelidir <xref:System.Activities.AsyncCodeActivity> . Aşağıdaki örnekte, `DisplayRandom` öğesinden türetilen bir etkinlik tanımlanmıştır <xref:System.Activities.AsyncCodeActivity> . Bu etkinlik etkinlik gibidir, `GetRandom` ancak bir sonuç döndürmek yerine konsola bir ileti görüntülenir.  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Dönüş değeri olmadığından, `DisplayRandom` <xref:System.Action> temsilcisini çağırmak için bir yerine bir kullanın, <xref:System.Func%602> ve temsilci hiçbir değer döndürmez.  
  
 <xref:System.Activities.AsyncCodeActivity>Ayrıca bir <xref:System.Activities.AsyncCodeActivity.Cancel%2A> geçersiz kılma sağlar. Ancak <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> gerekli geçersiz kılmalar, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> isteğe bağlıdır ve geçersiz kılınabilir, böylece etkinlik iptal edildiğinde veya iptal edildiğinde etkinliğin bekleyen zaman uyumsuz durumunu temizleyebilir. Temizleme olasılığı varsa ve ise, `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` `true` etkinlik çağırmalıdır <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> . Bu yöntemden oluşturulan özel durumlar, iş akışı örneği için önemli değildir.  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Bir sınıfta zaman uyumsuz yöntemleri çağırma  
 .NET Framework sınıfların birçoğu zaman uyumsuz işlevsellik sağlar ve bu işlevsellik, bir tabanlı etkinlik kullanılarak zaman uyumsuz olarak çağrılabilir <xref:System.Activities.AsyncCodeActivity> . Aşağıdaki örnekte, sınıfını kullanarak zaman uyumsuz olarak bir dosya oluşturan bir etkinlik oluşturulur <xref:System.IO.FileStream> .  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>BeginExecute ve Endexyürüme yöntemleri arasında durum paylaşma  
 Önceki örnekte, <xref:System.IO.FileStream> içinde oluşturulan nesnesine ' <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de erişildi <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . Bu, `file` değişkeni <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> içindeki özelliğinde geçirildiğinden mümkündür <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> . Bu, ve arasında durum paylaşmak için doğru yöntemdir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . `FileWriter` <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> Etkinlik nesnesine birden çok etkinlik örneği tarafından başvurulduğundan, türetilmiş sınıfta (Bu durumda) bir üye değişkeni kullanmak hatalıdır. Durumu paylaşmak için bir üye değişkeni kullanılmaya çalışılması, bir <xref:System.Activities.ActivityInstance> veya başka bir değerden bir veya daha fazla değerin kullanılmasına neden olabilir <xref:System.Activities.ActivityInstance> .  
  
### <a name="accessing-argument-values"></a>Bağımsız değişken değerlerine erişme  
 Öğesinin ortamı, <xref:System.Activities.AsyncCodeActivity> etkinlikte tanımlanan bağımsız değişkenlerden oluşur. Bu bağımsız değişkenlere <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> parametresi kullanılarak geçersiz kılmalardan erişilebilir <xref:System.Activities.AsyncCodeActivityContext> . Bağımsız değişkenlere, temsilciden erişilemez, ancak bağımsız değişken değerleri veya istenen herhangi bir veri, parametreleri kullanılarak temsilciye geçirilebilir. Aşağıdaki örnekte, bağımsız değişkeninden iç sınırı alan rastgele bir sayı üreten etkinlik tanımlanmıştır `Max` . Bağımsız değişkenin değeri, temsilci çağrıldığında zaman uyumsuz koda geçirilir.  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>AsyncCodeActivity kullanarak eylemleri veya alt etkinlikleri zamanlama  
 <xref:System.Activities.AsyncCodeActivity>türetilmiş özel etkinlikler iş akışı iş parçacığına göre zaman uyumsuz olarak iş yapmak için bir yöntem sağlar, ancak alt etkinlikleri veya eylemleri zamanlama olanağı sağlamaz. Ancak, zaman uyumsuz davranış bileşim aracılığıyla alt etkinliklerin planlanmasıyla birleştirilebilir. Zaman uyumsuz bir etkinlik oluşturulabilir ve daha sonra <xref:System.Activities.Activity> <xref:System.Activities.NativeActivity> alt etkinliklerin veya eylemlerin zaman uyumsuz davranışını ve zamanlamasını sağlamak için bir veya türetilmiş etkinlik ile oluşturulur. Örneğin, ' den türetilen bir etkinlik oluşturulabilir <xref:System.Activities.Activity> ve uygulamanın, <xref:System.Activities.Statements.Sequence> zaman uyumsuz etkinliği ve etkinliğin mantığını uygulayan diğer etkinlikleri içeren bir etkinliği vardır. Ve kullanarak etkinlik oluşturmaya yönelik daha fazla örnek için <xref:System.Activities.Activity> <xref:System.Activities.NativeActivity> bkz. [nasıl yapılır: etkinlik](how-to-create-an-activity.md) ve [etkinlik yazma seçenekleri](activity-authoring-options-in-wf.md)oluşturma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Action>
- <xref:System.Func%602>
