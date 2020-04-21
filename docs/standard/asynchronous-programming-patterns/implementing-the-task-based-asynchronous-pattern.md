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
ms.openlocfilehash: e09ed853598dcbb13cc8dc3fe963276e4b5e974d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739642"
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Deseni Uygulama
Görev Tabanlı Eşenkron Desen'i (TAP) üç şekilde uygulayabilirsiniz: Visual Studio'daki C# ve Visual Basic derleyicilerini kullanarak, el ile veya derleyici ve manuel yöntemlerin bir kombinasyonu aracılığıyla. Aşağıdaki bölümlerde her yöntem ayrıntılı olarak tartışılmaktadır. Hem bilgisayara bağlı hem de G/Ç bağlı asenkron işlemleri uygulamak için TAP deseni kullanabilirsiniz. [İş Yükleri](#workloads) bölümünde her işlem türü anlatılır.

## <a name="generating-tap-methods"></a>TAP yöntemleri oluşturma

### <a name="using-the-compilers"></a>Derleyicileri kullanma
.NET Framework 4.5 ile başlayarak, (Visual `async` `Async` Basic'te) anahtar kelimesiile atfedilen herhangi bir yöntem eşzamanlı bir yöntem olarak kabul edilir ve C# ve Visual Basic derleyicileri TAP kullanarak yöntemi eşzamanlı olarak uygulamak için gerekli dönüşümleri gerçekleştirir. Bir eşzamanlı yöntem bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesne döndürmelidir. İkincisi için, işlevin gövdesi bir `TResult`,, ve derleyici bu sonucu elde edilen görev nesnesi aracılığıyla kullanılabilir hale sağlar döndürmelidir. Benzer şekilde, yöntemin gövdesi içinde işlenmemiş giden tüm özel durumlar çıktı görevine marshaled ve ortaya <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> çıkan görevin durumda sona ermesine neden olur. Bu kuralın istisnası, <xref:System.OperationCanceledException> (veya türetilmiş tür) işlenmemiş olduğunda ve bu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumda ortaya çıkan görev in durumunda sona erer.

### <a name="generating-tap-methods-manually"></a>TAP yöntemlerini el ile oluşturma
Uygulama üzerinde daha iyi denetim için TAP desenini el ile uygulayabilirsiniz. Derleyici, <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanından ve <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında niçin destektürlerine maruz kalan ortak yüzey alanına dayanır. TAP'ı kendiniz uygulamak için <xref:System.Threading.Tasks.TaskCompletionSource%601> bir nesne oluşturur, eşzamanlı işlemi gerçekleştirir ve tamamlandığında <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>yani <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> , veya `Try` yönteme veya bu yöntemlerden birinin sürümünü arayın. Bir TAP yöntemini el ile uyguladığınız zaman, temsil edilen eşzamanlı işlem tamamlandığında ortaya çıkan görevi tamamlamanız gerekir. Örneğin:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Hibrit yaklaşım
 TAP deseni el ile uygulamak için yararlı olabilir ama derleme için uygulama için temel mantık temsilci. Örneğin, özel durumlar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesne aracılığıyla maruz kalmak yerine yöntemin doğrudan arayan alabilirsiniz böylece derleyici tarafından oluşturulan bir eşzamanlı yöntem dışında bağımsız değişkenleri doğrulamak istediğinizde karma yaklaşımı kullanmak isteyebilirsiniz:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Bu tür bir delegasyonun yararlı olduğu başka bir durum da, hızlı yol optimizasyonu uyguladığınız ve önbelleğe alınmış bir görevi döndürmek istediğiniz de durumdur.

## <a name="workloads"></a>İş yükleri
TAP yöntemleri olarak hem bilgisayara bağlı hem de G/Ç bağlı eşzamanlı işlemleri uygulayabilirsiniz. Ancak, TAP yöntemleri bir kitaplıktan herkese açık olduğunda, bunlar yalnızca G/Ç'ye bağlı işlemleri içeren iş yükleri için sağlanmalıdır (bunlar hesaplama da içerebilir, ancak tamamen hesaplamalı olmamalıdır). Bir yöntem tamamen bilgisayara bağlıysa, yalnızca eşzamanlı bir uygulama olarak ortaya konmalıdır. Bunu tüketen kod, daha sonra işi başka bir iş parçacığına boşaltmak veya paralellik elde etmek için bu senkron yöntemin bir çağrısını bir göreve sarıp sarmamayı seçebilir. Ve bir yöntem I/O'ya bağlıysa, yalnızca eşzamanlı bir uygulama olarak ortaya konmalıdır.

### <a name="compute-bound-tasks"></a>İşleme bağlı görevler
Sınıf, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> hesaplama lı yoğun işlemleri temsil etmek için idealdir. Varsayılan olarak, verimli yürütme sağlamak <xref:System.Threading.ThreadPool> için sınıf içinde özel destek yararlanır ve aynı zamanda ne zaman, nerede ve nasıl asynchronous hesaplamaları yürütmek üzerinde önemli denetim sağlar.

İşleme bağlı görevleri aşağıdaki yollarla oluşturabilirsiniz:

- .NET Framework 4'te, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bir temsilcinin (genellikle bir <xref:System.Action%601> veya <xref:System.Func%601>a) eş eşit olarak yürütülmesini kabul eden yöntemi kullanın. Bir <xref:System.Action%601> temsilci sağlarsanız, yöntem <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> bu temsilcinin eşzamanlı yürütmesini temsil eden bir nesne döndürür. Bir <xref:System.Func%601> temsilci sağlarsanız, yöntem <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> bir nesneyi döndürür. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> Yöntemin aşırı yükleri, görevin<xref:System.Threading.CancellationToken>zamanlaması ve<xref:System.Threading.Tasks.TaskCreationOptions>yürütülmesi üzerinde ayrıntılı denetim<xref:System.Threading.Tasks.TaskScheduler>sağlayan bir iptal belirteci (), görev oluşturma seçeneklerini ( ve görev zamanlayıcısını ( ) kabul eder. Geçerli görev zamanlayıcısı hedefleyen bir fabrika örneği<xref:System.Threading.Tasks.Task.Factory%2A> <xref:System.Threading.Tasks.Task> sınıfın statik özelliği ( ) olarak kullanılabilir; örneğin: `Task.Factory.StartNew(…)`.

- .NET Framework 4.5 ve sonraki sürümlerde (.NET Core ve .NET Standardı dahil), statik <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>'nin kısaltması olarak kullanın. İş parçacığı <xref:System.Threading.Tasks.Task.Run%2A> havuzunu hedefleyen bir işlem bağlı görevi kolayca başlatmak için kullanabilirsiniz. .NET Framework 4.5 ve sonraki sürümlerinde, bu işlem bağlı bir görev başlatmak için tercih edilen mekanizmadır. Yalnızca `StartNew` görev üzerinde daha ince taneli denetim istediğinizde doğrudan kullanın.

- Görevi ayrı ayrı oluşturmak `Task` ve `Start` zamanlamak istiyorsanız, tür veya yöntemin oluşturucularını kullanın. Ortak yöntemleryalnızca zaten başlatılmış görevleri döndürmelidir.

- Yöntemin <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> aşırı yüklerini kullanın. Bu yöntem, başka bir görev tamamlandığında zamanlanan yeni bir görev oluşturur. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Bazı aşırı yüklemeler, devam etme görevinin zamanlaması ve yürütülmesi üzerinde daha iyi denetim için bir iptal belirteci, devam seçenekleri ve görev zamanlayıcısı kabul eder.

- Yöntemleri <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemlerini kullanın. Bu yöntemler, sağlanan görevlerin tümü veya herhangi biri tamamlandığında zamanlanan yeni bir görev oluşturur. Bu yöntemler, bu görevlerin zamanlanması ve yürütülmesini denetlemek için aşırı yüklemeler de sağlar.

İşleme bağlı görevlerde, sistem, görevi çalıştırmaya başlamadan önce bir iptal isteği alırsa zamanlanan bir görevin yürütülmesini engelleyebilir. Bu nedenle, bir iptal belirteci (nesne)<xref:System.Threading.CancellationToken> sağlarsanız, bu belirteci belirteçleri izleyen eşzamanlı koda geçirebilirsiniz. Belirteci, `Task` çalışma zamanının belirteci de izleyebilecek `StartNew` `Run` şekilde daha önce bahsedilen yöntemlerden birine de sağlayabilirsiniz.

Örneğin, görüntüyü işleyen bir eşzamanlı yöntem düşünün. Görevin gövdesi, işleme sırasında bir iptal isteği geldiğinde kodun erken çıkabilmesi için iptal belirteciyle anket yapabilir. Ayrıca, işleme başlamadan önce iptal isteği gelirse, işleme işlemini engellemek isteyebilirsiniz:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Aşağıdaki koşullardan en az <xref:System.Threading.Tasks.TaskStatus.Canceled> biri doğruysa, hesaplamaya bağlı görevler bir durumda sona erer:

- Bir iptal isteği, <xref:System.Threading.CancellationToken> görev <xref:System.Threading.Tasks.TaskStatus.Running> duruma geçmeden önce oluşturma yöntemine (örneğin `StartNew` `Run`veya) bağımsız değişken olarak sağlanan nesne üzerinden gelir.

- Bir <xref:System.OperationCanceledException> özel durum böyle bir görevin gövdesi içinde işlenmemiş olur, bu özel durum göreve geçirilen aynı <xref:System.Threading.CancellationToken> içerir ve bu belirteç iptal istendiğini gösterir.

Görevin gövdesi içinde başka bir özel durum işlenmezse, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumda sona erer ve görevüzerinde bekleme veya sonucuna erişme girişimleri bir özel durum atılmasına neden olur.

### <a name="io-bound-tasks"></a>G/Ç'ye bağlı görevler
Yürütmesinin tamamı için iş parçacığı tarafından doğrudan yedeklenmemesi gereken bir görev <xref:System.Threading.Tasks.TaskCompletionSource%601> oluşturmak için türü kullanın. Bu tür ilişkili <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> <xref:System.Threading.Tasks.Task%601> bir örnek döndürür bir özellik ortaya çıkarır. Bu görevin yaşam döngüsü, <xref:System.Threading.Tasks.TaskCompletionSource%601> , <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>, , `TrySet` ve bunların türevleri gibi yöntemlerle kontrol edilir.

Belirli bir süre sonra tamamlanacak bir görev oluşturmak istediğinizi varsayalım. Örneğin, kullanıcı arabirimindeki bir etkinliği geciktirmek isteyebilirsiniz. Sınıf <xref:System.Threading.Timer?displayProperty=nameWithType> zaten belirli bir süre sonra bir temsilciyi eş zamanlı olarak çağırma <xref:System.Threading.Tasks.TaskCompletionSource%601> olanağı sağlar <xref:System.Threading.Tasks.Task%601> ve kullanarak zamanlayıcıya bir ön koyabilirsiniz, örneğin:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

.NET Framework 4.5 ile <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> başlayarak, yöntem bu amaç için sağlanır ve başka bir eşzamanlı yöntem içinde kullanabilirsiniz, örneğin, bir eşzamanlı yoklama döngüsü uygulamak için:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

Sınıfın <xref:System.Threading.Tasks.TaskCompletionSource%601> genel olmayan bir karşılığı yok. Ancak, <xref:System.Threading.Tasks.Task%601> türetilmiştir <xref:System.Threading.Tasks.Task>, böylece yalnızca <xref:System.Threading.Tasks.TaskCompletionSource%601> bir görevi döndüren G/Ç bağlı yöntemler için genel nesneyi kullanabilirsiniz. Bunu yapmak için, bir kukla `TResult` ile bir<xref:System.Boolean> kaynak kullanabilirsiniz (iyi bir varsayılan seçimdir, <xref:System.Threading.Tasks.Task> ancak bir downcasting kullanıcı hakkında endişeleriniz varsa <xref:System.Threading.Tasks.Task%601>, bunun yerine özel `TResult` bir tür kullanabilirsiniz). Örneğin, önceki `Delay` örnekteki yöntem, elde edilen ofset (`Task<DateTimeOffset>`ile birlikte geçerli saati döndürür. Böyle bir sonuç değeri gereksizse, yöntem bunun yerine aşağıdaki gibi kodlanabilir (dönüş türü <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>değişikliği ve bağımsız değişken değişikliği not):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Karışık işlem bağlı ve G/Ç bağlı görevler
Eşzamanlı yöntemler yalnızca bilgisayara bağlı veya G/Ç bağlı işlemlerle sınırlı değildir, ancak ikisinin bir karışımını temsil edebilir. Aslında, birden çok eşzamanlı işlem genellikle daha büyük karma operasyonlarda birleştirilir. Örneğin, önceki bir örnekte gösterilen `RenderAsync` yöntemi, bazı giriş `imageData` verilerine göre bir resmi işlemek için yoğun bir hesaplama işlem gerçekleştirdi. Bu, `imageData` eşit olarak erişebildiğiniz bir web hizmetinden gelebilir:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Bu örnek, tek bir iptal belirteci birden fazla eşzamanlı işlem yoluyla iş parçacığı olabilir nasıl gösterir. Daha fazla bilgi için, [Görev Tabanlı Asynchronous Deseni'ni Tüketme'deki](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)iptal kullanım bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
