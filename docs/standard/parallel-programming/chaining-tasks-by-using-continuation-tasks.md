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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159370"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
Eşzamanlı programlamada, ikinci bir işlemi çağırmak ve verileri ona aktarmak için, tamamlandığında tek bir eşzamanlı işlem yaygındır. Geleneksel olarak, devamı geri arama yöntemleri kullanılarak yapılmıştır. Görev Paralel Kitaplığı'nda, aynı işlevsellik *devam görevleri*tarafından sağlanır. Bir devam görevi (aynı zamanda bir devamı olarak da bilinir) öncül olarak bilinen başka *antecedent*bir görev tarafından çağrılan bir eşzamanlı görevdir, öncül bitirdiğinde.  
  
 Devamı nispeten kullanımı kolaydır, ancak yine de güçlü ve esnektir. Örneğin, şunları yapabilirsiniz:  
  
- Verileri öncülden devama aktarın.  
  
- Devamın çağrılacağı veya çağrılmayacağı kesin koşulları belirtin.  
  
- Başlamadan veya çalışırken işbirliği içinde devam etme iptal edin.  
  
- Devamı nasıl zamanlanması gerektiği hakkında ipuçları sağlayın.  
  
- Aynı öncülden birden çok devamı çağırın.  
  
- Birden çok öncülden biri tamamlandığında bir devamı çağırın.  
  
- Zincir herhangi bir rasgele uzunlukta birbiri ardına devam eder.  
  
- Öncül tarafından atılan özel durumları işlemek için bir devam kullanın.  
  
## <a name="about-continuations"></a>Devamları hakkında  
 <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> Devamı, durumda oluşturulan bir görevdir. Öncül görevi veya görevleri tamamlandığında otomatik olarak etkinleştirilir. Kullanıcı <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> kodunda devam çağrısında bulunmanın bir <xref:System.InvalidOperationException?displayProperty=nameWithType> özel durum oluşturur.  
  
 Devamı kendisi birdir <xref:System.Threading.Tasks.Task> ve başlatıldıği iş parçacığı engellemez. Devam <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> görevi bitene kadar engellemek için yöntemi çağırın.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Tek bir öncül için bir devam oluşturma  
 Öncül yöntemi çağırarak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> tamamlandığında çalıştıran bir devamı oluşturursunuz. Aşağıdaki örnekte temel desen gösterilmektedir (netlik için, özel durum işleme atlanır). Haftanın geçerli gününün adını `taskA`gösteren bir <xref:System.DayOfWeek> nesneyi döndüren öncül bir görev yürütür. Öncül tamamlandığında, devam görevi, `continuation`, öncül geçirilir ve sonucunu içeren bir dize görüntüler.

> [!NOTE]
> Bu makaledeki C# örnekleri yöntemüzerindeki `async` değiştiriciden `Main` yararlanır. Bu özellik C# 7.1 ve sonraki durumlarda kullanılabilir. Önceki sürümler, bu örnek kodu derlerken oluşturur. [`CS5001`](../../csharp/misc/cs5001.md) Dil sürümünü C# 7.1 veya daha yeni olarak ayarlamanız gerekir. Dil sürümünü yapılandırma makaledeki dil sürümünü nasıl [yapılandırabileceğinizi](../../csharp/language-reference/configure-language-version.md)öğrenebilirsiniz.
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Birden çok öncül için bir devam oluşturma  
 Ayrıca, bir görev grubundan herhangi biri veya tümü tamamlandığında çalışacak bir devam oluşturabilirsiniz. Tüm öncül görevler tamamlandığında bir devamı yürütmek için statik`Shared` (Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemini <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> veya örnek yöntemini çağırırsınız. Öncül görevlerden herhangi biri tamamlandığında bir devamı yürütmek için statik`Shared` (Visual <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Basic) yöntemini veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemini çağırırsınız.  
  
 Aramaları <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> aşırı yüklemeleri arama iş parçacığı engellemez unutmayın.  Ancak, genellikle arama iş <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> parçacığı <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> engellemez döndürülen <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği almak için tüm ama yöntemleri çağırır.  
  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 10 öncül görevinin sonuçlarını yansıtan bir devam görevi oluşturma yöntemini çağırır. Her öncül görev, 1 ile 10 arasında değişen bir dizin değerini kareler. Öncüller başarıyla tamamlanırsa (onların <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği), <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> devamı özelliği her öncül <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> tarafından döndürülen değerlerin bir dizi. Örnek, bir ile 10 arasındaki tüm sayıların karelerinin toplamını hesaplamak için bunları ekler.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Devam seçenekleri  
 Tek görev devamı oluşturduğunuzda, devamın <xref:System.Threading.Tasks.Task.ContinueWith%2A> hangi koşullar <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> altında başladığını belirtmek için numaralandırma değeri alan bir aşırı yük kullanabilirsiniz. Örneğin, devamın yalnızca öncül başarıyla tamamlanırsa veya yalnızca hatalı bir durumda tamamlanırsa çalışacak olduğunu belirtebilirsiniz. Öncül devam çağırmaya hazır olduğunda koşul doğru değilse, devam doğrudan <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma geçiş eder ve daha sonra başlatılamaz.  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> Yöntemin aşırı yüklemeleri gibi bir dizi çok görevli devam <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> yöntemi de bir parametre içerir. Ancak, yalnızca tüm <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> numaralandırma üyelerinin bir alt kümesi geçerlidir. Numaralandırmada <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> benzerleri olan değerleri belirtebilirsiniz, örneğin <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>ve . Çok görev devamı `NotOn` olan `OnlyOn` seçeneklerden herhangi birini belirtirseniz, çalışma zamanında bir <xref:System.ArgumentOutOfRangeException> özel durum atılır.  
  
 Görev devam seçenekleri hakkında daha <xref:System.Threading.Tasks.TaskContinuationOptions> fazla bilgi için konuya bakın.  
  
## <a name="passing-data-to-a-continuation"></a>Verileri Bir Devama Aktarma  
 Yöntem, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> bir bağımsız değişken olarak devamı kullanıcı temsilcisine öncül bir başvuru geçer. Öncül bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesneyse ve görev tamamlanana kadar çalıştırılırsa, devamı görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğine erişebilir.  
  
 Görev <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> tamamlanana kadar özellik engeller. Ancak, görev iptal edildiyse veya hatalıysa, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğe erişmeye <xref:System.AggregateException> çalışmak bir özel durum oluşturur. Aşağıdaki örnekte gösterildiği <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> gibi, seçeneği kullanarak bu sorunu önleyebilirsiniz.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Öncül başarılı bir şekilde tamamlanmamış olsa bile devamın çalışmasını istiyorsanız, özel durum lara karşı korumanız gerekir. Bir yaklaşım, öncül <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliğini sınamak ve yalnızca <xref:System.Threading.Tasks.Task%601.Result%2A> durum yoksa <xref:System.Threading.Tasks.TaskStatus.Faulted> veya <xref:System.Threading.Tasks.TaskStatus.Canceled>. Ayrıca öncül <xref:System.Threading.Tasks.Task.Exception%2A> özelliğini inceleyebilirsiniz. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) Aşağıdaki örnek, öncül özelliğine <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> erişmek için önceki örneği yalnızca durumu <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Devamı İptal Etme  
 Bir <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> devam Özelliği aşağıdaki <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumlarda ayarlanır:  
  
- İptal isteğine <xref:System.OperationCanceledException> yanıt olarak bir özel durum oluşturur. Herhangi bir görevde olduğu gibi, istisna devamına geçirilen aynı belirteci içeriyorsa, kooperatif iptali bildirimi olarak kabul edilir.  
  
- Devamı olan <xref:System.Threading.CancellationToken?displayProperty=nameWithType> <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği bir `true`geçirilir . Bu durumda, devamı başlamaz ve <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma geçiş yapar.  
  
- <xref:System.Threading.Tasks.TaskContinuationOptions> Bağımsız değişkentarafından ayarlanan koşul karşılanmadığından devamı asla çalışır. Örneğin, bir öncül bir <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> duruma geçerse, <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> geçirilen devamı seçeneği çalışmaz, <xref:System.Threading.Tasks.TaskStatus.Canceled> ancak duruma geçer.  
  
 Bir görev ve devamı aynı mantıksal işlemin iki bölümünü temsil ediyorsa, aşağıdaki örnekte gösterildiği gibi aynı iptal belirtecinizi her iki göreve de geçirebilirsiniz. 33 ile bölünebilen ve devamına geçen bir tamsayı listesi oluşturan bir öncülden oluşur. Devamı sırayla listegörüntüler. Hem öncül hem de devamı rasgele aralıklarla düzenli olarak duraklar. Buna ek <xref:System.Threading.Timer?displayProperty=nameWithType> olarak, bir nesne `Elapsed` beş saniyelik zaman aralığı sonra yöntemi yürütmek için kullanılır. Bu örnek, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> şu anda yürütülen görevin <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> yöntemi çağırmasına neden olan yöntemi çağırır. Yöntemin <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> öncül veya devamı yürütüldüğünde çağrılıp çağrılmadığı rasgele oluşturulan duraklamaların süresine bağlıdır. Öncül iptal edilirse, devamı başlamaz. Öncül iptal edilmezse, belirteç devamını iptal etmek için kullanılabilir.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Ayrıca, devamı oluştururken <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> seçeneği belirterek, bir iptal belirteci sağlamadan, öncülü iptal edilirse, devamın yürütülmesini de engelleyebilirsiniz. Aşağıdaki basit bir örnektir.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Bir devamı <xref:System.Threading.Tasks.TaskStatus.Canceled> devlet gider sonra, bu devamı için belirtilen bağlı <xref:System.Threading.Tasks.TaskContinuationOptions> olarak, takip devamı etkileyebilir.  
  
 Elden çıkarılan devamlar başlamaz.  
  
## <a name="continuations-and-child-tasks"></a>Devamı ve Alt Görevler  
 Bir devam, öncül ve bağlı tüm alt görevleri tamamlanana kadar çalışmaz. Devamı, ayrılmış alt görevlerin tamamlanmasını beklemez. Aşağıdaki iki örnek, bir devamı oluşturan bir öncül'e eklenen ve ondan ayrılan alt görevleri göstermektedir. Aşağıdaki örnekte, devam yalnızca tüm alt görevler tamamlandıktan sonra çalışır ve örneği birden çok kez çalıştırmak her seferinde aynı çıktıyı üretir. Varsayılan olarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntem varsayılan görev oluşturma seçeneği olan bir üst görev oluşturur, çünkü örnek, <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>yöntem çağırarak öncül başlattı.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Ancak, alt görevler öncülden ayrılmışsa, alt görevlerin durumu ne olursa olsun, sonlandırma sona erer bitmez devam çalışır. Sonuç olarak, aşağıdaki örnekten birden çok çalıştırma, görev zamanlayıcısının her alt görevi nasıl işleyiş ettiğine bağlı olarak değişken çıktı üretebilir.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Öncül görevin son durumu, ekli alt görevlerin son durumuna bağlıdır. Ayrılmış alt görevlerin durumu üst öğeyi etkilemez. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
  
## <a name="associating-state-with-continuations"></a>Devlet'i Devamı ile Ilişkilendirme  
 Rasgele durumu görev devamı ile ilişkilendirebilirsiniz. Yöntem, <xref:System.Threading.Tasks.Task.ContinueWith%2A> her devamı durumunu temsil <xref:System.Object> eden bir değer almak aşırı yüklenen sürümleri sağlar. Daha sonra özelliği kullanarak bu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> durum nesnesi erişebilirsiniz. Bir değer `null` sağlamazsanız, bu durum nesnesidir.  
  
 Devam durumu, TPL'yi kullanmak için [Asynchronous Programming Model(APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) kullanan varolan kodu dönüştürdüğünüzde yararlıdır. APM'de, genellikle **Begin**_Method_ yönteminde nesne durumu sağlar ve daha <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> sonra özelliği kullanarak bu duruma erişin. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Yöntemi kullanarak, TPL'yi kullanmak için APM kullanan kodu dönüştürdüğünüzde bu durumu koruyabilirsiniz.  
  
 Devamı durumu, Visual Studio hata <xref:System.Threading.Tasks.Task> ayıkcısındaki nesnelerle çalışırken de yararlı olabilir. Örneğin, Paralel **Görevler** penceresinde, **Görev** sütunu her görev için durum nesnesinin dize gösterimini görüntüler. **Paralel Görevler** penceresi hakkında daha fazla bilgi için [görevler penceresini kullanma'ya](/visualstudio/debugger/using-the-tasks-window)bakın.  
  
 Aşağıdaki örnek, devam durumunun nasıl kullanılacağını gösterir. Bu devam görevleri zinciri oluşturur. Her görev, <xref:System.DateTime> `state` <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemin parametresi için geçerli zamanı, nesneyi sağlar. Her <xref:System.DateTime> nesne, devam görevinin oluşturulduğu zamanı temsil eder. Her görev, sonucu olarak <xref:System.DateTime> görevin bittiği zamanı temsil eden ikinci bir nesne üretir. Tüm görevler tamamlandıktan sonra, bu örnek, oluşturma süresini ve her devam görevinin bittiği zamanı görüntüler.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Devamlardan Atılan Özel Durumları İşleme  
 Öncül-devam ilişkisi bir ebeveyn-alt ilişkisi değildir. Devamları tarafından atılan özel durumlar öncül için yayılmaz. Bu nedenle, başka bir görevde bunları işleyeceğiniz gibi, devamları tarafından atılan özel durumları aşağıdaki gibi işle:  
  
- Devamı beklemek <xref:System.Threading.Tasks.Task.Wait%2A>için <xref:System.Threading.Tasks.Task.WaitAll%2A>, <xref:System.Threading.Tasks.Task.WaitAny%2A> veya yöntem veya genel muadili kullanabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, öncül ve devamı `try` için aynı ifadede bekleyebilirsiniz.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- İlk devamının özelliğini <xref:System.Threading.Tasks.Task.Exception%2A> gözlemlemek için ikinci bir devamı kullanabilirsiniz. Aşağıdaki örnekte, bir görev var olmayan bir dosyadan okumaya çalışır. Devamı daha sonra öncül görevde özel durum hakkında bilgi görüntüler.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> Seçenekle çalıştırıldığı için, devamı yalnızca öncülde bir özel durum oluşursa yürütülür ve bu nedenle öncül <xref:System.Threading.Tasks.Task.Exception%2A> özelliğinin . `null` Devamı, öncülde bir özel durum atılıp atılmadığını yürütürse, aşağıdaki kod parçasının <xref:System.Threading.Tasks.Task.Exception%2A> gösterdiği gibi, öncül özelliğinin özel durumu işlemeye çalışmadan önce olup `null` olmadığını denetlemesi gerekir.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)  
  
- Devamı <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği kullanılarak oluşturulan ekli bir alt görev ise, özel durumları diğer ekli alt oyunda olduğu gibi, üst tarafından çağrı iş parçacığına geri yayılır. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
