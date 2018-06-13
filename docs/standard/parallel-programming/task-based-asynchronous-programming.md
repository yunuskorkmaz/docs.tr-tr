---
title: Görev tabanlı zaman uyumsuz programlama
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
ms.openlocfilehash: e3dad3e33968b72d199b412c65f04a4079020f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592595"
---
# <a name="task-based-asynchronous-programming"></a>Görev tabanlı zaman uyumsuz programlama
Görev paralel kitaplığı (TPL) kavramını esas bir *görev*, zaman uyumsuz işlemi temsil eder. Bazı yönlerden bir görev bir iş parçacığı benzer veya <xref:System.Threading.ThreadPool> öğesi, ancak daha yüksek bir soyutlama düzeyinde çalışır. Terim *görev paralelliği* eşzamanlı olarak çalışan bir veya daha fazla bağımsız görevlere başvuruyor. Görevler iki adet birincil avantaj sağlar:  
  
-   Sistem kaynaklarının daha verimli ve daha ölçeklenebilir kullanımı.  
  
     Görevleri arka planda, sıraya alınan <xref:System.Threading.ThreadPool>, hangi geliştirilmiştir belirlemek ve iş parçacığı sayısını ayarlayın ve sağlayan verimliliği en üst düzeye çıkarmak için Yük Dengeleme algoritmaları ile. Bu, görevleri oldukça basit hale getirir ve hassas paralellik sağlamak için bunlardan çok sayıda oluşturabilirsiniz.  
  
-   Bir iş parçacığı veya iş öğesi ile mümkün olandan daha programlı denetim.  
  
     Görevler ve bunların etrafına yerleşik çatı, bekleme, iptal, devamlılık, sağlam özel durum işleme, ayrıntılı durum, özel zamanlama ve daha fazlasını destekleyen zengin bir API kümesi sağlar.  
  
 Bu iki nedenle de TPL, .NET Framework'te çoklu iş parçalı, zaman uyumsuz ve paralel kod yazma için tercih edilen API'dir.  
  
## <a name="creating-and-running-tasks-implicitly"></a>Oluşturma ve görevleri örtük olarak çalıştırma  
 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Yöntemi rasgele deyimleri herhangi bir sayıda eşzamanlı olarak çalıştırmak için kolay bir yol sağlar. Yalnızca geçirin bir <xref:System.Action> her bir iş öğesi için temsilci. Lambda ifadelerini kullanmak, bu temsilcileri oluşturmanın en kolay yoludur. Lambda ifadesi adlandırılmış bir yöntemi çağırabilir veya satır içi kodu sağlayabilir. Aşağıdaki örnek, temel bir gösterir <xref:System.Threading.Tasks.Parallel.Invoke%2A> oluşturur ve iki başlatan çağrısı eşzamanlı olarak çalışan görevler. İlk görev adında bir yöntemi çağırır bir lambda ifadesi tarafından temsil edilen `DoSomeWork`, ve ikinci görev adında bir yöntemi çağırır bir lambda ifadesi tarafından temsil edilen `DoSomeOtherWork`.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
 [!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]  
  
> [!NOTE]
>  Sayısı <xref:System.Threading.Tasks.Task> tarafından arka planda oluşturulan örnekleri <xref:System.Threading.Tasks.Parallel.Invoke%2A> mutlaka sağlanan temsilciler sayıya eşit değil. TPL, özellikle çok sayıda temsilci bulunduğunda, çeşitli iyileştirmeler uygulayabilir.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: paralel işlemleri yürütmek için Parallel.Invoke kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).  
  
 Görev Yürütme üzerinden veya görevden değer döndürme için daha fazla denetim çalışmak zorunda <xref:System.Threading.Tasks.Task> daha açıkça nesneleri.  
  
## <a name="creating-and-running-tasks-explicitly"></a>Oluşturma ve görevleri açıkça çalıştırma  
 Bir değer döndürmeyen bir görev tarafından temsil edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı. Bir değer döndüren bir görev tarafından temsil edilen <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> devraldığı sınıfı <xref:System.Threading.Tasks.Task>. Görev nesnesi altyapı ayrıntılarını işler ve çağrıyı yapan iş parçacığının görevin ömrü boyunca erişebildiği yöntemler ve özellikler sağlar. Örneğin, erişim <xref:System.Threading.Tasks.Task.Status%2A> özelliği çalıştıran, başlatıldığından olup olmadığını belirlemek için herhangi bir zamanda bir görevin tamamlanması çalışan, iptal edildi veya bir özel durum oluşturdu. Durumu tarafından temsil edilen bir <xref:System.Threading.Tasks.TaskStatus> numaralandırması.  
  
 Görev oluşturduğunuzda, görevin yürüteceği kodu kapsülleyen bir kullanıcı temsilcisi verirsiniz. Temsilci adlandırılmış bir temsilci, adsız bir yöntem veya lambda ifadesi olarak ifade edilebilir. Lambda ifadeleri, aşağıdaki örnekte gösterildiği gibi adlandırılmış bir yönteme yapılan çağrıyı içerebilir. Örnek bir çağrı içerdiğine dikkat edin <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> görev yürütme konsol modu uygulama sonlandırılmadan önce tamamlandığından emin olmak için yöntem.  
  
 [!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
 [!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]  
  
 Aynı zamanda <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> oluşturma ve tek bir işlemde bir görev başlatma yöntemleri. Görev yönetmek için <xref:System.Threading.Tasks.Task.Run%2A> yöntemleri bağımsız olarak hangi Görev Zamanlayıcı, geçerli iş parçacığı ile ilişkilendirilmiş varsayılan Görev Zamanlayıcı kullanın. <xref:System.Threading.Tasks.Task.Run%2A> Yöntemleridir oluşturma ve görevini zamanlama hakkında daha fazla denetime gerekmediğinde görevleri başlatmak ve oluşturmak için tercih edilen yol.  
  
 [!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
 [!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]  
  
 Aynı zamanda <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> oluşturma ve tek bir işlemde bir görev başlatma yöntemi. Oluşturma ve zamanlama zorunda değilsiniz ayrılması ve ek görev oluşturma seçenekleri veya belirli bir zamanlayıcı kullanımını gerektiren veya ek durum görev uygulamasına geçirmek gereken bu yöntemi kullanmak, <xref:System.Threading.Tasks.Task.AsyncState%2A> gösterildiği gibi özelliği Aşağıdaki örnek.  
  
 [!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/startnew1.cs#3)]
 [!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/startnew1.vb#3)]  
  
 <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> her kullanıma statik <xref:System.Threading.Tasks.Task.Factory%2A> varsayılan örneği döndüren özelliği <xref:System.Threading.Tasks.TaskFactory>, böylece yöntemi olarak çağırabilirsiniz `Task.Factory.StartNew()`. Ayrıca, aşağıdaki örnekte, görevleri türde olmadığından <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, sahip oldukları her bir ortak <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> hesaplamanın sonucu içeren özelliği. Görevler zaman uyumsuz olarak çalışır ve herhangi bir sırada tamamlanabilir. Varsa <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği hesaplama tamamlanmadan önce erişilen, özellik değeri kullanılabilir hale gelene kadar çağıran iş parçacığı engeller.  
  
 [!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
 [!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir görevden değer döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 Temsilci oluşturmak için lambda ifadesini kullandığınızda, kaynak kodunuzun o noktasında görünür durumda olan tüm değişkenlere erişebilirsiniz. Ancak bazı durumlarda, çoğunlukla da döngülerde, bir lambda değişkeni beklenen şekilde yakalamaz. Her yinelemeden sonra oluşturduğu değeri değil, yalnızca son değeri yakalar. Aşağıdaki örnek, sorunu gösterir. Bir döngü başlatır bir lambda ifadesi sayaç geçirmeden bir `CustomData` nesnesini ve nesne tanımlayıcı olarak döngü sayacı kullanır. Örnek çıktı olarak gösterilir, her `CustomData` nesnesi aynı tanımlayıcı sahiptir.  
  
 [!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
 [!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]  
  
 Oluşturucusu aracılığıyla göreve durum nesnesi döndürerek her yinelemede değere erişebilirsiniz. Aşağıdaki örnek oluştururken döngü sayacı kullanarak önceki örnek değiştirir `CustomData` hangi sırayla lambda ifadesi geçirilen nesne.  Örnek çıktı olarak gösterilir, her `CustomData` nesne artık sahip nesne örneği aynı anda döngü sayaç değeri temel alınarak benzersiz bir tanımlayıcı.  
  
 [!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
 [!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]  
  
 Bu durum görev temsilciye bağımsız değişken olarak geçirilir ve kullanarak görev nesneden erişilebileceğini <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği.  Aşağıdaki örnek, önceki örneğin bir çeşididir. Kullandığı <xref:System.Threading.Tasks.Task.AsyncState%2A> hakkında bilgileri görüntülemek için özellik `CustomData` nesneleri geçirilen lambda ifadesi.  
  
 [!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
 [!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]  
  
## <a name="task-id"></a>Görev Kimliği  
 Her görev, benzersiz bir uygulama etki alanında tanımlar ve kullanarak erişilebilir bir tamsayı kimliği alır <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> özelliği. Visual Studio Hata Ayıklayıcısı'ndaki görev bilgilerini görüntülemek için kullanışlı bir kimliğidir **Paralel Yığınlar** ve **görevleri** windows. Kimlik gecikmeli olarak oluşturulur, yani istenene kadar oluşturulmaz; bu nedenle, program her çalıştırıldığında bir görevin farklı bir kimliği olabilir. Hata ayıklayıcıda görev kimlikleri görüntüleme hakkında daha fazla bilgi için bkz: [görevleri penceresini kullanma](/visualstudio/debugger/using-the-tasks-window) ve [Paralel Yığınlar penceresini kullanarak](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
## <a name="task-creation-options"></a>Görev Oluşturma Seçenekleri  
 Görevler oluşturma çoğu API'leri kabul aşırı sağlayan bir <xref:System.Threading.Tasks.TaskCreationOptions> parametresi. Bu seçeneklerden birini belirleyerek görev zamanlayıcıya iş parçacığı havuzundaki görevi nasıl zamanlayacağını söyleyebilirsiniz. Aşağıdaki tabloda, çeşitli görev oluşturma seçenekleri listelenmektedir.  
  
|<xref:System.Threading.Tasks.TaskCreationOptions> Parametre değeri|Açıklama|  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|  
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Hiç seçenek belirtilmemişse varsayılan değerdir. Zamanlayıcı, görevi zamanlamak için varsayılan buluşsal yöntemlerini kullanır.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Daha önce oluşturulmuş görevlerin daha önce çalıştırılabilmesi ve daha sonra oluşturulmuş görevlerin daha sonra çalıştırılabilmesi için görevin zamanlanması gerektiğini belirtir.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Görevin uzun süren bir işlemi temsil ettiğini belirtir.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Varsa, geçerli görevin eklenen bir alt görev olarak oluşturulması gerektiğini belirtir. Daha fazla bilgi için bkz: [eklenen ve ayrılan alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|  
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Bir iç görev belirtiyorsa belirleyen `AttachedToParent` seçeneği, bu göreve bağlı alt görev olmaz.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Görev Zamanlayıcı görevleri için yöntemler gibi çağrılarak oluşturulan belirtir <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> içinden belirli bir görevi bu görevin çalıştığı Zamanlayıcı yerine varsayılan Zamanlayıcı değil.|  
  
 Bit tabanlı kullanarak seçenekleri birleştirilebilir **veya** işlemi. Aşağıdaki örnek, olan bir görev gösterir <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> seçeneği.  
  
 [!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
 [!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]  
  
## <a name="tasks-threads-and-culture"></a>Görevleri, iş parçacıkları ve kültür  
 Her iş parçacığı bir ilişkili kültür ve tarafından tanımlanan UI kültürü sahip <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri, sırasıyla. Bir iş parçacığının kültür gibi işlemleri biçimlendirme, ayrıştırma, sıralama ve dize karşılaştırması olarak kullanılır. Bir iş parçacığının UI kültürü kaynak aramada kullanılır. Normalde, tüm iş parçacıkları için varsayılan kültürü kullanarak bir uygulama etki alanında belirtmediğiniz sürece <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özellikleri, varsayılan kültür ve iş parçacığı UI kültürü sistem kültürü tarafından tanımlanır. Açıkça bir iş parçacığı kültürünü ayarlamak ve yeni bir iş parçacığı başlatın, yeni bir iş parçacığı çağıran iş parçacığı kültürünü devralmıyor; Bunun yerine, kendi varsayılan sistem kültürü kültürdür. Görev tabanlı programlama modeli öncesinde .NET Framework sürümlerini hedefleyen uygulamalar için [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] bu uygulama için uygun.  
  
> [!IMPORTANT]
>  Bir görevin bağlamı bir parçası olarak çağıran iş parçacığının kültür uygulamalar için geçerlidir Not, *hedef* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], olmayan uygulamalar, *altında çalışacağı* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Bu sürüm üst kısmında aşağı açılan listeden seçerek projenizi Visual Studio'da oluşturduğunuzda belirli bir .NET Framework sürümü hedefleyebilirsiniz **yeni proje** iletişim kutusu, veya Visual Studio'da kullanabilirsiniz dışında <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliği. Öncesinde .NET Framework sürümlerini hedefleyen uygulamalar için [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], veya, değil hedef belirli bir .NET Framework sürümünü, bir görevin kültür üzerinde çalışan iş parçacığı kültürünü tarafından belirlenmesi devam eder.  
  
 Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], görev zaman uyumsuz olarak bir iş parçacığı havuzu iş parçacığı üzerinde çalıştırıyor olsa bile çağıran iş parçacığının kültür her görev tarafından devralınır.  
  
 Aşağıdaki örnekte basit bir gösterim sağlar. Kullandığı <xref:System.Runtime.Versioning.TargetFrameworkAttribute> hedef özniteliğe [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve uygulamanın geçerli kültür ya da Fransızca (Fransa) değiştirir veya Fransızca (Fransa) İngilizce (ABD) geçerli kültürü ise. Ardından adlı bir temsilcisini çağırır `formatDelegate` yeni kültür para birimi değerleri olarak biçimlendirilmiş bazı numaraları döndürür. Unutmayın olup olmadığını temsilci çağıran iş parçacığı kültürünü zaman uyumsuz görev tarafından devralındığından bir görev olarak zaman uyumlu veya zaman uyumsuz olarak, bu beklenen sonucu döndürür.  
  
 [!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
 [!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]  
  
 Visual Studio kullanıyorsanız, atlayabilirsiniz <xref:System.Runtime.Versioning.TargetFrameworkAttribute> özniteliği ve bunun yerine projede oluşturduğunuzda, .NET Framework 4.6 hedefi olarak seçin **yeni proje** iletişim.  
  
 .NET Framework öncesinde hedef sürümleri uygulamalarınızın davranışını yansıtır çıktı için [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], kaldırma <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak kodunu özniteliğinden. Çıkış, varsayılan sistem kültürü olmayan çağıran iş parçacığı kültürünü biçimlendirme kuralları yansıtır.  
  
 Zaman uyumsuz görevler ve kültür hakkında daha fazla bilgi için "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümüne bakın <xref:System.Globalization.CultureInfo> konu.  
  
## <a name="creating-task-continuations"></a>Görev devamlılıklar oluşturma  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> yöntemleri başlatılmak üzere bir görev belirtmenize izin *öncül görev* tamamlanır. Devamlılık görevi temsilci öncül görev başvuru öncül görevin durumunu inceleyebilirsiniz ve olacak şekilde, değerini alarak geçirilen <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği kullanabilir nın çıkış giriş olarak devamlılık için.  
  
 Aşağıdaki örnekte, `getData` görev için bir çağrı tarafından başlatılır <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> yöntemi. `processData` Görev başlatıldığında otomatik olarak ne zaman `getData` bitinceye ve `displayData` başlatıldığında `processData` tamamlanır. `getData` erişilebilir bir tamsayı dizisi üretir `processData` aracılığıyla görev `getData` görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği. `processData` Görev bu diziyi işler ve geçirilen lambda ifadesi dönüş türü türü çıkarımı yapılan bir sonuç döndürür <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> yöntemi. `displayData` Görevi yürütür otomatik olarak zaman `processData` bitinceye ve <xref:System.Tuple%603> tarafından döndürülen nesne `processData` lambda ifadesi için erişilebilir durumda `displayData` aracılığıyla görev `processData` görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özellik. `displayData` Görev sonucunu alır `processData` görev ve benzer şekilde, türü çıkarımı yapılan ve hangi yapılan programa için kullanılabilir bir sonuç üretir <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği.  
  
 [!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
 [!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]  
  
 Çünkü <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> bir örnek yöntemidir başlatmasını yerine birlikte yöntem çağrılarını zincir bir <xref:System.Threading.Tasks.Task%601> öncül her görev için nesne. Çağrı zincir dışında aşağıdaki örnek önceki örneğe işlevsel olarak aynıdır <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Unutmayın <xref:System.Threading.Tasks.Task%601> yöntem çağrılarını zincir tarafından döndürülen son devamlılık görevi nesnesidir.  
  
 [!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
 [!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> Ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri birden çok görevlerden devam olanak tanır.  
  
 Daha fazla bilgi için bkz: [zincirleme görevleri devamlılık görevlerini kullanarak tarafından](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="creating-detached-child-tasks"></a>Ayrılan alt görevler oluşturma  
 Bir görevin çalıştığı kullanıcı kodu zaman yeni bir görev oluşturur ve belirtmediği <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği, yeni görev eşitlenmemiş üst görevle özel bir yolla. Bu Eşitlenen görev türü olarak adlandırılan bir *iç içe geçmiş görev ayrılmış* veya *ayrılmış alt görev*. Aşağıdaki örnek, bağlantısı kesik bir tane alt görev oluşturan bir üst görevi gösterir.  
  
 [!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
 [!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]  
  
 Üst görevin, ayrılmış alt görevin tamamlanmasını beklemediğine dikkat edin.  
  
## <a name="creating-child-tasks"></a>Alt görevler oluşturma  
 Bir görevin çalıştığı kullanıcı kodu görevle oluşturduğunda <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneği, yeni bir görev olarak bilinir bir *alt görev bağlı* üst görev. Kullanabileceğiniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> üst görevi tamamlamak tüm bağlı alt görevler için örtük olarak bekler çünkü express yapılandırılmış görev paralelliği için seçenek. Aşağıdaki örnek, on tane bağlı alt görev oluşturan bir üst görevi gösterir. Örnek çağırır rağmen unutmayın <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> tamamlamak, üst görevin tamamlanmasını bekle yöntemi açıkça ekli alt görevlerinin tamamlanması için beklenecek yok.  
  
 [!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
 [!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]  
  
 Üst göreve kullanabilirsiniz <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> diğer görevleri üst göreve eklenmesini önleme seçeneği. Daha fazla bilgi için bkz: [eklenen ve ayrılan alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="waiting-for-tasks-to-finish"></a>Görevin bitmesini bekleniyor  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türleri sağlayan birçok aşırı <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ve <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>--> `System.Threading.Tasks.Task.Wait` bir görevi tamamlamak için beklenecek sağlayan yöntemler. Ayrıca statik overloads <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemlerden herhangi birini veya tümünü görevleri tamamlamak için bir dizi için bekleyin olanak sağlar.  
  
 Genellikle, aşağıdaki nedenlerden biri için beklemeniz gerekir:  
  
-   Ana iş parçacığı, bir göreve göre hesaplanan nihai sonuca bağlıdır.  
  
-   Görevden oluşturulan özel durumları işlemeniz gerekir.  
  
-   Uygulama, tüm görevlerin yürütmesi tamamlanmadan sonlanabilir. Örneğin, konsol uygulamaları tüm zaman uyumlu kodda olan en kısa sürede sonlandıracak `Main` (uygulama giriş noktası) yürütüldü.  
  
 Aşağıdaki örnek, özel durum işleme içermeyen temel düzeni gösterir.  
  
 [!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
 [!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]  
  
 Özel durum işleme gösteren bir örnek için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 Bazı aşırı zaman aşımı belirtmenizi sağlar ve diğer ek bir ele <xref:System.Threading.CancellationToken> giriş parametresi olarak, böylece bekleme iptal edilebilir ya da program aracılığıyla veya yanıt kullanıcı olarak giriş.  
  
 Bir görevin tamamlanmasını bekleyin, örtük olarak kullanılarak oluşturulmuş olan tüm alt öğeleri bu görevin beklemeniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> hemen görev zaten tamamlanmış olan döndürür. Bir görev tarafından gerçekleştirilen tüm özel durumlar tarafından oluşturulan bir <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi, bile <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi görevi tamamlandı çağrıldı.  
  
## <a name="composing-tasks"></a>Görevler oluşturma  
 <xref:System.Threading.Tasks.Task> Ve <xref:System.Threading.Tasks.Task%601> sınıfları sağlar yardımcı olacak birkaç yöntem ortak desenler uygulamak ve daha iyi C#, Visual Basic ve F # tarafından sağlanan zaman uyumsuz dil özellikleri kullanmak için birden çok görev oluşturun. Bu bölümde açıklanmıştır <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, ve <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemleri.  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Yöntemi için birden çok zaman uyumsuz olarak bekler <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> tamamlamak için nesneleri. Tek düzen olmayan görevler kümesini beklemenize olanak tanıyan aşırı yüklü sürümler sağlar. Örneğin, çoklu bekleyebilirsiniz <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> bir yöntem çağrısının tamamlamak için nesneleri.  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Yöntemi zaman uyumsuz olarak bekler birden çok biri için <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> tamamlamak için nesneleri. Olarak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi, bu yöntem, görevleri Tekdüzen olmayan kümeleri için beklenecek etkinleştirmeniz aşırı yüklü sürümlerini sağlar. <xref:System.Threading.Tasks.Task.WhenAny%2A> Yöntemi aşağıdaki senaryolarda özellikle yararlıdır.  
  
-   Yedekli işlemler. Birçok şekilde gerçekleştirilen bir algoritma veya işlem düşünün. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> ilk bittikten işlemi seçin ve ardından kalan işlemleri iptal etmek için yöntem.  
  
-   Dönüşümlü işlemler. Gerekir ve tüm son kullanan birden çok operations başlatabilirsiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi her işlemi bitirdiğinde sonuçları işleyemedi. Bir işlem tamamlandıktan sonra bir veya daha fazla ek görev başlatabilirsiniz.  
  
-   Daraltılmış işlemler. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> eşzamanlı işlem sayısını sınırlayarak önceki senaryoda genişletmek için yöntem.  
  
-   Süresi dolan işlemler. Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi tarafından döndürülen bir görev gibi belirli bir süre sonra tamamlandıktan bir görev ile bir veya daha fazla görev arasındaki seçmek için <xref:System.Threading.Tasks.Task.Delay%2A> yöntemi. <xref:System.Threading.Tasks.Task.Delay%2A> Yöntemi aşağıdaki bölümde açıklanmıştır.  
  
### <a name="taskdelay"></a>Task.Delay  
 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Yöntemi oluşturan bir <xref:System.Threading.Tasks.Task> belirtilen süreden sonra bittikten nesnesi. Bazen verileri yoklayan, zaman aşımlarını tanıtan, belirli bir süre boyunca kullanıcı girişinin işlenmesini erteleyen, vb. işlemler yapan döngüler oluşturmak için bu yöntemi kullanabilirsiniz.  
  
### <a name="tasktfromresult"></a>Task(T).FromResult  
 Kullanarak <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> oluşturabileceğiniz yöntemi, bir <xref:System.Threading.Tasks.Task%601> önceden hesaplanan bir sonuç tutan nesne. Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanır. Kullanan bir örnek <xref:System.Threading.Tasks.Task.FromResult%2A> önbellekte tutulur zaman uyumsuz indirme işlemlerinin sonuçlarını almak için bkz: [nasıl yapılır: oluşturmak Pre-Computed görevleri](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).  
  
## <a name="handling-exceptions-in-tasks"></a>Görevler özel durumları işleme  
 Bir görev bir veya daha fazla özel durum oluşturduğunda, özel durumlar kaydırılır bir <xref:System.AggregateException> özel durum. Özel durum, genellikle görevin tamamlanmasını bekleyen iş parçacığı veya erişen iş parçacığı olan görevle katıldığı geri iş parçacığı yayılır <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği. Bu davranış, tüm işlenmemiş özel durumların varsayılan olarak işlemi sonlandırması gerektiğini belirten .NET Framework ilkesini zorlamaya yarar. Çağrıyı yapan kod aşağıdakilerden herhangi birini kullanarak özel durumlar işleyebilir bir `try` / `catch` engelle:  
  
-   <xref:System.Threading.Tasks.Task.Wait%2A> Yöntemi  
  
-   <xref:System.Threading.Tasks.Task.WaitAll%2A> Yöntemi  
  
-   <xref:System.Threading.Tasks.Task.WaitAny%2A> Yöntemi  
  
-   <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği  
  
 Katılma iş parçacığı da özel durumlar erişerek işleyebilir <xref:System.Threading.Tasks.Task.Exception%2A> görev çöpünün toplanma önce özelliği. Bu özelliğe erişerek, işlenmeyen özel durumun, nesne hazırlandığında işlemi sonlandıran özel durum yayma davranışını tetiklemesini engellersiniz.  
  
 Özel durumlar ve görevleri hakkında daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="canceling-tasks"></a>Görevleri iptal etme  
 `Task` Sınıfını işbirlikçi iptal destekler ve tam olarak tümleşiktir <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> .NET Framework 4'te tanıtılan sınıfları. Oluşturucularda çoğu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı Al bir <xref:System.Threading.CancellationToken> giriş parametresi olarak nesne. Çoğu <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> ve <xref:System.Threading.Tasks.Task.Run%2A> aşırı yüklemeleri de dahil bir <xref:System.Threading.CancellationToken> parametresi.  
  
 Belirteç oluşturmak ve kullanarak bazı daha sonra iptal isteğini vermek <xref:System.Threading.CancellationTokenSource> sınıfı. Belirtecin geçip <xref:System.Threading.Tasks.Task> , bir bağımsız değişken ve başvuru kullanıcı temsilciniz aynı belirteçte da, iptal isteğine yanıt iş yapar.  
  
 Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: bir görevi ve ait alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
## <a name="the-taskfactory-class"></a>TaskFactory sınıfı  
 <xref:System.Threading.Tasks.TaskFactory> Sınıfı oluşturma ve başlangıç görevleri ve devamlılık görevlerini bazı ortak desenler saklayan statik yöntemler sağlar.  
  
-   En yaygın deseni <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, oluşturur ve bir deyimde bir görev başlatır.  
  
-   Devamlılık görevlerini birden çok antecedents oluşturduğunuzda kullanmak <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> yöntemi veya <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemini veya kendi eşdeğerlerine <xref:System.Threading.Tasks.Task%601> sınıfı. Daha fazla bilgi için bkz: [zincirleme görevleri devamlılık görevlerini kullanarak tarafından](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
-   Zaman uyumsuz programlama modeli yalıtılacak `BeginX` ve `EndX` yöntemleri bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> Bu örnek, kullanma <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemleri. Daha fazla bilgi için bkz: [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Varsayılan <xref:System.Threading.Tasks.TaskFactory> bir statik özellik olarak erişilebildiğinden <xref:System.Threading.Tasks.Task> sınıfı veya <xref:System.Threading.Tasks.Task%601> sınıfı. Ayrıca örneği bir <xref:System.Threading.Tasks.TaskFactory> doğrudan ve dahil çeşitli seçenekleri belirtin bir <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> seçeneği, bir <xref:System.Threading.Tasks.TaskContinuationOptions> seçeneği veya bir <xref:System.Threading.Tasks.TaskScheduler>. Görev Fabrika oluşturduğunuzda seçenekleri belirtilen oluşturduğu, tüm görevler sürece uygulanacak <xref:System.Threading.Tasks.Task> kullanılarak oluşturulan <xref:System.Threading.Tasks.TaskCreationOptions> , numaralandırma görev Fabrika içeriğiyle görevin seçenekleri geçersiz kılma durumda.  
  
## <a name="tasks-without-delegates"></a>Temsilciler olmayan görevler  
 Bazı durumlarda kullanmak isteyebilirsiniz bir <xref:System.Threading.Tasks.Task> kendi kullanıcı temsilci yerine dış bileşen tarafından gerçekleştirilen bazı zaman uyumsuz işlem yalıtılacak. İşlem zaman uyumsuz programlama modeli başlangıç/bitiş deseni temel alınarak, kullanabileceğiniz <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemleri. Bu durumda değilse, kullanabileceğiniz <xref:System.Threading.Tasks.TaskCompletionSource%601> işlemi de bir görevi sarmalamadan ve böylece avantajlarından bazıları kazanmak için nesne <xref:System.Threading.Tasks.Task> programlamasına, örneğin, özel durum yayma ve devamlılıklar için desteği. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="custom-schedulers"></a>Özel zamanlayıcılar  
 Çoğu uygulama veya kitaplık Geliştirici görevin çalıştığı hangi işlemci, nasıl diğer görevlerle çalışmasını eşitler veya nasıl üzerinde planlandığını önemli <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Bunlar yalnızca ana bilgisayarda olabildiğince verimli çalışmasını gerektirir. Zamanlama ayrıntıları üzerinde daha hassas bir denetim gerekiyorsa, Görev Paralel Kitaplığı varsayılan görev zamanlayıcı üzerinde bazı ayarları yapılandırmanıza ve hatta özel bir zamanlayıcı girmenize olanak tanır. Daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskScheduler>.  
  
## <a name="related-data-structures"></a>İlgili veri yapıları  
 TPL'de, hem paralel hem de sıralı senaryolarda yararlı olan çeşitli, yeni genel türler vardır. Birkaç iş parçacığı, hızlı ve ölçeklendirilebilir koleksiyonu sınıflarda bunlar <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve birkaç yeni eşitleme türleri, örneğin, <xref:System.Threading.Semaphore?displayProperty=nameWithType> ve <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, belirli öncellerine daha verimli olduğu iş yükü türleri. .NET Framework 4, örneğin, yeni diğer türlerinde <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.SpinLock?displayProperty=nameWithType>, önceki sürümlerde kullanılabilir değildi işlevsellik sağlar. Daha fazla bilgi için bkz: [paralel programlama için veri yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).  
  
## <a name="custom-task-types"></a>Özel görev türleri  
 Gelen devralmaz öneririz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Bunun yerine, kullanmanızı öneririz <xref:System.Threading.Tasks.Task.AsyncState%2A> özelliği ile durum veya ek veri ilişkilendirmek için bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesi. İşlevlerini genişletmek için genişletme yöntemleri kullanabilirsiniz <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> sınıfları. Uzantı yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) ve [genişletme yöntemleri](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Öğesinden devralmalıdır varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, kullanamazsınız <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, veya <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, veya <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> türü Bu mekanizmaların oluşturduğundan, özel görev örneklerini oluşturmak için sınıfları yalnızca <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri. Ayrıca, tarafından sağlanan görev devamlılığı mekanizmaları kullanamazsınız <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, ve <xref:System.Threading.Tasks.TaskFactory%601> Bu mekanizmaların de yalnızca oluşturduğundan, özel görev türü örnekleri oluşturmak için <xref:System.Threading.Tasks.Task> ve  <xref:System.Threading.Tasks.Task%601> nesneleri.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-|-|  
|[Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Devamlılıkların nasıl çalıştığını açıklar.|  
|[Eklenen ve Ayrılan Alt Görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Ekli ve ayrılmış alt görevler arasındaki farkı açıklar.|  
|[Görev İptali](../../../docs/standard/parallel-programming/task-cancellation.md)|İçinde yerleşik iptal desteğini açıklar <xref:System.Threading.Tasks.Task> nesnesi.|  
|[Özel Durum İşleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Eşzamanlı iş parçacıklarındaki özel durumların nasıl işlendiğini açıklar.|  
|[Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|  
|[Nasıl yapılır: Bir Görevden Değer Döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Değerlerin görevlerden nasıl döndürüleceğini açıklar.|  
|[Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Görevlerin nasıl iptal edildiğini açıklar.|  
|[Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> önbellekte tutulur zaman uyumsuz indirme işlemlerinin sonuçlarını alma yöntemi.|  
|[Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|İkili ağacı geçirmek için görevlerin nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Nasıl kullanılacağı ortaya <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemi.|  
|[Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Parallel.For%2A> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> verileri üzerinde paralel döngüler oluşturmak için.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework paralel programlama için üst düzey düğüm.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [.NET Framework ile paralel programlama için örnek](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
