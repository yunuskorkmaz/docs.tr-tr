---
title: Görev tabanlı zaman uyumsuz programlama - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad13a5771adbfbd389feeccd3e8c833c4c2f778a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300629"
---
# <a name="task-based-asynchronous-programming"></a>Görev tabanlı zaman uyumsuz programlama

Görev paralel kitaplığı (TPL) kavramını temel alan bir *görev*, zaman uyumsuz işlemi temsil eder. Bazı yönlerden, bir görev bir iş parçacığı benzer veya <xref:System.Threading.ThreadPool> öğesi ancak daha yüksek düzeyde soyutlama çalışır. Terim *görev paralelliği* eşzamanlı olarak çalışan bir veya daha fazla bağımsız görevi ifade eder. Görevler iki adet birincil avantaj sağlar:

- Sistem kaynaklarının daha verimli ve daha ölçeklenebilir kullanımı.

     Görevleri arka planda, sıraya alınan <xref:System.Threading.ThreadPool>, geliştirilmiş belirlemek ve iş parçacığı sayısını ayarlayın ve aktarım hızını en üst düzeye çıkarmak için Yük Dengeleme sağlayan algoritmalarla. Bu, görevleri oldukça basit hale getirir ve hassas paralellik sağlamak için bunlardan çok sayıda oluşturabilirsiniz.

- Bir iş parçacığı veya iş öğesi ile mümkün olandan daha programlı denetim.

     Görevler ve bunların etrafına yerleşik çatı, bekleme, iptal, devamlılık, sağlam özel durum işleme, ayrıntılı durum, özel zamanlama ve daha fazlasını destekleyen zengin bir API kümesi sağlar.

Bu iki nedenle de TPL, .NET Framework'te çoklu iş parçalı, zaman uyumsuz ve paralel kod yazma için tercih edilen API'dir.

## <a name="creating-and-running-tasks-implicitly"></a>Oluşturma ve görevleri örtülü olarak çalıştırma

<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Yöntemi aynı anda istenen sayıda rasgele deyimin çalıştırılması için kolay bir yol sağlar. Yalnızca geçirin bir <xref:System.Action> her iş öğesi için temsilci. Lambda ifadelerini kullanmak, bu temsilcileri oluşturmanın en kolay yoludur. Lambda ifadesi adlandırılmış bir yöntemi çağırabilir veya satır içi kodu sağlayabilir. Aşağıdaki örnek, bir temel gösterir <xref:System.Threading.Tasks.Parallel.Invoke%2A> oluşturan ve başlatan iki çağrı, aynı anda çalışan görev. İlk görev adında bir yöntemi çağıran bir lambda ifadesi tarafından temsil edilen `DoSomeWork`, ikinci görev adında bir yöntemi çağıran bir lambda ifadesi tarafından temsil edilen ve `DoSomeOtherWork`.

> [!NOTE]
> TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Sayısını <xref:System.Threading.Tasks.Task> tarafından arka planda oluşturulan örnekleri <xref:System.Threading.Tasks.Parallel.Invoke%2A> mutlaka sağlanan temsilcilerin sayısına eşit değil. TPL, özellikle çok sayıda temsilci bulunduğunda, çeşitli iyileştirmeler uygulayabilir.

Daha fazla bilgi için [nasıl yapılır: Paralel işlemleri yürütmek için Parallel.Invoke kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Görev Yürütme üzerinde ya da görevden bir değer döndürmek için daha fazla denetim ile çalışmak zorunda <xref:System.Threading.Tasks.Task> daha açık nesneleri.

## <a name="creating-and-running-tasks-explicitly"></a>Oluşturma ve açıkça görevleri çalıştırma

Bir değeri döndürmeyen görev tarafından temsil edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı. Bir değer döndüren görev tarafından temsil edilen <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> öğesinden devralan sınıf <xref:System.Threading.Tasks.Task>. Görev nesnesi altyapı ayrıntılarını işler ve çağrıyı yapan iş parçacığının görevin ömrü boyunca erişebildiği yöntemler ve özellikler sağlar. Örneğin, erişebileceğiniz <xref:System.Threading.Tasks.Task.Status%2A> özelliği, çalışan, başlayıp başlamadığını belirlemek için dilediğiniz zaman bir görevin tamamlanması çalıştı, iptal edildi veya bir özel durum oluşturdu. Durum tarafından temsil edilen bir <xref:System.Threading.Tasks.TaskStatus> sabit listesi.

Görev oluşturduğunuzda, görevin yürüteceği kodu kapsülleyen bir kullanıcı temsilcisi verirsiniz. Temsilci adlandırılmış bir temsilci, adsız bir yöntem veya lambda ifadesi olarak ifade edilebilir. Lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi adlandırılmış bir yönteme yapılan çağrıyı içerebilir. Örnek bir çağrı içerdiğine dikkat edin <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yürütme konsol modu uygulama sonlandırılmadan önce görevin tamamlanmasını sağlamak için yöntemi.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Ayrıca <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> oluşturabilir ve tek bir işlemde bir görevi başlatmak için yöntem. Görevi yönetmek için <xref:System.Threading.Tasks.Task.Run%2A> yöntemleri bağımsız olarak hangi Görev Zamanlayıcısının geçerli iş parçasıyla ilişkilendirildiğine varsayılan Görev Zamanlayıcısını kullanır. <xref:System.Threading.Tasks.Task.Run%2A> Yöntemlerdir oluşturulması ve oluşturma ve zamanlama görevin üzerinde daha fazla denetim gerekmediğinde görevleri başlatmanın tercih edilen yoludur.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Ayrıca <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> oluşturun ve tek bir işlemde bir görevi başlatmak için yöntem. Oluşturma ve zamanlama zorunda değilsiniz ayrılması ve ek görev oluşturma seçenekleri veya belirli bir zamanlayıcı kullanımı gerektiğinde veya ek durumu göreve aracılığıyla alabilir geçirmek istediğinizde bu yöntemi kullanın, <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği, aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> her bir statik kullanıma <xref:System.Threading.Tasks.Task.Factory%2A> varsayılan örneğini döndüren özellik <xref:System.Threading.Tasks.TaskFactory>, böylece yöntemi olarak çağırabilirsiniz `Task.Factory.StartNew()`. Ayrıca, aşağıdaki örnekte, görev türü olduğundan <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, sahip oldukları her bir ortak <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> biri hesaplama sonucunu içeren özelliği. Görevler zaman uyumsuz olarak çalışır ve herhangi bir sırada tamamlanabilir. Varsa <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğine hesaplama tamamlanmadan önce erişilirse, değeri kullanılabilir duruma gelene kadar özellik arama iş parçacığını engeller.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Daha fazla bilgi için [nasıl yapılır: Bir görevden değer döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Temsilci oluşturmak için lambda ifadesini kullandığınızda, kaynak kodunuzun o noktasında görünür durumda olan tüm değişkenlere erişebilirsiniz. Ancak bazı durumlarda, çoğunlukla da döngülerde, bir lambda değişkeni beklenen şekilde yakalamaz. Her yinelemeden sonra oluşturduğu değeri değil, yalnızca son değeri yakalar. Aşağıdaki örnek, sorunu gösterir. Bu sayaç başlatan bir lambda ifadesine döngü geçirir bir `CustomData` nesnesini ve nesne tanımlayıcısı olarak döngü sayacını kullanır. Olarak örnekteki çıktının gösterdiği gibi her `CustomData` nesnesi özdeş tanımlayıcıya sahiptir.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Oluşturucusu aracılığıyla göreve durum nesnesi döndürerek her yinelemede değere erişebilirsiniz. Aşağıdaki örnek oluşturulurken döngü sayacını kullanarak önceki örneği değiştiren `CustomData` sırayla, lambda ifadesine geçirilen nesne.  Olarak örnekteki çıktının gösterdiği gibi her `CustomData` nesnesi, artık nesne zamanki döngü sayacı değerine göre belirlenmiş benzersiz tanımlayıcıya sahiptir.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Bu durum görev temsilcisine bir bağımsız değişken olarak geçirilir ve kullanarak görev nesnesinden erişilebileceğini <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği.  Aşağıdaki örnek, önceki örneğin bir çeşididir. Kullandığı <xref:System.Threading.Tasks.Task.AsyncState%2A> özelliği hakkında bilgi görüntülemek için `CustomData` nesneleri, lambda ifadesine geçirilen.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Görev Kimliği

Her görev, benzersiz bir uygulama etki alanında tanımlar ve kullanarak erişilebilir bir tamsayı kimliği alır <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> özelliği. Kimlik, görev bilgilerini Visual Studio hata ayıklayıcıda görüntülemek için yararlıdır **Paralel Yığınlar** ve **görevleri** windows. Kimlik gecikmeli olarak oluşturulur, yani istenene kadar oluşturulmaz; bu nedenle, program her çalıştırıldığında bir görevin farklı bir kimliği olabilir. Görev ID'lerini hata ayıklayıcıda görüntülenmesi hakkında daha fazla bilgi için bkz. [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window) ve [Paralel Yığınlar penceresini kullanma](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Görev oluşturma seçenekleri

Görevler oluşturan çoğu API'ler, kabul eden aşırı yüklemeler sağlar bir <xref:System.Threading.Tasks.TaskCreationOptions> parametresi. Bu seçeneklerden birini belirleyerek görev zamanlayıcıya iş parçacığı havuzundaki görevi nasıl zamanlayacağını söyleyebilirsiniz. Aşağıdaki tabloda, çeşitli görev oluşturma seçenekleri listelenmektedir.

|<xref:System.Threading.Tasks.TaskCreationOptions> Parametre değeri|Açıklama|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Hiç seçenek belirtilmemişse varsayılan değerdir. Zamanlayıcı, görevi zamanlamak için varsayılan buluşsal yöntemlerini kullanır.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Daha önce oluşturulmuş görevlerin daha önce çalıştırılabilmesi ve daha sonra oluşturulmuş görevlerin daha sonra çalıştırılabilmesi için görevin zamanlanması gerektiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Görevin uzun süren bir işlemi temsil ettiğini belirtir.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Varsa, geçerli görevin eklenen bir alt görev olarak oluşturulması gerektiğini belirtir. Daha fazla bilgi için [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Bir iç görev belirtiyorsa `AttachedToParent` seçeneği, bu görevin bir eklenmiş alt görev olmayacağını.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Görevler için Görev Zamanlayıcısı'nı gibi yöntemleri çağırarak oluşturulan belirtir <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> içinden belirli bir görevin bu görevin çalıştığı Zamanlayıcı yerine varsayılan Zamanlayıcı olduğunu.|

Seçenekler bit düzeyinde kullanarak birleştirilebilir **veya** işlemi. Aşağıdaki örnek, sahip bir görevi gösterir. <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> seçeneği.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Görevler, iş parçacıkları ve kültür

Her iş parçacığı bir ilişkili kültür ve tanımlanan kullanıcı Arabirimi kültürünü sahip <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri, sırasıyla. Bir iş parçacığının kültürünün biçimlendirme, ayrıştırma, sıralama ve dize karşılaştırma olarak bu işlemler kullanılır. Kaynak arama bir iş parçacığı UI kültürü kullanılır. Normalde, tüm iş parçacıkları için bir varsayılan kültürü kullanarak bir uygulama etki alanında belirtmediğiniz sürece <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özellikleri, varsayılan kültür ve iş parçacığı UI kültürü sistem kültür tarafından tanımlanır. Yeni iş parçacığı, açıkça bir iş parçacığı kültürü ayarlamanıza ve yeni bir iş parçacığı başlatın, çağıran iş parçacığı kültürünü devralmıyor; Bunun yerine, kendi varsayılan sistem kültürü kültürdür. .NET Framework 4.6 önce .NET Framework sürümlerini hedefleyen uygulamalar için görev-tabanlı programlama modeli için bu yöntem uyar.

> [!IMPORTANT]
> Görev bağlamı bir parçası olarak çağıran iş parçacığının kültürünün uygulamaları için geçerli bir Not, *hedef* uygulamaları .NET Framework 4.6, *altında çalıştırılması* .NET Framework 4.6. Bu sürümün en üstündeki aşağı açılan listeden seçerek projenizi Visual Studio'da oluşturduğunuzda belirli bir .NET Framework sürümünü hedefleyebilirsiniz **yeni proje** iletişim kutusu, kullandığınız Visual Studio dışındaki <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliği. Uygulamalar için .NET Framework 4.6 veya önce .NET Framework'ün sürümlerini hedefleyen .NET Framework'ün belirli bir sürümü hedeflemesini değil bir görevin kültür çalıştığı iş parçacığı kültürü tarafından belirlenecek devam eder.

Görev bir iş parçacığı havuzu iş parçacığında zaman uyumsuz olarak çalıştırıyor olsa bile uygulamalarla hedefleyen .NET Framework 4.6 başlayarak, her görev tarafından çağıran iş parçacığının kültürünün devralınır.

Aşağıdaki örnek, basit bir gösterim sağlar. Kullandığı <xref:System.Runtime.Versioning.TargetFrameworkAttribute> hedef .NET Framework 4.6 özniteliğini ve uygulamanın geçerli kültür ya da Fransızca (Fransa) değiştirir veya Fransızca (Fransa) geçerli kültürü İngilizce (Amerika Birleşik Devletleri) zaten varsa. Daha sonra adlandırılmış bir temsilci çağıran `formatDelegate` yeni kültüründeki para birimi değeri olarak biçimlendirilmiş bazı sayıları döndürür. Unutmayın olmadığını temsilci zaman uyumsuz görev tarafından çağıran iş parçacığı kültürünü devralındığından bir görev olarak zaman uyumlu veya zaman uyumsuz olarak beklenen sonucu döndürür.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Visual Studio kullanıyorsanız, atlayabilirsiniz <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliği ve bunun yerine .NET Framework 4.6 hedefi olarak seçin, projeyi oluşturduğunuzda **yeni proje** iletişim.

.NET Framework 4.6 önce .NET Framework'ün sürümlerini hedefleyen uygulamalar davranışını yansıtan çıktısını kaldırmak <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak kodundan özniteliği. Çıkış, varsayılan sistem kültürü, çağıran iş parçacığı kültürü biçimlendirme kurallarını yansıtır.

Zaman uyumsuz görevler ve kültür hakkında daha fazla bilgi için bkz: "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümünde <xref:System.Globalization.CultureInfo> konu.

## <a name="creating-task-continuations"></a>Görev devamlılıkları oluşturma

<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> yöntemleri başlayacak şekilde bir görevi belirtmenize olanak tanır *öncül görev* tamamlanır. Devamlılık görevinin temsilcisi öncül göreve bir başvuru geçirilir, böylece öncül görevin durumunu inceleyebilir ve değerini alarak <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği öncülün çıkışını giriş olarak devamlılık için kullanabilir.

Aşağıdaki örnekte, `getData` görev yapılan bir çağrıyla başlatılır <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> yöntemi. `processData` Görev başlatıldığında otomatik olarak zaman `getData` bitinceye ve `displayData` başlatıldığında `processData` tamamlanır. `getData` erişilebilir bir tamsayı dizisi üretir `processData` aracılığıyla görev `getData` görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği. `processData` Görevi o diziyi işler ve iletilen lambda ifadesinin dönüş türünden türü çıkarılan bir sonuç döndürür <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> yöntemi. `displayData` Görev yürütülmeden otomatik olarak zaman `processData` bitinceye ve <xref:System.Tuple%603> tarafından döndürülen nesne `processData` lambda ifadesi için erişilebilir `displayData` aracılığıyla görev `processData` görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özellik. `displayData` Görev sonucunu alır `processData` görev ve türü benzer bir şekilde çıkarılan ve program kullanılabilir yapılan bir sonuç üretir <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Çünkü <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> bir örnek yöntemi olduğundan birlikte başlatmak yerine yöntem çağrılarını zincirleyebilirsiniz bir <xref:System.Threading.Tasks.Task%601> her bir öncül görev nesnesi. Birlikte yapılan çağrıları zincir dışında aşağıdaki örnek önceki örneğe işlevsel olarak aynıdır <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Unutmayın <xref:System.Threading.Tasks.Task%601> yöntem çağrıları zinciri tarafından döndürülen son devam görevi nesnedir.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> Ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri birden fazla görevden devam etmenize olanak sağlar.

Daha fazla bilgi için [kullanarak devamlılık görevleri zinciri görevleriyle](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Ayrılmış alt görevler oluşturma

Ne zaman bir görevde çalışan kullanıcı kodu yeni görev oluşturduğunda ve belirttiğinde <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği, yeni görev üst görevle herhangi bir özel yol eşitlenmemiş. Görev eşzamanlı olmayan bu tür olarak adlandırılan bir *ayrılmış iç içe görev* veya *ayrılmış alt görev*. Aşağıdaki örnek, bağlantısı kesik bir tane alt görev oluşturan bir üst görevi gösterir.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Üst görevin, ayrılmış alt görevin tamamlanmasını beklemediğine dikkat edin.

## <a name="creating-child-tasks"></a>Alt görevler oluşturma

Görevde çalışan kullanıcı kodu ile bir görev oluşturduğunda <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği, yeni bir görev olarak bilinen bir *iliştirilmiş alt görevi* üst görevin. Kullanabileceğiniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> üst görev örtük olarak tamamlamak tüm eklenen alt görevlerin bitirmesini beklediğinden yapılandırılmış görev paralelliğini ifade etmek için seçenek. Aşağıdaki örnek, on tane bağlı alt görev oluşturan bir üst görevi gösterir. Örnek unutmayın <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tamamlamak ana görevin sonlanmasını beklemek için bunu tamamlamak eklenen alt görevlerin tamamlanmasını açıkça beklemek zorunda değildir.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Üst görev kullanabilirsiniz <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görevine eklenmesini diğer görevleri engellemek için seçeneği. Daha fazla bilgi için [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Görevlerin tamamlanmasını bekleme

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türlerine ilişkin çeşitli aşırı yükler sağlar <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bir görevin bitmesini beklemenize olanak tanıyan yöntemler. Ayrıca, statik aşırı <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemlerden herhangi birini veya tümünü bir dizi görev tamamlanması için bekleyin izin verir.

Genellikle, aşağıdaki nedenlerden biri için beklemeniz gerekir:

- Ana iş parçacığı, bir göreve göre hesaplanan nihai sonuca bağlıdır.

- Görevden oluşturulan özel durumları işlemeniz gerekir.

- Uygulama, tüm görevlerin yürütmesi tamamlanmadan sonlanabilir. Örneğin, konsol uygulamaları içindeki tüm eş zamanlı kod olan en kısa sürede sona erer `Main` (uygulama giriş noktası) yürütüldüğünde sonlanacaktır.

Aşağıdaki örnek, özel durum işleme içermeyen temel düzeni gösterir.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Özel durum yönetimini gösteren bir örnek için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Bazı aşırı yüklemeler zaman aşımı belirtmenizi sağlar ve diğer ek ele <xref:System.Threading.CancellationToken> giriş parametresi olarak, böylece beklemenin kendisi iptal edilebilir ya da programlı olarak veya kullanıcının girişine yanıt.

Bir görevi beklerken, örtülü olarak söz konusu görevin kullanılarak oluşturulmuş tüm alt beklemeniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> görev zaten tamamlandıysa, hemen döner. Bir görev nedeniyle ortaya çıkan özel durumlar tarafından oluşturulan bir <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bile <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi görev tamamlandıktan sonra çağrıldı.

## <a name="composing-tasks"></a>Görevleri oluşturma

<xref:System.Threading.Tasks.Task> Ve <xref:System.Threading.Tasks.Task%601> sınıfları, ortak desenler uygulamak ve tarafından sağlanan zaman uyumsuz dil özelliklerini daha iyi kullanmak için birden çok görev oluşturmanıza yardımcı olabilen çeşitli yöntemler sağlar C#, Visual Basic ve F#. Bu bölümde açıklanmaktadır <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, ve <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemleri.

### <a name="taskwhenall"></a>Task.WhenAll

<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Yöntemi, birden çok zaman uyumsuz olarak bekler <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> tamamlanmasını. Tek düzen olmayan görevler kümesini beklemenize olanak tanıyan aşırı yüklü sürümler sağlar. Örneğin, birden çok bekleyebilir <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> bir yöntem çağrısından tamamlamak için nesneleri.

### <a name="taskwhenany"></a>Task.WhenAny

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Yöntemi zaman uyumsuz olarak bekler biri birden çok <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> tamamlanmasını. Olarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi, bu yöntem, tek düzen olmayan görevler kümesini beklemenize olanak tanıyan aşırı yüklü sürümler sağlar. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntemi aşağıdaki senaryolarda özellikle yararlıdır.

- Yedekli işlemler. Birçok şekilde gerçekleştirilen bir algoritma veya işlem düşünün. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> önce sona eren işlemi seçmek, sonra da kalan işlemleri iptal etmek için yöntemi.

- Dönüşümlü işlemler. Tümünün bitmesi gerekir ve kullanan birden çok işlem başlatabilir <xref:System.Threading.Tasks.Task.WhenAny%2A> her işlem bittiğinde sonuçları işlemek için yöntemi. Bir işlem tamamlandıktan sonra bir veya daha fazla ek görev başlatabilirsiniz.

- Daraltılmış işlemler. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> eşzamanlı işlemlerin sayısını sınırlayarak önceki senaryoyu genişletmek için yöntemi.

- Süresi dolan işlemler. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> arasında bir veya daha fazla görevleri ve tarafından döndürülen görev gibi belirli bir süre sonunda biten görevi seçmek için <xref:System.Threading.Tasks.Task.Delay%2A> yöntemi. <xref:System.Threading.Tasks.Task.Delay%2A> Yöntemi aşağıdaki bölümde açıklanmıştır.

### <a name="taskdelay"></a>Task.Delay

<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Yöntemi oluşturan bir <xref:System.Threading.Tasks.Task> belirtilen zamandan sonra biten bir nesne. Bazen verileri yoklayan, zaman aşımlarını tanıtan, belirli bir süre boyunca kullanıcı girişinin işlenmesini erteleyen, vb. işlemler yapan döngüler oluşturmak için bu yöntemi kullanabilirsiniz.

### <a name="tasktfromresult"></a>Task(T).FromResult

Kullanarak <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> yöntemi oluşturmak için kullanabileceğiniz bir <xref:System.Threading.Tasks.Task%601> önceden hesaplanmış sonucu tutan nesne. Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanmışsa. Kullanan bir örnek için <xref:System.Threading.Tasks.Task.FromResult%2A> zaman uyumsuz indirme işlemlerinin bir ön bellekte tutulan sonuçlarını almak için bkz: [nasıl yapılır: Önceden hesaplanan görevler oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Görevlerde özel durumları işleme

Bir görev bir veya daha fazla özel durum oluşturduğunda, özel durumlar olarak sarmalanır ve bir <xref:System.AggregateException> özel durum. Özel durum, genellikle görevin sonlanmasını bekleyen iş parçacığı veya erişen iş parçacığı olan görev ile Birleşen iş parçacığına geri yayılır <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği. Bu davranış, tüm işlenmemiş özel durumların varsayılan olarak işlemi sonlandırması gerektiğini belirten .NET Framework ilkesini zorlamaya yarar. Çağıran kod, aşağıdakilerden herhangi birini kullanarak özel durumları işleyebilir bir `try` / `catch` engelle:

- <xref:System.Threading.Tasks.Task.Wait%2A> Yöntemi

- <xref:System.Threading.Tasks.Task.WaitAll%2A> Yöntemi

- <xref:System.Threading.Tasks.Task.WaitAny%2A> Yöntemi

- <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği

Katılan iş parçacığına özel durumları erişerek işleyebilir <xref:System.Threading.Tasks.Task.Exception%2A> görev çöp olarak toplanmadan önce özelliği. Bu özelliğe erişerek, işlenmeyen özel durumun, nesne hazırlandığında işlemi sonlandıran özel durum yayma davranışını tetiklemesini engellersiniz.

Özel durumlar ve görevler hakkında daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Görevleri iptal etme

<xref:System.Threading.Tasks.Task> Sınıfı, ortak iptali destekler ve tam olarak tümleşiktir <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> .NET Framework 4'te tanıtılan sınıfları. Oluşturucuların birçoğu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfındaki oluşturucuların bir <xref:System.Threading.CancellationToken> giriş parametresi olarak nesnesi. Çoğu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> ve <xref:System.Threading.Tasks.Task.Run%2A> aşırı yüklemeleri de dahil bir <xref:System.Threading.CancellationToken> parametresi.

Belirteci oluşturmak ve kullanarak bazı daha sonraki bir zamanda iptal isteğini sorun <xref:System.Threading.CancellationTokenSource> sınıfı. İçin belirtecin geçip <xref:System.Threading.Tasks.Task> olan bir bağımsız değişken ve kullanıcı temsilcinizde aynı belirtece başvuru da, bir iptal isteğine yanıt verme işini yapar.

Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: Bir görevi ve alt öğelerini iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>TaskFactory sınıfı

<xref:System.Threading.Tasks.TaskFactory> Sınıfı, görevler ve devamlılık görevleri oluşturmak ve başlatmak için bazı ortak desenleri saklayan statik yöntemler sağlar.

- En yaygın desen <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, oluşturur ve tek bir deyimde bir görev başlatır.

- Birden çok öncülden devamlılık görevleri oluştururken kullanmak <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> yöntemi veya <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemi veya bunların eşdeğerlerini <xref:System.Threading.Tasks.Task%601> sınıfı. Daha fazla bilgi için [kullanarak devamlılık görevleri zinciri görevleriyle](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Zaman uyumsuz programlama modeli `BeginX` ve `EndX` yöntemleri bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> kullanın, örnek <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemleri. Daha fazla bilgi için [TPL ve geleneksel .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Varsayılan <xref:System.Threading.Tasks.TaskFactory> statik bir özellik olarak erişilebilir <xref:System.Threading.Tasks.Task> sınıfı veya <xref:System.Threading.Tasks.Task%601> sınıfı. Başlatabilir bir <xref:System.Threading.Tasks.TaskFactory> doğrudan ve içeren çeşitli seçenekleri belirtebilirsiniz bir <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> seçeneği, bir <xref:System.Threading.Tasks.TaskContinuationOptions> seçeneği veya bir <xref:System.Threading.Tasks.TaskScheduler>. Görev fabrikasını oluşturduğunuzda belirtilen seçenekler onu oluşturan tüm görevlere uygulanır <xref:System.Threading.Tasks.Task> kullanılarak oluşturulan <xref:System.Threading.Tasks.TaskCreationOptions> sabit listesi, bu görev fabrikasını görevin seçeneklerini geçersiz kıl durumda.

## <a name="tasks-without-delegates"></a>Temsilcisiz görevler

Bazı durumlarda kullanmak isteyebilirsiniz bir <xref:System.Threading.Tasks.Task> kendi kullanıcı Temsilcinizin yerine harici bir bileşen tarafından gerçekleştirilen bazı zaman uyumsuz işlemleri kapsülleyebilirsiniz. İşlem üzerinde zaman uyumsuz programlama modeli başlangıç/bitiş desenini esas alıyorsa kullanabileceğiniz <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemleri. Durum bu değilse, kullanabileceğiniz <xref:System.Threading.Tasks.TaskCompletionSource%601> nesnesini bir görevde işlemi ve dolayısıyla bazı avantajları elde etmeye yönelik <xref:System.Threading.Tasks.Task> programlama, örneğin, özel durum doldurma ve devamlılık desteği. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Özel planlayıcılar

Çoğu uygulama veya kitaplık geliştiricisi hangi işlemci üzerinde çalıştığını görev, nasıl çalışmasını diğer görevlerle eşitlenir veya bunun üzerinde nasıl planlandığını önemsemez <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Bunlar yalnızca ana bilgisayarda olabildiğince verimli çalışmasını gerektirir. Zamanlama ayrıntıları üzerinde daha hassas bir denetim gerekiyorsa, Görev Paralel Kitaplığı varsayılan görev zamanlayıcı üzerinde bazı ayarları yapılandırmanıza ve hatta özel bir zamanlayıcı girmenize olanak tanır. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>İlgili veri yapıları

TPL'de, hem paralel hem de sıralı senaryolarda yararlı olan çeşitli, yeni genel türler vardır. Birden çok iş parçacığı açısından güvenli, hızlı ve ölçeklenebilir koleksiyon sınıflarını bunlar <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve çeşitli yeni eşitleme türlerini, örneğin, <xref:System.Threading.Semaphore?displayProperty=nameWithType> ve <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, öncekilere göre belirli daha etkili olan iş yükü türleri. .NET Framework 4, örneğin,'deki diğer yeni türler <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.SpinLock?displayProperty=nameWithType>, daha önceki sürümlerde kullanılamayan işlevselliği sağlar. Daha fazla bilgi için [paralel programlama için veri yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Özel görev türleri

Seçeneğinden devralmamanızı öneririz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Bunun yerine kullanmanızı öneriyoruz <xref:System.Threading.Tasks.Task.AsyncState%2A> ilişkilendirmek ek verileri veya durumu özelliği bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesne. İşlevlerini genişletmek için genişletme yöntemleri de kullanabilirsiniz <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> sınıfları. Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [genişletme yöntemleri](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) ve [genişletme yöntemleri](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Devralmanız gerekirse <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, kullanamazsınız <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, veya <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, veya <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> sınıfları kullanarak özel görev örnekleri oluşturmak için çünkü bu mekanizmalar oluşturma yazın yalnızca <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri. Ayrıca, tarafından sağlanan görev sürekliliği mekanizmasını kullanamazsınız <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, ve <xref:System.Threading.Tasks.TaskFactory%601> çünkü bu mekanizmalar yalnızca de oluşturma özel görev türünüzün örneğini oluşturmak için <xref:System.Threading.Tasks.Task> ve  <xref:System.Threading.Tasks.Task%601> nesneleri.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-|-|
|[Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Devamlılıkların nasıl çalıştığını açıklar.|
|[Eklenen ve Ayrılan Alt Görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Ekli ve ayrılmış alt görevler arasındaki farkı açıklar.|
|[Görev İptali](../../../docs/standard/parallel-programming/task-cancellation.md)|Yerleşik olan iptal desteğini açıklar <xref:System.Threading.Tasks.Task> nesne.|
|[Özel Durum İşleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Eşzamanlı iş parçacıklarındaki özel durumların nasıl işlendiğini açıklar.|
|[Nasıl yapılır: Paralel işlemleri yürütmek için Parallel.Invoke kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Nasıl yapılır: Bir görevden değer döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Değerlerin görevlerden nasıl döndürüleceğini açıklar.|
|[Nasıl yapılır: Bir görevi ve alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Görevlerin nasıl iptal edildiğini açıklar.|
|[Nasıl yapılır: Önceden hesaplanan görevler oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> zaman uyumsuz indirme işlemlerinin bir ön bellekte tutulan sonuçlarını almak için yöntemi.|
|[Nasıl yapılır: Paralel Görevler içeren bir ikili ağacı gezme](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|İkili ağacı geçirmek için görevlerin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: İç içe geçmiş bir görevi sarmalamadan çıkarma](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Nasıl kullanılacağını gösteren <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemi.|
|[Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Parallel.For%2A> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> veriler üzerinde paralel döngüler oluşturmak için.|
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama için üst düzey düğüm.|

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [.NET Framework ile paralel programlama için örnekler](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
