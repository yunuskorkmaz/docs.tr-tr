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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a218633ed607222fec3e46629a9bcd614c3d0610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678219"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
Görev tabanlı zaman uyumsuz desen (TAP) üç yolla gerçekleştirebilirsiniz: Visual Studio'da C# ve Visual Basic derleyicileri kullanarak, el ile veya derleyici ve el yönteminin bir birleşimi yoluyla. Aşağıdaki bölümlerde, her bir yöntemin ayrıntılı ele alınmıştır. DOKUNUN deseni hesaplama bağlantılı hem miyim/O-ilişkili zaman uyumsuz işlemleri uygulamak için kullanabilirsiniz. [İş yükleri](#workloads) bölümde her işlem türü açıklanmaktadır.

## <a name="generating-tap-methods"></a>DOKUNUN yöntemleri üretiliyor

### <a name="using-the-compilers"></a>Derleyiciler kullanma
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ile öznitelendirilen herhangi bir yöntemi `async` anahtar sözcüğü (`Async` Visual Basic'te) zaman uyumsuz bir yöntem ve C# ve Visual Basic derleyicileri gerçekleştirme uygulamak için gerekli dönüştürmeleri olarak kabul edilir DOKUNUN kullanarak zaman uyumsuz yöntem. Zaman uyumsuz bir yöntem ya da döndürmelidir bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesne. İkincisi, işlev gövdesini döndürmelidir bir `TResult`, ve bu sonucu elde edilen görev nesnesi sunulacağını derleyici sağlar. Benzer şekilde, Git Yöntemin gövdesi içinde işlenmeyen özel durumları için çıktı görevi sıralanmış ve bitecek şekilde elde edilen görevle neden <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumu. Özel durum olduğunda bir <xref:System.OperationCanceledException> (veya türetilmiş tür) gelecek işlenmemiş, elde edilen görev, bu durumda biten <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.

### <a name="generating-tap-methods-manually"></a>DOKUNUN yöntemleri el ile oluşturma
Uygulama üzerinde daha iyi denetim için el ile DOKUNUN deseni uygulayabilir. Öğesinden gösterilen ortak yüzey alanını derleyici dayanan <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanı ve türlerini destekleyen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı. DOKUNUN kendiniz uygulamak için oluşturduğunuz bir <xref:System.Threading.Tasks.TaskCompletionSource%601> nesnesi, zaman uyumsuz işlemi gerçekleştirebilir ve tamamlandığında, çağrı <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, veya <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> yöntemi veya `Try` aşağıdaki yöntemlerden birini sürümü. El ile bir TAP yöntemi uyguladığınızda, gösterilen zaman uyumsuz işlem tamamlandığında elde edilen görevi tamamlamanız gerekir. Örneğin:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Karma yaklaşım
 DOKUNUN el ile tasarımın uygulandığı ancak çekirdek mantığını derleyici uygulaması için temsilci seçmek için faydalı. Örneğin, özel durumlar yöntemin doğrudan çağıran yerine aracılığıyla kullanıma çizgilerden kaçınabilirsiniz dışında bir derleyici tarafından oluşturulan zaman uyumsuz yöntem bağımsız değişkenleri doğrulamak istediğinizde, karma bir yaklaşım kullanmak isteyebilirsiniz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesnesi:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Hızlı yolu iyileştirme uygulama ve önbelleğe alınmış bir görevi döndürmek istediğiniz zaman bu tür bir temsilci kullanışlı olduğu başka bir durumdur.

## <a name="workloads"></a>İş yükleri
TAP yöntemi hesaplama bağlantılı hem miyim/O-ilişkili zaman uyumsuz işlemleri uygulayabilir. Ancak, bunlar DOKUNUN yöntemleri herkese açık şekilde kitaplığından maruz kaldığında, (Bunlar ayrıca, hesaplama içerebilir, ancak tamamen hesaplama olmamalıdır) ben/Ç işlemleri gerektiren yükleri sağlanmalıdır. İşlem bağlı yalnızca bir yöntemi ise yalnızca zaman uyumlu bir uygulama açılmamalıdır. Kullandığı kod bir görev paralelliği elde etmek için ya da başka bir iş parçacığı için iş yüklerini boşaltmak üzere zaman uyumlu yöntemin bir çağrısını sarmalamak seçebilirsiniz. Ve bir yöntem, ı/O-ilişkili ise, bunu yalnızca zaman uyumsuz bir uygulama açığa çıkarılmamalıdır.

### <a name="compute-bound-tasks"></a>İşlem bağlı görevler
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Sınıfı ideal olarak uygun işlem bakımından yoğun işlemleri temsil etmek için. İsteğe bağlı olarak varsayılan olarak, içinde özel destek avantajlarından yararlanır <xref:System.Threading.ThreadPool> verimli yürütme sağlamak için sınıf ve ayrıca önemli denetimi zaman, nerede ve nasıl sağladığı zaman uyumsuz hesaplamalar yürütün.

İşlem bağlı görevleri aşağıdaki yollarla oluşturabilirsiniz:

- .NET Framework 4'te kullanmak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> kabul eden bir temsilci yöntemi (genellikle bir <xref:System.Action%601> veya <xref:System.Func%601>) zaman uyumsuz olarak yürütülecek. Sağlarsanız bir <xref:System.Action%601> yöntemi döndürür, temsilci bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz yürütme bu temsilcinin temsil eden nesne. Sağlarsanız bir <xref:System.Func%601> yöntemi döndürür, temsilci bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesne. Overloads biri <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi, bir iptal belirteci kabul (<xref:System.Threading.CancellationToken>), görev oluşturma seçenekleri (<xref:System.Threading.Tasks.TaskCreationOptions>) ve bir Görev Zamanlayıcı'yı (<xref:System.Threading.Tasks.TaskScheduler>), her biri, zamanlama ve yürütme görevin üzerinde ayrıntılı denetim sağlar. Geçerli Görev Zamanlayıcı'yı hedefleyen bir Fabrika örnek statik bir özellik olarak kullanılabilir (<xref:System.Threading.Tasks.Task.Factory%2A>), <xref:System.Threading.Tasks.Task> sınıfı; örneğin: `Task.Factory.StartNew(…)`.

- İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümlerinde (.NET Core ve .NET Standard dahil), statik <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi için bir kısayol olarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Kullanmanızı <xref:System.Threading.Tasks.Task.Run%2A> kolayca iş parçacığı havuzunu hedefleyen bir hesaplama bağlantılı görevini başlatmak üzere. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümlerinde, bu işlem bağlı görevi başlatmak için tercih edilen mekanizması. Kullanım `StartNew` doğrudan yalnızca görev üzerinde daha kapsamlı denetim istediğinizde.

- Oluşturucular Kullanma `Task` türü veya `Start` oluşturmak ve ayrı olarak görevi zamanlamak istiyorsanız yöntemi. Genel yöntemler yalnızca zaten başlatıldığından görev döndürmelidir.

- Aşırı yüklemelerini kullanın <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, başka bir görev tamamlandığında zamanlanmış yeni bir görev oluşturur. Bazı <xref:System.Threading.Tasks.Task.ContinueWith%2A> aşırı bir iptal belirteci, devamlılık seçenekleri ve zamanlama ve yürütme devamlılık görevinin üzerinde daha iyi denetim için bir Görev Zamanlayıcı kabul etmiş olursunuz.

- Kullanım <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemleri. Bu yöntemlerin tümü veya herhangi biri sağlanan bir dizi görev tamamlandıktan sonra zamanlanan yeni bir görev oluşturun. Bu yöntemler de zamanlama denetlemek için aşırı yüklemeler ve bu görevlerin yürütülmesini sağlar.

Görevi çalıştırmak başlamadan önce bir iptal isteği alırsa hesaplama bağlantılı görevleri'nde, sistem zamanlanmış bir görevin yürütülmesini engelleyebilirsiniz. Örneğin, bir iptal belirteci sağlarsanız olarak (<xref:System.Threading.CancellationToken> nesne), bu belirteci izleyen belirteç için zaman uyumsuz kodu geçirebilirsiniz. Yukarıda açıklanan yöntemlerden birini belirtece gibi sağlayabilir `StartNew` veya `Run` böylece `Task` çalışma zamanı belirteç de izlemek.

Örneğin, görüntüyü işleyen zaman uyumsuz bir yöntem düşünün. İşleme sırasında bir iptal isteğine geldiğinde, erken çıkış kodu, görevin iptal belirtecini yoklama. Ayrıca, işleme başlamadan önce iptal isteği alınırsa, işleme işlemi önlemek isteyeceksiniz:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

İşlem bağlı görevleri bitiş içinde bir <xref:System.Threading.Tasks.TaskStatus.Canceled> en az biri aşağıdaki koşullardan biri doğru olup olmadığını belirtin:

- Aracılığıyla bir iptal isteğine ulaşan <xref:System.Threading.CancellationToken> oluşturma yöntemi için bağımsız değişken olarak sağlanan nesne (örneğin, `StartNew` veya `Run`) görev geçişleri önce <xref:System.Threading.Tasks.TaskStatus.Running> durumu.

- Bir <xref:System.OperationCanceledException> özel durum işlenmemiş özel durum aynı içerdiğinden bu tür bir görev gövdesinde gider <xref:System.Threading.CancellationToken> göreve geçirilen ve iptalin istendiğini belirtecini gösterir.

Görev başka bir özel durum işlenmemiş görevin gövdesinden aşması durumunda, biten <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu ve görev ya da sonuç bir özel durum oluşturulmasına neden olan erişim bekleyin girişimleri.

### <a name="io-bound-tasks"></a>Ben/O-bağımlı görevler
Doğrudan tamamen yürütme için bir iş parçacığı tarafından yedeklenmemelidir bir görev oluşturmak için kullanın <xref:System.Threading.Tasks.TaskCompletionSource%601> türü. Bu tür sunan bir <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> ilişkili bir döndüren özellik <xref:System.Threading.Tasks.Task%601> örneği. Bu görev yaşam döngüsünü denetleyen <xref:System.Threading.Tasks.TaskCompletionSource%601> gibi yöntemler <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>ve bunların `TrySet` çeşitleri.

Belirtilen bir süre sonra tamamlanacak bir görev oluşturmak istediğinizi varsayalım. Örneğin, kullanıcı arabiriminde bir etkinlik geciktirmek isteyebilirsiniz. <xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı zaten süreyi ve kullanarak belirli bir süre sonra zaman uyumsuz olarak bir temsilci çağırma yeteneği sağlar <xref:System.Threading.Tasks.TaskCompletionSource%601> koyabilirsiniz bir <xref:System.Threading.Tasks.Task%601> Zamanlayıcıyı, örneğin ön:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemi, bu amaç için sağlanır ve bunu başka bir zaman uyumsuz yöntemde, örneğin, bir zaman uyumsuz Yoklama döngüsü uygulamak için kullanabilirsiniz:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> Sınıfı, genel olmayan karşılığı yok. Ancak, <xref:System.Threading.Tasks.Task%601> türetildiği <xref:System.Threading.Tasks.Task>, genel kullanabilmeniz için <xref:System.Threading.Tasks.TaskCompletionSource%601> yalnızca bir görev döndüren miyim/O-bağlı yöntemler için nesne. Bunu yapmak için bir kaynak ile bir kukla kullanabilirsiniz `TResult` (<xref:System.Boolean> kullanıcısı hakkında endişe ancak ek olarak, iyi bir varsayılan seçim <xref:System.Threading.Tasks.Task> alta dönüştürme işlemi için bir <xref:System.Threading.Tasks.Task%601>, özel bir kullanabilirsiniz `TResult` bunun yerine yazın). Örneğin, `Delay` önceki örnekte yöntemi ortaya çıkan yanı sıra geçerli saati uzaklığı döndürür (`Task<DateTimeOffset>`). Böyle bir sonuç değeri gereksizse yöntemi bunun yerine şu şekilde kodlanmasını (dönüş türü değişikliğini ve bağımsız değişkenin Not <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Karma hesaplama bağlantılı ve ben/O-bağımlı görevler
Zaman uyumsuz yöntemler işlem bağlı veya miyim/O-bağlama işlemleri sınırlı değildir ancak ikisinin karışımı temsil edebilir. Aslında, birden çok zaman uyumsuz işlemler genellikle daha büyük karma işlemlere birleştirilir. Örneğin, önceki bir örnekte gösterilen `RenderAsync` yöntemi, bazı giriş `imageData` verilerine göre bir resmi işlemek için yoğun bir hesaplama işlem gerçekleştirdi. Bu `imageData` zaman uyumsuz olarak erişen bir web hizmetinden gelebilir:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Tek bir iptal belirteci aracılığıyla birden çok zaman uyumsuz işlemler nasıl akıtılan, bu örnek ayrıca gösterir. Daha fazla bilgi için bkz: iptal kullanım bölümünde [görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
