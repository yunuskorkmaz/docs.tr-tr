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
ms.openlocfilehash: 561d0759af4f7557bae39540cbb00f8038726ddc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950802"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
Olay tabanlı zaman uyumsuz model, tanıdık olay ve temsilci semantiğinin bulunduğu sınıflarda zaman uyumsuz davranışı açığa çıkarmak için etkili bir yol sağlar. Olay tabanlı zaman uyumsuz model uygulamak için bazı belirli davranış gereksinimlerini izlemeniz gerekir. Aşağıdaki bölümlerde, olay tabanlı zaman uyumsuz düzeniyle takip eden bir sınıfı uyguladığınızda göz önünde bulundurmanız gereken gereksinimler ve yönergeler açıklanır.  
  
 Genel bakış için bkz. [olay tabanlı zaman uyumsuz model uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Gerekli davranış garantisi  
 Olay tabanlı zaman uyumsuz model uygularsanız, sınıfınızın düzgün şekilde davrandığından ve sınıfınızın istemcilerinin bu davranışa güvendiğinden emin olmak için bir dizi garanti sağlamanız gerekir.  
  
### <a name="completion"></a>Tamamlama  
 Başarılı bir tamamlama, hata veya iptal ettiğiniz durumlarda <em>MethodName</em>**tamamlandı** olay işleyicisini her zaman çağırın. Uygulamalar, boşta kaldığı ve tamamlanmanın asla gerçekleşmediği hiçbir durumda hiçbir şekilde karşılaşmamalıdır. Bu kural için bir özel durum, zaman uyumsuz işlemin kendisi tarafından tamamlanmaması için tasarlandıysa.  
  
### <a name="completed-event-and-eventargs"></a>Tamamlanan olay ve EventArgs  
 Her ayrı <em>MethodName</em>**zaman uyumsuz** yöntemi için aşağıdaki tasarım gereksinimlerini uygulayın:  
  
- Yöntemiyle aynı sınıfta <em>MethodName</em>**tamamlandı** olayını tanımlayın.  
  
- Sınıfından türetilen <xref:System.EventArgs> MethodName tamamlandı olayı için bir sınıf ve eşlik eden temsilci tanımlayın. <xref:System.ComponentModel.AsyncCompletedEventArgs> Varsayılan sınıf adı <em>MethodName</em>**CompletedEventArgs**biçiminde olmalıdır.  
  
- Sınıfın MethodName yönteminin dönüş değerlerine özgü olduğundan emin olun. <xref:System.EventArgs> <xref:System.EventArgs> Sınıfını kullandığınızda, geliştiricilerin sonucu saçmasını asla gerektirmemelidir.  
  
     Aşağıdaki kod örneği, bu tasarım gereksiniminin sırasıyla iyi ve hatalı uygulanmasını gösterir.  
  
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
  
- Döndüren metotları <xref:System.EventArgs> `void`döndürmek için bir sınıf tanımlamayın. Bunun yerine, <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfının bir örneğini kullanın.  
  
- <em>MethodName</em>**tamamlandı** olayını her zaman yükseltdiğinizden emin olun. Bu olay başarıyla tamamlandığında, bir hatada veya İptalde oluşturulmalıdır. Uygulamalar, boşta kaldığı ve tamamlanmanın asla gerçekleşmediği hiçbir durumda hiçbir şekilde karşılaşmamalıdır.  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakatığınızdan ve yakalanan özel durumu <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliğe atadığınızdan emin olun.  
  
- Görev tamamlanırken bir hata oluşursa, sonuçlara erişilememelidir. Özelliği olmadığında `null`, <xref:System.EventArgs> yapıdaki herhangi bir özelliğe erişmenin bir özel durum harekete geçirdiğinden emin olun. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> Bu doğrulamayı gerçekleştirmek için yönteminikullanın.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>  
  
- Bir hata olarak zaman aşımı modeli. Zaman aşımı oluştuğunda, <em>MethodName</em>**tamamlandı** olayını yükseltin <xref:System.TimeoutException> ve <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliğine atayın.  
  
- Sınıfınız birden çok eşzamanlı çağırmaları destekliyorsa, <em>MethodName</em>**tamamlandı** olayının uygun `userSuppliedState` nesneyi içerdiğinden emin olun.  
  
- <em>MethodName</em>**tamamlandı** olayının uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="simultaneously-executing-operations"></a>Eşzamanlı olarak çalıştırılan Işlemler  
  
- Sınıfınız birden çok eş zamanlı çağrıyı destekliyorsa, bir nesne değerli durum parametresi ya da çağrılan `userSuppliedState`görev kimliği olan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemeyi tanımlayarak her çağrıyı ayrı olarak izlemek için geliştiriciyi etkinleştirin. Bu parametrenin her zaman <em>MethodName</em>**zaman uyumsuz** yöntemin imzasında son parametre olması gerekir.  
  
- Sınıfınız, nesne değerli durum parametresi veya görev KIMLIĞI alan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemesini TANıMLıYORSA, bu görev kimliğiyle birlikte işlemin ömrünü izlemediğinizden emin olun ve tamamlama işleyicisine geri sağladığınızdan emin olun. Yardım için kullanılabilen yardımcı sınıflar vardır. Eşzamanlılık yönetimi hakkında daha fazla bilgi için bkz [. nasıl yapılır: Olay tabanlı zaman uyumsuz stili](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)destekleyen bir bileşen uygulayın.  
  
- Sınıfınız, durum parametresi olmadan <em>MethodName</em>**zaman uyumsuz** yöntemini tanımlıyorsa ve birden çok eşzamanlı çağırma 'Yı desteklemiyorsa, önceki MethodName parametresinden önce <em>MethodName</em>**zaman uyumsuz** çağırma denemelerinde emin olun **Zaman uyumsuz** çağrı tamamlandı bir <xref:System.InvalidOperationException>oluşturur.  
  
- Genel olarak, `userSuppliedState` parametresi olmayan <em>MethodName</em>**zaman uyumsuz** yöntemi birden çok kez çağrıldığında, birden çok bekleyen işlem olması için bir özel durum oluşturmaz. Sınıfınız açıkça bu durumu işleyemezse bir özel durum oluşturabilir, ancak geliştiricilerin bu birden fazla ayırt edilemeyen geri çağırmaları işleyebileceğini varsayabilirsiniz  
  
### <a name="accessing-results"></a>Sonuçlara erişme  
  
- Zaman uyumsuz işlemin yürütülmesi sırasında bir hata oluşursa, sonuçlara erişilemeyebilir. <xref:System.ComponentModel.AsyncCompletedEventArgs> ' Deki <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> herhangi bir özelliğe erişmenin, tarafından <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>başvurulan özel `null` durumu harekete geçirmediğinden emin olun. Sınıfı bu amaçla <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> yöntemi sağlar. <xref:System.ComponentModel.AsyncCompletedEventArgs>  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir <xref:System.InvalidOperationException> sonuç aldığından emin olun. Bu doğrulamayı gerçekleştirmek için yönteminikullanın.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>  
  
### <a name="progress-reporting"></a>İlerleme raporlaması  
  
- Mümkünse ilerleme raporlamayı destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- Bir **ProgressChanged & lt** veya <em>MethodName</em>**ProgressChanged & lt** olayı uygularsanız, bu işlemin <em>MethodName</em> olayını tamamladıktan sonra belirli bir zaman uyumsuz işlem için oluşturulan bir olay olmadığından emin olun yükseltildi.  
  
- Standart <xref:System.ComponentModel.ProgressChangedEventArgs> Doldurulmakta ise, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman yüzde olarak yorumlanabileceğinden emin olun. Yüzdenin doğru olması gerekmez, ancak bir yüzdeyi temsil etmelidir. İlerleme raporlama ölçümünüzün bir yüzdeden başka bir şey olması gerekiyorsa, <xref:System.ComponentModel.ProgressChangedEventArgs> sınıftan bir sınıf türetirsiniz ve 0 ' dan ayrılın. <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> Yüzde dışında bir raporlama ölçümü kullanmaktan kaçının.  
  
- `ProgressChanged` Olayın uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="isbusy-implementation"></a>Imeşgul uygulama  
  
- Sınıfınız birden çok eşzamanlı `IsBusy` çağırmaları destekliyorsa, bir özelliği açığa çıkarın. Örneğin, XML Web hizmeti proxy 'leri, zaman uyumsuz yöntemlerin `IsBusy` birden çok eş zamanlı etkinleştirmeleri desteklediklerinden bir özelliği kullanıma sunmuyor.  
  
- `true` Özelliği, MethodName zaman uyumsuz yöntemi çağrıldıktan sonra ve MethodName Completed olayı oluşturulduktan önce döndürmelidir. `IsBusy` Aksi takdirde, döndürmelidir `false`. Ve <xref:System.ComponentModel.BackgroundWorker> `IsBusy` bileşenleri, bir özelliği kullanıma sunan sınıfların örnekleridir. <xref:System.Net.WebClient>  
  
### <a name="cancellation"></a>İptal Etme  
  
- Mümkünse iptali destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- İptal durumunda, <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> <xref:System.ComponentModel.AsyncCompletedEventArgs> nesnesinde bayrağını ayarlayın.  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir <xref:System.InvalidOperationException> sonuç aldığından emin olun. Bu doğrulamayı gerçekleştirmek için yönteminikullanın.<xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>  
  
- Bir iptal yöntemine yapılan çağrıların her zaman başarıyla geri dönmesi ve hiçbir zaman özel durum geçirmeyeceğinden emin olun. Genel olarak, bir işlem belirli bir zamanda bir işlemin gerçekten iptal edilebilir olup olmadığı konusunda bilgilendirilmez ve daha önce verilen İptalin başarılı olup olmadığı bildirilmiyor. Ancak, uygulama tamamlanma durumunda bir parçası olduğundan, bir iptal işlemi başarılı olduğunda uygulamaya her zaman bildirim verilir.  
  
- İşlem iptal edildiğinde <em>MethodName</em>**tamamlandı** olayını yükseltin.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve özel durumlar  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakalayın ve <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğin değerini bu özel duruma ayarlayın.  
  
### <a name="threading-and-contexts"></a>İş parçacığı oluşturma ve bağlamlar  
 Sınıfınızın doğru çalışması için, istemcinin olay işleyicilerinin ASP.NET ve Windows Forms uygulamaları da dahil olmak üzere, belirtilen uygulama modeli için uygun iş parçacığında veya bağlamda çağrılması önemlidir. Zaman uyumsuz sınıfınızın herhangi bir uygulama modelinde doğru şekilde davrandığından emin olmak için iki önemli yardımcı sınıfı sağlanır <xref:System.ComponentModel.AsyncOperation> : <xref:System.ComponentModel.AsyncOperationManager>ve.  
  
 <xref:System.ComponentModel.AsyncOperationManager><xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, döndüren bir yöntem sağlar. <xref:System.ComponentModel.AsyncOperation> <em>MethodName</em>**zaman uyumsuz** Yöntem çağrılarınız <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> ve sınıfınız, zaman uyumsuz <xref:System.ComponentModel.AsyncOperation> görevin ömrünü izlemek için döndürülen öğesini kullanır.  
  
 İlerleme durumunu, artımlı sonuçları ve tamamlanmayı istemciye bildirmek için, <xref:System.ComponentModel.AsyncOperation.Post%2A> ve <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> üzerindeki <xref:System.ComponentModel.AsyncOperation>yöntemlerini çağırın. <xref:System.ComponentModel.AsyncOperation>, istemcinin olay işleyicilerinde yapılan çağrıların doğru iş parçacığına veya içeriğe sıralanmasından sorumludur.  
  
> [!NOTE]
> Uygulama modeli ilkesine karşı açıkça gitmek istiyorsanız bu kuralları atlayabilirsiniz, ancak hala olay tabanlı zaman uyumsuz model kullanmanın diğer avantajlarından faydalanabilirsiniz. Örneğin, Windows Forms üzerinde çalışan bir sınıfın ücretsiz olarak iş parçacıklı olmasını isteyebilirsiniz. Geliştiriciler kapsanan kısıtlamaları anlamış olduğu sürece, ücretsiz bir iş parçacıklı sınıf oluşturabilirsiniz. Konsol uygulamaları <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrıların yürütülmesini eşitlemez. Bu, olayların `ProgressChanged` sırada oluşturulmasına neden olabilir. <xref:System.ComponentModel.AsyncOperation.Post%2A> Çağrıların serileştirilmiş yürütülmesini istiyorsanız, bir <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> sınıfı uygulayın ve yükleyebilirsiniz.  
  
 ' I kullanma <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager> zaman uyumsuz işlemlerinizi etkinleştirme hakkında daha fazla bilgi için [bkz. nasıl yapılır: Olay tabanlı zaman uyumsuz stili](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)destekleyen bir bileşen uygulayın.  
  
## <a name="guidelines"></a>Kuralları  
  
- İdeal olarak, her yöntem çağrısı diğerlerinden bağımsız olmalıdır. Paylaşılan kaynaklarla ilgili bağlantısı önlemeyi kullanmaktan kaçının. Kaynaklar, çağırmaları arasında paylaşılırsa, uygulamanızda uygun bir eşitleme mekanizması sağlamanız gerekir.  
  
- İstemcinin eşitleme uygulaması için gerekli olan tasarımlar önerilmez. Örneğin, bir parametre olarak genel statik nesne alan zaman uyumsuz bir metoda sahip olabilirsiniz; Böyle bir yöntemin birden çok eş zamanlı çağırma verisi bozulmaya veya kilitlenmeleri oluşmasına neden olabilir.  
  
- Birden çok çağırma aşırı yüklemesiyle (`userState` İmzada) bir yöntem uygularsanız, sınıfınızın Kullanıcı durumlarının veya görev kimliklerinin ve bunlara karşılık gelen bekleyen işlemlerin bir koleksiyonunu yönetmesi gerekir. Çeşitli etkinleştirmeleri koleksiyondaki nesneleri ekleyip kaldırmasına `lock` `userState` yönelik olan bu koleksiyonun bölgeleriyle korunması gerekir.  
  
- Uygun yerlerde `CompletedEventArgs` sınıfları yeniden kullanmayı düşünün. Bu durumda, belirtilen bir temsilci ve <xref:System.EventArgs> tür tek bir yönteme bağlı olmadığından, adlandırma yöntem adı ile tutarlı değildir. Ancak, geliştiricilerin ' de <xref:System.EventArgs> bir özellikten alınan değeri dönüştürmeyi zorlamak hiç kabul edilebilir değildir.  
  
- Öğesinden <xref:System.ComponentModel.Component>türetilen bir sınıf yazıyorsanız kendi <xref:System.Threading.SynchronizationContext> sınıfınızı uygulamaz ve yüklemeyin. Uygulama modelleri, bileşen değil, kullanılan denetim <xref:System.Threading.SynchronizationContext> .  
  
- Herhangi bir sıralama için çoklu iş parçacığı kullandığınızda, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız. Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce bkz. [yönetilen Iş parçacığı En Iyi yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
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
- [Nasıl yapılır: Olay tabanlı zaman uyumsuz stili destekleyen bileşenleri kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl yapılır: Olay tabanlı zaman uyumsuz stili destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
