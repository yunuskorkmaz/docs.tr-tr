---
title: Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: e50f455ab83b0b057f8ce3c32f874e6856632d70
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133629"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
Olay tabanlı zaman uyumsuz desen sınıflarda, alışık olduğunuz olay ile zaman uyumsuz davranış ve semantiği temsilci etkili bir yol sağlar. Olay tabanlı zaman uyumsuz desen uygulamak için bazı belirli davranış gereksinimini takip etmeniz gerekir. Aşağıdaki bölümlerde, gereksinimleri ve olay-tabanlı zaman uyumsuz deseni izleyen bir sınıf uygularken dikkate almanız gereken yönergeler açıklanmaktadır.  
  
 Genel bakış için bkz. [olay tabanlı zaman uyumsuz deseni uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Davranış garantileri gerekiyor  
 Olay tabanlı zaman uyumsuz desen uygulamak, garantileri sınıfınıza düzgün şekilde davranır ve sınıfınızın istemciler üzerinde benzer bir davranış güvenebilirsiniz emin olmak için birkaç sağlamanız gerekir.  
  
### <a name="completion"></a>Tamamlama  
 Her zaman çağırır <em>MethodName</em>**tamamlandı** başarıyla tamamlandığında, bir hata veya İptal'e sahip olduğunuzda bir olay işleyicisi. Uygulamalar hiçbir zaman nerede bunlar boşta kalır ve hiçbir zaman tamamlama gerçekleşir bir durumla karşılaşmamanız gerekir. Bu kuralın tek istisnası, böylece hiçbir zaman tamamlanmadan zaman uyumsuz işlem üzere tasarlanmış, ' dir.  
  
### <a name="completed-event-and-eventargs"></a>Tamamlanan Olay ve EventArgs  
 Her ayrı için <em>MethodName</em>**zaman uyumsuz** yöntemi, aşağıdaki tasarım gereksinimleri geçerlidir:  
  
-   Tanımlayan bir <em>MethodName</em>**tamamlandı** olay yöntemi olarak aynı sınıfta.  
  
-   Tanımlayan bir <xref:System.EventArgs> sınıfı ve eşlik eden bir temsilci için <em>MethodName</em>**tamamlandı** türetildiği olay <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı. Varsayılan sınıf adı biçiminde olmalıdır <em>MethodName</em>**CompletedEventArgs**.  
  
-   Emin <xref:System.EventArgs> sınıfı, dönüş değerleri belirli <em>MethodName</em> yöntemi. Kullanırken <xref:System.EventArgs> sınıfı, sonuç olarak, geliştiriciler hiçbir zaman gerektiren.  
  
     Aşağıdaki kod örneği, sırasıyla bu tasarım gereksiniminin iyi hem kötü yanları uygulanışı gösterilmektedir.  
  
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
  
-   Tanımlamıyor bir <xref:System.EventArgs> döndüren yöntemler döndürmek için sınıf `void`. Bunun yerine, bir örneğini kullanması <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı.  
  
-   Her zaman yükseltmek olun <em>MethodName</em>**tamamlandı** olay. Bu olay başarıyla tamamlandığında, bir hata veya iptal oluşmalıdır. Uygulamalar hiçbir zaman nerede bunlar boşta kalır ve hiçbir zaman tamamlama gerçekleşir bir durumla karşılaşmamanız gerekir.  
  
-   Zaman uyumsuz işlemde oluşur ve özel durum yakalandı atama özel durumları yakaladığınızdan emin olmak <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği.  
  
-   Görev tamamlama hata oluşursa, sonuçları erişilebilir olmamalıdır. Zaman <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği değil `null`, erişim herhangi bir özelliği sağlamak <xref:System.EventArgs> yapısı bir özel durum oluşturur. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> bu doğrulamayı gerçekleştirmek için yöntemi.  
  
-   Zaman aşımı, hata olarak model. Zaman aşımı meydana geldiğinde yükseltmek <em>MethodName</em>**tamamlandı** olay ve ata bir <xref:System.TimeoutException> için <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği.  
  
-   Sınıfınız birden çok eş zamanlı çağrılarını destekliyorsa, emin <em>MethodName</em>**tamamlandı** olay içeren uygun `userSuppliedState` nesne.  
  
-   Emin <em>MethodName</em>**tamamlandı** uygun iş parçacığı ve uygulama yaşam döngüsü içinde uygun zamanda olayı oluşturulur. Daha fazla bilgi için parçacıkları ve bağlamları bölümüne bakın.  
  
### <a name="simultaneously-executing-operations"></a>İşlemler aynı anda yürütülüyor  
  
-   Sınıfınız birden çok eş zamanlı çağrılarını destekliyorsa, her çağrıldığında, ayrı olarak tanımlayarak izlemek Geliştirici etkinleştirme <em>MethodName</em>**zaman uyumsuz** nesne değerli bir duruma alan aşırı yükleme parametresi veya görev kimliği adlı `userSuppliedState`. Bu parametre, her zaman son parametre olmalıdır <em>MethodName</em>**zaman uyumsuz** yöntemin imzası.  
  
-   Sınıfınıza tanımlıyorsa <em>MethodName</em>**zaman uyumsuz** bir nesne değerli state parametresi ya da görev kimliği alan aşırı yükleme işlemi, görev kimliği ile ömrünü izlemek ve geri sağladığınızdan emin emin olun Tamamlama işleyicisine. Oluşturmada yardımcı olması için yardımcı sınıfı vardır. Eşzamanlılık yönetimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Sınıfınıza tanımlıyorsa <em>MethodName</em>**zaman uyumsuz** yöntemi ve durum parametresi olmadan, birden çok eş zamanlı çağrılarını desteklemiyor, tüm çağrılacak çalışacağından emin <em>MethodName</em>  **Zaman uyumsuz** önceden önce <em>MethodName</em>**zaman uyumsuz** çağırma harekete geçirirse tamamlandı bir <xref:System.InvalidOperationException>.  
  
-   Genel olarak, bir özel durum, geçirmeyin <em>MethodName</em>**zaman uyumsuz** olmadan yöntemi `userSuppliedState` parametre birden fazla bekleyen işlemlerin, böylece birden çok kez çağrılır. Sınıfınıza açıkça olamaz bu durumu yönetmek, ancak geliştiriciler bu birden çok farksız geri çağırmaları işleyebileceğini varsayar bir özel durum oluşturabilir.  
  
### <a name="accessing-results"></a>Sonuçlarına erişme  
  
-   Zaman uyumsuz işlemin yürütülmesi sırasında bir hata varsa, sonuçları erişilebilir olmamalıdır. Herhangi bir özellikte erişim sağlamak <xref:System.ComponentModel.AsyncCompletedEventArgs> olduğunda <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> değil `null` tarafından başvurulan durum harekete <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. <xref:System.ComponentModel.AsyncCompletedEventArgs> Sağlar sınıfını <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> bu amaç için yöntemi.  
  
-   Herhangi bir sonuç harekete geçirirse erişme girişimi olun bir <xref:System.InvalidOperationException> belirten işlem iptal edildi. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> bu doğrulamayı gerçekleştirmek için yöntemi.  
  
### <a name="progress-reporting"></a>İlerleme durumunu bildirme  
  
-   İlerleme durumunu bildirme, mümkünse destekler. Bu, geliştiricilerin kendi sınıfınızı kullanıldığında daha iyi bir uygulama kullanıcı deneyimi sağlamak sağlar.  
  
-   Uygularsanız bir **ProgressChanged** veya <em>MethodName</em>**ProgressChanged** olay, belirli bir zaman uyumsuz işlem için oluşturulan hiçbir tür olaylara olduğundan emin olun Bu işlemin sonra <em>MethodName</em>**tamamlandı** olay tetiklenir.  
  
-   Standart <xref:System.ComponentModel.ProgressChangedEventArgs> olduğundan emin doldurulmasını, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman bir yüzdesi olarak yorumlanabilir. Yüzde doğru olması gerekmez, ancak bir yüzdesini temsil etmelidir. Ölçüm raporlama ilerleme durumunuzu yüzde dışında bir şey olması gerekiyorsa, öğesinden bir sınıf türetin <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfı ve bırakın <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 0. Bir raporlama ölçüm yüzde dışında kullanmaktan kaçının.  
  
-   Emin `ProgressChanged` uygun iş parçacığı ve uygulama yaşam döngüsü içinde uygun zamanda olayı oluşturulur. Daha fazla bilgi için parçacıkları ve bağlamları bölümüne bakın.  
  
### <a name="isbusy-implementation"></a>IsBusy uygulama  
  
-   Kullanıma bir `IsBusy` sınıfınız birden çok eş zamanlı çağrılarını destekliyorsa özelliği. Örneğin, XML Web hizmeti proxy kullanıma bir `IsBusy` özelliği zaman uyumsuz yöntemlerin birden çok eş zamanlı çağrılarını destekledikleri için.  
  
-   `IsBusy` Özelliği döndürmelidir `true` sonra <em>MethodName</em>**zaman uyumsuz** yönteminin çağrılıp çağrılmadığını ve önce <em>MethodName</em>  **Tamamlanan** olay tetiklenir. Aksi takdirde döndürmelidir `false`. <xref:System.ComponentModel.BackgroundWorker> Ve <xref:System.Net.WebClient> bileşenlerdir kullanıma sınıfların örnekleri bir `IsBusy` özelliği.  
  
### <a name="cancellation"></a>İptal Etme  
  
-   İptal etme, mümkünse destekler. Bu, geliştiricilerin kendi sınıfınızı kullanıldığında daha iyi bir uygulama kullanıcı deneyimi sağlamak sağlar.  
  
-   İptal durumunda ayarlamak <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> bayrağını <xref:System.ComponentModel.AsyncCompletedEventArgs> nesne.  
  
-   Herhangi bir sonuç harekete geçirirse erişme girişimi olun bir <xref:System.InvalidOperationException> belirten işlem iptal edildi. Kullanım <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> bu doğrulamayı gerçekleştirmek için yöntemi.  
  
-   İptal yöntemine yönelik çağrılar her zaman başarıyla döndürür ve hiçbir zaman bir özel durum yükseltir emin olun. Genel olarak, bir istemcinin bir işlemi belirli bir zamanda gerçekten iptal edilebilir olup seçeceğine bildirilmez ve daha önce verilen iptali başarılı oldu seçeceğine bildirilmez. İptal başarılı olduğunda uygulama tamamlanma durumu bölümü aldığından ancak, uygulama her zaman bildirim sunulur.  
  
-   Raise <em>MethodName</em>**tamamlandı** işlemi iptal edildiğinde olay.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve özel durumlar  
  
-   Zaman uyumsuz işlemde oluşur ve değerini özel durumları yakalama <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği, özel duruma bakın.  
  
### <a name="threading-and-contexts"></a>Parçacıkları ve bağlamları  
 Sınıfınıza doğru çalışması için istemcinin olay işleyicileri doğru iş parçacığı veya belirli bir uygulama modeli için bağlam çağrılır kritik dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve Windows Forms uygulamaları. İki önemli yardımcı sınıfları, zaman uyumsuz sınıfınızın herhangi bir uygulama modeli altında düzgün şekilde davranan emin olmak için sağlanır: <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> bir yöntem sağlar <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, döndüren bir <xref:System.ComponentModel.AsyncOperation>. <em>MethodName</em>**zaman uyumsuz** yöntem çağrılarını <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> ve sınıfınız döndürülen kullanan <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz görev ömrünü izlemek için.  
  
 İlerleme durumunu, artımlı sonuçları ve istemciye tamamlama bildirmek için çağrı <xref:System.ComponentModel.AsyncOperation.Post%2A> ve <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> yöntemlerde <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> çağrıları istemcinin olay işleyicileri doğru iş parçacığı veya içerik hazırlama için sorumludur.  
  
> [!NOTE]
>  Açıkça uygulama modeli ilkesini karşı geçmek istiyorsanız, ancak olay tabanlı zaman uyumsuz desen kullanma diğer avantajlarından faydalanmaya devam edebilirsiniz, bu kurallar atlayabilir. Örneğin, bir sınıf ücretsiz olarak Windows Forms'ta işletim iş parçacıklı isteyebilirsiniz. Geliştiriciler örtük kısıtlamaları anlama olduğu sürece ücretsiz iş parçacıklı bir sınıf oluşturabilirsiniz. Konsol uygulamaları yürütülmesini eşitleme <xref:System.ComponentModel.AsyncOperation.Post%2A> çağırır. Bu neden `ProgressChanged` olayları sipariş dışında oluşturulur. Yürütülmesini serileştirilmiş istiyorsanız <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrıları, uygulamak ve yükleme bir <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> sınıfı.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager> , zaman uyumsuz işlemleri etkinleştirmek için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Kuralları  
  
-   İdeal olarak, her yöntem çağırma bağımsız olmalıdır. Paylaşılan kaynaklarla çağrılarını eşlenmesiyle kaçınmanız gerekir. Çağrıları arasında paylaşılan kaynaklar varsa, uygulamanızda uygun eşitleme mekanizmaya gerekecektir.  
  
-   Eşitleme uygulamak istemci gerektiren tasarımları önerilmez. Örneğin, bir genel statik nesne parametre olarak alan zaman uyumsuz bir yöntem olabilir. birden çok eş zamanlı benzer bir yöntem çağrılarını, veri bozulmasına veya kilitlenmeleri neden olabilir.  
  
-   Birden çok çağrı aşırı yükleme yöntemiyle uygularsanız (`userState` imzası), kendi sınıfınızı kullanıcı durumları veya görev kimlikleri ve bekleyen işlemler karşılık gelen bir koleksiyonu yönetmek için ihtiyacınız olacaktır. Bu koleksiyon ile korunması gerektiğini `lock` bölgeler, çeşitli çağrıları ekleme ve kaldırma nedeni `userState` koleksiyonundaki nesneleri.  
  
-   Yeniden göz önünde bulundurun `CompletedEventArgs` uygulanabilir ve uygun yerlerde sınıfları. Bu durumda, adlandırma yöntem adı ile tutarlı değil çünkü belirli bir temsilci ve <xref:System.EventArgs> türü tek bir yönteme bağlı değil. Ancak, geliştiricilerin üzerinde bir özellikten alınan değerde dönüştürme zorlama <xref:System.EventArgs> hiçbir zaman kullanılabilir.  
  
-   Türetilen bir sınıf yazıyorsanız <xref:System.ComponentModel.Component>değil uygulamak ve kendi yükleme <xref:System.Threading.SynchronizationContext> sınıfı. Uygulama modelleri olmayan bileşenleri, Denetim <xref:System.Threading.SynchronizationContext> kullanılır.  
  
-   Kullandığınızda, çoklu iş parçacığı her tür, büyük olasılıkla kendiniz için çok önemli ve karmaşık hataları ortaya. Çoklu iş parçacığı kullanımlar herhangi bir çözümü uygulamadan önce [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
