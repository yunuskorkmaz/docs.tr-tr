---
title: "Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac206e41f727d24e7748226101b9b8a86ee77376
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
Olay tabanlı zaman uyumsuz desen ve semantiği temsilci sınıflarıyla tanıdık olay zaman uyumsuz davranışı kullanıma sunmak için etkili bir yol sağlar. Olay tabanlı zaman uyumsuz desen uygulamak için bazı belirli davranış gereksinimini takip gerekir. Aşağıdaki bölümlerde, gereksinimleri ve olay tabanlı zaman uyumsuz deseni izler bir sınıf uygulama dikkate almanız yönergeler açıklanmaktadır.  
  
 Genel bir bakış için bkz: [olay tabanlı zaman uyumsuz deseni uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Davranış garanti gerekli  
 Olay tabanlı zaman uyumsuz desen uygulamak, garanti sınıfınızın doğru şekilde davranır ve sınıfınızın istemcileri bu tür davranış güvenebilirsiniz emin olmak için çeşitli sağlamanız gerekir.  
  
### <a name="completion"></a>Tamamlama  
 Her zaman çağırma *MethodName* `Completed` başarılı bir şekilde tamamlandığında, bir hata ya da iptal olduğunda olay işleyicisi. Uygulamalar, hiçbir zaman burada boşta kalır ve tamamlanma hiçbir zaman oluşur bir durum karşılaşabilirsiniz. Bu kural için bir özel, böylece hiçbir zaman tamamlanmıyor zaman uyumsuz işlemi üzere tasarlanmış varsa ' dir.  
  
### <a name="completed-event-and-eventargs"></a>Tamamlanan Olay ve EventArgs  
 Her ayrı için *MethodName* `Async` yöntemi, aşağıdaki tasarım gereksinimleri geçerlidir:  
  
-   Tanımlayan bir *MethodName* `Completed` olayı yöntemi ile aynı sınıfta.  
  
-   Tanımlayan bir <xref:System.EventArgs> sınıfı ve eşlik eden temsilci için *MethodName* `Completed` türetilen olay <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı. Varsayılan sınıf adı biçiminde olmalıdır *MethodName*`CompletedEventArgs`.  
  
-   Emin <xref:System.EventArgs> sınıftır dönüş değerleri belirli *MethodName* yöntemi. Kullandığınızda <xref:System.EventArgs> sınıfı, sonuç yayınlanamıyor geliştiriciler hiçbir zaman gerektiren.  
  
     Aşağıdaki kod örneği, bu tasarım gereksiniminin iyi ve hatalı uyarlamasını sırasıyla gösterir.  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)   
{   
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)   
{   
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
-   Değil tanımlayan bir <xref:System.EventArgs> döndüren yöntemler döndürmek için sınıf `void`. Bunun yerine, bir örneğini kullanması <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı.  
  
-   Her zaman Yükselt olun *MethodName* `Completed` olay. Bu olay, başarılı bir şekilde tamamlandığında, bir hata veya iptal oluşmalıdır. Uygulamalar, hiçbir zaman burada boşta kalır ve tamamlanma hiçbir zaman oluşur bir durum karşılaşabilirsiniz.  
  
-   Zaman uyumsuz işlemi oluşur ve yakalanan özel durum atamak istediğiniz özel durumları yakalamak olun <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği.  
  
-   Görevi tamamlamak hata oluşursa, sonuçları erişilebilir olmamalıdır. Zaman <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği `null`, o herhangi bir özellik erişimini sağlamak <xref:System.EventArgs> yapısı özel bir durum oluşturur. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> bu doğrulamayı gerçekleştirmek için yöntem.  
  
-   Zaman aşımı, hata olarak model. Zaman aşımı oluştuğunda Yükselt *MethodName* `Completed` olay ve ata bir <xref:System.TimeoutException> için <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği.  
  
-   Sınıfınıza birden çok eşzamanlı çağrılarını destekliyorsa, emin *MethodName* `Completed` olayı uygun içeren `userSuppliedState` nesnesi.  
  
-   Emin *MethodName* `Completed` uygun iş parçacığı üzerinde ve uygulama yaşam döngüsü uygun zamanında olayı oluşturulur. Daha fazla bilgi için parçacıkları ve bağlamları bölümüne bakın.  
  
### <a name="simultaneously-executing-operations"></a>Aynı anda işlemleri çalıştırma  
  
-   Sınıfınıza birden çok eşzamanlı çağrılarını destekliyorsa, tanımlayarak her çağrıldığında ayrı ayrı izlemek Geliştirici etkinleştirmek *MethodName* `Async` adlı bir nesne değerli state parametresi ya da görev kimliği alır aşırı yüklemesi `userSuppliedState`. Bu parametre her zaman son parametre olmalıdır *MethodName* `Async` yöntemin imzası.  
  
-   Sınıfınızda tanımlıyorsa *MethodName* `Async` bir durum nesnesi değerli parametresi ya da görev kimliği alır aşırı yükleme işlemi o görev kimliği'yla ömrü izlemek ve tamamlama geri sağladığınızdan emin olun emin olun işleyici. Yardımcı sınıfları yardımcı olmak kullanılabilir vardır. Eşzamanlılık yönetimi hakkında daha fazla bilgi için bkz: [izlenecek yol: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Sınıfınızda tanımlıyorsa *MethodName* `Async` herhangi çağırma girişimi emin olun, yöntemi ve durum parametresi olmadan birden çok eşzamanlı çağrılarını desteklemiyor *MethodName* `Async` önceden önce *MethodName* `Async` çağırma başlatır tamamlandı bir <xref:System.InvalidOperationException>.  
  
-   Genel olarak, bir özel durum varsa yükseltmeyin *MethodName* `Async` yöntemi olmadan `userSuppliedState` parametresi birden çok bekleyen işlemler vardır; böylece birden çok kez çağrılır. Sınıfınıza açıkça olamaz bu durumu yönetmek, ancak geliştiriciler bu birden çok ayırt geri aramalar işleyebilir varsayın bir özel durum yükseltebilirsiniz.  
  
### <a name="accessing-results"></a>Sonuçlarına erişme  
  
-   Zaman uyumsuz işlemi yürütülürken bir hata varsa, sonuçlar erişilebilir olmamalıdır. Bu herhangi bir özellik erişimini sağlamak <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> değil `null` başvurduğu özel durumu tetikler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> SAX <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> bu amaçla yöntemi.  
  
-   Herhangi bir sonuç başlatır erişme girişimi olun bir <xref:System.InvalidOperationException> belirten işlemi iptal edildi. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> bu doğrulamayı gerçekleştirmek için yöntem.  
  
### <a name="progress-reporting"></a>İlerleme durumunu bildirme  
  
-   İlerleme durumu raporlama, mümkünse destekler. Bu sınıfınız kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamak için geliştiriciler sağlar.  
  
-   Öğesini uygularsanız bir `ProgressChanged` / *MethodName* `ProgressChanged` olay, sonra bu işlem belirli bir zaman uyumsuz işlem için oluşturulan hiçbir tür olaylara olduğundan emin olun *MethodName* `Completed` olay tetiklenir.  
  
-   Varsa standart <xref:System.ComponentModel.ProgressChangedEventArgs> olduğundan emin doldurulmuş <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman bir yüzde olarak yorumlanır. Yüzde doğru olması gerekmez, ancak bir yüzdesini temsil etmelidir. Ölçüm raporlama ilerleme durumunuzu yüzde dışında bir şey olması gerekiyorsa öğesinden bir sınıf türetin <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfı ve bırakın <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 0. Bir raporlama ölçümü yüzde dışında kullanmaktan kaçının.  
  
-   Emin `ProgressChanged` uygun iş parçacığı üzerinde ve uygulama yaşam döngüsü uygun zamanında olayı oluşturulur. Daha fazla bilgi için parçacıkları ve bağlamları bölümüne bakın.  
  
### <a name="isbusy-implementation"></a>IsBusy uygulama  
  
-   Değil kullanıma bir `IsBusy` sınıfınız birden çok eşzamanlı çağrılarını destekliyorsa özelliği. Örneğin, XML Web hizmeti proxy'si değil ortaya bir `IsBusy` özelliğini zaman uyumsuz yöntemleri yönelik birden çok eşzamanlı çağrılarını desteklemediğinden.  
  
-   `IsBusy` Özelliği döndürmelidir `true` sonra *MethodName* `Async` yöntemi çağrılmadan önce *MethodName* `Completed` olay tetiklenir. Aksi takdirde döndürmelidir `false`. <xref:System.ComponentModel.BackgroundWorker> Ve <xref:System.Net.WebClient> bileşenleri kullanıma sınıfların örnekleri olan bir `IsBusy` özelliği.  
  
### <a name="cancellation"></a>İptal Etme  
  
-   İptal etme, mümkünse destekler. Bu sınıfınız kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamak için geliştiriciler sağlar.  
  
-   İptal etme söz konusu olduğunda, ayarlamak <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> içinde bayrak <xref:System.ComponentModel.AsyncCompletedEventArgs> nesnesi.  
  
-   Herhangi bir sonuç başlatır erişme girişimi olun bir <xref:System.InvalidOperationException> belirten işlemi iptal edildi. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> bu doğrulamayı gerçekleştirmek için yöntem.  
  
-   İptal yöntemine yönelik çağrılar her zaman başarıyla döndürür ve hiçbir zaman bir özel durum Yükselt emin olun. Genel olarak, bir istemci bir işlem belirli bir zamanda gerçekten iptal edilebilen olup seçeceğine bildirilmez ve daha önce verilen iptal başarılı oldu konusunda bildirilmez. İptal başarılı olduğunda, uygulama tamamlanma durumu bölümü aldığından ancak, uygulama her zaman bildirim verilir.  
  
-   Yükselt *MethodName* `Completed` işlemi iptal ettiğinizde olay.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve özel durumlar  
  
-   Zaman uyumsuz işlemi gerçekleştiğinde ve değerini ayarlama tüm özel durumları yakalamak <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> için bu özel özellik.  
  
### <a name="threading-and-contexts"></a>Parçacıkları ve bağlamları  
 Sınıfınızın doğru çalışması için istemcinin olay işleyicileri uygun iş parçacığı veya belirtilen uygulama modeli bağlamının çağrılır kritik dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve Windows Forms uygulamaları. Zaman uyumsuz sınıfınız altında herhangi bir uygulama modeli düzgün şekilde davranan emin olmak için iki önemli yardımcı sınıfları sağlanır: <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager>bir yöntem sağlar <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, döndüren bir <xref:System.ComponentModel.AsyncOperation>. *MethodName* `Async` yöntem çağrılarını <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> ve sınıfınız döndürülen kullanır <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz görev ömrü izlemek için.  
  
 İlerleme durumunu, artımlı sonuçları ve istemciye tamamlama bildirmek için arama <xref:System.ComponentModel.AsyncOperation.Post%2A> ve <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> yöntemlere <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation>istemcinin olay işleyicilerine uygun iş parçacığı veya bağlam çağrıları hazırlama için sorumludur.  
  
> [!NOTE]
>  Açıkça uygulama modeli ilkesini karşı gitmek istiyorsanız, ancak hala olay tabanlı zaman uyumsuz desen kullanmanın diğer avantajları yararlanan bu kurallar atlayabilir. Örneğin, boş olması için Windows Forms'ta işletim bir sınıf akıtılan isteyebilirsiniz. Geliştiriciler zımni sınırlamaları anlayın sürece, ücretsiz iş parçacıklı sınıfı oluşturabilirsiniz. Konsol uygulamaları yürütülmesi senkronize değil <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrıları. Bu neden `ProgressChanged` sıralama dışında çıkarılmasına olaylar. Yürütülmesi serileştirilmiş isterseniz, <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrıları, uygulamak ve yükleme bir <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> sınıfı.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager> zaman uyumsuz işlemleri etkinleştirmek için bkz: [izlenecek yol: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Kuralları  
  
-   İdeal olarak, her yöntem çağırma bağımsız olması gerekir. Paylaşılan kaynaklarla çağrılarını Kuplaj kaçınmalısınız. Kaynakları çağrılarını arasında paylaşılacak varsa, uygun eşitleme mekanizması uygulamanızda sağlamanız gerekir.  
  
-   Eşitleme uygulamak istemci gerektirir tasarımları önerilmez. Örneğin, bir genel statik nesnesini parametre olarak alır zaman uyumsuz bir yöntem olabilir; Bu tür bir yöntemin birden çok eşzamanlı çağrılarını veri bozulması veya kilitlenmeleri neden olabilir.  
  
-   Birden çok çağırma aşırı yüklemeye sahip bir yöntem uygularsanız (`userState` imzada), sınıfınız kullanıcı durumları veya görev kimlikleri ve karşılık gelen bekleyen işlemler koleksiyonunu yönetmek için ihtiyacınız olacaktır. Bu koleksiyon ile korunması gereken `lock` bölgeler, çeşitli çağrıları ekleme ve kaldırma nedeni `userState` koleksiyonundaki nesneleri.  
  
-   Yeniden göz önünde bulundurun `CompletedEventArgs` uygun ve uygun yerlerde sınıfları. Bu durumda, adlandırma yöntem adı ile tutarlı değil çünkü belirli bir temsilci ve <xref:System.EventArgs> türü tek bir yönteme bağlı değil. Ancak, geliştiricilerin üzerinde bir özellikten alınan değeri cast zorlama <xref:System.EventArgs> hiçbir zaman kabul edilebilir değil.  
  
-   Öğesinden türeyen bir sınıf yazıyorsanız <xref:System.ComponentModel.Component>, değil uygulamak ve kendi yükleme <xref:System.Threading.SynchronizationContext> sınıfı. Uygulama modelleri değil bileşenleri, Denetim <xref:System.Threading.SynchronizationContext> kullanılan.  
  
-   Kullandığınızda, çoklu iş parçacığı kullanımı herhangi bir tür, büyük olasılıkla kendiniz için çok önemli ve karmaşık hatalar ortaya. Çoklu iş parçacığı kullanımı, bakın herhangi bir çözümü uygulamadan önce [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [İzlenecek yol: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
