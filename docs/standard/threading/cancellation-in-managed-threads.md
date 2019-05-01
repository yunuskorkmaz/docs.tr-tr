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
ms.openlocfilehash: ca42512daa35d7efd7296c277a575bf131749ad2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795061"
---
# <a name="cancellation-in-managed-threads"></a>Yönetilen İş Parçacıklarında İptal
İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework, ortak iptali zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler için birleşik bir modeli kullanır. Bu model, bir iptal belirteci adlı basit bir nesne üzerinde temel alır. Yeni iş parçacıkları veya görevleri oluşturarak iptal edilebilir işlemleri, bir veya daha fazla örneğin çağıran nesnesi belirteç her işlem için iletir. Tek işlemler, diğer işlemler için belirteç kopyalarını sırayla geçirebilirsiniz. Bazı daha sonraki bir zamanda belirteci oluşturan nesnesini bu işlemler neler yaptıklarını durdurma isteği için kullanabilirsiniz. İstekte bulunan nesne yalnızca iptal isteği gönderebilir ve her dinleyici isteği fark ve uygun ve hızlı bir şekilde yanıt sorumludur.  
  
 Ortak iptali modeli uygulamada genel düzen şöyledir:  
  
- Örneği bir <xref:System.Threading.CancellationTokenSource> nesne yöneten ve tek tek iptal belirteçleri iptal bildirimi gönderir.  
  
- Tarafından döndürülen belirtecin geçip <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> her görev veya iptal için bekleyen iş parçacığı özelliği.  
  
- Her görev veya iptal için yanıt vermek için iş parçacığı için bir mekanizma sağlar.  
  
- Çağrı <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> iptal bildirim sağlamak için yöntemi.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Sınıfının Implements <xref:System.IDisposable> arabirimi. Çağırdığınızdan emin olmalıdır <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> iptal belirteci kaynağı, tüm ücretsiz kullanmayı bitirdiğinizde yöntemi yönetilmeyen kaynakları da tutar.  
  
 Aşağıdaki çizimde, bir belirteç kaynağı ve onun belirteç tüm kopyalarını arasındaki ilişkiyi gösterir.  
  
 ![CancellationTokenSource ve iptal belirteçlerini](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Yeni iptal etme modeli iptal algılayan uygulamaları ve kitaplıkları oluşturmak kolaylaştırır ve aşağıdaki özellikleri destekler:  
  
- İptali ortaktır ve Dinleyicide zorunlu değildir. Dinleyici düzgün bir şekilde bir iptal isteğine yanıt olarak sonlandırmak nasıl belirler.  
  
- İsteyen dinleme yapması farklıdır. İptal edilebilir bir işlem çağıran bir nesne, ne zaman (Şimdiye kadar değilse) İptal işlemi istendikten kontrol edebilirsiniz.  
  
- İstenen nesne, yalnızca bir yöntem çağrısı kullanarak belirteç tüm kopyalarını iptal isteğini verir.  
  
- Dinleyici için birden çok belirteç aynı anda bunları birine katılarak dinleyebilirsiniz *bağlı belirteci*.  
  
- Kullanıcı kodu dikkat edin ve kitaplık koddan iptal isteklerini yanıtlamasını ve kitaplık kodu dikkat edin ve kullanıcı kodundan iptal isteklerini yanıtlamasını.  
  
- Dinleyiciler, yoklama, geri çağırma kaydı ya da bekleme tanıtıcıları üzerinde bekleyen iptal isteklerini bildirilebilir.  
  
## <a name="cancellation-types"></a>İptal türleri  
 İptal framework, aşağıdaki tabloda listelenen ilgili türleri kümesi olarak uygulanır.  
  
|Tür adı|Açıklama|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Bir iptal belirteci oluşturur ve ayrıca o belirteç tüm kopyalarını iptal isteği yayınlar nesne.|  
|<xref:System.Threading.CancellationToken>|Basit değer türü, bir veya daha fazla dinleyici, genellikle bir yöntem parametresi olarak geçirildi. Dinleyicileri izleme değerini `IsCancellationRequested` yoklama, geri çağırma ve bekleme tanıtıcısı tarafından belirteç özelliği.|  
|<xref:System.OperationCanceledException>|Bu özel durumun oluşturucusunu aşırı kabul bir <xref:System.Threading.CancellationToken> bir parametre olarak. Dinleyicileri isteğe bağlı olarak iptal nedeni doğrulamak ve diğerlerinin bir iptal isteğine yanıt verdi bildirmek için bu durum oluşturabilir.|  
  
 Yeni iptal etme modeli içinde tümleşik olarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] çeşitli türlerde. En önemli olanlardır <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Bu yeni iptal etme modeli için tüm yeni kitaplık ve uygulama kodu kullanmanızı öneririz.  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnekte, istekte bulunan nesneyi oluşturur bir <xref:System.Threading.CancellationTokenSource> nesne ve geçişleri kendi <xref:System.Threading.CancellationTokenSource.Token%2A> iptal edilebilir işleme özelliği. İsteği aldığında işlemi değerini izler <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> yoklama belirteç özelliği. Değer olduğunda `true`, uygun herhangi bir şekilde dinleyicinin sonlandırabilirsiniz. Bu örnekte, yöntem yalnızca, çoğu durumda gerekli olduğu çıkar.  
  
> [!NOTE]
>  Örnekte <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yeni iptalini çerçevesi eski API'leri ile uyumlu olduğunu göstermek için yöntemi. Yeni kullanan bir örnek için tercih edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> yazın, bkz: [nasıl yapılır: Bir görevi ve alt öğelerini iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>İşlemi iptal nesnesi iptal karşılaştırması  
 Yeni iptal Framework'te İptal işlemleri, nesneleri gösterir. İptal isteği, gerekli tüm temizleme işlemlerini gerçekleştirdikten sonra işlemi olabildiğince çabuk durması gerektiğini anlamına gelir. Bu işlem, programınızda uygulanabilir ancak bir iptal belirteci bir "iptal edilebilir işlemine," başvurmanız gerekir. Sonra <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği belirtecin sınıflandırmalara ayarlandığı `true`, için sıfırlanamaz `false`. Bu nedenle, iptal belirteçlerini iptal edildikten sonra kullanılamayacak.  
  
 Bir nesne iptal mekanizması ihtiyacınız varsa, bu işlemi iptal mekanizması hakkında çağırarak dayandırabilirsiniz <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Bir nesne birden fazla eş zamanlı iptal edilebilir işlemi destekliyorsa, ayrı bir belirteç, her ayrı iptal edilebilir işlemi için giriş olarak geçirin. Bu şekilde, tek bir işlem diğerlerini etkilemeden iptal edilebilir.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Dinleme ve iptal isteklerini yanıtlama  
 Kullanıcı temsilcisiyle iptal edilebilir bir işlemin uygulayan bir iptal isteğine yanıt olarak bir işlemi sonlandırmak nasıl belirler. Çoğu durumda, kullanıcı temsilcisi yalnızca gerekli tüm temizleme işlemlerini gerçekleştirmek ve hemen döndürür.  
  
 Ancak, daha karmaşık durumlarda, kullanıcı temsilcisi iptali oluştu kitaplık kodu bildirmek gerekli olabilir. Bu gibi durumlarda, işlemi sonlandırmak için doğru şekilde çağrılacak temsilci için olan <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, neden olacak yöntemi bir <xref:System.OperationCanceledException> oluşturulması için. Kitaplık kodu, bu özel durum kullanıcı temsilcisi iş parçacığı üzerinde catch ve özel durumun ortak iptali veya diğer bir olağanüstü durum belirtir olup olmadığını belirlemek için özel durumun belirteci inceleyin.  
  
 <xref:System.Threading.Tasks.Task> Sınıfı tanıtıcıları <xref:System.OperationCanceledException> bu şekilde. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Yoklama tarafından dinleme  
 Uzun süre çalışan hesaplamalar için söz konusu döngü veya recurse, sizin için bir iptal isteğine değerini düzenli yoklayarak dinleyebilirsiniz <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> özelliği. Öğenin değeri ise `true`, yöntem temizlemek ve mümkün olan en kısa sürede sonlandır. Yoklama sıklığı en iyi uygulama türüne bağlıdır. Bu, geliştirici yoklama sıklığı herhangi belirli bir programı için en iyi şekilde belirlemek için en fazla olur. Kendisini yoklama performansı önemli ölçüde etkilemez. Aşağıdaki örnek yoklamak için olası yollarından biri gösterilmektedir.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: Yoklama ile iptal isteklerini dinleme](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Bir geri çağırma kaydederek dinleme  
 Bazı işlemler, iptal belirteci değeri zamanında denetleyemiyor şekilde engellenmiş olur. Bu durumlarda, bir iptal isteğine alındığında, yöntem engellemesinin kaldırıldığı bir geri çağırma yöntemi kaydedebilirsiniz.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Yöntemi döndürür bir <xref:System.Threading.CancellationTokenRegistration> özellikle bu amaç için kullanılan nesne. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Threading.CancellationToken.Register%2A> zaman uyumsuz bir Web isteği iptal etmek için yöntemi.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Nesne iş parçacığı eşitleme yönetir ve zaman içinde kesin bir noktada yürütme geri çağırma durdurur sağlar.  
  
 Sistem yanıt hızını sağlamak üzere ve kilitlenmeleri önlemek için aşağıdaki yönergeleri geri çağırmaları kaydederken gelmelidir:  
  
- Zaman uyumlu ve bu nedenle çağrısı adlandırılır çünkü geri çağırma yöntemi hızlı olmalıdır <xref:System.Threading.CancellationTokenSource.Cancel%2A> geri dönene kadar döndürmez.  
  
- Eğer <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> geri çağırma çalıştığından ve geri çağırma bekleyen bir kilidi tutan sırada programınızı kilitlenme. Sonra `Dispose` döndüren geri çağırma tarafından gerekli tüm kaynakları serbest bırakabilirsiniz.  
  
- Geri çağırmaları el ile herhangi bir iş parçacığı değil gerçekleştirmesi gereken veya <xref:System.Threading.SynchronizationContext> kullanımı bir geri çağırma. Bir geri çağırma belirli bir iş parçacığı üzerinde çalışması gerekiyorsa kullanın <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> hedef syncContext, belirtmenize olanak tanıyan Oluşturucusu olan etkin <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. El ile bir geri çağırma iş parçacığı gerçekleştirme kilitlenmeye neden olabilir.  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: İptal isteklerini geri aramaları kaydetme](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Bekleme tanıtıcısı kullanarak dinleme  
 İptal edilebilir bir işlemi engelliyken eşitleme gibi basit beklerken bir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> veya <xref:System.Threading.Semaphore?displayProperty=nameWithType>, kullanabileceğiniz <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> olay hem iptal isteğini beklemeye işlemi etkinleştirmek için özelliği. İptal belirteci bekleme tanıtıcısı bir iptal isteğine yanıt olarak sinyal haline ve yöntemin dönüş değerini kullanabilirsiniz <xref:System.Threading.WaitHandle.WaitAny%2A> işareti belirteç iptal olup olmadığını belirlemek için yöntemi. İşlemi daha sonra yalnızca çıkış throw veya bir <xref:System.OperationCanceledException>uygun şekilde.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 Hedefleyen yeni kodda [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> ve <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> hem de yeni iptal framework desteği, `Wait` yöntemleri. Geçirebilirsiniz <xref:System.Threading.CancellationToken> yöntemine İptal işlemi istendikten sonra olay uyanır ve oluşturur ve bir <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: Bekleme tanıtıcıları içeren iptal isteklerini dinleme](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Aynı anda birden çok belirteç için dinleme  
 Bazı durumlarda, aynı anda birden çok iptal belirteçleri dinlemek bir dinleyici olabilir. Örneğin, iptal edilebilir bir işlemi bir iç iptal belirteci bir belirteç dışarıdan bağımsız değişken olarak bir yöntem parametresi için geçirilen ek olarak izlemek zorunda kalabilirsiniz. Bunu yapmak için aşağıdaki örnekte gösterildiği gibi iki veya daha fazla belirteç bir belirteç katılabilir bağlantılı bir belirteç kaynağı oluşturun.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Çağırmalısınız bildirimi `Dispose` ile işiniz bittiğinde bağlı belirteç kaynağı. Daha eksiksiz bir örnek için bkz: [nasıl yapılır: Birden çok iptal isteğini dinleme](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Kitaplık kodu ve kullanıcı kodu arasında işbirliği  
 Birleşik iptalini çerçevesi, kullanıcı kodu çalışılabilir bir kitaplık kodu iptal etmek ve kullanıcı kodu iptal etmek kitaplık kodu için mümkün kılar. Sorunsuz bir işbirliği yaparak bu yönergeleri izleyerek her bir tarafta bağlıdır:  
  
- Kitaplık kodu iptal edilebilir işlemleri sağlıyorsa, bir dış iptal belirtecini kabul edin ve böylece kullanıcı kodu iptal isteğinde bulunabilirsiniz genel yöntemleri de sağlamalıdır.  
  
- Kitaplık kodu kullanıcı kodu çağırırsa, kitaplık kodu bir OperationCanceledException(externalToken) olarak yorumlamak *ortak iptali*ve bir hata özel durum olarak mutlaka.  
  
- Kullanıcı temsilcilerinde iptal isteklerine kitaplığı koddan zamanında yanıt vermek denemelidir.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> örnekler sınıflarının aşağıdaki yönergeleri izleyin. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: PLINQ sorgusunu iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
