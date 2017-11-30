---
title: "Yönetilen İş Parçacıklarında İptal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 819f564b93d54c41b879fbfcb20997a8abdebc6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cancellation-in-managed-threads"></a>Yönetilen İş Parçacıklarında İptal
İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler işbirlikçi iptali için birleşik bir modeli kullanır. Bu model, bir iptal belirteci adlı basit bir nesne üzerinde temel alır. Yeni iş parçacıkları veya görevleri oluşturarak iptal edilebilen işlemleri, bir veya daha fazla örneğin çağırır nesnesi belirteç her işleme iletir. Tek tek işlemleri, diğer işlemler için belirteç kopyalarını sırayla geçirebilirsiniz. Bazı daha sonra belirteç oluşturulan nesne bu işlemleri ne yaptıklarını durdurmanızı için kullanabilirsiniz. Yalnızca isteyen nesnesi iptal isteğini verebilir ve her dinleyicisi istek haberiniz bile ve uygun ve güncel bir şekilde yanıt sorumludur.  
  
 İşbirlikçi iptal modeli uygulamak için genel modeli aşağıdaki gibidir:  
  
-   Örneği bir <xref:System.Threading.CancellationTokenSource> yönetir ve tek tek iptal belirteçlerini iptal bildirim gönderir nesnesidir.  
  
-   Tarafından döndürülen belirtecin geçip <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği her görev veya iptal için bekleyen iş parçacığı.  
  
-   Her bir görev veya iptal için yanıt iş parçacığı için bir mekanizma sağlar.  
  
-   Çağrı <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> iptal bildirim sağlamak için yöntem.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Uygulayan sınıf <xref:System.IDisposable> arabirimi. Çağırdığınızdan emin olmalıdır <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> herhangi boşaltmak için iptal belirteci kaynağı kullanmayı bitirdikten sonra yöntemi yönetilmeyen bu kaynakları.  
  
 Aşağıdaki çizimde bir belirteç kaynağı ve onun belirteci tüm kopyalarını arasındaki ilişkiyi gösterir.  
  
 ![CancellationTokenSource ve iptal belirteçleri](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Yeni iptal modeli iptali kullanan uygulama ve kitaplıkları oluşturmak kolaylaştırır ve aşağıdaki özellikleri destekler:  
  
-   İptal işbirlikçi ve Dinleyicide zorunlu değildir. Dinleyici iptal isteğine yanıt olarak düzgün biçimde sonlandırmak nasıl belirler.  
  
-   İsteyen dinleme yapması farklıdır. İptal işlemi çağıran bir nesne, zaman iptal (Şimdiye kadar varsa) istenen kontrol edebilirsiniz.  
  
-   İstekte bulunan nesne, yalnızca bir yöntem çağrısı kullanarak, belirteç tüm kopyalarını iptal isteği gönderir.  
  
-   Dinleyici için birden çok belirteç aynı anda bunları birine birleştirerek dinleme *bağlantılı belirteci*.  
  
-   Kullanıcı kodu dikkat edin ve kitaplık koddan iptal isteklerini yanıtlamak ve kitaplık kodu dikkat edin ve kullanıcı kodundan iptal isteklerine yanıt.  
  
-   Dinleyicileri iptal isteklerini yoklama, geri çağırma kaydını ya da bekleme tanıtıcıları üzerinde bekleyen bildirilebilir.  
  
## <a name="cancellation-types"></a>İptal türleri  
 İptal framework aşağıdaki tabloda listelenen ilgili türleri kümesi olarak uygulanır.  
  
|Tür adı|Açıklama|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Bir iptal belirteci oluşturur ve aynı zamanda tüm kopyalarını belirtecini iptal isteği yayınlar nesne.|  
|<xref:System.Threading.CancellationToken>|Basit değer türü, bir veya daha fazla dinleyicileri için genellikle bir yöntem parametresi olarak geçirildi. Dinleyicileri izlemek değerini `IsCancellationRequested` yoklama, geri çağırma ya da bekleme tanıtıcısı belirteç özelliği.|  
|<xref:System.OperationCanceledException>|Bu özel durumun Oluşturucusu aşırı kabul bir <xref:System.Threading.CancellationToken> bir parametre olarak. Dinleyicileri isteğe bağlı olarak iptal kaynak doğrulamak ve diğerleri iptal isteğine yanıt verdi bildirmek için bu özel durum.|  
  
 Yeni iptal modeli tümleştirilmiş [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] çeşitli türlerde. En önemli olanlardır <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Bu yeni iptal model için tüm yeni kitaplık ve uygulama kodu kullanmanızı öneririz.  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnekte, istekte bulunan nesnesi oluşturur bir <xref:System.Threading.CancellationTokenSource> nesne ve geçişleri kendi <xref:System.Threading.CancellationTokenSource.Token%2A> İptal işlemi özelliğine. İsteği alır işlemi değerini izler <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> yoklama ile belirteç özelliği. Değer olduğunda `true`, dinleyiciyi uygun herhangi bir şekilde sonlandırabilir. Bu örnekte, yöntem yalnızca, çoğu durumda gerekli olduğu çıkar.  
  
> [!NOTE]
>  Örnek kullanır <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yeni iptal framework eski API'leri ile uyumlu olduğunu göstermek için yöntem. Yeni kullanan bir örnek için tercih edilen <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> yazın, bkz: [nasıl yapılır: bir görevi ve ait alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>İşlemi iptal nesne iptal karşılaştırması  
 Yeni iptal Framework'te İptal işlemleri, nesneleri gösterir. İptal isteğini tüm gerekli temizleme işlemi yapıldıktan sonra işlemi mümkün olan en kısa sürede durması gerektiğini anlamına gelir. Bu işlem, programınıza uygulanmamış olabilir ancak bir iptal belirteci bir "İptal işlemi için" başvurmalıdır. Sonra <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> belirteç özelliği ayarlanmış `true`, için sıfırlanamaz `false`. Bu nedenle, iptal edildikten sonra iptal belirteçlerini yeniden kullanılamaz.  
  
 Bir nesne iptal mekanizması gerektiriyorsa, bu işlemi iptal mekanizması hakkında çağırarak temel alabilir <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Bir nesnenin birden fazla eş zamanlı İptal işlemi destekliyorsa, her ayrı İptal işlemi için giriş olarak ayrı bir belirteç geçirin. Bu şekilde, bir işlem diğerlerini etkilemeden iptal edilebilir.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Dinleme ve iptal isteklerini yanıtlama  
 Kullanıcı temsilci uygulayan İptal işlemi iptal isteğine yanıt olarak işlemi sonlandırmak nasıl belirler. Çoğu durumda, kullanıcı temsilci yalnızca tüm gerekli temizlenmesini ve hemen döndürür.  
  
 Ancak, daha karmaşık durumlarda, kullanıcı temsilci iptal oluştu kitaplık kodu bildirmek gerekli olabilir. Böyle durumlarda, işlemi sonlandırmak için doğru bir şekilde çağrılacak için temsilcisidir <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, neden olacak yöntemi bir <xref:System.OperationCanceledException> oluşturulmasına. Kitaplık kodu, bu özel durumu kullanıcı temsilci iş parçacığı üzerinde yakalamak ve özel durum işbirlikçi iptal veya diğer bir olağanüstü durum gösterip göstermeyeceğini belirlemek için özel durumun belirteci inceleyin.  
  
 <xref:System.Threading.Tasks.Task> Sınıf tanıtıcıları <xref:System.OperationCanceledException> bu şekilde. Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Yoklama tarafından dinleme  
 Uzun süre çalışan hesaplamaları için bu döngü veya recurse, iptal isteği için düzenli aralıklarla değerini yoklayarak dinleme <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> özelliği. Öğenin değeri ise `true`, yöntem temizlemek ve mümkün olan en kısa sürede sonlandırılacak. En iyi yoklama sıklığını uygulama türüne bağlıdır. Yoklama sıklığı verilen her program için en iyi belirlemek için geliştirici kadar olur. Kendisini yoklama performansı önemli ölçüde etkilemez. Aşağıdaki örnek yoklamak için olası bir yol gösterir.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: yoklama ile iptal isteklerini dinleme](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Bir geri çağırma kaydederek dinleme  
 Bunlar iptal belirteci değeri zamanında denetlenemiyor şekilde bazı işlemler engellenmiş duruma gelebilir. Bu durumlarda, iptal isteği alındığında yöntemi engelini kaldırır bir geri çağırma yöntemi kaydedebilirsiniz.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Yöntemi döndürür bir <xref:System.Threading.CancellationTokenRegistration> özellikle bu amaç için kullanılan nesne. Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Threading.CancellationToken.Register%2A> zaman uyumsuz Web isteği iptal etmek için yöntem.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Nesnenin iş parçacığı eşitleme yönetir ve kesin bir noktada yürütme süresi içinde geri çağırma durdurur sağlar.  
  
 Sistem Yanıtlama Hızı sağlamak için ve kilitlenmeleri önlemek için aşağıdaki kılavuzları geri aramalar kaydedilirken gelmelidir:  
  
-   Bu zaman uyumlu olarak ve bu nedenle çağrısı çağrıldığı için geri çağırma yöntemi hızlı olmalıdır <xref:System.Threading.CancellationTokenSource.Cancel%2A> geri çağırma dönene kadar döndürmüyor.  
  
-   Çağırırsanız <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> geri çağırma çalıştıran ve geri çağırma bekleyen bir kilit tutun olsa da, programınızı kilitlenme. Sonra `Dispose` geri çağırmasının tarafından gerekli tüm kaynakları serbest döndürür.  
  
-   Geri aramalar el ile herhangi bir iş parçası olmayan gerçekleştirmesi gerektiğini veya <xref:System.Threading.SynchronizationContext> bir geri çağırma kullanımı. Bir geri çağırma belirli bir iş parçacığı üzerinde çalıştırmanız gerekiyorsa kullanın <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> hedef syncContext, belirtmenize olanak tanıyan Oluşturucusu etkin olduğu <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. İçinde bir geri çağırma el ile iş parçacığı oluşturma gerçekleştirme kilitlenmeye neden olabilir.  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: iptal istekleri için geri çağırmaları kaydetme](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Bir bekleme tanıtıcısı kullanılarak dinleme  
 Ne zaman iptal işlemi engelleme gibi basit bir eşitleme beklerken bir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> veya <xref:System.Threading.Semaphore?displayProperty=nameWithType>, kullanabileceğiniz <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> olay hem iptal isteğini beklemeye işlemi etkinleştirmek için özellik. İptal belirteci bekleme tanıtıcısı iptal isteğine yanıt olarak işaret haline gelir ve yöntemin dönüş değerini kullanabilirsiniz <xref:System.Threading.WaitHandle.WaitAny%2A> iptal olup olmadığını belirlemek için yöntemi işareti simge. İşlemi daha sonra yalnızca çıkış throw veya bir <xref:System.OperationCanceledException>uygun şekilde.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 Hedefleyen yeni kod [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> ve <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> hem de yeni iptal çerçevesini destekleyen kendi `Wait` yöntemleri. Geçirebilirsiniz <xref:System.Threading.CancellationToken> yöntemine İptal istendiğinde, olay uyanır ve oluşturur ve bir <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: iptal istekleri sahip bekleyin işleme için dinleme](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Aynı anda birden çok belirteç dinleme  
 Bazı durumlarda, aynı anda birden çok iptal belirteçlerini dinlemek bir dinleyici olabilir. Örneğin, bir İptal işlemi bir iç iptal belirteci dışarıdan bağımsız değişken olarak bir yöntem parametresi geçirilen belirteç yanı sıra izlemek zorunda kalabilirsiniz. Bunu başarmak için aşağıdaki örnekte gösterildiği gibi iki veya daha fazla belirteçleri bir belirteç katılabilirsiniz bağlantılı bir belirteç kaynağı oluşturun.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Çağırmalısınız bildirimi `Dispose` ile bittiğinde kaynağında bağlantılı belirteci. Daha eksiksiz bir örnek için bkz: [nasıl yapılır: birden çok iptal isteğini dinleme](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Kitaplık kodu kullanıcı kodu arasında iş Birliği  
 Birleşik iptal Framework'te kullanıcı kodu iptal etmek kitaplık kodu ve kitaplık kodu İşbirlikçi bir biçimde iptal etmek kullanıcı kodu mümkün kılar. Kesintisiz işbirliği yaparak bu yönergeleri izleyerek her bir tarafta bağlıdır:  
  
-   Kitaplık kodu iptal edilebilen işlemleri sağlıyorsa, ayrıca bir dış iptal belirteci kabul etmek ve böylece kullanıcı kodu iptal isteyebilir genel yöntemler sağlamalıdır.  
  
-   Kitaplık kodu kullanıcı koda çağırırsa, kitaplık kodu bir OperationCanceledException(externalToken) olarak yorumlanan *işbirlikçi iptal*, değildir hata özel durum.  
  
-   Kullanıcı temsilcileri kitaplık koddan zamanında iptal isteklerini yanıtlamasını denemelidir.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>ve <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> bu yönergeleri aşağıdaki sınıflar olarak gösterilebilir. Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md)ve [nasıl yapılır: PLINQ sorgusunu iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen iş parçacığı oluşturma temelleri](../../../docs/standard/threading/managed-threading-basics.md)
