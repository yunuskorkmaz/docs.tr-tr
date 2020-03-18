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
ms.openlocfilehash: 439b862612d7997c9277ffb2cf4f15b14bd0b106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156055"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
Olay tabanlı Asynchronous Pattern, tanıdık olay ve temsilci semantiği ile sınıflarda asynchronous davranışı ortaya çıkarmak için etkili bir yol sağlar. Olay tabanlı Eşzamanlılık uygulamak için bazı belirli davranış gereksinimlerini izlemeniz gerekir. Aşağıdaki bölümlerde, Olay tabanlı Asynchronous Deseni'ni izleyen bir sınıf uygularken göz önünde bulundurmanız gereken gereksinimler ve yönergeler açıklanmaktadır.  
  
 Genel bakış için bkz: [Olay tabanlı Asynchronous Deseni'ni uygulama.](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
  
## <a name="required-behavioral-guarantees"></a>Gerekli Davranış Salahiyetleri  
 Olay tabanlı Eşzamanlı Desen'i uygularsanız, sınıfınızın düzgün davranmasını ve sınıfınızın istemcilerinin bu tür davranışlara güvenebilmesini sağlamak için bir dizi garanti sağlamanız gerekir.  
  
### <a name="completion"></a>Tamamlama  
 Başarılı bir tamamlanma, hata veya iptal olduğunda Her zaman <em>MethodName</em>**Tamamlanmış** olay işleyicisini çağırın. Uygulamalar boşta kaldıkları ve tamamlanmadıkları bir durumla asla karşılaşmamalıdır. Bu kuralın bir istisnası, eşzamanlı işlemin kendisi asla tamamlanamayacak şekilde tasarlanmış olmasıdır.  
  
### <a name="completed-event-and-eventargs"></a>Tamamlanan Etkinlik ve EventArgs  
 Her ayrı <em>MethodName</em>**Async** yöntemi için aşağıdaki tasarım gereksinimlerini uygulayın:  
  
- Yöntemle aynı sınıfta bir <em>MethodName</em>**Tamamlandı** olayını tanımlayın.  
  
- Sınıftan <xref:System.EventArgs> türeyen <em>MethodName</em>**Completed** olayı için bir sınıf <xref:System.ComponentModel.AsyncCompletedEventArgs> ve beraberindeki temsilci tanımlayın. Varsayılan sınıf adı <em>MethodName</em>**CompletedEventArgs**şeklinde olmalıdır.  
  
- <xref:System.EventArgs> Sınıfın <em>MethodName</em> yönteminin iade değerlerine özgü olduğundan emin olun. <xref:System.EventArgs> Sınıfı kullandığınızda, geliştiricilerin sonucu kullanmasını asla gerektirmezsiniz.  
  
     Aşağıdaki kod örneği, bu tasarım gereksiniminin sırasıyla iyi ve kötü bir şekilde uygulanmasını gösterir.  
  
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
  
- Döndüren <xref:System.EventArgs> yöntemler için bir sınıf `void`tanımlamayın. Bunun yerine, sınıfın <xref:System.ComponentModel.AsyncCompletedEventArgs> bir örneğini kullanın.  
  
- <em>MethodName</em>**Tamamlanan** olayı her zaman yükselttiğinizden emin olun. Bu olay başarılı bir şekilde tamamlandığında, bir hatada veya iptalde yükseltilmelidir. Uygulamalar boşta kaldıkları ve tamamlanmadıkları bir durumla asla karşılaşmamalıdır.  
  
- Eşzamanlı işlemde oluşan özel durumları yakaladığınızı ve yakalanan özel durumu <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliğe atadığınızdan emin olun.  
  
- Görevi tamamlayan bir hata varsa, sonuçlara erişilememelidir. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> Özellik olmadığında, `null`yapıdaki herhangi bir özelliğe erişimin bir özel durum doğurduğundan <xref:System.EventArgs> emin olun. Bu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> doğrulamayı gerçekleştirmek için yöntemi kullanın.  
  
- Bir zaman dilimini hata olarak modelle. Bir zaman dışında kalma gerçekleştiğinde, <em>MethodName</em>**Tamamlanan** <xref:System.TimeoutException> olayı <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> yükseltin ve tesise bir aat layın.  
  
- Sınıfınız birden çok eşzamanlı çağrıyı destekliyorsa, <em>MethodName</em>**Tamamlanan** olayın uygun `userSuppliedState` nesneyi içerdiğinden emin olun.  
  
- <em>MethodName</em>**Tamamlanan** olayın uygun iş parçacığı üzerinde ve uygulama yaşam döngüsünde uygun zamanda yükseltilmesini sağlayın. Daha fazla bilgi için İş Parçacığı ve Bağlamlar bölümüne bakın.  
  
### <a name="simultaneously-executing-operations"></a>İşlemleri Aynı Anda Yürütme  
  
- Sınıfınız birden çok eşzamanlı çağrıyı destekliyorsa, nesne değerinde bir durum parametresi veya görev kimliği alan <em>MethodName</em>**Async** aşırı yükünü `userSuppliedState`tanımlayarak geliştiricinin her çağrıyı ayrı ayrı izlemesini sağlar. Bu parametre her zaman <em>MethodName</em>**Async** yönteminin imzasındaki son parametre olmalıdır.  
  
- Sınıfınız, nesne değerinde bir durum parametresi veya görev kimliği alan <em>MethodName</em>**Async** aşırı yükünü tanımlıyorsa, bu görev kimliğiyle işlemin ömrünü izlediğinizden emin olun ve bunu tamamlama işleyicisine geri sağladığınızdan emin olun. Yardımcı sınıflar yardımcı olabilir. Eşzamanlılık yönetimi hakkında daha fazla bilgi için [bkz: Olay tabanlı Asynchronous Deseni destekleyen bir Bileşeni uygulama.](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
  
- Sınıfınız, durum parametresi olmadan <em>MethodName</em>**Async** yöntemini tanımlıyorsa ve birden çok eşzamanlı çağrıyı desteklemiyorsa, önceki <em>MethodName</em>**Async** çağırması <xref:System.InvalidOperationException>tamamlanmadan önce <em>MethodName</em>**Async'i** çağırmak için herhangi bir girişimin bir .  
  
- Genel olarak, `userSuppliedState` parametresi olmayan <em>MethodName</em>**Async** yöntemi birden çok kez çağrılması durumunda, birden çok bekleyen işlem olması için bir özel durum çıkarmayın. Sınıfınız açıkça bu durumu kaldıramıyorsa bir özel durum yükseltebilirsiniz, ancak geliştiricilerin bu birden çok ayırt edilemeyen geri aramaları işleyebileceğini varsayabilirsiniz  
  
### <a name="accessing-results"></a>Sonuçlara Erişim  
  
- Eşil işlemin yürütülmesi sırasında bir hata varsa, sonuçlara erişilemez. Herhangi <xref:System.ComponentModel.AsyncCompletedEventArgs> bir özelliğe erişimin, <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> `null` başvurulan <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>özel durumu yükseltmediğinden emin olun. Sınıf <xref:System.ComponentModel.AsyncCompletedEventArgs> bu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> amaç için yöntemi sağlar.  
  
- Sonuca erişim için herhangi bir <xref:System.InvalidOperationException> girişimin, işlemin iptal edildiğini belirten bir artış olduğundan emin olun. Bu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> doğrulamayı gerçekleştirmek için yöntemi kullanın.  
  
### <a name="progress-reporting"></a>İlerleme Raporlama  
  
- Mümkünse ilerleme raporlamayı destekleyin. Bu, geliştiricilerin sınıfınızı kullanırken daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak tanır.  
  
- **Bir ProgressChanged** veya <em>MethodName</em>**ProgressChanged** olayı uygularsanız, bu işlemin <em>MethodName</em>**Tamamlanan** olayı yükseltildikten sonra belirli bir eşzamanlı işlem için bu tür olayların yükseltilmiş olmadığından emin olun.  
  
- Standart <xref:System.ComponentModel.ProgressChangedEventArgs> dolduruluyorsa, standardın <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman bir yüzde olarak yorumlanadığından emin olun. Yüzdenin doğru olması gerekmez, ancak bir yüzdeyi temsil etmelidir. İlerleme raporlama ölçümünüzün yüzdeden başka bir şey olması <xref:System.ComponentModel.ProgressChangedEventArgs> gerekiyorsa, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> sınıftan bir sınıf türetin ve 0'da ayrılın. Yüzde dışında bir raporlama ölçümü kullanmaktan kaçının.  
  
- `ProgressChanged` Olayın uygun iş parçacığı üzerinde ve uygulama yaşam döngüsünde uygun zamanda yükseltilmesini sağlayın. Daha fazla bilgi için İş Parçacığı ve Bağlamlar bölümüne bakın.  
  
### <a name="isbusy-implementation"></a>IsBusy Uygulaması  
  
- Sınıfınız birden `IsBusy` çok eşzamanlı çağrıyı destekliyorsa bir özelliği açığa çıkarmayın. Örneğin, XML Web hizmeti vekilleri, `IsBusy` eşzamanlı eşzamanlı yöntemlerin birden çok çağrılarını destekledikleri için bir özelliği açığa çıkarmaz.  
  
- `IsBusy` Özellik, MethodName**Async** yöntemi çağrıldıktan ve <em>MethodName</em> <em>MethodName</em>**Tamamlanan** olay yükseltilmeden önce geri dönmelidir. `true` Aksi takdirde `false`geri dönmelidir. Ve <xref:System.ComponentModel.BackgroundWorker> <xref:System.Net.WebClient> bileşenleri bir `IsBusy` özelliği ortaya sınıfların örnekleridir.  
  
### <a name="cancellation"></a>İptal  
  
- Mümkünse iptali destekleyin. Bu, geliştiricilerin sınıfınızı kullanırken daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak tanır.  
  
- İptal durumunda, <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> <xref:System.ComponentModel.AsyncCompletedEventArgs> nesneye bayrağı ayarlayın.  
  
- Sonuca erişim için herhangi bir <xref:System.InvalidOperationException> girişimin, işlemin iptal edildiğini belirten bir artış olduğundan emin olun. Bu <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> doğrulamayı gerçekleştirmek için yöntemi kullanın.  
  
- İptal yöntemine yapılan çağrıların her zaman başarılı bir şekilde geri döndüğünden ve asla bir özel durum çıkarmadığından emin olun. Genel olarak, bir istemciye herhangi bir zamanda bir işlemin gerçekten iptal edilip edilemeyeceği bildirilmez ve daha önce verilmiş bir iptalişleminin başarılı olup olmadığı konusunda bilgilendirilmez. Ancak, başvuru tamamlanma durumunda yer aldığından, iptal başarılı olduğunda başvuruya her zaman bildirim verilir.  
  
- İşlem iptal edildiğinde <em>MethodName</em>**Tamamlandı** olayını yükseltin.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve Özel Durumlar  
  
- Eşzamanlı işlemde oluşan özel durumları yakalayın ve özelliğin <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> değerini bu özel durum için ayarlayın.  
  
### <a name="threading-and-contexts"></a>İş Parçacığı ve Bağlamlar  
 Sınıfınızın doğru çalışması için, istemcinin olay işleyicilerinin ASP.NET ve Windows Forms uygulamaları da dahil olmak üzere, verilen uygulama modeli için uygun iş parçacığı veya bağlam üzerinde çağrılması önemlidir. Eşkron sınıfın herhangi bir uygulama modeli altında doğru şekilde şekilde şekilde diğinden emin <xref:System.ComponentModel.AsyncOperation> <xref:System.ComponentModel.AsyncOperationManager>olmak için iki önemli yardımcı sınıf sağlanır: ve .  
  
 <xref:System.ComponentModel.AsyncOperationManager>bir <xref:System.ComponentModel.AsyncOperation>yöntem <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>sağlar, bir . <em>MethodName</em>**Async** yönteminiz çağrıları <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> ve <xref:System.ComponentModel.AsyncOperation> sınıfınız, asynchronous görevin ömrünü izlemek için döndürülenleri kullanır.  
  
 İlerlemeyi, artımlı sonuçları ve tamamlanması nı istemciye <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> bildirmek <xref:System.ComponentModel.AsyncOperation>için, ''nin ' üzerindeki <xref:System.ComponentModel.AsyncOperation.Post%2A> yöntemleri ve yöntemleri ni <xref:System.ComponentModel.AsyncOperation>istemcinin olay işleyicilerine yapılan çağrıları uygun iş parçacığına veya bağlama ya da bağlama da mareşallemekten sorumludur.  
  
> [!NOTE]
> Uygulama modelinin ilkesine açıkça karşı çıkmak istiyorsanız, ancak yine de Olay tabanlı Asynchronous Deseni'ni kullanmanın diğer avantajlarından yararlanın. Örneğin, Windows Forms'ta çalışan bir sınıfın serbest iş parçacığı olmasını isteyebilirsiniz. Geliştiriciler zımni kısıtlamaları anladığı sürece, ücretsiz iş parçacığı sınıfı oluşturabilirsiniz. Konsol uygulamaları çağrıların yürütülmesini <xref:System.ComponentModel.AsyncOperation.Post%2A> eşitlemez. Bu, `ProgressChanged` olayların sıra dışı olarak yükseltilmesine neden olabilir. Çağrıları seri olarak yürütmek <xref:System.ComponentModel.AsyncOperation.Post%2A> istiyorsanız, bir <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> sınıf uygulayın ve yükleyin.  
  
 Eşzamanlı işlemlerinizi <xref:System.ComponentModel.AsyncOperation> kullanma <xref:System.ComponentModel.AsyncOperationManager> ve etkinleştirme hakkında daha fazla bilgi için [bkz: Olay tabanlı Eşzamanlı Deseni destekleyen bir Bileşen uygulama.](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
  
## <a name="guidelines"></a>Yönergeler  
  
- İdeal olarak, her yöntem çağırma diğerlerinden bağımsız olmalıdır. Çağrıları paylaşılan kaynaklarla birleştirmekten kaçınmalısınız. Kaynaklar davetler arasında paylaşılacaksa, uygulamanızda uygun bir eşitleme mekanizması sağlamanız gerekir.  
  
- İstemcinin eşitleme uygulamasını gerektiren tasarımlar önerilmez. Örneğin, parametre olarak global statik bir nesne alan bir eşzamanlı yöntem olabilir; böyle bir yöntemin birden çok eşzamanlı çağrıları veri bozulması veya kilitlenmelere neden olabilir.  
  
- Birden çok çağrı lı aşırı yükleme (imzada)`userState` içeren bir yöntem uygularsanız, sınıfınızın kullanıcı durumları veya görev kimliklerini ve bunların karşılık gelen bekleyen işlemleri bir koleksiyon yönetmesi gerekir. Çeşitli çağırmalar koleksiyondaki nesneleri ekleyip kaldırdığından, `lock` `userState` bu koleksiyon bölgelerle birlikte korunmalıdır.  
  
- Mümkün ve `CompletedEventArgs` uygun olan yerlerde sınıfları yeniden kullanmayı düşünün. Belirli bir temsilci ve <xref:System.EventArgs> tür tek bir yönteme bağlı olmadığından, bu durumda adlandırma yöntem adı ile tutarlı değildir. Ancak, geliştiricileri bir mülkten alınan değeri <xref:System.EventArgs> bir mülkte atmaya zorlamak asla kabul edilemez.  
  
- Eğer türetilmiş bir sınıf <xref:System.ComponentModel.Component>yazarsanız, uygulamak ve kendi <xref:System.Threading.SynchronizationContext> sınıf yüklemeyin. Uygulama modelleri, bileşenleri değil, kullanılan kontrol. <xref:System.Threading.SynchronizationContext>  
  
- Herhangi bir türde çoklu iş parçacığı kullandığınızda, kendinizi çok ciddi ve karmaşık hatalara maruz bırakabilirsiniz. Çok iş parçacığı kullanan herhangi bir çözüm uygulamadan önce, [Yönetilen İş Parçacığı En İyi Uygulamaları'na](../../../docs/standard/threading/managed-threading-best-practices.md)bakın.  
  
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
