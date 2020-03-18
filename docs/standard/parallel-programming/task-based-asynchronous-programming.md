---
title: Görev tabanlı eşzamanlı programlama - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 51292d977f2be87cec7c3481f5004fe5fe756224
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204538"
---
# <a name="task-based-asynchronous-programming"></a>Görev tabanlı asynchronous programlama

Görev Paralel Kitaplığı (TPL), eşzamanlı *bir*işlemi temsil eden görev kavramına dayanır. Bazı yönlerden, bir görev iş <xref:System.Threading.ThreadPool> parçacığına veya iş öğesine benzer, ancak daha yüksek bir soyutlama düzeyindedir. Görev *paralelliği* terimi, aynı anda çalışan bir veya daha fazla bağımsız görevi ifade eder. Görevler iki adet birincil avantaj sağlar:

- Sistem kaynaklarının daha verimli ve daha ölçeklenebilir kullanımı.

     Arka planda, <xref:System.Threading.ThreadPool>görevler, iş parçacığı sayısını belirleyen ve ayarlayan ve iş parçacığı sayısını en üst düzeye çıkarmak için yük dengelemesağlayan algoritmalarla geliştirilmiş olan , Bu, görevleri oldukça basit hale getirir ve hassas paralellik sağlamak için bunlardan çok sayıda oluşturabilirsiniz.

- Bir iş parçacığı veya iş öğesi ile mümkün olandan daha programlı denetim.

     Görevler ve bunların etrafına yerleşik çatı, bekleme, iptal, devamlılık, sağlam özel durum işleme, ayrıntılı durum, özel zamanlama ve daha fazlasını destekleyen zengin bir API kümesi sağlar.

Bu iki nedenle de TPL, .NET Framework'te çoklu iş parçalı, zaman uyumsuz ve paralel kod yazma için tercih edilen API'dir.

## <a name="creating-and-running-tasks-implicitly"></a>Görevleri örtülü olarak oluşturma ve çalıştırma

Yöntem, <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> aynı anda rasgele ifadeler herhangi bir sayı çalıştırmak için uygun bir yol sağlar. Her iş <xref:System.Action> öğesi için bir temsilci geçmenizi istiyorum. Lambda ifadelerini kullanmak, bu temsilcileri oluşturmanın en kolay yoludur. Lambda ifadesi adlandırılmış bir yöntemi çağırabilir veya satır içi kodu sağlayabilir. Aşağıdaki örnek, aynı <xref:System.Threading.Tasks.Parallel.Invoke%2A> anda çalışan iki görev oluşturan ve başlatan temel bir çağrıyı gösterir. İlk görev, adlı `DoSomeWork`bir yöntemi çağıran bir lambda ifadesi yle temsil edilir ve ikinci görev ise `DoSomeOtherWork`bir lambda ifadesi ile temsil edilir.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Sahne arkasında <xref:System.Threading.Tasks.Task> oluşturulan örnek sayısı, sağlanan <xref:System.Threading.Tasks.Parallel.Invoke%2A> temsilci sayısına eşit olmayabilir. TPL, özellikle çok sayıda temsilci bulunduğunda, çeşitli iyileştirmeler uygulayabilir.

Daha fazla bilgi için [bkz: Paralel İşlemleri Yürütmek için Parallel.Invoke'ı kullanın.](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)

Görev yürütme üzerinde daha fazla denetim veya görevden bir değer <xref:System.Threading.Tasks.Task> döndürmek için nesnelerle daha açık bir şekilde çalışmanız gerekir.

## <a name="creating-and-running-tasks-explicitly"></a>Görevleri açıkça oluşturma ve çalıştırma

Değer döndürmeyen bir görev <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıf tarafından temsil edilir. Bir değer döndüren bir görev, 'den <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task>devralınan sınıf tarafından temsil edilir. Görev nesnesi altyapı ayrıntılarını işler ve çağrıyı yapan iş parçacığının görevin ömrü boyunca erişebildiği yöntemler ve özellikler sağlar. Örneğin, bir görevin <xref:System.Threading.Tasks.Task.Status%2A> çalışmaya başlayıp başmadığını, tamamlanmak üzere çalışıp çalışmadığını, iptal edilip edilip edilemediğini veya bir özel durum atmadığını belirlemek için istediğiniz zaman bir görevin özelliğine erişebilirsiniz. Durum numaralandırma <xref:System.Threading.Tasks.TaskStatus> ile temsil edilir.

Görev oluşturduğunuzda, görevin yürüteceği kodu kapsülleyen bir kullanıcı temsilcisi verirsiniz. Temsilci adlandırılmış bir temsilci, adsız bir yöntem veya lambda ifadesi olarak ifade edilebilir. Lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi adlandırılmış bir yönteme yapılan çağrıyı içerebilir. Örneğin, görevin konsol modu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> uygulaması sona ermeden önce yürütmeyi tamamlamasını sağlamak için yönteme bir çağrı içerdiğini unutmayın.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Bir işlemde <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> görev oluşturmak ve başlatmak için yöntemleri de kullanabilirsiniz. Görevi yönetmek <xref:System.Threading.Tasks.Task.Run%2A> için, yöntemler, geçerli iş parçacığıyla ilişkili olan görev zamanlayıcısından bağımsız olarak varsayılan görev zamanlayıcısı'nı kullanır. Yöntem, <xref:System.Threading.Tasks.Task.Run%2A> görevin oluşturulması ve zamanlaması üzerinde daha fazla denetim gerekmediğinde görevleri oluşturma ve başlatma nın tercih edilen yoludur.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Bir işlemde <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> görev oluşturmak ve başlatmak için yöntemi de kullanabilirsiniz. Oluşturma ve zamanlamanın ayrılması gerekmiyorsa ve ek görev oluşturma seçeneklerine veya belirli bir zamanlayıcının kullanımına ihtiyaç duyduğunuzda veya aşağıdaki örnekte gösterildiği <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> gibi, özelliği nden alabileceğiniz göreve ek durum geçirmeniz gerektiğinde bu yöntemi kullanın.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task>ve <xref:System.Threading.Tasks.Task%601> her biri <xref:System.Threading.Tasks.Task.Factory%2A> varsayılan bir örneğini <xref:System.Threading.Tasks.TaskFactory>döndüren statik bir `Task.Factory.StartNew()`özellik ortaya çıkarır, böylece yöntemi . Ayrıca, aşağıdaki örnekte, görevler türde <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>olduğundan, her <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> biri hesaplama sonucunu içeren bir kamu malı vardır. Görevler zaman uyumsuz olarak çalışır ve herhangi bir sırada tamamlanabilir. Bilgisayar <xref:System.Threading.Tasks.Task%601.Result%2A> bitmeden önce özelliğe erişilirse, özellik değer kullanılabilir olana kadar çağrı iş parçacığının engellemesini engeller.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Daha fazla bilgi için [bkz: Görevden Değer Döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Temsilci oluşturmak için lambda ifadesini kullandığınızda, kaynak kodunuzun o noktasında görünür durumda olan tüm değişkenlere erişebilirsiniz. Ancak bazı durumlarda, çoğunlukla da döngülerde, bir lambda değişkeni beklenen şekilde yakalamaz. Her yinelemeden sonra oluşturduğu değeri değil, yalnızca son değeri yakalar. Aşağıdaki örnek, sorunu gösterir. Bir `CustomData` nesneyi anında ifade eden ve cismin tanımlayıcısı olarak döngü sayacını kullanan bir lambda ifadesine bir döngü sayacı geçer. Örnekteki çıktının gösterdiği gibi, her `CustomData` nesnenin özdeş bir tanımlayıcısı vardır.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Oluşturucusu aracılığıyla göreve durum nesnesi döndürerek her yinelemede değere erişebilirsiniz. Aşağıdaki örnek, `CustomData` sırayla lambda ifadesine geçirilen nesneyi oluştururken döngü sayacını kullanarak önceki örneği değiştirir.  Örnekteki çıktının gösterdiği gibi, her `CustomData` nesnenin artık, nesnenin anlık olarak bulunduğu anda döngü sayacının değerine dayalı benzersiz bir tanımlayıcısı vardır.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Bu durum görev temsilcisine bağımsız değişken olarak geçirilir ve <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özellik kullanılarak görev nesnesinden erişilebilir.  Aşağıdaki örnek, önceki örneğin bir çeşididir. Lambda <xref:System.Threading.Tasks.Task.AsyncState%2A> ifadesine aktarılan `CustomData` nesneler hakkında bilgi görüntülemek için özelliği kullanır.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Görev Kimliği

Her görev, bir uygulama etki alanında benzersiz olarak tanımlayan ve <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> özelliği kullanarak erişilebilen bir bir sonda kimliği alır. Kimlik, Visual Studio hata ayıklama **Paralel Yığınlar** ve **Görevler** pencerelerinde görev bilgilerini görüntülemek için yararlıdır. Kimlik gecikmeli olarak oluşturulur, yani istenene kadar oluşturulmaz; bu nedenle, program her çalıştırıldığında bir görevin farklı bir kimliği olabilir. Hata ayıklamada görev dislerini nasıl görüntüleyeceğimiz hakkında daha fazla bilgi için görevler [penceresini kullanma](/visualstudio/debugger/using-the-tasks-window) ve [Paralel Yığınlar Penceresini Kullanma](/visualstudio/debugger/using-the-parallel-stacks-window)bölümüne bakın.

## <a name="task-creation-options"></a>Görev oluşturma seçenekleri

Görev oluşturan çoğu API, <xref:System.Threading.Tasks.TaskCreationOptions> parametre kabul eden aşırı yüklemeler sağlar. Bu seçeneklerden birini belirleyerek görev zamanlayıcıya iş parçacığı havuzundaki görevi nasıl zamanlayacağını söyleyebilirsiniz. Aşağıdaki tabloda, çeşitli görev oluşturma seçenekleri listelenmektedir.

|<xref:System.Threading.Tasks.TaskCreationOptions>parametre değeri|Açıklama|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Hiç seçenek belirtilmemişse varsayılan değerdir. Zamanlayıcı, görevi zamanlamak için varsayılan buluşsal yöntemlerini kullanır.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Daha önce oluşturulmuş görevlerin daha önce çalıştırılabilmesi ve daha sonra oluşturulmuş görevlerin daha sonra çalıştırılabilmesi için görevin zamanlanması gerektiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Görevin uzun süren bir işlemi temsil ettiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Varsa, geçerli görevin eklenen bir alt görev olarak oluşturulması gerektiğini belirtir. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|İç görev seçeneği belirtirse, `AttachedToParent` bu görevin ekli bir alt görev olmayacağını belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Belirli bir görev gibi <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> içinde arama yöntemleri yle oluşturulan görevler için görev zamanlayıcısının, bu görevin çalıştığı zamanlayıcı yerine varsayılan zamanlayıcı olduğunu belirtir.|

Seçenekler bitwise **VEYA** işlemi kullanılarak birleştirilebilir. Aşağıdaki örnekte, seçeneği <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> seçeneği olan bir görev gösterilmektedir.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Görevler, iş parçacıkları ve kültür

Her iş parçacığı, sırasıyla ve özellikleri tarafından <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> tanımlanan <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> ilişkili bir kültür ve UI kültürü vardır. İş parçacığının kültürü biçimlendirme, ayrıştırma, sıralama ve dize karşılaştırması gibi işlemlerde kullanılır. Kaynak aramasında iş parçacığının UI kültürü kullanılır. Normalde, bir uygulama etki alanında tüm iş parçacıkları için bir uygulama <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> etki <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> alanı ve özelliklerini kullanarak varsayılan bir kültür belirtmediğiniz sürece, bir iş parçacığının varsayılan kültürü ve Kullanıcı Arabirimi kültürü sistem kültürü tarafından tanımlanır. Bir iş parçacığının kültürünü açıkça ayarlar ve yeni bir iş parçacığı başlatın, yeni iş parçacığı çağrı iş parçacığının kültürünü devralmaz; bunun yerine, kendi kültürü varsayılan sistem kültürüdür. .NET Framework 4.6'dan önce .NET Framework sürümlerini hedefleyen uygulamalar için görev tabanlı programlama modeli bu uygulamaya uyar.

> [!IMPORTANT]
> Arama iş parçacığının bir görev bağlamının bir parçası olarak kültürünün .NET Framework 4.6 altında *çalışan* uygulamalar için değil,.NET Framework 4.6'yı *hedefleyen* uygulamalar için geçerli olduğunu unutmayın. **Projenizi** Visual Studio'da oluştururken .NET Framework'ün belirli bir sürümünü, Yeni Proje iletişim kutusunun üst kısmındaki açılır listeden veya Visual <xref:System.Runtime.Versioning.TargetFrameworkAttribute> Studio dışında bu sürümü seçerek hedefleyebilirsiniz. .NET Framework 4.6'dan önce .NET Framework sürümlerini hedefleyen veya .NET Framework'ün belirli bir sürümünü hedeflemeyan uygulamalar için, görevin kültürü çalıştığı iş parçacığının kültürüne göre belirlenmeye devam eder.

.NET Framework 4.6'yı hedefleyen uygulamalardan başlayarak, görev iş parçacığı iş parçacığı iş parçacığı üzerinde eşit olarak çalışıyor olsa bile, arama iş parçacığının kültürü her görev tarafından devralır.

Aşağıdaki örnek basit bir örnek sağlar. .NET <xref:System.Runtime.Versioning.TargetFrameworkAttribute> Framework 4.6'yı hedeflemek için bu özelliği kullanır ve uygulamanın geçerli kültürünü Fransızca (Fransa) veya Fransızca (Fransa) zaten geçerli kültür, İngilizce (ABD) olarak değiştirir. Daha sonra, yeni `formatDelegate` kültürde para birimi değerleri olarak biçimlendirilmiş bazı sayıları döndüren adlandırılmış bir temsilci çağırır. Görev olarak temsilcinin eşzamanlı veya eşzamanlı olarak olsun, çağrı iş parçacığının kültürü eşzamanlı görev tarafından devralınan bu nedenle beklenen sonucu döndürür unutmayın.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Visual Studio kullanıyorsanız, özniteliği atlayabilir <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ve **yeni proje** iletişim kutusunda projeyi oluştururken hedef olarak .NET Framework 4.6'yı seçebilirsiniz.

.NET Framework 4.6'dan önce .NET Framework'ün hedef sürümlerinde uygulamaların davranışını yansıtan çıktı için özniteliği kaynak kodundan kaldırın. <xref:System.Runtime.Versioning.TargetFrameworkAttribute> Çıktı, çağrı iş parçacığının kültürünü değil, varsayılan sistem kültürünün biçimlendirme kurallarını yansıtır.

Eşzamanlı görevler ve kültür hakkında daha fazla bilgi için, konuyla ilgili "Kültür ve asynchronous görev tabanlı işlemler" bölümüne <xref:System.Globalization.CultureInfo> bakın.

## <a name="creating-task-continuations"></a>Görev devamı oluşturma

Ve <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> yöntemler, *öncül görev* tamamlandığında başlayacak bir görev belirtmenize izin verirken. Devam görevinin temsilcisi, öncül görevin durumunu inceleyebilmek ve <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğin değerini alarak, öncül çıktıyı devamı için giriş olarak kullanabilmek için öncül göreve bir başvuru dan geçirilir.

Aşağıdaki örnekte, `getData` görev <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> yönteme bir çağrı tarafından başlatılır. Görev `processData` tamamlandığında `getData` otomatik olarak başlatılır `displayData` ve `processData` bittiğinde başlatılır. `getData``getData` Görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği üzerinden görev için `processData` erişilebilir bir bir sonsayı dizisi üretir. Lambda `processData` ifadesinin dönüş türünden türü çıkarılan bir sonucu dizileyen ve döndüren <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> görev işler yönteme geçer. Görev `displayData` `processData` bittiğinde otomatik olarak yürütülür <xref:System.Tuple%603> ve `processData` lambda ifadesi tarafından döndürülen `displayData` nesne `processData` görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği aracılığıyla görev için erişilebilir. Görev `displayData` `processData` görevin sonucunu alır ve türü benzer bir şekilde çıkarılan ve <xref:System.Threading.Tasks.Task%601.Result%2A> özellikteki programa sunulan bir sonuç üretir.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Örnek <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> bir yöntem olduğundan, her öncül görev için bir <xref:System.Threading.Tasks.Task%601> nesneyi anında almak yerine yöntem çağrılarını birbirine zincirleyebilirsiniz. Aşağıdaki örnek, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yönteme çağrıları birbirine zincirlemesi dışında, işlevsel olarak önceki örnekle aynıdır. Yöntem çağrıları <xref:System.Threading.Tasks.Task%601> zinciri tarafından döndürülen nesnenin son devam görevi olduğunu unutmayın.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemler, birden çok görevden devam etmenizi sağlar.

Daha fazla bilgi için, [Devam Görevlerini Kullanarak Görevleri Zincirleme'ye](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)bakın.

## <a name="creating-detached-child-tasks"></a>Ayrılmış alt görevler oluşturma

Görevde çalışan kullanıcı kodu yeni bir görev oluşturduğunda ve <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği belirtmezse, yeni görev üst görevle özel bir şekilde eşitlenmez. Eşitlenmemiş görevbu tür bir ayrılmış *iç içe görev* veya *ayrılmış alt görev*denir. Aşağıdaki örnek, bağlantısı kesik bir tane alt görev oluşturan bir üst görevi gösterir.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Üst görevin, ayrılmış alt görevin tamamlanmasını beklemediğine dikkat edin.

## <a name="creating-child-tasks"></a>Alt görevler oluşturma

Görevde çalışan kullanıcı kodu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği olan bir görev oluşturduğunda, yeni görev üst *görevin eklenmiş alt görevi* olarak bilinir. Üst görev <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> örtülü olarak eklenen tüm alt görevlerin tamamlanmasını beklediğinden, yapılandırılmış görev paralelliğini ifade etme seçeneğini kullanabilirsiniz. Aşağıdaki örnek, on tane bağlı alt görev oluşturan bir üst görevi gösterir. Örnek, ana görevin <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tamamlanmasını beklemek için yöntemi çağırsa da, ekteki alt görevlerin tamamlanmasını açıkça beklemesi gerekmediğini unutmayın.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Bir üst görev, <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> diğer görevlerin üst göreve eklenmesini önlemek için seçeneği kullanabilir. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)

## <a name="waiting-for-tasks-to-finish"></a>Görevlerin tamamlanmasını bekleme

Ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türleri, bir görevin <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tamamlanmasını beklemenizi sağlayan yöntemlerin birkaç aşırı yüklemesini sağlar. Buna ek olarak, statik <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> ve yöntemlerin aşırı yükleri, bir dizi görevin tamamlanmasını beklemenize izin verebilirsiniz.

Genellikle, aşağıdaki nedenlerden biri için beklemeniz gerekir:

- Ana iş parçacığı, bir göreve göre hesaplanan nihai sonuca bağlıdır.

- Görevden oluşturulan özel durumları işlemeniz gerekir.

- Uygulama, tüm görevlerin yürütmesi tamamlanmadan sonlanabilir. Örneğin, konsol uygulamaları tüm senkron kodu `Main` (uygulama giriş noktası) yürütülür yürütülür yürütülür gibi sona erer.

Aşağıdaki örnek, özel durum işleme içermeyen temel düzeni gösterir.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Özel durum işlemeyi gösteren bir örnek [için](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)bkz.

Bazı aşırı yüklemeler bir zaman sonu belirtmenize <xref:System.Threading.CancellationToken> izin verenir ve diğerleri giriş parametresi olarak ek bir şey alır, böylece beklemenin kendisi programlı olarak veya kullanıcı girişine yanıt olarak iptal edilebilir.

Bir görevi beklerken, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> bu görevin tüm çocuklarını dolaylı olarak bu seçeneği kullanarak oluşturulursınız. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>görev zaten tamamlanmamışsa hemen döndürür. Görev tamamlandıktan sonra <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntem çağrılsa bile, görev tarafından yükseltilen tüm özel durumlar bir yöntemtarafından atılır.

## <a name="composing-tasks"></a>Görevleri oluşturma

Ve <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> sınıflar, ortak desenleri uygulamak ve C#, Visual Basic ve F# tarafından sağlanan eşzamanlı dil özelliklerini daha iyi kullanmanız için birden çok görev oluşturmanıza yardımcı olabilecek çeşitli yöntemler sağlar. Bu bölümde <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A> <xref:System.Threading.Tasks.Task.Delay%2A>, <xref:System.Threading.Tasks.Task.FromResult%2A> , ve yöntemleri açıklanır.

### <a name="taskwhenall"></a>Task.WhenAll

Yöntem <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> eş senkronize olarak birden <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> çok veya nesnenin tamamlanmasını bekler. Tek düzen olmayan görevler kümesini beklemenize olanak tanıyan aşırı yüklü sürümler sağlar. Örneğin, birden çok <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesnelerin tek bir yöntem çağrısından tamamlanmasını bekleyebilirsiniz.

### <a name="taskwhenany"></a>Task.WhenAny

Yöntem, <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birden çok <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesneden birinin tamamlanmasını eş senkronize olarak bekler. <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Yöntemde olduğu gibi, bu yöntem, tek düze olmayan görev kümelerini beklemenizi sağlayan aşırı yüklenmiş sürümler sağlar. Yöntem <xref:System.Threading.Tasks.Task.WhenAny%2A> özellikle aşağıdaki senaryolarda yararlıdır.

- Yedekli işlemler. Birçok şekilde gerçekleştirilen bir algoritma veya işlem düşünün. Önce bitiren <xref:System.Threading.Tasks.Task.WhenAny%2A> işlemi seçmek ve sonra kalan işlemleri iptal etmek için yöntemi kullanabilirsiniz.

- Dönüşümlü işlemler. Tüm bitirmek ve her işlem sona <xref:System.Threading.Tasks.Task.WhenAny%2A> ererken sonuçları işlemek için yöntemi kullanması gereken birden çok işlem başlatabilirsiniz. Bir işlem tamamlandıktan sonra bir veya daha fazla ek görev başlatabilirsiniz.

- Daraltılmış işlemler. Eşzamanlı işlem <xref:System.Threading.Tasks.Task.WhenAny%2A> sayısını sınırlayarak önceki senaryoyu genişletmek için yöntemi kullanabilirsiniz.

- Süresi dolan işlemler. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntem tarafından döndürülen bir görev gibi, bir veya daha fazla görev ve belirli bir süre <xref:System.Threading.Tasks.Task.Delay%2A> sonra sona eren bir görev arasında seçim yapmak için yöntemi kullanabilirsiniz. Yöntem <xref:System.Threading.Tasks.Task.Delay%2A> aşağıdaki bölümde açıklanmıştır.

### <a name="taskdelay"></a>Task.Delay

Yöntem, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> belirtilen <xref:System.Threading.Tasks.Task> süreden sonra biten bir nesne üretir. Bazen verileri yoklayan, zaman aşımlarını tanıtan, belirli bir süre boyunca kullanıcı girişinin işlenmesini erteleyen, vb. işlemler yapan döngüler oluşturmak için bu yöntemi kullanabilirsiniz.

### <a name="tasktfromresult"></a>Task(T).FromResult

<xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> Yöntemi kullanarak, önceden hesaplanmış <xref:System.Threading.Tasks.Task%601> bir sonucu tutan bir nesne oluşturabilirsiniz. Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesne döndüren bir eşyoklama işlemi gerçekleştirdiğinizde <xref:System.Threading.Tasks.Task%601> ve bu nesnenin sonucu zaten hesaplandığında yararlıdır. Önbellekte tutulan <xref:System.Threading.Tasks.Task.FromResult%2A> eşzamanlı indirme işlemlerinin sonuçlarını almak için kullanan bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)

## <a name="handling-exceptions-in-tasks"></a>Görevlerdeki özel durumları işleme

Bir görev bir veya daha fazla özel durum attığında, <xref:System.AggregateException> özel durumlar bir özel durumla sarılır. Bu özel durum, genellikle görevin tamamlanmasını bekleyen iş parçacığı veya <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğe erişen iş parçacığı olan görevle birleşen iş parçacığına geri yayılır. Bu davranış, tüm işlenmemiş özel durumların varsayılan olarak işlemi sonlandırması gerektiğini belirten .NET Framework ilkesini zorlamaya yarar. Arama kodu, bir `try` / `catch` blokta aşağıdakilerden birini kullanarak özel durumları işleyebilir:

- Yöntem <xref:System.Threading.Tasks.Task.Wait%2A>

- Yöntem <xref:System.Threading.Tasks.Task.WaitAll%2A>

- Yöntem <xref:System.Threading.Tasks.Task.WaitAny%2A>

- Özellik <xref:System.Threading.Tasks.Task%601.Result%2A>

Birleştirme iş parçacığı, görev çöp toplamadan önce <xref:System.Threading.Tasks.Task.Exception%2A> özelliğe erişerek özel durumları da işleyebilir. Bu özelliğe erişerek, işlenmeyen özel durumun, nesne hazırlandığında işlemi sonlandıran özel durum yayma davranışını tetiklemesini engellersiniz.

Özel durumlar ve görevler hakkında daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)

## <a name="canceling-tasks"></a>Görevleri iptal etme

Sınıf <xref:System.Threading.Tasks.Task> kooperatif iptalini destekler ve <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> <xref:System.Threading.CancellationToken?displayProperty=nameWithType> .NET Framework 4'te tanıtılan ve sınıflarla tam olarak entegre edilmiştir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Sınıftaki oluşturucuların çoğu bir <xref:System.Threading.CancellationToken> nesneyi giriş parametresi olarak alır. Ve <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> <xref:System.Threading.Tasks.Task.Run%2A> aşırı yüklerin çoğu <xref:System.Threading.CancellationToken> da bir parametre içerir.

Belirteci oluşturabilir ve sınıfı kullanarak daha sonraki bir zamanda <xref:System.Threading.CancellationTokenSource> iptal isteği verebilirsiniz. Belirteci bağımsız <xref:System.Threading.Tasks.Task> değişken olarak geçirin ve ayrıca iptal isteğine yanıt verme işini yapan kullanıcı temsilcinizde aynı belirteci başvurun.

Daha fazla bilgi için görev [iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve nasıl yapılacağını görmek [için: Bir Görevi ve Çocuklarını İptal Et.](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)

## <a name="the-taskfactory-class"></a>TaskFactory sınıfı

Sınıf <xref:System.Threading.Tasks.TaskFactory> oluşturma ve başlangıç görevleri ve devam görevleri için bazı ortak desenler kapsüllemek statik yöntemler sağlar.

- En yaygın <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>desen, bir görevi tek bir deyimde oluşturur ve başlatır.

- Birden çok öncülden devam görevleri oluşturduğunuzda, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntem veya yöntemi veya <xref:System.Threading.Tasks.Task%601> bunların eşdeğerlerini sınıfta kullanın. Daha fazla bilgi için, [Devam Görevlerini Kullanarak Görevleri Zincirleme'ye](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)bakın.

- `BeginX` Asynchronous Programlama Modeli ve `EndX` yöntemlerini bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örnekte <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> özetlemek için yöntemleri kullanın. Daha fazla bilgi için [TPL ve Traditional .NET Framework Asynchronous Programming'e](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)bakın.

Varsayılan <xref:System.Threading.Tasks.TaskFactory> sınıf veya <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> sınıf üzerinde statik bir özellik olarak erişilebilir. Ayrıca <xref:System.Threading.Tasks.TaskFactory> doğrudan bir instantiate ve bir , <xref:System.Threading.CancellationToken>bir <xref:System.Threading.Tasks.TaskCreationOptions> seçenek, <xref:System.Threading.Tasks.TaskContinuationOptions> bir seçenek <xref:System.Threading.Tasks.TaskScheduler>veya bir . Görev fabrikasını oluşturduğunuzda hangi seçenekler belirtilirse, numaralandırma kullanılarak <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.TaskCreationOptions> oluşturulmadığı sürece, oluşturduğu tüm görevlere uygulanır ve bu durumda görevseçenekleri görev fabrikasının seçeneklerini geçersiz kılar.

## <a name="tasks-without-delegates"></a>Temsilci olmayan görevler

Bazı durumlarda, kendi kullanıcı temsilciniz yerine harici bir bileşen tarafından gerçekleştirilen bazı eşzamanlı işlemi özetlemek için a <xref:System.Threading.Tasks.Task> kullanmak isteyebilirsiniz. İşlem Asynchronous Programming Model Begin/End desenini temel alıyorsa, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemleri kullanabilirsiniz. Bu durumda, nesneyi <xref:System.Threading.Tasks.TaskCompletionSource%601> işlemi bir göreve sarmak için kullanabilir ve bu nedenle programlanabilirliğin bazı avantajlarından <xref:System.Threading.Tasks.Task> (örneğin, özel durum yayılması ve devamı için destek) yararlanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Özel zamanlayıcılar

Çoğu uygulama veya kitaplık geliştiricisi görevin hangi işlemcide çalıştığını, çalışmasını diğer görevlerle nasıl <xref:System.Threading.ThreadPool?displayProperty=nameWithType>eşitlediği veya görevde nasıl zamanlandığını umursamaz. Bunlar yalnızca ana bilgisayarda olabildiğince verimli çalışmasını gerektirir. Zamanlama ayrıntıları üzerinde daha hassas bir denetim gerekiyorsa, Görev Paralel Kitaplığı varsayılan görev zamanlayıcı üzerinde bazı ayarları yapılandırmanıza ve hatta özel bir zamanlayıcı girmenize olanak tanır. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>İlgili veri yapıları

TPL'de, hem paralel hem de sıralı senaryolarda yararlı olan çeşitli, yeni genel türler vardır. Bunlar, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanında birkaç iş parçacığı güvenli, hızlı ve ölçeklenebilir toplama sınıfları ve <xref:System.Threading.Semaphore?displayProperty=nameWithType> örneğin <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>birkaç yeni eşitleme türleri içerir ve belirli iş yükleri türleri için öncüllerinden daha verimlidir. Örneğin.NET Framework 4'teki diğer yeni <xref:System.Threading.Barrier?displayProperty=nameWithType> <xref:System.Threading.SpinLock?displayProperty=nameWithType>türler ve önceki sürümlerde kullanılamayan işlevsellik sağlar. Daha fazla bilgi [için Paralel Programlama için Veri Yapıları'na](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)bakın.

## <a name="custom-task-types"></a>Özel görev türleri

Size miras <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> kalmamanızı veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Bunun yerine, ek verileri <xref:System.Threading.Tasks.Task.AsyncState%2A> ilişkilendirmek veya durumu bir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> veya nesneyle ilişkilendirmek için özelliği kullanmanızı öneririz. Sınıfların işlevselliğini <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> genişletmek için uzantı yöntemlerini de kullanabilirsiniz. Uzantı yöntemleri hakkında daha fazla bilgi için, [Uzantı Yöntemleri](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ve [Uzatma Yöntemleri'ne](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)bakın.

Bu mekanizmalar <xref:System.Threading.Tasks.Task> yalnızca <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneler <xref:System.Threading.Tasks.Task.Run%2A> <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>oluşturduğundan, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> özel görev türünüzden örnekler oluşturmak için özel görev türünüzden örnekler oluşturmak için bu tür lerden devralmanız veya kullanamazsınız. <xref:System.Threading.Tasks.Task>Ayrıca, bu mekanizmalar da yalnızca <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.TaskFactory> <xref:System.Threading.Tasks.TaskFactory%601> <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneler oluşturmak, çünkü , , , tarafından sağlanan görev devam mekanizmaları kullanamazsınız ve özel görev türü örnekleri oluşturmak için.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-|-|
|[Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Devamlılıkların nasıl çalıştığını açıklar.|
|[Eklenen ve Ayrılan Alt Görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Ekli ve ayrılmış alt görevler arasındaki farkı açıklar.|
|[Görev İptali](../../../docs/standard/parallel-programming/task-cancellation.md)|<xref:System.Threading.Tasks.Task> Nesnenin içine yerleşik iptal desteğini açıklar.|
|[Özel Durum Taşıma](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Eşzamanlı iş parçacıklarındaki özel durumların nasıl işlendiğini açıklar.|
|[Nasıl Kullanılır: Paralel İşlemleri Yürütmek için Parallel.Invoke'ı kullanın](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Nasıl kullanılacağını <xref:System.Threading.Tasks.Parallel.Invoke%2A>açıklar.|
|[Nasıl yapılır: Bir Görevden Değer Döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Değerlerin görevlerden nasıl döndürüleceğini açıklar.|
|[Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Görevlerin nasıl iptal edildiğini açıklar.|
|[Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Önbellekte <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> tutulan eşzamanlı indirme işlemlerinin sonuçlarını almak için yöntemin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|İkili ağacı geçirmek için görevlerin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Uzantı yönteminin <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> nasıl kullanılacağını gösterir.|
|[Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Veriler üzerinde <xref:System.Threading.Tasks.Parallel.For%2A> paralel <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngülerin nasıl kullanılacağını ve oluşturulmasını açıklar.|
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama için üst düzey düğüm.|

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [.NET Framework ile Paralel Programlama Örnekleri](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
