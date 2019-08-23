---
title: Yönetilen İş Parçacıklarında İptal
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e39ee597f5142f2b3ccbd4ded49e59d6700ec8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960137"
---
# <a name="cancellation-in-managed-threads"></a>Yönetilen İş Parçacıklarında İptal
.NET Framework 4 ' te başlayarak, .NET Framework zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler için bir birleştirilmiş model kullanır. Bu model, iptal belirteci adlı hafif bir nesneyi temel alır. Bir veya daha fazla iptal edilebilen işlemi çağıran nesne (örneğin, yeni iş parçacıkları veya görevler oluşturarak) belirteci her bir işleme geçirir. Tek tek işlemler, belirtecin kopyalarını diğer işlemlere geçirebilir. Daha sonra, belirteci oluşturan nesne, işlemin ne yaptığını durdurmasını istemek için bunu kullanabilir. Yalnızca istenen nesne iptal isteğini verebilir ve her dinleyici, isteği yaşıyorsanız ve uygun ve zamanında yanıt verecek şekilde sorumludur.  
  
 Birlikte çalışırken iptal modelinin uygulanması için genel bir örüntü şunlardır:  
  
- Ayrı ayrı <xref:System.Threading.CancellationTokenSource> iptal belirteçlerine yönelik iptali bildirimini yöneten ve gönderen bir nesne örneği oluşturur.  
  
- <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> Özelliği tarafından döndürülen belirteci, iptal için dinleyen her bir göreve veya iş parçacığına geçirin.  
  
- Her görev veya iş parçacığının iptaline yanıt vermesi için bir mekanizma sağlar.  
  
- İptal bildirimi sağlamak için yönteminiçağırın.<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>  
  
> [!IMPORTANT]
> <xref:System.Threading.CancellationTokenSource> Sınıfı ,<xref:System.IDisposable> arabirimini uygular. Tuttuğu yönetilmeyen kaynakları serbest bırakmak için İptal <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> belirteci kaynağını kullanmayı bitirdiğinizde yöntemini çağırmanız gerekir.  
  
 Aşağıdaki çizimde, belirteç kaynağı ve belirtecinin tüm kopyalarından oluşan ilişki gösterilmektedir.  
  
 ![CancellationTokenSource ve iptal belirteçleri](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Yeni iptal modeli, iptal kullanan uygulamalar ve kitaplıklar oluşturmayı kolaylaştırır ve aşağıdaki özellikleri destekler:  
  
- İptal etme birlikte çalışır ve dinleyicide zorlanmaz. Dinleyici, bir iptal isteğine yanıt olarak düzgün bir şekilde nasıl sonlandırıldığını belirler.  
  
- İstek, dinlemeye göre farklıdır. İptal edilebilen bir işlemi çağıran bir nesne, (varsa) iptalinin ne zaman istenmediğini denetleyebilir.  
  
- İstekte bulunan nesne, yalnızca bir yöntem çağrısı kullanarak, iptal isteğini belirtecin tüm kopyalarına yayınlar.  
  
- Bir dinleyici, tek bir *bağlı belirtece*katılarak birden fazla belirteci aynı anda dinleyebilir.  
  
- Kullanıcı kodu kitaplık kodundan gelen iptal isteklerini fark edebilir ve yanıtlayabilir ve kitaplık kodu kullanıcı kodundan gelen iptal isteklerini görebilir ve bunlara yanıt verebilir.  
  
- Dinleyiciler yoklamaya, geri çağırma kaydına veya bekleme tanıtıcılarını beklemeye göre iptal istekleri hakkında bildirim alabilir.  
  
## <a name="cancellation-types"></a>İptal türleri  
 İptal çerçevesi, aşağıdaki tabloda listelenen ilgili türler kümesi olarak uygulanır.  
  
|Tür adı|Açıklama|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|İptal belirteci oluşturan ve ayrıca söz konusu belirtecin tüm kopyalarının iptal isteğini veren nesne.|  
|<xref:System.Threading.CancellationToken>|Hafif değer türü, genellikle yöntem parametresi olarak bir veya daha fazla dinleyicilerine geçirildi. Dinleyiciler, belirteç `IsCancellationRequested` özelliğinin değerini yoklama, geri çağırma veya bekleme tanıtıcısıyla izler.|  
|<xref:System.OperationCanceledException>|Bu özel durumun oluşturucusunun aşırı yüklemeleri parametre olarak <xref:System.Threading.CancellationToken> bir parametresini kabul eder. Bu özel durum, İptalin kaynağını doğrulamak ve diğer kullanıcılara bir iptal isteğine yanıt verdiğini bildirmek için isteğe bağlı olarak bu özel durumu oluşturabilir.|  
  
 Yeni iptal modeli, .NET Framework çeşitli türlerde tümleştirilir. En <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>önemli olanlar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ,ve<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>'dir. <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> Tüm yeni kitaplık ve uygulama kodu için bu yeni iptal modelini kullanmanızı öneririz.  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnekte, istenen nesne bir <xref:System.Threading.CancellationTokenSource> nesne oluşturur ve sonra <xref:System.Threading.CancellationTokenSource.Token%2A> özelliğini iptal edilebilen işleme geçirir. İsteği alan işlem, belirteç <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğinin değerini yoklayarak izler. Değer ne olursa olsun `true`, dinleyici uygun şekilde sonlandırılır. Bu örnekte, yöntemi birçok durumda gerekli olan tek çıkar.  
  
> [!NOTE]
> Örnek, yeni iptal <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> çerçevesinin eski API 'lerle uyumlu olduğunu göstermek için yöntemini kullanır. Yeni ve tercih edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü kullanan bir örnek için bkz [. nasıl yapılır: Bir görevi ve alt öğelerini](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)iptal edin.  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>İşlem Iptali ve nesne Iptaline karşı  
 Yeni iptal çerçevesinde, iptal, nesneleri değil, işlemler anlamına gelir. İptal isteği, gerekli temizleme gerçekleştirildikten sonra işlemin en kısa sürede durması gerektiği anlamına gelir. Bir iptal belirtecinin "iptal edilebilen işlem" öğesine başvurması gerekir, ancak bu işlem programınızda uygulanabilir. Belirtecinin özelliği olarak `true`ayarlandıktan sonra, ' a sıfırlanamaz `false`. <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Bu nedenle, iptal belirteçleri iptal edildikten sonra yeniden kullanılamaz.  
  
 Bir nesne iptali mekanizmasına ihtiyacınız varsa, aşağıdaki örnekte gösterildiği gibi <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> yöntemini çağırarak işlem iptali mekanizmasına temel alabilirsiniz.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Bir nesne birden fazla eşzamanlı iptal edilebilen işlemi destekliyorsa, ayrı bir iptal edilebilen her işlem için ayrı bir belirteç girişi olarak geçirin. Bu şekilde, bir işlem diğerleri etkilenmeden iptal edilebilir.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Iptal Isteklerini dinleme ve yanıtlama  
 Kullanıcı temsilcisinde, iptal edilebilen bir işlemin uygulayıcısı bir iptal isteğine yanıt olarak işlemin nasıl sonlandırıldığını belirler. Çoğu durumda, kullanıcı temsilcisi gerekli temizleme işlemini gerçekleştirebilir ve hemen geri dönebilir.  
  
 Bununla birlikte, daha karmaşık durumlarda, kullanıcı temsilcisinin iptal eden kitaplık kodunu bildirmesi gerekebilir. Bu gibi durumlarda, işlemi sonlandırmak için doğru yol, bir <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> <xref:System.OperationCanceledException> , oluşturulmasına neden olacak şekilde temsilcinin, yöntemini çağırmasına yöneliktir. Kitaplık kodu, kullanıcı temsilcisi iş parçacığında bu özel durumu yakalayabilir ve özel durumun, ortak iptali mi yoksa başka bir özel durum mi olduğunu anlamak için özel durumun belirtecini inceleyebilirsiniz.  
  
 Sınıfı bu şekilde <xref:System.OperationCanceledException>işler. <xref:System.Threading.Tasks.Task> Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Yoklamayla dinleme  
 Döngü veya recurse sağlayan uzun süre çalışan hesaplamalar için, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> özelliğin değerini düzenli aralıklarla yoklayarak bir iptal isteği dinleyebilirsiniz. Değeri ise `true`, yöntemin en kısa sürede temizlenmesi ve sonlandırılması gerekir. En iyi yoklama sıklığı, uygulamanın türüne bağlıdır. Bu, belirli bir program için en iyi yoklama sıklığını belirlemede geliştiriciye yöneliktir. Yoklama, performansı önemli ölçüde etkilemez. Aşağıdaki örnekte, yoklamaya yönelik olası bir yol gösterilmektedir.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Daha kapsamlı bir örnek için bkz [. nasıl yapılır: Yoklayarak](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md)iptal isteklerini dinleyin.  
  
### <a name="listening-by-registering-a-callback"></a>Geri çağırma kaydederek dinleme  
 Bazı işlemler, iptal belirtecinin değerini zamanında denetlenebilmeleri için bu şekilde engellenmiş hale gelebilir. Bu gibi durumlarda, bir iptal isteği alındığında yöntemini engelleyen bir geri çağırma yöntemi kaydedebilirsiniz.  
  
 Yöntemi <xref:System.Threading.CancellationToken.Register%2A> , bu amaçla <xref:System.Threading.CancellationTokenRegistration> özel olarak kullanılan bir nesne döndürür. Aşağıdaki örnek, zaman uyumsuz bir web isteğini <xref:System.Threading.CancellationToken.Register%2A> iptal etmek için yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 Nesnesi <xref:System.Threading.CancellationTokenRegistration> , iş parçacığı eşitlemesini yönetir ve geri aramanın yürütme işlemini zaman içinde kesin bir noktada durdurmasını sağlar.  
  
 Sistem yanıt verdiğini sağlamak ve kilitlenmeleri önlemek için geri çağrılar kaydedilirken aşağıdaki yönergelerin izlenmesi gerekir:  
  
- Geri arama yöntemi, zaman uyumlu olarak çağrıldığı ve bu nedenle çağrısı geri çağırma görünene kadar <xref:System.Threading.CancellationTokenSource.Cancel%2A> döndürülmediği için hızlı olmalıdır.  
  
- Geri çağırma sırasında <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> çağrı yaparsanız ve geri aramanın beklediği bir kilit tutarsanız, programınız kilitlenebilir. Geri `Dispose` döndüğünde, geri çağırma için gereken tüm kaynakları serbest bırakabilirsiniz.  
  
- Geri çağrılar hiçbir el ile iş parçacığı veya <xref:System.Threading.SynchronizationContext> bir geri aramada kullanım gerçekleştirmemelidir. Belirli bir iş parçacığında bir geri çağırma çalışması gerekiyorsa, hedef syncContext 'in etkin <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>olduğunu belirtmenize olanak sağlayan oluşturucuyu kullanın. Bir geri aramada el ile iş parçacığı gerçekleştirmek kilitlenmeye neden olabilir.  
  
 Daha kapsamlı bir örnek için bkz [. nasıl yapılır: Iptal Istekleri](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md)için geri çağırmaları kaydedin.  
  
### <a name="listening-by-using-a-wait-handle"></a>Bekleme tutamacı kullanarak dinleme  
 İptal edilebilen bir işlem <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> <xref:System.Threading.Semaphore?displayProperty=nameWithType>, veya gibi bir eşitleme temel aldığı sırada engelleyebilen zaman, işlemin hem olay hem de iptal isteğinde beklemesini sağlamak için özelliğinikullanabilirsiniz.<xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> İptal belirtecinin bekleme tutamacı bir iptal isteğine yanıt olarak sinyal verecektir ve yöntemi, sinyal döndüren iptal belirteci olup olmadığını anlamak için <xref:System.Threading.WaitHandle.WaitAny%2A> yönteminin dönüş değerini kullanabilir. İşlem daha sonra yalnızca çıkabilir veya uygun şekilde bir <xref:System.OperationCanceledException>oluşturabilir.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 .NET Framework 4 ' ü hedefleyen yeni kodda, <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> her ikisi de `Wait` yöntemlerinde yeni iptal çerçevesini destekler. Yöntemine geçirebilirsiniz <xref:System.Threading.CancellationToken> ve iptal istendiğinde olay uyandırır ve bir <xref:System.OperationCanceledException>oluşturur.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Daha kapsamlı bir örnek için bkz [. nasıl yapılır: Bekleyen tutamaçları](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md)olan iptal isteklerini dinleyin.  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Aynı anda birden çok belirtece dinleme  
 Bazı durumlarda, bir dinleyicinin aynı anda birden fazla iptal belirtecini dinlemesi gerekebilir. Örneğin, bir iptal edilebilen işlemin, dışarıdan bir yöntem parametresine bağımsız değişken olarak geçirilen bir belirtece ek olarak iç iptal belirtecini izlemesi gerekebilir. Bunu gerçekleştirmek için, aşağıdaki örnekte gösterildiği gibi, iki veya daha fazla belirteci bir belirtece birleştiren bağlantılı bir belirteç kaynağı oluşturun.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 İle işiniz bittiğinde bağlantılı belirteç `Dispose` kaynağını çağırmanız gerektiğini unutmayın. Daha kapsamlı bir örnek için bkz [. nasıl yapılır: Birden çok Iptal Isteğini](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md)dinleyin.  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Kitaplık kodu ve Kullanıcı kodu arasındaki ortak işlem  
 Birleşik iptal çerçevesi, kitaplık kodunun Kullanıcı kodunu iptal etmelerini ve kullanıcı kodunun kitaplık kodunu birlikte iptal edebilmesini sağlar. Kesintisiz birlikte işlem, aşağıdaki yönergelerin ardından her bir tarafa bağlıdır:  
  
- Kitaplık kodu iptal edilebilen işlemler sağlıyorsa, kullanıcı kodunun iptali istemesi için bir dış iptal belirtecini kabul eden ortak yöntemler de sağlamalıdır.  
  
- Kitaplık kodu kullanıcı koduna çağırırsa, kitaplık kodu bir Operationolaydexception (externalToken) ile *birlikte işlem iptali*olarak yorumlanmalıdır ve hata özel durumu olarak değildir.  
  
- Kullanıcı temsilcileri, kitaplık kodundaki iptal isteklerini zamanında yanıtlamayı denemelidir.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> bu yönergeleri izleyen sınıfların örnekleridir. Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: PLıNQ sorgusunu](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)iptal edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
