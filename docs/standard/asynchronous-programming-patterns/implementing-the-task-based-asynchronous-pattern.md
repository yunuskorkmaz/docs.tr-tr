---
title: Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
ms.date: 06/14/2017
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
ms.openlocfilehash: 6218aa1a7b813601e9b718abf862e20a7cbcd313
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124285"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
Görev tabanlı zaman uyumsuz model (dokunma) seçeneğini üç şekilde uygulayabilirsiniz: Visual Studio 'daki C# ve Visual Basic derleyicilerini kullanarak, el ile veya derleyicinin ve el ile yapılan yöntemlerin bir birleşimi aracılığıyla. Aşağıdaki bölümlerde her bir yöntem ayrıntılı olarak ele alınmaktadır. İşlem-bağlantılı ve g/ç ile bağlantılı zaman uyumsuz işlemleri uygulamak için dokunma düzenine de yararlanabilirsiniz. [Iş yükleri](#workloads) bölümü her bir işlem türünü ele alır.

## <a name="generating-tap-methods"></a>DOKUNMA yöntemlerini oluşturma

### <a name="using-the-compilers"></a>Derleyicileri kullanma
.NET Framework 4,5 ' den başlayarak, `async` anahtar sözcüğüyle (Visual Basic ' de`Async`) ilişkilendirilen tüm yöntemler zaman uyumsuz bir yöntem olarak değerlendirilir ve C# ve Visual Basic derleyicileri, DOKUNMA kullanılarak zaman uyumsuz yöntem. Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ya da <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi döndürmelidir. İkincisi için, işlevin gövdesi bir `TResult`döndürmelidir ve derleyici bu sonucun elde edilen görev nesnesi aracılığıyla kullanılabilir hale gelmesini sağlar. Benzer şekilde, yöntemin gövdesinde işlenmemiş olan tüm özel durumlar çıkış görevine göre sıralanır ve sonuçta elde edilen görevin <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda sonlanmasına neden olur. Özel durum, bir <xref:System.OperationCanceledException> (veya türetilen tür) işlenmemiş bir şekilde geçtiğinde, sonuçta elde edilen görevin <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumunda sona erdiği durumdur.

### <a name="generating-tap-methods-manually"></a>DOKUNMA yöntemlerini el ile oluşturma
Uygulama üzerinde daha iyi denetim için dokunma deseninin el ile uygulanmasını sağlayabilirsiniz. Derleyici, <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanından ve <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanındaki destekleyici türlerden kullanıma sunulan genel yüzey alanını kullanır. DOKUNARAK kendinize uygulamak için bir <xref:System.Threading.Tasks.TaskCompletionSource%601> nesnesi oluşturur, zaman uyumsuz işlemi gerçekleştirir ve tamamlandığında, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>veya <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> yöntemini ya da bu yöntemlerden birinin `Try` sürümünü çağırın. DOKUNMA yöntemini el ile uyguladığınızda, gösterilen zaman uyumsuz işlem tamamlandığında ortaya çıkan görevi tamamlamalısınız. Örneğin:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Karma yaklaşım
 DOKUNMA deseninin el ile uygulanmasını, ancak derleyicinin çekirdek mantığını derleyiciye devretmek için yararlı bulabilirsiniz. Örneğin, bir derleyicinin ürettiği zaman uyumsuz yöntem dışındaki bağımsız değişkenleri doğrulamak istiyorsanız karma yaklaşımı kullanmak isteyebilirsiniz, böylece özel durumlar, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesnesi aracılığıyla sunulmak yerine metodun doğrudan çağıranına çıkabilir:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Bu tür bir temsilcinin yararlı olduğu başka bir durum da hızlı yol iyileştirme uygulıyoruz ve önbelleğe alınmış bir görevi döndürmek isteyeceksiniz.

## <a name="workloads"></a>İş yükleri
İşlem-bağlantılı ve g/ç ile bağlantılı zaman uyumsuz işlemleri dokunarak yöntemler olarak uygulayabilirsiniz. Bununla birlikte, bir kitaplıktan ortak yöntemler genel kullanıma sunulduğunda, yalnızca g/ç 'ye bağlanan işlemleri içeren iş yükleri için sağlanması gerekir (hesaplamayı da içerebilir, ancak tamamen hesaplama olmamalıdır). Bir yöntem yalnızca işlem bağlantılı ise, yalnızca zaman uyumlu bir uygulama olarak kullanıma sunulmalıdır. Bunu kullanan kod daha sonra, işi başka bir iş parçacığına devretmek veya paralellik elde etmek için, bu zaman uyumlu yöntemin bir çağrısını bir göreve sarmayı tercih edebilir. Bir yöntem g/ç bağlantılı ise, yalnızca zaman uyumsuz bir uygulama olarak kullanıma sunulmalıdır.

### <a name="compute-bound-tasks"></a>İşlem bağlantılı görevler
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı, yoğun şekilde yoğun işlemleri temsil etmek için idealdir. Varsayılan olarak, verimli yürütme sağlamak için <xref:System.Threading.ThreadPool> sınıfı içindeki özel destekten yararlanır ve ayrıca zaman uyumsuz hesaplamaların ne zaman, nerede ve nasıl yürütüldüğü üzerinde önemli bir denetim sağlar.

Aşağıdaki yollarla, işlem ile bağlantılı görevler oluşturabilirsiniz:

- .NET Framework 4 ' te, zaman uyumsuz olarak yürütülecek bir temsilciyi kabul eden <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemini kullanın (genellikle bir <xref:System.Action%601> veya <xref:System.Func%601>). Bir <xref:System.Action%601> temsilcisi sağlarsanız, yöntemi bu temsilcinin zaman uyumsuz yürütmesini temsil eden bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesnesi döndürür. Bir <xref:System.Func%601> temsilcisi sağlarsanız, yöntem bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi döndürür. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yönteminin aşırı yüklemeleri, bir iptal belirtecini (<xref:System.Threading.CancellationToken>), görev oluşturma seçeneklerini (<xref:System.Threading.Tasks.TaskCreationOptions>) ve bir görev zamanlayıcısını (<xref:System.Threading.Tasks.TaskScheduler>) kabul edip, bu da görevin zamanlanması ve yürütülmesi üzerinde ayrıntılı denetim sağlar. Geçerli görev zamanlayıcısını hedefleyen bir fabrika örneği, <xref:System.Threading.Tasks.Task> sınıfının statik özelliği (<xref:System.Threading.Tasks.Task.Factory%2A>) olarak kullanılabilir; Örneğin: `Task.Factory.StartNew(…)`.

- .NET Framework 4,5 ve sonraki sürümlerinde (.NET Core ve .NET Standard dahil), statik <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemini <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>için bir kısayol olarak kullanın. İş parçacığı havuzunu hedefleyen bir işlem ile bağlantılı görevi kolayca başlatmak için <xref:System.Threading.Tasks.Task.Run%2A> kullanabilirsiniz. .NET Framework 4,5 ve sonraki sürümlerde, bu, işlem ile sınırlı bir görevi başlatmak için tercih edilen mekanizmadır. Yalnızca görev üzerinde daha ayrıntılı denetim istediğinizde `StartNew` doğrudan kullanın.

- Görevi ayrı olarak oluşturmak ve çizelgelemek istiyorsanız `Task` türünün veya `Start` yönteminin oluşturucularını kullanın. Ortak yöntemler yalnızca önceden başlatılmış görevleri döndürmelidir.

- <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini kullanın. Bu yöntem, başka bir görev tamamlandığında zamanlanan yeni bir görev oluşturur. Bazı <xref:System.Threading.Tasks.Task.ContinueWith%2A> aşırı yüklemeleri, devam görevinin zamanlanması ve yürütülmesi üzerinde daha iyi denetim için bir iptal belirteci, devamlılık seçeneği ve bir görev zamanlayıcısını kabul eder.

- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemlerini kullanın. Bu yöntemler, sağlanan bir görev kümesinin tümü veya herhangi biri tamamlandığında zamanlanan yeni bir görev oluşturur. Bu yöntemler Ayrıca, bu görevlerin planlanmasını ve yürütülmesini denetlemek için aşırı yüklemeler sağlar.

İşlem bağlantılı görevlerde, sistem, görevi çalıştırmaya başlamadan önce bir iptal isteği alırsa, zamanlanmış bir görevin yürütülmesini önleyebilir. Bu nedenle, bir iptal belirteci (<xref:System.Threading.CancellationToken> nesnesi) sağlarsanız, bu belirteci belirteci izleyen zaman uyumsuz koda geçirebilirsiniz. Ayrıca, `Task` çalışma zamanının belirteci izleyebilmesi için `StartNew` veya `Run` gibi yukarıda bahsedilen metotlardan birine belirteç sağlayabilirsiniz.

Örneğin, bir görüntüyü işleyen zaman uyumsuz bir yöntem düşünün. Görevin gövdesi, işleme sırasında bir iptal isteği geldiğinde kodun erken çıkabilmesi için iptal belirtecini yoklayabilirler. Ayrıca, işleme başlamadan önce iptal isteği alınırsa, işleme işlemini engellemek isteyeceksiniz:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Aşağıdaki koşullardan en az biri doğru ise, işlem bağlantılı görevler <xref:System.Threading.Tasks.TaskStatus.Canceled> bir durumda biter:

- Bir iptal isteği, görev <xref:System.Threading.Tasks.TaskStatus.Running> durumuna geçmeden önce, oluşturma yöntemine bir bağımsız değişken olarak (örneğin, `StartNew` veya `Run`) olarak girilen <xref:System.Threading.CancellationToken> nesnesine ulaşır.

- <xref:System.OperationCanceledException> bir özel durum, bu tür bir görevin gövdesinde işlenmemiş olur, bu özel durum göreve geçirilen aynı <xref:System.Threading.CancellationToken> içerir ve bu belirteç iptalinin istendiğini gösterir.

Görevin gövdesinde başka bir özel durum yakalanıyorsa, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sona erer ve görevde bekleyen ya da sonucun oluşmasına neden olan herhangi bir istisna oluşur.

### <a name="io-bound-tasks"></a>G/ç bağlantılı görevler
Yürütmenin tamamı için bir iş parçacığı tarafından doğrudan yedeklenmez bir görev oluşturmak için <xref:System.Threading.Tasks.TaskCompletionSource%601> türünü kullanın. Bu tür, ilişkili bir <xref:System.Threading.Tasks.Task%601> örneğini döndüren bir <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> özelliğini kullanıma sunar. Bu görevin yaşam döngüsü <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>ve `TrySet` türevleri gibi <xref:System.Threading.Tasks.TaskCompletionSource%601> yöntemlerle denetlenir.

Belirli bir süre sonra tamamlanacak bir görev oluşturmak istediğinizi varsayalım. Örneğin, Kullanıcı arabirimindeki bir etkinliği geciktirmek isteyebilirsiniz. <xref:System.Threading.Timer?displayProperty=nameWithType> sınıfı zaten belirli bir süre geçtikten sonra bir temsilciyi zaman uyumsuz olarak çağırma özelliği sağlar ve <xref:System.Threading.Tasks.TaskCompletionSource%601> kullanarak <xref:System.Threading.Tasks.Task%601> önüne bir ekleyebilirsiniz, örneğin:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

.NET Framework 4,5 ' den başlayarak, bu amaçla <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemi sağlanır ve örneğin zaman uyumsuz bir yoklama döngüsü uygulamak için başka bir zaman uyumsuz yöntemin içinde kullanabilirsiniz:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> sınıfı genel olmayan bir karşılığına sahip değil. Ancak, <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task>türetilir, böylece yalnızca bir görevi döndüren g/ç 'ye bağlanan yöntemler için genel <xref:System.Threading.Tasks.TaskCompletionSource%601> nesnesi kullanabilirsiniz. Bunu yapmak için, bir kaynağı kukla `TResult` kullanabilirsiniz (<xref:System.Boolean> iyi bir varsayılan seçenektir, ancak <xref:System.Threading.Tasks.Task> kullanıcısı bir <xref:System.Threading.Tasks.Task%601>`TResult`, bunun yerine bir özel türü kullanabilirsiniz). Örneğin, önceki örnekteki `Delay` yöntemi, elde edilen fark (`Task<DateTimeOffset>`) ile birlikte geçerli saati döndürür. Böyle bir sonuç değeri gereksiz ise, yöntemi aşağıdaki şekilde kodlanır (dönüş türü değişikliğini ve bağımsız değişkenin <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>değişiklik olduğunu aklınızda):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Karma işlem ile bağlantılı ve g/ç 'ye sınırlı görevler
Zaman uyumsuz yöntemler yalnızca işlem ile bağlantılı veya g/ç bağlantılı işlemlerle sınırlı değildir ancak ikisinin bir karışımını temsil edebilir. Aslında, birden çok zaman uyumsuz işlem genellikle daha büyük karışık işlemler halinde birleştirilir. Örneğin, önceki bir örnekte gösterilen `RenderAsync` yöntemi, bazı giriş `imageData` verilerine göre bir resmi işlemek için yoğun bir hesaplama işlem gerçekleştirdi. Bu `imageData`, zaman uyumsuz olarak erişebileceğiniz bir Web hizmetinden gelebilir:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Bu örnek ayrıca, çoklu zaman uyumsuz işlemler aracılığıyla tek bir iptal belirtecinin nasıl iş parçacıklı olabileceğini gösterir. Daha fazla bilgi için, [görev tabanlı zaman uyumsuz model](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma konusunun iptal kullanımı bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
