---
title: Görev tabanlı zaman uyumsuz programlama-.NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 66904a24817eee0161d877ace7f4584d58fe30f0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507578"
---
# <a name="task-based-asynchronous-programming"></a>Görev tabanlı zaman uyumsuz programlama

Görev paralel kitaplığı (TPL), zaman uyumsuz bir işlemi temsil eden bir *görev*kavramını temel alır. Bazı yollarla, bir görev bir iş parçacığına veya <xref:System.Threading.ThreadPool> iş öğesine benzer, ancak daha yüksek bir soyutlama düzeyinde olur. *Görev Paralelliği* terimi aynı anda çalışan bir veya daha fazla bağımsız görevi ifade eder. Görevler iki adet birincil avantaj sağlar:

- Sistem kaynaklarının daha verimli ve daha ölçeklenebilir kullanımı.

     Arka planda görevler, iş parçacığı sayısını belirleyen ve <xref:System.Threading.ThreadPool>izleyen ve aktarım hızını en üst düzeye çıkarmak için Yük Dengeleme sağlayan algoritmalarla geliştirilmiş olan öğesine sıraya alınır. Bu, görevleri oldukça basit hale getirir ve hassas paralellik sağlamak için bunlardan çok sayıda oluşturabilirsiniz.

- Bir iş parçacığı veya iş öğesi ile mümkün olandan daha programlı denetim.

     Görevler ve bunların etrafına yerleşik çatı, bekleme, iptal, devamlılık, sağlam özel durum işleme, ayrıntılı durum, özel zamanlama ve daha fazlasını destekleyen zengin bir API kümesi sağlar.

Bu iki nedenle de TPL, .NET Framework'te çoklu iş parçalı, zaman uyumsuz ve paralel kod yazma için tercih edilen API'dir.

## <a name="creating-and-running-tasks-implicitly"></a>Görevleri örtülü olarak oluşturma ve çalıştırma

Yöntemi <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> , her türlü rastgele deyimi eşzamanlı olarak çalıştırmak için kullanışlı bir yol sağlar. Her iş öğesi için <xref:System.Action> bir temsilci geçirin. Lambda ifadelerini kullanmak, bu temsilcileri oluşturmanın en kolay yoludur. Lambda ifadesi adlandırılmış bir yöntemi çağırabilir veya satır içi kodu sağlayabilir. Aşağıdaki örnek, aynı anda çalışan <xref:System.Threading.Tasks.Parallel.Invoke%2A> iki görev oluşturan ve Başlatan temel bir çağrıyı gösterir. İlk görev adlı `DoSomeWork`bir yöntemi çağıran bir lambda ifadesiyle temsil edilir ve ikinci görev adlı `DoSomeOtherWork`bir yöntemi çağıran bir lambda ifadesiyle temsil edilir.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Tarafından <xref:System.Threading.Tasks.Parallel.Invoke%2A> arka planda <xref:System.Threading.Tasks.Task> oluşturulan örneklerin sayısı, sağlanmış olan temsilcilerin sayısına eşit değildir. TPL, özellikle çok sayıda temsilci bulunduğunda, çeşitli iyileştirmeler uygulayabilir.

Daha fazla bilgi için bkz. [nasıl yapılır: paralel Işlemleri yürütmek Için Parallel. Invoke kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Görev yürütme üzerinde daha fazla denetim veya görevden bir değer döndürme için <xref:System.Threading.Tasks.Task> nesnelerle daha açık bir şekilde çalışmanız gerekir.

## <a name="creating-and-running-tasks-explicitly"></a>Görevleri açıkça oluşturma ve çalıştırma

Değer döndürmeyen bir görev, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı tarafından temsil edilir. Değeri döndüren bir görev, öğesinden <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task>devralan sınıf tarafından temsil edilir. Görev nesnesi altyapı ayrıntılarını işler ve çağrıyı yapan iş parçacığının görevin ömrü boyunca erişebildiği yöntemler ve özellikler sağlar. Örneğin, bir görevin <xref:System.Threading.Tasks.Task.Status%2A> özelliğine, çalışmaya başlayıp başlamadığına, tamamlanana kadar çalışıp çalışmadığını, iptal edildiğini veya bir özel durum oluşturdu. Durum, bir <xref:System.Threading.Tasks.TaskStatus> sabit listesi ile temsil edilir.

Görev oluşturduğunuzda, görevin yürüteceği kodu kapsülleyen bir kullanıcı temsilcisi verirsiniz. Temsilci adlandırılmış bir temsilci, adsız bir yöntem veya lambda ifadesi olarak ifade edilebilir. Lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi adlandırılmış bir yönteme yapılan çağrıyı içerebilir. Örneğin, konsol modu uygulaması bitmeden önce görevin yürütmeyi <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tamamlamasını sağlamak için yöntemine bir çağrı içerdiğine dikkat edin.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Tek bir işlemde bir görevi <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> oluşturmak ve başlatmak için yöntemlerini de kullanabilirsiniz. Görevi yönetmek için <xref:System.Threading.Tasks.Task.Run%2A> Yöntemler, geçerli iş parçacığıyla hangi görev çizelgeleyicinin ilişkili olduğuna bakılmaksızın varsayılan görev zamanlayıcısını kullanır. Görevin <xref:System.Threading.Tasks.Task.Run%2A> oluşturulması ve zamanlanması üzerinde daha fazla denetim yapmanız gerekmiyorsa, görevler oluşturmak ve başlatmak için tercih edilen yöntem, yöntemler için tercih edilen yoldur.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Aynı zamanda bir işlem içinde <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bir görevi oluşturmak ve başlatmak için yöntemini de kullanabilirsiniz. Oluşturma ve zamanlamanın ayrılması gerekmiyorsa ve ek görev oluşturma seçeneklerine veya belirli bir Zamanlayıcı kullanımına ihtiyacınız varsa ya da aşağıdaki örnekte gösterildiği gibi, <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği aracılığıyla alabileceğiniz göreve ek durum iletmeniz gerektiğinde bu yöntemi kullanın.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task>ve <xref:System.Threading.Tasks.Task%601> her biri varsayılan bir <xref:System.Threading.Tasks.Task.Factory%2A> örneğini döndüren statik bir özellik sunar <xref:System.Threading.Tasks.TaskFactory>, böylece yöntemini olarak `Task.Factory.StartNew()`çağırabilirsiniz. Ayrıca, aşağıdaki örnekte, görevler türünde <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>olduğundan, her birinin hesaplama sonucunu içeren bir public <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği vardır. Görevler zaman uyumsuz olarak çalışır ve herhangi bir sırada tamamlanabilir. Hesaplama tamamlanmadan <xref:System.Threading.Tasks.Task%601.Result%2A> önce özelliğe erişilirse, özelliği, değer kullanılabilir olana kadar çağıran iş parçacığını engeller.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Daha fazla bilgi için bkz. [nasıl yapılır: görevden değer döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Temsilci oluşturmak için lambda ifadesini kullandığınızda, kaynak kodunuzun o noktasında görünür durumda olan tüm değişkenlere erişebilirsiniz. Ancak bazı durumlarda, çoğunlukla da döngülerde, bir lambda değişkeni beklenen şekilde yakalamaz. Her yinelemeden sonra oluşturduğu değeri değil, yalnızca son değeri yakalar. Aşağıdaki örnek, sorunu gösterir. Bir `CustomData` nesneyi örnekleyen ve döngü sayacını nesnenin tanımlayıcısı olarak kullanan bir lambda ifadesine döngü sayacı geçirir. Örneğin çıkışının gösterdiği gibi, her `CustomData` nesnenin aynı tanımlayıcısı vardır.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Oluşturucusu aracılığıyla göreve durum nesnesi döndürerek her yinelemede değere erişebilirsiniz. Aşağıdaki örnek, `CustomData` nesnesi oluşturulurken döngü sayacını kullanarak önceki örneği değiştirir, bu, sırasıyla lambda ifadesine geçirilir.  Örneğin çıkışının gösterdiği gibi, her `CustomData` bir nesne artık nesnenin örneği oluşturulduğu zaman döngü sayacının değerine göre benzersiz bir tanımlayıcıya sahiptir.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Bu durum, görev temsilcisine bir bağımsız değişken olarak geçirilir ve <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği kullanılarak görev nesnesinden erişilebilir.  Aşağıdaki örnek, önceki örneğin bir çeşididir. Lambda ifadesine geçirilen <xref:System.Threading.Tasks.Task.AsyncState%2A> `CustomData` nesneler hakkındaki bilgileri göstermek için özelliğini kullanır.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Görev Kimliği

Her görev, kendisini bir uygulama etki alanında benzersiz bir şekilde tanımlayan bir tamsayı KIMLIĞI alır ve <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> özelliği kullanılarak erişilebilir. KIMLIK, Visual Studio hata ayıklayıcısı **paralel yığınları** ve **Görevler** Windows 'da görev bilgilerini görüntülemek için yararlıdır. Kimlik gecikmeli olarak oluşturulur, yani istenene kadar oluşturulmaz; bu nedenle, program her çalıştırıldığında bir görevin farklı bir kimliği olabilir. Görev kimliklerinin hata ayıklayıcıda nasıl görüntüleneceği hakkında daha fazla bilgi için, bkz. [Görevler penceresini kullanma](/visualstudio/debugger/using-the-tasks-window) ve [Paralel Yığınlar penceresini kullanma](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Görev oluşturma seçenekleri

Görevleri oluşturan çoğu API, bir <xref:System.Threading.Tasks.TaskCreationOptions> parametreyi kabul eden aşırı yüklemeler sağlar. Bu seçeneklerden birini belirleyerek görev zamanlayıcıya iş parçacığı havuzundaki görevi nasıl zamanlayacağını söyleyebilirsiniz. Aşağıdaki tabloda, çeşitli görev oluşturma seçenekleri listelenmektedir.

|<xref:System.Threading.Tasks.TaskCreationOptions>parametre değeri|Açıklama|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Hiç seçenek belirtilmemişse varsayılan değerdir. Zamanlayıcı, görevi zamanlamak için varsayılan buluşsal yöntemlerini kullanır.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Daha önce oluşturulmuş görevlerin daha önce çalıştırılabilmesi ve daha sonra oluşturulmuş görevlerin daha sonra çalıştırılabilmesi için görevin zamanlanması gerektiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Görevin uzun süren bir işlemi temsil ettiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Varsa, geçerli görevin eklenen bir alt görev olarak oluşturulması gerektiğini belirtir. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Bir iç görev `AttachedToParent` seçeneği belirtiyorsa, bu görevin iliştirilmiş bir alt görev olmayacaktır.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Belirli bir görev içinde veya <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> gibi yöntemleri çağırarak oluşturulan görevlere yönelik görev zamanlayıcının, bu görevin çalıştığı Zamanlayıcı yerine varsayılan Zamanlayıcı olduğunu belirtir.|

Seçenekler bit düzeyinde **or** işlemi kullanılarak birleştirilebilir. Aşağıdaki örnek, <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> seçeneğine sahip bir görevi gösterir.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Görevler, iş parçacıkları ve kültür

Her iş parçacığında, sırasıyla <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri tarafından tanımlanan ILIŞKILI bir kültür ve UI kültürü vardır. Bir iş parçacığının kültürü, bu gibi işlemlerde biçimlendirme, ayrıştırma, sıralama ve dize karşılaştırması gibi kullanılır. Bir iş parçacığının UI kültürü, kaynak aramasında kullanılır. Normalde, <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özelliklerini kullanarak bir uygulama etki alanındaki tüm iş parçacıkları için varsayılan bir kültür belirtmediğiniz müddetçe, bir iş parçacığının varsayılan kültürü ve Kullanıcı arabirimi kültürü sistem kültürü tarafından tanımlanır. Bir iş parçacığının kültürünü açık olarak ayarlayıp yeni bir iş parçacığı başlattığınızda, yeni iş parçacığı çağıran iş parçacığının kültürünü almaz; Bunun yerine, kültürü varsayılan sistem kültürüdür. .NET Framework 4,6 ' den önceki .NET Framework sürümlerini hedefleyen uygulamalar için görev tabanlı programlama modeli bu uygulamaya uymuyor.

> [!IMPORTANT]
> Çağıran iş parçacığının bir görevin bir parçası olarak bir görev bağlamının bir parçası olarak, .NET Framework 4,6 *altında çalışan* uygulamalar değil .NET Framework 4,6 ' i *hedefleyen* uygulamalar için geçerli olduğunu unutmayın. **Yeni proje** iletişim kutusunun en üstündeki veya Visual Studio <xref:System.Runtime.Versioning.TargetFrameworkAttribute> dışında açılan listeden bu sürümü seçerek, projenizi visual Studio 'da oluştururken .NET Framework belirli bir sürümünü hedefleyebilirsiniz. .NET Framework 4,6 ' den önceki .NET Framework sürümlerini hedef alan veya .NET Framework belirli bir sürümünü Hedeflemeyin, bir görevin kültürü, çalıştığı iş parçacığının kültürü tarafından belirlenmeye devam eder.

.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, çağıran iş parçacığının kültürü, görev bir iş parçacığı havuzu iş parçacığında zaman uyumsuz olarak çalıştırılsa bile her bir görev tarafından devralınır.

Aşağıdaki örnek basit bir çizim sağlar. .NET Framework 4,6 ' <xref:System.Runtime.Versioning.TargetFrameworkAttribute> i hedeflemek için özniteliğini kullanır ve uygulamanın geçerli kültürünü Fransızca (Fransa) ya da Fransızca (Fransa) zaten geçerli kültür, ingilizce (Birleşik Devletler) olarak değiştirir. Daha sonra yeni kültürde para `formatDelegate` birimi değeri olarak biçimlendirilen bazı sayılar döndüren adlı bir temsilciyi çağırır. Temsilci bir görev olarak zaman uyumlu veya zaman uyumsuz olarak, çağıran iş parçacığının kültürü zaman uyumsuz görev tarafından devralındığından beklenen sonucu döndürür.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Visual Studio kullanıyorsanız, bu <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliği atlayabilirsiniz ve **Yeni proje** iletişim kutusunda projeyi oluştururken hedef olarak .NET Framework 4,6 ' u seçebilirsiniz.

Uygulamaların .NET Framework .NET Framework 4,6 ' den önce hedef sürümlerini yansıtan çıktı için, kaynak koddan <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliğini kaldırın. Çıktı, çağıran iş parçacığının kültürüne değil, varsayılan sistem kültürünün biçimlendirme kurallarını yansıtır.

Zaman uyumsuz görevler ve kültür hakkında daha fazla bilgi için, <xref:System.Globalization.CultureInfo> konusunun "Kültür ve zaman uyumsuz görev tabanlı işlemler" bölümüne bakın.

## <a name="creating-task-continuations"></a>Görev devamlılıkları oluşturma

Ve <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> yöntemleri, *öncül görevi* bittiğinde başlamak için bir görev belirtmenizi sağlar. Devamlılık görevinin temsilcisi öncül göreve bir başvuru geçirdiğinden, öncül görevin durumunu inceleyebilir ve <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğinin değerini alarak, öncül 'un çıkışını devamlılık için giriş olarak kullanabilir.

Aşağıdaki örnekte, `getData` görev <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> yöntemine bir çağrı ile başlatılır. `processData` Görev `getData` tamamlandığında otomatik olarak başlatılır ve `displayData` `processData` tamamlandığında başlatılır. `getData`görevin `processData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği aracılığıyla `getData` görevle erişilebilen bir tamsayı dizisi üretir. `processData` Görev bu diziyi işler ve türü, <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metoduna geçirilen lambda ifadesinin dönüş türünden çıkarılan bir sonuç döndürür. `displayData` Görev `processData` <xref:System.Tuple%603> tamamlandığında otomatik olarak yürütülür ve `processData` lambda ifadesinin döndürdüğü nesne görevin `displayData` `processData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği aracılığıyla görev için erişilebilir olur. `displayData` Görev, `processData` görevin sonucunu alır ve türü benzer bir şekilde çıkarılan ve <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğindeki program için kullanılabilir hale getirilen bir sonuç üretir.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Bir <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> örnek yöntemi olduğundan, her öncül görev için bir <xref:System.Threading.Tasks.Task%601> nesne oluşturmak yerine Yöntem çağrılarını birlikte zincirleyebilirsiniz. Aşağıdaki örnek, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yönteme bir araya gelen çağrıları zincirden hariç olmak üzere önceki örnekle aynıdır. Yöntem çağrılarının zinciri <xref:System.Threading.Tasks.Task%601> tarafından döndürülen nesnenin son devamlılık görevi olduğunu unutmayın.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri, birden çok görevden devam etmeyi sağlar.

Daha fazla bilgi için bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Ayrılmış alt görevler oluşturma

Bir görevde çalışan Kullanıcı kodu yeni bir görev oluşturduğunda ve bu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği belirtmediği zaman, yeni görev üst görevle herhangi bir özel şekilde eşitlenmez. Eşitlenmemiş bu görev türü, *ayrılmış iç içe görev* veya *ayrılmış alt görev*olarak adlandırılır. Aşağıdaki örnek, bağlantısı kesik bir tane alt görev oluşturan bir üst görevi gösterir.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Üst görevin, ayrılmış alt görevin tamamlanmasını beklemediğine dikkat edin.

## <a name="creating-child-tasks"></a>Alt görevler oluşturma

Bir görevde çalışan Kullanıcı kodu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneğiyle bir görev oluşturduğunda, yeni görev üst görevin *iliştirilmiş alt görevi* olarak bilinir. Üst görev örtük olarak <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> tüm eklenen alt görevlerin bitmesini beklediği için yapılandırılmış görev paralelliğini ifade etmek için seçeneğini kullanabilirsiniz. Aşağıdaki örnek, on tane bağlı alt görev oluşturan bir üst görevi gösterir. Örnek, üst görevin bitmesini beklemek için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırırsa, eklenen alt görevlerin tamamlanmasını açıkça beklemek zorunda değildir.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Üst görev, diğer görevlerin üst <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> göreve iliştirmesini engellemek için seçeneğini kullanabilir. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Görevlerin bitmesi bekleniyor

Ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türleri, bir görevin bitmesini beketmenize <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> olanak sağlayan yöntemlerin birkaç aşırı yüklemesini sağlar. Ayrıca, statik <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemlerin aşırı yüklemeleri, bir görev dizisinin herhangi birinin veya tümünün bitmesini beketmenize olanak tanır.

Genellikle, aşağıdaki nedenlerden biri için beklemeniz gerekir:

- Ana iş parçacığı, bir göreve göre hesaplanan nihai sonuca bağlıdır.

- Görevden oluşturulan özel durumları işlemeniz gerekir.

- Uygulama, tüm görevlerin yürütmesi tamamlanmadan sonlanabilir. Örneğin, (uygulama giriş noktası) içindeki `Main` tüm zaman uyumlu kod yürütüldüğü anda konsol uygulamaları sonlandırılır.

Aşağıdaki örnek, özel durum işleme içermeyen temel düzeni gösterir.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Özel durum işlemeyi gösteren bir örnek için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Bazı aşırı yüklemeler bir zaman aşımı belirtmenize izin verir ve diğer bir deyişle, bir <xref:System.Threading.CancellationToken> giriş parametresi olarak diğerleri, bekleme süresi programlı bir şekilde veya kullanıcı girdisine yanıt olarak iptal edilebilir.

Bir görevi beklerken, bu görevin, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği kullanılarak oluşturulan tüm alt öğelerini örtük olarak beklemiş olursunuz. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>görev zaten tamamlanmışsa, hemen döndürür. Bir görev tarafından oluşturulan tüm özel durumlar, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi görev tamamlandıktan sonra çağrılsa bile bir yöntemi tarafından oluşturulur.

## <a name="composing-tasks"></a>Görevler oluşturuluyor

<xref:System.Threading.Tasks.Task> Ve <xref:System.Threading.Tasks.Task%601> sınıfları, yaygın desenleri uygulamak ve C#, Visual Basic ve F # tarafından sağlanan zaman uyumsuz dil özelliklerini daha iyi kullanmak için birden fazla görev oluşturmanıza yardımcı olabilecek çeşitli yöntemler sağlar. Bu bölümde <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A> <xref:System.Threading.Tasks.Task.Delay%2A>, ve <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemleri açıklanmaktadır.

### <a name="taskwhenall"></a>Task.WhenAll

Yöntemi <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> , birden fazla <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesinin tamamlanmasını zaman uyumsuz olarak bekler. Tek düzen olmayan görevler kümesini beklemenize olanak tanıyan aşırı yüklü sürümler sağlar. Örneğin, birden çok <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesnesinin bir yöntem çağrısından tamamlanmasını bekleyebilirsiniz.

### <a name="taskwhenany"></a>Task.WhenAny

Yöntemi <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , birden fazla <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesneden birinin tamamlanmasını zaman uyumsuz olarak bekler. <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Yönteminde olduğu gibi bu yöntem, Tekdüzen olmayan görev kümelerini beklemenizi sağlayan aşırı yüklenmiş sürümler sağlar. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntemi, aşağıdaki senaryolarda özellikle yararlıdır.

- Yedekli işlemler. Birçok şekilde gerçekleştirilen bir algoritma veya işlem düşünün. İlk olarak sona erme işlemini seçmek için <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemini kullanabilir ve ardından kalan işlemleri iptal edebilirsiniz.

- Dönüşümlü işlemler. Her işlem tamamlandığında birden çok işlem başlatabilir ve her işlem bittiğinde sonuçları <xref:System.Threading.Tasks.Task.WhenAny%2A> işlemek için yöntemini kullanmanız gerekir. Bir işlem tamamlandıktan sonra bir veya daha fazla ek görev başlatabilirsiniz.

- Daraltılmış işlemler. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntemi, eşzamanlı işlemlerin sayısını sınırlayarak önceki senaryoyu genişletmek için kullanabilirsiniz.

- Süresi dolan işlemler. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntemi, bir veya daha fazla görev arasında seçim yapmak için yöntemini ve <xref:System.Threading.Tasks.Task.Delay%2A> yöntemi tarafından döndürülen bir görev gibi belirli bir zamandan sonra sona ererek geçen bir görevi kullanabilirsiniz. <xref:System.Threading.Tasks.Task.Delay%2A> Yöntemi aşağıdaki bölümde açıklanmıştır.

### <a name="taskdelay"></a>Task.Delay

Yöntemi <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> , belirtilen zamandan <xref:System.Threading.Tasks.Task> sonra bitiyor bir nesne oluşturur. Bazen verileri yoklayan, zaman aşımlarını tanıtan, belirli bir süre boyunca kullanıcı girişinin işlenmesini erteleyen, vb. işlemler yapan döngüler oluşturmak için bu yöntemi kullanabilirsiniz.

### <a name="tasktfromresult"></a>Task(T).FromResult

<xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> Yöntemini kullanarak, önceden hesaplanmış sonucu tutan bir <xref:System.Threading.Tasks.Task%601> nesne oluşturabilirsiniz. Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesne döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> nesnenin sonucu zaten hesaplanmışsa yararlıdır. Bir önbellekte tutulan zaman uyumsuz <xref:System.Threading.Tasks.Task.FromResult%2A> indirme işlemlerinin sonuçlarını almak için kullanan bir örnek için bkz. [nasıl yapılır: önceden hesaplanan görevler oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Görevlerde özel durumları işleme

Bir görev bir veya daha fazla özel durum oluşturduğunda, özel durumlar bir <xref:System.AggregateException> özel durumla sarmalanır. Bu özel durum, genellikle görevin bitmesi için bekleyen iş parçacığı veya <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğe erişen iş parçacığı olan görevle birleştiren iş parçacığına geri yayılır. Bu davranış, tüm işlenmemiş özel durumların varsayılan olarak işlemi sonlandırması gerektiğini belirten .NET Framework ilkesini zorlamaya yarar. Çağıran kod, bir `try` / `catch` blokta aşağıdakilerden birini kullanarak özel durumları işleyebilir:

- <xref:System.Threading.Tasks.Task.Wait%2A> Yöntemi

- <xref:System.Threading.Tasks.Task.WaitAll%2A> Yöntemi

- <xref:System.Threading.Tasks.Task.WaitAny%2A> Yöntemi

- <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği

Katılım iş parçacığı, görev atık toplanmadan önce <xref:System.Threading.Tasks.Task.Exception%2A> özelliğe erişerek özel durumları da işleyebilir. Bu özelliğe erişerek, işlenmeyen özel durumun, nesne hazırlandığında işlemi sonlandıran özel durum yayma davranışını tetiklemesini engellersiniz.

Özel durumlar ve görevler hakkında daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Görevleri iptal etme

<xref:System.Threading.Tasks.Task> Sınıfı birlikte iptalleri destekler ve .NET Framework 4 ' te tanıtılan <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> sınıflarıyla tamamen tümleşiktir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Sınıftaki oluşturucuların birçoğu bir giriş parametresi olarak bir <xref:System.Threading.CancellationToken> nesnesi alır. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> Ve <xref:System.Threading.Tasks.Task.Run%2A> aşırı yüklemelerin birçoğu Ayrıca bir <xref:System.Threading.CancellationToken> parametre içerir.

Belirtecini oluşturabilir ve daha sonra <xref:System.Threading.CancellationTokenSource> sınıfını kullanarak iptal isteğini daha sonra verebilirsiniz. Belirteci bağımsız değişken <xref:System.Threading.Tasks.Task> olarak öğesine geçirin ve ayrıca, bir iptal isteğine yanıt verme işini sağlayan Kullanıcı temsilcinizdeki aynı belirtece başvurun.

Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: bir görevi ve alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>TaskFactory Sınıfı

Sınıfı <xref:System.Threading.Tasks.TaskFactory> , görevler ve devamlılık görevleri oluşturmak ve başlatmak için bazı ortak desenleri kapsülleyen statik yöntemler sağlar.

- En yaygın desenler <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, tek bir bildirimde bir görev oluşturan ve Başlatan bir görevdir.

- Birden çok öncüllerin 'dan devamlılık görevleri oluştururken, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> <xref:System.Threading.Tasks.Task%601> sınıfındaki yöntemini veya yöntemini ya da eşdeğerlerini kullanın. Daha fazla bilgi için bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Zaman uyumsuz programlama `BeginX` modelini ve `EndX` yöntemlerini bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örneğinde kapsüllemek için <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemlerini kullanın. Daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Varsayılan <xref:System.Threading.Tasks.TaskFactory> olarak, <xref:System.Threading.Tasks.Task> sınıf veya <xref:System.Threading.Tasks.Task%601> sınıf üzerinde statik bir özellik olarak erişilebilir. <xref:System.Threading.Tasks.TaskFactory> Ayrıca, doğrudan bir örnek oluşturabilir ve bir <xref:System.Threading.CancellationToken>, bir <xref:System.Threading.Tasks.TaskCreationOptions> seçenek, <xref:System.Threading.Tasks.TaskContinuationOptions> seçenek veya içeren çeşitli seçenekler belirtebilirsiniz. <xref:System.Threading.Tasks.TaskScheduler> Görev fabrikasını oluştururken belirtilen her türlü seçenek, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.TaskCreationOptions> numaralandırma kullanılarak oluşturulmadığı takdirde, görev seçeneklerinin görev fabrikasının özelliklerini geçersiz kılması durumunda, oluşturduğu tüm görevlere uygulanır.

## <a name="tasks-without-delegates"></a>Temsilcileri olmayan görevler

Bazı durumlarda, kendi Kullanıcı temsilciniz yerine bir dış bileşen <xref:System.Threading.Tasks.Task> tarafından gerçekleştirilen bazı zaman uyumsuz işlemleri kapsüllemek için bir kullanmak isteyebilirsiniz. İşlem zaman uyumsuz programlama modeli başlangıç/bitiş düzenine dayanıyorsa, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemlerini kullanabilirsiniz. Böyle bir durum söz konusu değilse, bir görevde işlemi kaydırmak <xref:System.Threading.Tasks.TaskCompletionSource%601> için nesnesini kullanabilir ve bu sayede, özel durum yayma ve devamlılık desteği gibi <xref:System.Threading.Tasks.Task> programlama avantajlarından bazılarını elde edebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Özel zamanlayıcılar

Çoğu uygulama veya kitaplık geliştiricisi, görevin hangi işlemci üzerinde çalıştığını, çalışmasını diğer görevlerle nasıl eşitleyeceğini veya üzerinde nasıl zamanlandığını önemsemez <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Bunlar yalnızca ana bilgisayarda olabildiğince verimli çalışmasını gerektirir. Zamanlama ayrıntıları üzerinde daha hassas bir denetim gerekiyorsa, Görev Paralel Kitaplığı varsayılan görev zamanlayıcı üzerinde bazı ayarları yapılandırmanıza ve hatta özel bir zamanlayıcı girmenize olanak tanır. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>İlgili veri yapıları

TPL'de, hem paralel hem de sıralı senaryolarda yararlı olan çeşitli, yeni genel türler vardır. Bunlar, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanında çok sayıda iş parçacığı açısından güvenli, hızlı ve ölçeklenebilir koleksiyon sınıfları ve örneğin <xref:System.Threading.Semaphore?displayProperty=nameWithType> ve <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>belirli iş yükü türleri için öncüllerinden daha verimli olan birkaç yeni eşitleme türü içerir. .NET Framework 4 ' deki diğer yeni türler, örneğin <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.SpinLock?displayProperty=nameWithType>, önceki sürümlerde kullanılamayan işlevselliği sağlar. Daha fazla bilgi için bkz. [paralel programlama Için veri yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Özel görev türleri

Veya <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>' den devralma yapmanızı öneririz. Bunun yerine, ek verileri veya durumu bir <xref:System.Threading.Tasks.Task.AsyncState%2A> <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesiyle ilişkilendirmek için özelliğini kullanmanızı öneririz. <xref:System.Threading.Tasks.Task> Ve <xref:System.Threading.Tasks.Task%601> sınıflarının işlevlerini genişletmek için uzantı yöntemlerini de kullanabilirsiniz. Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ve [genişletme yöntemleri](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Veya <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>' den ' i veya ' den devralma yapmanız <xref:System.Threading.Tasks.Task.Run%2A>gerekiyorsa, bu <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>mekanizmalar <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>yalnızca <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri oluşturduğundan özel görev tipinizi oluşturmak için, veya, ya da sınıflarını kullanamazsınız. Bunlara ek olarak,,,, ve tarafından sunulan görev devamlılık mekanizmalarını <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.TaskFactory>,, ve <xref:System.Threading.Tasks.TaskFactory%601> tarafından özel görev türü örnekleri oluşturmak için kullanamazsınız, çünkü bu mekanizmalar yalnızca <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesnelerini de oluşturur.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-|-|
|[Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Devamlılıkların nasıl çalıştığını açıklar.|
|[Eklenen ve Ayrılan Alt Görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Ekli ve ayrılmış alt görevler arasındaki farkı açıklar.|
|[Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md)|<xref:System.Threading.Tasks.Task> Nesnesinde yerleşik olan iptal desteğini açıklar.|
|[Özel Durum İşleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Eşzamanlı iş parçacıklarındaki özel durumların nasıl işlendiğini açıklar.|
|[Nasıl yapılır: Paralel İşlemleri Yürütmek için parallel_invoke Kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|' Nin nasıl kullanılacağını <xref:System.Threading.Tasks.Parallel.Invoke%2A>açıklar.|
|[Nasıl yapılır: Bir Görevden Değer Döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Değerlerin görevlerden nasıl döndürüleceğini açıklar.|
|[Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Görevlerin nasıl iptal edildiğini açıklar.|
|[Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Bir önbellekte tutulan zaman uyumsuz <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> indirme işlemlerinin sonuçlarını almak için yönteminin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|İkili ağacı geçirmek için görevlerin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Uzantı yönteminin nasıl kullanılacağını gösterir.|
|[Veri paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Verilerin üzerinde paralel döngüler <xref:System.Threading.Tasks.Parallel.For%2A> oluşturmayı <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve kullanmayı açıklar.|
|[Paralel programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama için üst düzey düğüm.|

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel programlama](../../../docs/standard/parallel-programming/index.md)
- [.NET Core & paralel programlama örnekleri .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
