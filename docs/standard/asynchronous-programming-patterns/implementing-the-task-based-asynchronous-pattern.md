---
title: "Görev Tabanlı Zaman Uyumsuz Deseni Uygulama"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e61b0c94b1512509008d67017389fa11f938999
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
Görev tabanlı zaman uyumsuz desen (TAP) üç yolla uygulayabilirsiniz: C# ve Visual Basic derleyicileri Visual Studio kullanarak el ile veya derleyici ve el ile yöntemlerinin bir birleşimini yoluyla. Aşağıdaki bölümlerde her yöntemin ayrıntılı açıklanmaktadır. İşlem bağlama ve g/Ç-bağlı zaman uyumsuz işlemleri uygulamak için DOKUNUN desen kullanabilirsiniz. [İş yükleri](#workloads) bölüm işlemi her türünü açıklar.

## <a name="generating-tap-methods"></a>DOKUNUN yöntemleri oluşturma

### <a name="using-the-compilers"></a>Derleyicileri kullanma
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ile öznitelikli herhangi bir yöntemini `async` anahtar sözcüğü (`Async` Visual Basic'te) zaman uyumsuz bir yöntem ve C# ve Visual Basic derleyicileri gerçekleştirmek uygulamak için gerekli dönüşümleri olarak kabul edilir DOKUNUN kullanarak zaman uyumsuz olarak yöntemi. Zaman uyumsuz bir yöntem ya da döndürmelidir bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi. İkincisi, işlevinin gövdesini döndürmelidir bir `TResult`, ve bu sonucu elde edilen görev nesnesi sunulacağını derleyici sağlar. Benzer şekilde, yöntem gövdesi içinde işlenmeyen Git tüm özel durumlar çıktı görevi sıralanmış ve sonuçta elde edilen görevin sonunda neden <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumu. Özel durum olduğunda bir <xref:System.OperationCanceledException> (veya türetilmiş türü) gider işlenmemiş, sonuçta elde edilen görev; bu durumda biten <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.

### <a name="generating-tap-methods-manually"></a>DOKUNUN yöntemleri el ile oluşturma
Uygulama üzerinde daha iyi denetim için el ile DOKUNUN düzeni uygulayabilir. Gelen kullanıma sunulan genel yüzey alanını derleyici dayanan <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanı ve türlerini destekleyen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı. DOKUNUN kendiniz uygulamak için oluşturduğunuz bir <xref:System.Threading.Tasks.TaskCompletionSource%601> nesne, zaman uyumsuz işlemi gerçekleştirmek ve tamamlandığında, çağrısı <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, veya <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> yöntemini veya `Try` aşağıdaki yöntemlerden birini sürümü. El ile bir DOKUNUN yöntemi uyguladığınızda gösterilen zaman uyumsuz işlemi tamamlandıktan sonra sonuç görevi tamamlamanız gerekir. Örneğin:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Karma yaklaşımı
 DOKUNUN düzeni el ile uygulama ancak derleyici uygulaması için çekirdek mantığını temsilci seçmek için yararlı. Örneğin, böylece özel durumlar yöntemin doğrudan çağıran yerine aracılığıyla yararlanılmasını kaçış derleyicinin ürettiği zaman uyumsuz yöntem dışında bağımsız değişkenleri doğrulamak istediğinizde karma yaklaşımı kullanmak isteyebilirsiniz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesnesi:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Hızlı yolu iyileştirme uygulama ve önbelleğe alınan görev döndürmek istediğinizde bu tür temsilci yararlı olduğu başka bir durumdur.

## <a name="workloads"></a>İş yükleri
İşlem bağlama ve g/Ç-bağlı zaman uyumsuz işlemleri DOKUNUN yöntemleri olarak uygulayabilir. Ancak, bunlar DOKUNUN yöntemleri kitaplıktan genel olarak kullanıma sunulan zaman (bunlar da hesaplama içerebilir, ancak tamamen hesaplama olmamalıdır) g/Ç işlemleri ile ilgili yalnızca iş yükleri için sağlanmalıdır. Bir yöntem tamamen işlem bağlı ise, yalnızca zaman uyumlu bir uygulama açılmamalıdır. İçereceği tükettiği kod bir o zaman uyumlu yöntemi çağrısını başka bir iş parçacığı çalışmaya boşaltma veya paralellik elde etmek için bir görev olarak kaydırmak seçebilirsiniz. Ve bir yöntem GÇ bağlı ise, onu yalnızca zaman uyumsuz bir uygulama açılmamalıdır.

### <a name="compute-bound-tasks"></a>İşlem bağlı görevler
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Sınıfı ideal olarak uygun hesaplama yoğunluklu işlemlerdir temsil etmek için. Varsayılan olarak, bu özel destek içinde yararlanır <xref:System.Threading.ThreadPool> verimli yürütme sağlamak için sınıf de önemli denetim zaman, nerede ve nasıl sağlar ve zaman uyumsuz hesapları yürütün.

İşlem bağlama görevleri aşağıdaki yollarla oluşturabilirsiniz:

- .NET Framework 4'te kullanmak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bir temsilci kabul yöntemi (genellikle bir <xref:System.Action%601> veya <xref:System.Func%601>) zaman uyumsuz olarak yürütülecek. Sağlarsanız bir <xref:System.Action%601> temsilci, yöntem bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz yürütme bu temsilciyi işlemi temsil eden nesne. Sağlarsanız bir <xref:System.Func%601> temsilci, yöntem bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi. Overloads <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi bir iptal belirteci kabul (<xref:System.Threading.CancellationToken>), görev oluşturma seçenekleri (<xref:System.Threading.Tasks.TaskCreationOptions>) ve bir Görev Zamanlayıcısı'nı (<xref:System.Threading.Tasks.TaskScheduler>), tüm zamanlama ve yürütme görevinin üzerinde ayrıntılı denetim sağlar. Geçerli Görev Zamanlayıcısı'nı hedefleyen bir Fabrika örnek bir statik özellik olarak kullanılabilir (<xref:System.Threading.Tasks.Task.Factory%2A>), <xref:System.Threading.Tasks.Task> sınıf; örneğin: `Task.Factory.StartNew(…)`.

- İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümlerinde (.NET Core ve .NET standart dahil), statik <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi için bir kısayol olarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Kullanabilirsiniz <xref:System.Threading.Tasks.Task.Run%2A> kolayca iş parçacığı havuzu hedefleyen bir işlem bağlı görevini başlatmak üzere. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümleri, bu işlem bağımlı görev başlatmak için tercih edilen mekanizması. Kullanım `StartNew` doğrudan yalnızca görev üzerinde daha ayrıntılı denetim istediğinizde.

- Oluşturucular Kullanma `Task` türü veya `Start` oluşturmak ve görev ayrı olarak zamanlamak isterseniz yöntemi. Genel yöntemler yalnızca zaten başlatıldı görevleri döndürmesi gerekir.

- Aşırı kullanmak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, başka bir görev tamamlandığında, zamanlanan yeni bir görev oluşturur. Bazı <xref:System.Threading.Tasks.Task.ContinueWith%2A> aşırı bir iptal belirteci, devamlılık seçenekleri ve zamanlama ve yürütme devamlılık görevi, üzerinde daha iyi denetim için bir Görev Zamanlayıcı kabul edin.

- Kullanım <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemleri. Bu yöntemler tüm ya da herhangi bir sağlanan bir dizi görevi tamamlandığında zamanlanmış yeni bir görev oluşturun. Bu yöntemler, zamanlama denetlemek için aşırı ve bu görevlerin yürütülmesine de sağlar.

Görevi çalıştırmak başlamadan önce bir iptal isteği aldığında, işlem bağlı görevleri'nde, zamanlanmış bir görev yürütme sistem engelleyebilir. Şekilde bir iptal belirteci sağlarsanız (<xref:System.Threading.CancellationToken> nesnesi), belirteç izleyen zaman uyumsuz koda belirtecini geçirebilirsiniz. Yukarıda açıklanan yöntemlerden birini belirtece gibi sağlayabilir `StartNew` veya `Run` böylece `Task` çalışma zamanı belirteç de izlemeniz.

Örneğin, bir görüntü işler zaman uyumsuz bir yöntem göz önünde bulundurun. İptal isteği işleme sırasında gelirse erken çıkış kodu, görevin iptal belirteci yoklama. Ayrıca, iptal isteğini işleme başlamadan önce gelirse oluşturma işleminin engellemek isteyeceksiniz:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

İşlem bağlama görevleri sonlandırmak bir <xref:System.Threading.Tasks.TaskStatus.Canceled> en az biri aşağıdaki koşulların doğru olup olmadığını belirtin:

- İptal isteği aracılığıyla ulaşan <xref:System.Threading.CancellationToken> oluşturma yöntemi için bağımsız değişken olarak sağlanan nesne (örneğin, `StartNew` veya `Run`) görev geçişleri önce <xref:System.Threading.Tasks.TaskStatus.Running> durumu.

- Bir <xref:System.OperationCanceledException> özel aynı içeriyor gibi bir görevin gövdesi içinde işlenmeyen özel durum gider <xref:System.Threading.CancellationToken> göreve geçirilen ve belirtecini iptal başlatması gerektiğini gösterir.

Başka bir özel durum görev gövdesi içinde işlenmeyen kalırsa, görev ile biten <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu ve girişimlerini görev veya sonuç bir özel durum oluşturulmasına neden olan erişim üzerinde bekleyin.

### <a name="io-bound-tasks"></a>G/Ç-bağlı görevler
Doğrudan tamamen yürütme için bir iş parçacığı tarafından yedeklenmelidir olmayan bir görev oluşturmak için kullanmak <xref:System.Threading.Tasks.TaskCompletionSource%601> türü. Bu tür kullanıma sunan bir <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> ilişkili bir döndüren özelliği <xref:System.Threading.Tasks.Task%601> örneği. Bu görev yaşam döngüsünü tarafından denetlenen <xref:System.Threading.Tasks.TaskCompletionSource%601> gibi yöntemler <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>ve bunların `TrySet` çeşitleri.

Belirtilen bir süre sonra tamamlayacak bir görev oluşturmak istediğinizi varsayalım. Örneğin, kullanıcı arabiriminde bir etkinlik geciktirmek isteyebilirsiniz. <xref:System.Threading.Timer?displayProperty=nameWithType> Sınıf zaten bir temsilci süreyi ve kullanarak belirli bir süre sonra zaman uyumsuz olarak çağırma yeteneği sağlar <xref:System.Threading.Tasks.TaskCompletionSource%601> , koyabilirsiniz bir <xref:System.Threading.Tasks.Task%601> süreölçer örneğin ön:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemi, bu amaçla sağlanır ve onu içinde başka bir zaman uyumsuz yöntem, örneğin, bir zaman uyumsuz Yoklama döngüsü uygulamak için kullanabilirsiniz:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> Sınıfı genel olmayan karşılık gelen sahip değil. Ancak, <xref:System.Threading.Tasks.Task%601> türetilen <xref:System.Threading.Tasks.Task>, genel kullanabilmeniz için <xref:System.Threading.Tasks.TaskCompletionSource%601> yalnızca bir görev döndürür g/Ç-bağlı yöntemler için nesne. Bunu yapmak için bir kaynağı ile bir kukla kullanabilir `TResult` (<xref:System.Boolean> kullanıcısı hakkında ilgilenen ancak ek olarak, iyi varsayılan seçim <xref:System.Threading.Tasks.Task> alt türe çevirme için bir <xref:System.Threading.Tasks.Task%601>, özel kullanabilirsiniz `TResult` yerine yazın). Örneğin, `Delay` yöntemi önceki örnekte elde edilen birlikte geçerli saati uzaklık döndürür (`Task<DateTimeOffset>`). Böyle bir sonuç değeri gereksizse yöntemi bunun yerine aşağıdaki gibi kodlanmasını (değişiklik dönüş türü ve bağımsız değişkeni değişiklik Not <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Karma işlem bağlanmış ve g/Ç-bağlı görevler
Zaman uyumsuz yöntemleri için yalnızca işlem bağlı veya g/Ç-bağlı işlemleri sınırlı değildir ancak ikisinin bir karışımıyla gösterebilir. Aslında, birden çok zaman uyumsuz işlemleri genellikle daha büyük karma işlemlere birleştirilir. Örneğin, önceki bir örnekte gösterilen `RenderAsync` yöntemi, bazı giriş `imageData` verilerine göre bir resmi işlemek için yoğun bir hesaplama işlem gerçekleştirdi. Bu `imageData` zaman uyumsuz olarak erişim bir web hizmetinden gelebilir:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Bu örnek ayrıca bir tek iptal belirteci ile birden çok zaman uyumsuz işlemleri nasıl akıtılan gösterir. Daha fazla bilgi için İptal kullanım bölümüne bakın [görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Ayrıca bkz.
 [Görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)  
 [Diğer zaman uyumsuz desen ve türlerle birlikte çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)  
