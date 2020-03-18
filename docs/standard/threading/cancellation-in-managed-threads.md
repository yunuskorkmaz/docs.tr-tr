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
ms.openlocfilehash: d4bbf30923d65ad7aeced80efa626136ae27491b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138134"
---
# <a name="cancellation-in-managed-threads"></a>Yönetilen İş Parçacıklarında İptal
.NET Framework 4'ten başlayarak,.NET Framework, eşzamanlı veya uzun süreli senkron işlemlerin birlikte iptali için birleşik bir model kullanır. Bu model, iptal jetonu adı verilen hafif bir nesneye dayanır. Örneğin yeni iş parçacıkları veya görevler oluşturarak bir veya daha fazla iptal edilebilir işlemi çağıran nesne, belirteci her işlemiçin geçirir. Tek tek işlemler sırayla belirteç kopyalarını diğer işlemlere geçirebilir. Daha sonra, belirteci oluşturan nesne, işlemlerin ne yaptığını durdurmasını istemek için bunu kullanabilir. İptal isteğini yalnızca isteyen nesne verebilir ve her dinleyici isteği fark etmekten ve uygun ve zamanında yanıt vermekten sorumludur.  
  
 Kooperatif iptal modelinin uygulanması için genel model:  
  
- Bireysel iptal jetonlarını yöneten ve iptal bildirimi gönderen bir <xref:System.Threading.CancellationTokenSource> nesneyi anında belirtin.  
  
- <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> Özellik tarafından döndürülen belirteci iptal idinleyen her görev veya iş parçacığına geçirin.  
  
- İptal işlemine yanıt vermek için her görev veya iş parçacığı için bir mekanizma sağlayın.  
  
- İptal <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> bildirimisağlamak için yöntemi arayın.  
  
> [!IMPORTANT]
> <xref:System.Threading.CancellationTokenSource> sınıfı, <xref:System.IDisposable> arabirimini uygular. Sahip olduğu yönetilmeyen <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> kaynakları serbest etmek için iptal belirteci kaynağını kullanmayı bitirdiğinizde yöntemi aradığından emin olmalısınız.  
  
 Aşağıdaki resimde, bir belirteç kaynağı ile belirtecinin tüm kopyaları arasındaki ilişki gösterilmektedir.  
  
 ![İptalTokenSource ve iptal jetonları](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Yeni iptal modeli, iptale duyarlı uygulamalar ve kitaplıklar oluşturmayı kolaylaştırır ve aşağıdaki özellikleri destekler:  
  
- İptal kooperatif ve dinleyici üzerinde zorlanmaz. Dinleyici, iptal isteğine yanıt olarak nasıl zarif bir şekilde sonlandırılaca karar verirse.  
  
- İsteme dinlemekten farklıdır. İptal edilebilir bir işlemi çağıran bir nesne, iptalin ne zaman (eğer hiç) istendiğini denetleyebilir.  
  
- İstenen nesne, yalnızca bir yöntem çağrısı kullanarak belirteci tüm kopyaları için iptal isteği sorunları.  
  
- Dinleyici, birden çok belirteçleri aynı anda *bir bağlantılı belirteç*içine birleştirerek dinleyebilirsiniz.  
  
- Kullanıcı kodu, kütüphane kodundan gelen iptal isteklerini fark edebilir ve yanıtlayabilir ve kitaplık kodu kullanıcı kodundan gelen iptal isteklerini fark edebilir ve yanıtlayabilir.  
  
- Dinleyiciler, yoklama, geri arama kaydı veya bekleme tutamaçlarını bekleyerek iptal isteklerihakkında bilgilendirilebilir.  
  
## <a name="cancellation-types"></a>İptal Türleri  
 İptal çerçevesi, aşağıdaki tabloda listelenen ilgili türler kümesi olarak uygulanır.  
  
|Tür adı|Açıklama|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|İptal belirteci oluşturan ve aynı zamanda bu belirtecitüm kopyaları için iptal isteği veren nesne.|  
|<xref:System.Threading.CancellationToken>|Hafif değer türü, genellikle yöntem parametresi olarak bir veya daha fazla dinleyiciye aktarılır. Dinleyiciler, yoklama, `IsCancellationRequested` geri arama veya bekleme tutamacı ile belirteç özelliğinin değerini izler.|  
|<xref:System.OperationCanceledException>|Bu özel durum oluşturucusu aşırı <xref:System.Threading.CancellationToken> yükleri bir parametre olarak kabul eder. Dinleyiciler isteğe bağlı olarak iptalin kaynağını doğrulamak ve iptal isteğine yanıt verdiğini başkalarına bildirmek için bu özel durumu atabilir.|  
  
 Yeni iptal modeli .NET Framework'e çeşitli türlerde entegre edilmiştir. En önemlileri <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Bu yeni iptal modelini tüm yeni kitaplık ve uygulama kodu için kullanmanızı öneririz.  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnekte, isteyen nesne bir <xref:System.Threading.CancellationTokenSource> nesne oluşturur ve <xref:System.Threading.CancellationTokenSource.Token%2A> sonra özelliğini iptal edilebilir işlem için geçirir. İstek alan işlem, belirteç özelliğinin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> değerini yoklama ile izler. Değer olduğunda, `true`dinleyici uygun olan şekilde sonlandırAbilir. Bu örnekte, yöntem sadece çıkar, birçok durumda gerekli olan tüm.  
  
> [!NOTE]
> Örnek, yeni <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> iptal çerçevesinin eski API'lerle uyumlu olduğunu göstermek için yöntemi kullanır. Yeni, tercih edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü kullanan bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>İşlem İptali Karşı Nesne İptali  
 Yeni iptal çerçevesinde, iptal işlemleri değil, nesneleri ifade eder. İptal isteği, gerekli temizleme yapıldıktan sonra işlemin mümkün olan en kısa sürede durdurulması gerektiği anlamına gelir. Bir iptal belirteci bir "iptal edilebilir işlem" anlamına gelir, ancak bu işlem programınızda uygulanabilir. Belirteci <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği ayarlandıktan sonra `true`, 'ye `false`sıfırlanamaz. Bu nedenle, iptal belirteçleri iptal edildikten sonra yeniden kullanılamaz.  
  
 Nesne iptal mekanizmasına ihtiyacınız varsa, aşağıdaki örnekte gösterildiği gibi <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> yöntemi çağırarak işlem iptal mekanizmasına dayandırabilirsiniz.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Bir nesne birden fazla eşzamanlı iptal işlemi destekliyorsa, her ayrı iptal işlemi için giriş olarak ayrı bir belirteç geçirin. Bu şekilde, bir işlem diğerlerini etkilemeden iptal edilebilir.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>İptal İsteklerini Dinleme ve Yanıtlama  
 Kullanıcı temsilcisinde, iptal edilebilir bir işlemin uygulayıcısı, iptal isteğine yanıt olarak işlemi nasıl sonlandıracağını belirler. Çoğu durumda, kullanıcı temsilcisi gerekli herhangi bir temizleme gerçekleştirebilir ve hemen geri dönebilir.  
  
 Ancak, daha karmaşık durumlarda, kullanıcı temsilcisinin iptal in gerçekleştiğini kitaplık koduna bildirmesi gerekebilir. Bu gibi durumlarda, işlemi sonlandırmanın doğru yolu, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>temsilcinin , yöntemi <xref:System.OperationCanceledException> çağırmasıdır ve bu da bir işlemin atılmasına neden olur. Kitaplık kodu, kullanıcı temsilci iş parçacığında bu özel durumu yakalayabilir ve özel durumun kooperatif iptalini mi yoksa başka bir istisnadurumu mu gösterdiğini belirlemek için özel durumun belirteci'ni inceleyebilir.  
  
 Sınıf <xref:System.Threading.Tasks.Task> bu <xref:System.OperationCanceledException> şekilde işler. Daha fazla bilgi için [Görev İptal'e](../../../docs/standard/parallel-programming/task-cancellation.md)bakın.  
  
### <a name="listening-by-polling"></a>Yoklama ile Dinleme  
 Döngü veya recurse uzun soluklu hesaplamalar için, düzenli aralıklarla <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> özelliğin değerini yoklama tarafından bir iptal isteği için dinleyebilirsiniz. Değeri ise, `true`yöntem temizlemek ve mümkün olduğunca çabuk sona erdirmek gerekir. En uygun yoklama sıklığı uygulama türüne bağlıdır. Herhangi bir program için en iyi yoklama sıklığını belirlemek geliştiriciye bağlıdır. Yoklamanın kendisi performansı önemli ölçüde etkilemez. Aşağıdaki örnek, anket için olası bir yolu gösterir.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Daha eksiksiz bir örnek için [bkz: Yoklama ile İptal İsteklerini Dinleyin.](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md)  
  
### <a name="listening-by-registering-a-callback"></a>Geri Arama Kaydederek Dinleme  
 Bazı işlemler, iptal jetonunun değerini zamanında kontrol edemeyecek şekilde engellenebilir. Bu gibi durumlarda, iptal isteği geldiğinde yöntemin engelini iptal eden bir geri arama yöntemi kaydedebilirsiniz.  
  
 Yöntem, <xref:System.Threading.CancellationToken.Register%2A> bu <xref:System.Threading.CancellationTokenRegistration> amaç için özel olarak kullanılan bir nesneyi döndürür. Aşağıdaki örnekte, eşzamanlı <xref:System.Threading.CancellationToken.Register%2A> bir Web isteğini iptal etmek için yöntemin nasıl kullanılacağı gösterilmektedir.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 Nesne <xref:System.Threading.CancellationTokenRegistration> iş parçacığı eşitlemesini yönetir ve geri aramanın tam bir zamanda yürütmeyi durdurmasını sağlar.  
  
 Sistem yanıt verme yi sağlamak ve kilitlenmeleri önlemek için geri aramaları kaydederken aşağıdaki yönergelere uyulmalıdır:  
  
- Geri arama yöntemi, eşzamanlı olarak çağrıldığı için hızlı olmalıdır <xref:System.Threading.CancellationTokenSource.Cancel%2A> ve bu nedenle geri arama geri dönene kadar geri dönmez.  
  
- Geri arama <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> çalışırken ararsanız ve geri aramanın beklediği bir kilidi tutarsanız, programınız kilitlenebilir. İadelerden sonra, `Dispose` geri arama nın gerektirdiği tüm kaynakları serbest kullanabilirsiniz.  
  
- Geri aramalar, geri aramada <xref:System.Threading.SynchronizationContext> herhangi bir el ile iş parçacığı veya kullanım gerçekleştirmemelidir. Bir geri aramabelirli bir iş parçacığı <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> üzerinde çalışması gerekiyorsa, hedef eşitleme Bağlamı etkin <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>olduğunu belirtmenizi sağlayan oluşturucu kullanın. Geri aramada el ile iş parçacığı gerçekleştirmek kilitlenmeye neden olabilir.  
  
 Daha eksiksiz bir örnek için [bkz: İptal İstekleri için Geri Aramaları Kaydetme](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Bekleme Tutamacı Kullanarak Dinleme  
 İptal edilebilir bir işlem, bir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> veya , <xref:System.Threading.Semaphore?displayProperty=nameWithType>işlem hem olay hem de iptal <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> isteği beklemek etkinleştirmek için özelliği kullanabilirsiniz gibi bir eşitleme ilkel beklerken engelleyebilir. İptal belirteci bekleme kolu, bir iptal isteğine yanıt olarak sinyal verecektir ve <xref:System.Threading.WaitHandle.WaitAny%2A> yöntem, sinyal veren iptal belirteci olup olmadığını belirlemek için yöntemin dönüş değerini kullanabilir. İşlem daha sonra sadece çıkmak, <xref:System.OperationCanceledException>ya da bir atmak , uygun olarak.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 .NET Framework 4'e yönelik <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> yeni <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> kodda ve her `Wait` ikisi de yöntemleriyle yeni iptal çerçevesini destekler. <xref:System.Threading.CancellationToken> Yönteme geçebilirsiniz ve iptal istendiğinde, olay uyanır ve bir <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Daha eksiksiz bir örnek için [bkz: Bekleme Tutamaçları olan İptal İsteklerini Dinleyin.](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md)  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Birden Çok Belirteçleri Aynı Anda Dinleme  
 Bazı durumlarda, dinleyici aynı anda birden çok iptal belirteçleri dinlemek zorunda kalabilir. Örneğin, iptal edilebilir bir işlemin, yöntem parametresine bağımsız değişken olarak dışarıdan geçirilen bir belirteç ek olarak dahili iptal belirteci izlemek zorunda kalabilir. Bunu gerçekleştirmek için, aşağıdaki örnekte gösterildiği gibi, iki veya daha fazla belirteçleri bir araya getirebilecek bağlantılı bir belirteç kaynağı oluşturun.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Bu işi bitirdiğinizde bağlantılı jeton kaynağını aramanız `Dispose` gerektiğine dikkat edin. Daha eksiksiz bir örnek için [bkz: Birden Çok İptal İsteği'ni Dinleyin.](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md)  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Kütüphane Kodu ve Kullanıcı Kodu Arasındaki İşbirliği  
 Birleştirilmiş iptal çerçevesi, kitaplık kodunun kullanıcı kodunu iptal etmesini ve kullanıcı kodunun kitaplık kodunu işbirliği içinde iptal etmesini mümkün kılar. Sorunsuz işbirliği, aşağıdaki yönergeleri izleyerek her iki tarafa da bağlıdır:  
  
- Kitaplık kodu iptal edilebilir işlemler sağlıyorsa, kullanıcı kodunun iptal talebinde bulunabilmesi için harici bir iptal belirteci kabul eden genel yöntemler de sağlamalıdır.  
  
- Kitaplık kodu kullanıcı koduna çağrı gerektiriyorsa, kitaplık kodu bir OperationCanceledException'ı (harici Token) *işbirliği iptali*olarak yorumlamalıdır ve mutlaka bir hata istisnası olarak yorumlamalıdır.  
  
- Kullanıcı temsilcileri, kitaplık kodundan gelen iptal isteklerini zamanında yanıtlamaya çalışmalıdır.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> bu yönergeleri izleyen sınıflara örneklerdir. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılacağını görün: PLINQ Sorgusu'nun iptali.](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
