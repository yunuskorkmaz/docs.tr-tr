---
title: Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
description: Bu makalede, görev tabanlı zaman uyumsuz düzenin nasıl uygulanacağı açıklanmaktadır. İşlem bağlantılı ve g/ç ile bağlantılı zaman uyumsuz işlemleri uygulamak için bunu kullanabilirsiniz.
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
ms.openlocfilehash: 7d031bab6ba0a4420062eff107aeb1262d9b3b40
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421234"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
Görev tabanlı zaman uyumsuz model ' i (dokunarak) üç şekilde uygulayabilirsiniz: C# ve Visual Basic derleyicileri, Visual Studio 'da, el ile veya derleyicinin ve el ile yapılan yöntemlerin bir birleşimi aracılığıyla. Aşağıdaki bölümlerde her bir yöntem ayrıntılı olarak ele alınmaktadır. İşlem-bağlantılı ve g/ç ile bağlantılı zaman uyumsuz işlemleri uygulamak için dokunma düzenine de yararlanabilirsiniz. [Iş yükleri](#workloads) bölümü her bir işlem türünü ele alır.

## <a name="generating-tap-methods"></a>DOKUNMA yöntemlerini oluşturma

### <a name="using-the-compilers"></a>Derleyicileri kullanma
.NET Framework 4,5 ' den başlayarak, `async` anahtar kelimesiyle ( `Async` Visual Basic) nitelendirilen tüm yöntemler zaman uyumsuz bir yöntem olarak değerlendirilir ve C# ve Visual Basic DERLEYICILERI, dokunarak yöntemi zaman uyumsuz olarak uygulamak için gereken dönüştürmeleri gerçekleştirir. Zaman uyumsuz bir yöntem, ya da <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi döndürmelidir. İkincisi için, işlevin gövdesi bir döndürmelidir `TResult` ve derleyici bu sonucun elde edilen görev nesnesi aracılığıyla kullanılabilir hale gelmesini sağlar. Benzer şekilde, yöntemin gövdesinde işlenmemiş olan tüm özel durumlar, çıkış görevine göre sıralanır ve sonuçta elde edilen görevin durumunda sonlanmasına neden olur <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> . Bu kuralın istisnası, bir <xref:System.OperationCanceledException> (ya da türetilmiş tür) işlenmemiş olduğunda, sonuçta elde edilen görevin durumu sona erdiği durumdur <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> .

### <a name="generating-tap-methods-manually"></a>DOKUNMA yöntemlerini el ile oluşturma
Uygulama üzerinde daha iyi denetim için dokunma deseninin el ile uygulanmasını sağlayabilirsiniz. Derleyici, ad <xref:System.Threading.Tasks?displayProperty=nameWithType> alanı ve ad alanındaki destekleme türlerinden açığa çıkarılan genel yüzey alanını kullanır <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> . DOKUNARAK kendinize uygulamak için bir <xref:System.Threading.Tasks.TaskCompletionSource%601> nesne oluşturur, zaman uyumsuz işlem gerçekleştirir ve tamamlandığında,, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> veya <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> yöntemini ya da `Try` Bu yöntemlerin birinin sürümünü çağırın. DOKUNMA yöntemini el ile uyguladığınızda, gösterilen zaman uyumsuz işlem tamamlandığında ortaya çıkan görevi tamamlamalısınız. Örnek:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Karma yaklaşım
 DOKUNMA deseninin el ile uygulanmasını, ancak derleyicinin çekirdek mantığını derleyiciye devretmek için yararlı bulabilirsiniz. Örneğin, bir derleyicinin ürettiği zaman uyumsuz yöntem dışındaki bağımsız değişkenleri doğrulamak istediğinizde karma yaklaşımı kullanmak isteyebilirsiniz, böylece özel durumlar, nesne aracılığıyla gösterilmektense metodun doğrudan çağıranına çıkabilir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> :

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Bu tür bir temsilcinin yararlı olduğu başka bir durum da hızlı yol iyileştirme uygulıyoruz ve önbelleğe alınmış bir görevi döndürmek isteyeceksiniz.

## <a name="workloads"></a>İş yükleri
İşlem-bağlantılı ve g/ç ile bağlantılı zaman uyumsuz işlemleri dokunarak yöntemler olarak uygulayabilirsiniz. Bununla birlikte, bir kitaplıktan ortak yöntemler genel kullanıma sunulduğunda, yalnızca g/ç 'ye bağlanan işlemleri içeren iş yükleri için sağlanması gerekir (hesaplamayı da içerebilir, ancak tamamen hesaplama olmamalıdır). Bir yöntem yalnızca işlem bağlantılı ise, yalnızca zaman uyumlu bir uygulama olarak kullanıma sunulmalıdır. Bunu kullanan kod daha sonra, işi başka bir iş parçacığına devretmek veya paralellik elde etmek için, bu zaman uyumlu yöntemin bir çağrısını bir göreve sarmayı tercih edebilir. Bir yöntem g/ç bağlantılı ise, yalnızca zaman uyumsuz bir uygulama olarak kullanıma sunulmalıdır.

### <a name="compute-bound-tasks"></a>İşlem bağlantılı görevler
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Sınıfı, yoğun şekilde yoğun işlemleri temsil etmek için idealdir. Varsayılan olarak, <xref:System.Threading.ThreadPool> verimli yürütme sağlamak için sınıfındaki özel desteğin avantajlarından yararlanır ve ayrıca zaman uyumsuz hesaplamaların ne zaman, nerede ve nasıl yürütüldüğü üzerinde önemli bir denetim sağlar.

Aşağıdaki yollarla, işlem ile bağlantılı görevler oluşturabilirsiniz:

- .NET Framework 4 ' te, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> zaman uyumsuz olarak yürütülecek bir temsilciyi (genellikle bir <xref:System.Action%601> veya a) kabul eden yöntemini kullanın <xref:System.Func%601> . Bir <xref:System.Action%601> temsilci sağlarsanız, yöntemi <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Bu temsilcinin zaman uyumsuz yürütmesini temsil eden bir nesne döndürür. Bir <xref:System.Func%601> temsilci sağlarsanız, yöntemi bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesnesi döndürür. Yöntemin aşırı yüklemeleri, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> bir iptal belirtecini ( <xref:System.Threading.CancellationToken> ), görev oluşturma seçeneklerini ( <xref:System.Threading.Tasks.TaskCreationOptions> ) ve bir görev zamanlayıcısını () kabul eder <xref:System.Threading.Tasks.TaskScheduler> . Bu, hepsi görevin zamanlanması ve yürütülmesi üzerinde ayrıntılı denetim sağlar. Geçerli görev zamanlayıcısını hedefleyen bir fabrika örneği, sınıfının statik özelliği () olarak kullanılabilir <xref:System.Threading.Tasks.Task.Factory%2A> <xref:System.Threading.Tasks.Task> . Örneğin: `Task.Factory.StartNew(…)` .

- .NET Framework 4,5 ve sonraki sürümlerde (.NET Core ve .NET Standard dahil), <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> için bir kısayol olarak statik yöntemi kullanın <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.Task.Run%2A>İş parçacığı havuzunu hedefleyen bir işlem ile bağlantılı görevi kolayca başlatmak için kullanabilirsiniz. .NET Framework 4,5 ve sonraki sürümlerde, bu, işlem ile sınırlı bir görevi başlatmak için tercih edilen mekanizmadır. `StartNew`Yalnızca görev üzerinde daha ayrıntılı denetim istediğinizde, doğrudan kullanın.

- `Task` `Start` Görevi ayrı olarak oluşturmak ve çizelgelemek istiyorsanız tür veya yöntem oluşturucularını kullanın. Ortak yöntemler yalnızca önceden başlatılmış görevleri döndürmelidir.

- Yönteminin aşırı yüklerini kullanın <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> . Bu yöntem, başka bir görev tamamlandığında zamanlanan yeni bir görev oluşturur. Bazı <xref:System.Threading.Tasks.Task.ContinueWith%2A> aşırı yüklemeler bir iptal etme belirteci, devamlılık seçeneklerini ve devam görevinin zamanlanması ve yürütülmesi üzerinde daha iyi denetim için bir görev zamanlayıcısını kabul eder.

- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>Ve yöntemlerini kullanın <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> . Bu yöntemler, sağlanan bir görev kümesinin tümü veya herhangi biri tamamlandığında zamanlanan yeni bir görev oluşturur. Bu yöntemler Ayrıca, bu görevlerin planlanmasını ve yürütülmesini denetlemek için aşırı yüklemeler sağlar.

İşlem bağlantılı görevlerde, sistem, görevi çalıştırmaya başlamadan önce bir iptal isteği alırsa, zamanlanmış bir görevin yürütülmesini önleyebilir. Bu nedenle, bir iptal belirteci ( <xref:System.Threading.CancellationToken> nesne) sağlarsanız, belirteci izleyen zaman uyumsuz koda bu belirteci geçirebilirsiniz. Ayrıca `StartNew` , ya da `Run` `Task` çalışma zamanının belirteci izleyebilmesi için, veya gibi yukarıda bahsedilen metotlardan birine belirteç sağlayabilirsiniz.

Örneğin, bir görüntüyü işleyen zaman uyumsuz bir yöntem düşünün. Görevin gövdesi, işleme sırasında bir iptal isteği geldiğinde kodun erken çıkabilmesi için iptal belirtecini yoklayabilirler. Ayrıca, işleme başlamadan önce iptal isteği alınırsa, işleme işlemini engellemek isteyeceksiniz:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

<xref:System.Threading.Tasks.TaskStatus.Canceled>Aşağıdaki koşullardan en az biri doğru ise, işlem bağlantılı görevler bir durum ile biter:

- Bir iptal isteği <xref:System.Threading.CancellationToken> , `StartNew` `Run` görev durumuna geçmeden önce oluşturma yöntemine (örneğin, veya) bağımsız değişken olarak belirtilen nesnesine ulaşır <xref:System.Threading.Tasks.TaskStatus.Running> .

- Bu <xref:System.OperationCanceledException> tür bir görevin gövdesinde işlenmeyen bir özel durum, bu özel durum <xref:System.Threading.CancellationToken> göreve geçirilmiş ve bu belirteç iptalinin istendiğini gösterdiği bir durumdur.

Görevin gövdesinde başka bir özel durum yakalanıyorsa, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sonlanır ve görevde bekleyen ya da sonuç olarak bir özel durum oluşturulmasına neden olur.

### <a name="io-bound-tasks"></a>G/ç bağlantılı görevler
Yürütmenin tamamı için bir iş parçacığı tarafından doğrudan yedeklenmez bir görev oluşturmak için <xref:System.Threading.Tasks.TaskCompletionSource%601> türünü kullanın. Bu tür <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> , ilişkili bir örnek döndüren bir özelliği gösterir <xref:System.Threading.Tasks.Task%601> . Bu görevin yaşam döngüsü,,, <xref:System.Threading.Tasks.TaskCompletionSource%601> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> ve çeşitleri gibi yöntemlerle denetlenir `TrySet` .

Belirli bir süre sonra tamamlanacak bir görev oluşturmak istediğinizi varsayalım. Örneğin, Kullanıcı arabirimindeki bir etkinliği geciktirmek isteyebilirsiniz. <xref:System.Threading.Timer?displayProperty=nameWithType>Sınıfı zaten belirli bir süre geçtikten sonra bir temsilciyi zaman uyumsuz olarak çağırma özelliği sağlar ve <xref:System.Threading.Tasks.TaskCompletionSource%601> bunu kullanarak <xref:System.Threading.Tasks.Task%601> süreölçer üzerine bir ön nokta koyabilirsiniz, örneğin:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

.NET Framework 4,5 ile başlayarak, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemi bu amaçla sağlanır ve örneğin zaman uyumsuz bir yoklama döngüsü uygulamak için başka bir zaman uyumsuz yöntemin içinde kullanabilirsiniz:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601>Sınıfta genel olmayan bir karşılık yok. Ancak, <xref:System.Threading.Tasks.Task%601> öğesinden türetilir <xref:System.Threading.Tasks.Task> , bu nedenle, <xref:System.Threading.Tasks.TaskCompletionSource%601> yalnızca bir görevi döndüren g/ç 'ye bağlanan yöntemler için genel nesneyi kullanabilirsiniz. Bunu yapmak için, bir kaynağı kukla ile kullanabilirsiniz `TResult` ( <xref:System.Boolean> iyi bir varsayılan seçenektir, ancak bunu bir alta doğru atama Kullanıcı hakkında endişeleriniz varsa <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> , `TResult` bunun yerine özel bir tür kullanabilirsiniz). Örneğin, `Delay` önceki örnekteki yöntemi, elde edilen fark () ile birlikte geçerli saati döndürür `Task<DateTimeOffset>` . Böyle bir sonuç değeri gereksiz ise, yöntemi aşağıdaki şekilde kodlanmış olabilir (dönüş türünün değişikliğini ve bağımsız değişkenin değişikliğini <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A> ):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Karma işlem ile bağlantılı ve g/ç 'ye sınırlı görevler
Zaman uyumsuz yöntemler yalnızca işlem ile bağlantılı veya g/ç bağlantılı işlemlerle sınırlı değildir ancak ikisinin bir karışımını temsil edebilir. Aslında, birden çok zaman uyumsuz işlem genellikle daha büyük karışık işlemler halinde birleştirilir. Örneğin, önceki bir örnekte gösterilen `RenderAsync` yöntemi, bazı giriş `imageData` verilerine göre bir resmi işlemek için yoğun bir hesaplama işlem gerçekleştirdi. Bu `imageData` , zaman uyumsuz olarak erişebileceğiniz bir Web hizmetinden gelebilir:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Bu örnek ayrıca, çoklu zaman uyumsuz işlemler aracılığıyla tek bir iptal belirtecinin nasıl iş parçacıklı olabileceğini gösterir. Daha fazla bilgi için, [görev tabanlı zaman uyumsuz model](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma konusunun iptal kullanımı bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
