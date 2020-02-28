---
title: Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
ms.date: 02/11/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: 7de8c4e44e1866e3df36c666c9ecc210dc6a7d83
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159370"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
Zaman uyumsuz programlamada, bir zaman uyumsuz işlem için, tamamlandığında ikinci bir işlemi çağırmak ve verileri iletmek için yaygındır. Geleneksel olarak, devamlılıklar geri çağırma yöntemleri kullanılarak yapılır. Görev paralel kitaplığında, aynı işlevler *devamlılık görevleri*tarafından sağlanır. Devamlılık görevi (sadece devamlılık olarak da bilinir *), öncül*olarak bilinen başka bir görev tarafından çağrılan zaman uyumsuz bir görevdir.  
  
 Devamlılıkların kullanımı nispeten kolaydır, ancak bu, güçlü ve esnektir. Örneğin, şunları yapabilirsiniz:  
  
- Verileri öncül bilgisayardan devamlıya geçirin.  
  
- Devamlılığın çağrılacağını veya çağrılmaması gereken kesin koşulları belirtin.  
  
- Çalışmaya başlamadan önce veya çalışmaya devam etmeden önce bir devamlılığın iptal edildiğini yapın.  
  
- Devamlılığın nasıl zamanlanması gerektiği hakkında ipuçları sağlayın.  
  
- Aynı öncül öğesinden birden çok devamlılık çağırın.  
  
- Bir veya birden çok öncüllerin tamamlandıktan sonra bir devamlılık çağırın.  
  
- Zincirden sonra herhangi bir rastgele uzunluğa kadar zincir devamlılıkları.  
  
- Öncül tarafından oluşturulan özel durumları işlemek için devamlılık kullanın.  
  
## <a name="about-continuations"></a>Devamlılıklar hakkında  
 Devamlılık, <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> durumunda oluşturulan bir görevdir. Öncül görevi veya görevleri tamamlandığında otomatik olarak etkinleştirilir. Kullanıcı kodundaki bir devamlılığın <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> çağrılması <xref:System.InvalidOperationException?displayProperty=nameWithType> özel durum oluşturur.  
  
 Devamlılık bir <xref:System.Threading.Tasks.Task> ve başlatıldığı iş parçacığını engellemez. Devamlılık görevi bitene kadar engellemek için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırın.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tek bir öncül için devamlılık oluşturma  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemini çağırarak öncül öğesinin son tamamlandığında yürütülen bir devamlılık oluşturursunuz. Aşağıdaki örnekte temel desenler gösterilmektedir (açıklık için özel durum işleme atlanır). Bir öncül görevini yürütür, bu, haftanın geçerli gününün adını belirten bir <xref:System.DayOfWeek> nesnesi döndüren `taskA`. Öncül tamamlandığında, devamlılık görevi `continuation`, öncül işlemi geçirilir ve sonucunu içeren bir dize görüntüler.

> [!NOTE]
> Bu C# makaledeki örneklerde, `Main` yönteminde `async` değiştiricisinden yararlanabilirsiniz. Bu özellik C# 7,1 ve üzeri sürümlerde kullanılabilir. Önceki sürümler bu örnek kodu derlerken [`CS5001`](../../csharp/misc/cs5001.md) oluşturur. Dil sürümünü C# 7,1 veya daha yeni bir sürüme ayarlamanız gerekir. Dil sürümünü [yapılandırma sürümünü yapılandırma](../../csharp/language-reference/configure-language-version.md)makalesindeki makaleyi yapılandırma hakkında bilgi edinebilirsiniz.
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Birden çok öncüllerin için devamlılık oluşturma  
 Ayrıca, bir görev grubunun herhangi biri veya tümü tamamlandığında çalıştırılacak bir devamlılık oluşturabilirsiniz. Tüm öncül görevler tamamlandığında bir devamlılık yürütmek için, statik (`Shared` Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodunu veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemini çağırın. Öncül görevlerden herhangi biri tamamlandığında bir devamlılık yürütmek için, statik (`Shared` Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metodunu veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemini çağırın.  
  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> çağrıları ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> aşırı yüklemeleri çağıran iş parçacığını engellemez.  Ancak, çağıran iş parçacığını engelleyen döndürülen <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğini almak için genellikle <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> yöntemleri hariç tümünü çağırabilirsiniz.  
  
 Aşağıdaki örnek, 10 öncül görevlerinin sonuçlarını yansıtan bir devamlılık görevi oluşturmak için <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> yöntemini çağırır. Her öncül görev, birinden 10 ' a değişen bir dizin değeri sağlar. Öncüllerin başarıyla tamamlandıysanız (<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), devamlılık <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği her öncül tarafından döndürülen <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> değerlerinin bir dizisidir. Örnek, bir ve 10 arasındaki tüm sayıların karelerinin toplamını hesaplamak için bunları ekler.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Devamlılık seçenekleri  
 Tek bir görev devamlılığı oluşturduğunuzda, Devamlılığın başladığı koşulları belirtmek için <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> numaralandırma değeri alan bir <xref:System.Threading.Tasks.Task.ContinueWith%2A> aşırı yüklemesi kullanabilirsiniz. Örneğin, Devamlılığın yalnızca öncül işlemi başarıyla tamamlandığında veya hatalı bir durumda tamamlanırsa çalıştırılacağını belirtebilirsiniz. Öncül, devamlılık çağırmaya hazırlandığında koşul doğru değilse, devamlılık geçişleri doğrudan <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma geçer ve daha sonra başlatılamaz.  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yönteminin aşırı yüklemeleri gibi çok sayıda çoklu görev devamlılığı yöntemi de bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametresi içerir. Ancak tüm <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> numaralandırma üyelerinin yalnızca bir alt kümesi geçerlidir. <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>gibi <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> numaralandırmasında karşılıkları olan <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> değerler belirtebilirsiniz. Çoklu görev devamlılığı ile `NotOn` veya `OnlyOn` seçeneklerinden birini belirtirseniz, çalışma zamanında bir <xref:System.ArgumentOutOfRangeException> özel durumu oluşturulur.  
  
 Görev devamlılık seçenekleri hakkında daha fazla bilgi için <xref:System.Threading.Tasks.TaskContinuationOptions> konusuna bakın.  
  
## <a name="passing-data-to-a-continuation"></a>Verileri Devamlıya geçirme  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi, öncül öğesine bir başvuruyu bir bağımsız değişken olarak devamlılık Kullanıcı temsilcisine geçirir. Öncül bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesneysa ve görev tamamlanana kadar çalışırsa, devamlılık görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğine erişebilir.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği, görev tamamlanana kadar engeller. Ancak, görev iptal edildiyse veya hata verdiyse, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğine erişme girişimi bir <xref:System.AggregateException> özel durumu oluşturur. Aşağıdaki örnekte gösterildiği gibi <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> seçeneğini kullanarak bu sorundan kaçınabilirsiniz.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Öncül başarıyla tamamlanmayı çalıştırmadığından bile devamlılığın çalıştırılmasını istiyorsanız özel duruma karşı koruma gerekir. Bir yaklaşım, öncül öğesinin <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliğini test etmek ve yalnızca durum <xref:System.Threading.Tasks.TaskStatus.Faulted> veya <xref:System.Threading.Tasks.TaskStatus.Canceled>değilse <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğine erişmeyi dener. Ayrıca, öncül öğesinin <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini inceleyebilirsiniz. Daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Aşağıdaki örnek, önceki örneği, öncül 'ın <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğine yalnızca durumu <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>olarak erişmek için değiştirir.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Devamlılığını iptal etme  
 Bir devamlılığın <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği, aşağıdaki durumlarda <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> olarak ayarlanır:  
  
- İptal isteğine yanıt olarak <xref:System.OperationCanceledException> bir özel durum oluşturur. Herhangi bir görevde olduğu gibi, özel durum devamlılığın geçirildiği aynı belirteci içeriyorsa, birlikte iptalin iptali onayı olarak değerlendirilir.  
  
- Devamlılık, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği `true`olan bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> geçirilir. Bu durumda, devamlılık başlamaz ve <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma geçer.  
  
- <xref:System.Threading.Tasks.TaskContinuationOptions> bağımsız değişkeni tarafından ayarlanan koşul karşılanmadığından devamlılık hiçbir şekilde çalışmaz. Örneğin, bir öncül <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> duruma geçtiğinde, <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> seçeneğini geçen devamlılık çalışmaz ancak <xref:System.Threading.Tasks.TaskStatus.Canceled> durumuna geçer.  
  
 Bir görev ve devamlılık aynı mantıksal işlemin iki parçasını temsil ediyorsa, aşağıdaki örnekte gösterildiği gibi aynı iptal belirtecini her iki göreve da geçirebilirsiniz. Bu, 33 ile bölünebilen tamsayıların bir listesini üreten bir öncül öğesinden oluşur ve bu da devamlıya geçirilir. Devam eden devamlılık listeyi görüntüler. Hem öncül hem de devamlılık rastgele aralıklarla düzenli olarak duraklatılır. Ayrıca, bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesnesi, beş saniyelik bir zaman aşımı aralığından sonra `Elapsed` metodunu yürütmek için kullanılır. Bu örnek, şu anda yürütülmekte olan görevin <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> yöntemi aramasına neden olan <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemini çağırır. Öncül veya devamlılık yürütüldüğü zaman <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yönteminin çağrılmaması, rastgele oluşturulan duraklamalar süresine bağlıdır. Öncül iptal edilirse, devamlılık başlamacaktır. Öncül iptal edilmediğinde, belirteç devam etmek için hala kullanılabilir.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Devamlılığın, devamlılığı oluştururken <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> seçeneğini belirterek devamlılık belirteci vermeden iptal edilse de devamlılığın yürütülmesini engelleyebilirsiniz. Aşağıda basit bir örnek verilmiştir.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Devamlılık <xref:System.Threading.Tasks.TaskStatus.Canceled> duruma geçtikten sonra, bu devamlılıklar için belirtilen <xref:System.Threading.Tasks.TaskContinuationOptions> bağlı olarak, izleyen devamlılıkları etkileyebilir.  
  
 Bırakılan devamlılık başlamaz.  
  
## <a name="continuations-and-child-tasks"></a>Devamlılıklar ve alt görevler  
 Bir devamlılık, eklenen alt görevlerinin tümü tamamlanana kadar çalışmaz. Devamlılık, ayrılmış alt görevlerin bitmesini beklemez. Aşağıdaki iki örnek, bir devamlılık oluşturan bir öncül öğesine iliştirilmiş ve bu gruptan ayrılan alt görevleri gösterir. Aşağıdaki örnekte, devamlılık yalnızca tüm alt görevler tamamlandıktan sonra çalışır ve örneği birden çok kez çalıştırarak her seferinde aynı çıktıyı üretir. Örnek, varsayılan olarak <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi, varsayılan görev oluşturma seçeneği <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>olan bir üst görev oluşturduğunda <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemini çağırarak antecedent 'yi başlatır.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Ancak alt görevler öncül öğesinden ayrılımışsa, alt görevlerin durumundan bağımsız olarak öncül sona erer tamamlanmaz devamlılık çalışır. Sonuç olarak, aşağıdaki örnekte birden çok çalıştırma, görev zamanlayıcının her bir alt görevi nasıl ele dığına bağlı olarak değişken çıktı üretebilir.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Öncül görevin son durumu, bağlı olan tüm alt görevlerin son durumuna bağlıdır. Ayrılmış alt görevlerin durumu üst öğeyi etkilemez. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Durumu devamlılıklar ile ilişkilendirme  
 Rastgele durumu, bir görev devamlılığı ile ilişkilendirebilirsiniz. <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemi, her birinin devamlılık durumunu temsil eden bir <xref:System.Object> değer alan aşırı yüklenmiş sürümler sağlar. Daha sonra <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliğini kullanarak bu durum nesnesine erişebilirsiniz. Değer sağlamazsanız bu durum nesnesi `null`.  
  
 Devamlılık durumu, [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) kullanan mevcut kodu tpl 'yi kullanacak şekilde dönüştürdüğünüzde faydalıdır. APM 'de, genellikle **BEGIN**_Method_ yönteminde nesne durumu sağlarsınız ve daha sonra bu duruma <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> özelliğini kullanarak erişirsiniz. <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemini kullanarak, TPL 'yi kullanmak için APM kullanan kodu dönüştürürken bu durumu koruyabilirsiniz.  
  
 Devamlılık durumu, Visual Studio hata ayıklayıcısında <xref:System.Threading.Tasks.Task> nesneleriyle çalıştığınızda da yararlı olabilir. Örneğin, **paralel görevler** penceresinde, **görev** sütunu her görev için durum nesnesinin dize gösterimini görüntüler. **Paralel görevler** penceresi hakkında daha fazla bilgi için, bkz. [Görevler penceresini kullanma](/visualstudio/debugger/using-the-tasks-window).  
  
 Aşağıdaki örnek, devamlılık durumunun nasıl kullanılacağını göstermektedir. Bir devamlılık görevleri zinciri oluşturur. Her görev, <xref:System.Threading.Tasks.Task.ContinueWith%2A> yönteminin `state` parametresi için geçerli saati bir <xref:System.DateTime> nesnesi sağlar. Her <xref:System.DateTime> nesnesi, devamlılık görevinin oluşturulduğu süreyi temsil eder. Her görev, görevin bittiği süreyi temsil eden ikinci bir <xref:System.DateTime> nesnesi sonucu olarak üretilir. Tüm görevler bittikten sonra bu örnek, oluşturma zamanını ve her devamlılık görevinin bittiği saati görüntüler.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Devamlılıklardan oluşan özel durumları işleme  
 Öncül-devamlılık ilişkisi üst-alt ilişkisi değildir. Devamlılıklar tarafından oluşturulan özel durumlar, öncül öğesine yayılmaz. Bu nedenle, devamlılıklar tarafından oluşturulan özel durumları aşağıdaki gibi başka bir görevde idare ettiğiniz şekilde işleyin:  
  
- Devamlılığın bekleneceği <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemini ya da genel karşılığına sahip olabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, bir öncül ve sürekliliği için aynı `try` deyimindeki devamlılığını bekleyebilirsiniz.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- İlk devamlılığın <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini gözlemlemek için ikinci devamlılık kullanabilirsiniz. Aşağıdaki örnekte, bir görev var olmayan bir dosyadan okumaya çalışır. Devamlılık daha sonra, öncül görevde özel durumla ilgili bilgileri görüntüler.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> seçeneğiyle çalıştırıldığı için, devamlılık yalnızca öncül içinde bir özel durum oluşursa yürütülür ve bu nedenle, öncül 'un <xref:System.Threading.Tasks.Task.Exception%2A> özelliğinin `null`olmadığını varsayabilir. Devamlılık, öncül içinde bir özel durum oluşturulup oluşturulmayacağını denetlüyorsa, aşağıdaki kod parçasının gösterdiği gibi, özel durumu işlemeye çalışmadan önce, öncül 'ın <xref:System.Threading.Tasks.Task.Exception%2A> özelliğinin `null` olup olmadığını denetlemesi gerekir.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
- Devamlılık, <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği kullanılarak oluşturulan iliştirilmiş bir alt görev ise, diğer tüm bağlı alt bir örnekte olduğu gibi, özel durumları üst öğe tarafından çağıran iş parçacığına yayılır. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
