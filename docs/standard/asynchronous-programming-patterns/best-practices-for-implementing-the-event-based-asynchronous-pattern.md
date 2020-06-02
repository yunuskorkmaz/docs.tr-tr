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
ms.openlocfilehash: 66979415f2951acc78dc4eb7b2aafe3c84e85397
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289947"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler
Olay tabanlı zaman uyumsuz model, tanıdık olay ve temsilci semantiğinin bulunduğu sınıflarda zaman uyumsuz davranışı açığa çıkarmak için etkili bir yol sağlar. Olay tabanlı zaman uyumsuz model uygulamak için bazı belirli davranış gereksinimlerini izlemeniz gerekir. Aşağıdaki bölümlerde, olay tabanlı zaman uyumsuz düzeniyle takip eden bir sınıfı uyguladığınızda göz önünde bulundurmanız gereken gereksinimler ve yönergeler açıklanır.  
  
 Genel bakış için bkz. [olay tabanlı zaman uyumsuz model uygulama](implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Gerekli davranış garantisi  
 Olay tabanlı zaman uyumsuz model uygularsanız, sınıfınızın düzgün şekilde davrandığından ve sınıfınızın istemcilerinin bu davranışa güvendiğinden emin olmak için bir dizi garanti sağlamanız gerekir.  
  
### <a name="completion"></a>Tamamlama  
 Başarılı bir tamamlama, hata veya iptal ettiğiniz durumlarda <em>MethodName</em>**tamamlandı** olay işleyicisini her zaman çağırın. Uygulamalar, boşta kaldığı ve tamamlanmanın asla gerçekleşmediği hiçbir durumda hiçbir şekilde karşılaşmamalıdır. Bu kural için bir özel durum, zaman uyumsuz işlemin kendisi tarafından tamamlanmaması için tasarlandıysa.  
  
### <a name="completed-event-and-eventargs"></a>Tamamlanan olay ve EventArgs  
 Her ayrı <em>MethodName</em>**zaman uyumsuz** yöntemi için aşağıdaki tasarım gereksinimlerini uygulayın:  
  
- Yöntemiyle aynı sınıfta <em>MethodName</em>**tamamlandı** olayını tanımlayın.  
  
- <xref:System.EventArgs>Sınıfından türetilen <em>MethodName</em>**tamamlandı** olayı için bir sınıf ve eşlik eden temsilci tanımlayın <xref:System.ComponentModel.AsyncCompletedEventArgs> . Varsayılan sınıf adı <em>MethodName</em>**CompletedEventArgs**biçiminde olmalıdır.  
  
- <xref:System.EventArgs>Sınıfın <em>MethodName</em> yönteminin dönüş değerlerine özgü olduğundan emin olun. <xref:System.EventArgs>Sınıfını kullandığınızda, geliştiricilerin sonucu saçmasını asla gerektirmemelidir.  
  
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
  
- Döndüren metotları döndürmek için bir sınıf tanımlamayın <xref:System.EventArgs> `void` . Bunun yerine, sınıfının bir örneğini kullanın <xref:System.ComponentModel.AsyncCompletedEventArgs> .  
  
- <em>MethodName</em>**tamamlandı** olayını her zaman yükseltdiğinizden emin olun. Bu olay başarıyla tamamlandığında, bir hatada veya İptalde oluşturulmalıdır. Uygulamalar, boşta kaldığı ve tamamlanmanın asla gerçekleşmediği hiçbir durumda hiçbir şekilde karşılaşmamalıdır.  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakatığınızdan ve yakalanan özel durumu özelliğe atadığınızdan emin olun <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> .  
  
- Görev tamamlanırken bir hata oluşursa, sonuçlara erişilememelidir. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>Özelliği olmadığında `null` , yapıdaki herhangi bir özelliğe erişmenin <xref:System.EventArgs> bir özel durum harekete geçirdiğinden emin olun. <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>Bu doğrulamayı gerçekleştirmek için yöntemini kullanın.  
  
- Bir hata olarak zaman aşımı modeli. Zaman aşımı oluştuğunda, <em>MethodName</em>**tamamlandı** olayını yükseltin ve <xref:System.TimeoutException> özelliğine atayın <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> .  
  
- Sınıfınız birden çok eşzamanlı çağırmaları destekliyorsa, <em>MethodName</em>**tamamlandı** olayının uygun nesneyi içerdiğinden emin olun `userSuppliedState` .  
  
- <em>MethodName</em>**tamamlandı** olayının uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="simultaneously-executing-operations"></a>Eşzamanlı olarak çalıştırılan Işlemler  
  
- Sınıfınız birden çok eş zamanlı çağrıyı destekliyorsa, bir nesne değerli durum parametresi ya da çağrılan görev KIMLIĞI olan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemeyi tanımlayarak her çağrıyı ayrı olarak izlemek için geliştiriciyi etkinleştirin `userSuppliedState` . Bu parametrenin her zaman <em>MethodName</em>**zaman uyumsuz** yöntemin imzasında son parametre olması gerekir.  
  
- Sınıfınız, nesne değerli durum parametresi veya görev KIMLIĞI alan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemesini TANıMLıYORSA, bu görev kimliğiyle birlikte işlemin ömrünü izlemediğinizden emin olun ve tamamlama işleyicisine geri sağladığınızdan emin olun. Yardım için kullanılabilen yardımcı sınıflar vardır. Eşzamanlılık yönetimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşen uygulama](component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Sınıfınız, durum parametresi olmadan <em>MethodName</em>**zaman uyumsuz** yöntemini tanımlar ve birden çok eşzamanlı çağırma 'Yı desteklemiyorsa, önceki <em>MethodName</em>**zaman uyumsuz** çağrının tamamlanmadan önce <em>MethodName</em>**zaman uyumsuz** çağırma girişiminin bir örneğini başlattığınızdan emin olun <xref:System.InvalidOperationException> .  
  
- Genel olarak, parametresi olmayan <em>MethodName</em>**zaman uyumsuz** yöntemi `userSuppliedState` birden çok kez çağrıldığında, birden çok bekleyen işlem olması için bir özel durum oluşturmaz. Sınıfınız açıkça bu durumu işleyemezse bir özel durum oluşturabilir, ancak geliştiricilerin bu birden fazla ayırt edilemeyen geri çağırmaları işleyebileceğini varsayabilirsiniz  
  
### <a name="accessing-results"></a>Sonuçlara erişme  
  
- Zaman uyumsuz işlemin yürütülmesi sırasında bir hata oluşursa, sonuçlara erişilemeyebilir. ' Deki herhangi bir özelliğe erişmenin, <xref:System.ComponentModel.AsyncCompletedEventArgs> <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> `null` tarafından başvurulan özel durumu harekete geçirmediğinden emin olun <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> . <xref:System.ComponentModel.AsyncCompletedEventArgs>Sınıfı <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> Bu amaçla yöntemi sağlar.  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir sonuç aldığından emin olun <xref:System.InvalidOperationException> . <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>Bu doğrulamayı gerçekleştirmek için yöntemini kullanın.  
  
### <a name="progress-reporting"></a>İlerleme raporlaması  
  
- Mümkünse ilerleme raporlamayı destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- Bir **ProgressChanged & lt** veya <em>MethodName</em>**ProgressChanged & lt** olayı uygularsanız, söz konusu işlemin <em>MethodName</em>**olayı oluşturulduktan** sonra belirli bir zaman uyumsuz işlem için oluşturulan bir olay olmadığından emin olun.  
  
- Standart <xref:System.ComponentModel.ProgressChangedEventArgs> Doldurulmakta ise, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman yüzde olarak yorumlanabileceğinden emin olun. Yüzdenin doğru olması gerekmez, ancak bir yüzdeyi temsil etmelidir. İlerleme raporlama ölçümünüzün bir yüzdeden başka bir şey olması gerekiyorsa, sınıftan bir sınıf türetirsiniz <xref:System.ComponentModel.ProgressChangedEventArgs> ve 0 ' dan ayrılın <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> . Yüzde dışında bir raporlama ölçümü kullanmaktan kaçının.  
  
- `ProgressChanged`Olayın uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="isbusy-implementation"></a>Imeşgul uygulama  
  
- `IsBusy`Sınıfınız birden çok eşzamanlı çağırmaları destekliyorsa, bir özelliği açığa çıkarın. Örneğin, XML Web hizmeti proxy 'leri, `IsBusy` zaman uyumsuz yöntemlerin birden çok eş zamanlı etkinleştirmeleri desteklediklerinden bir özelliği kullanıma sunmuyor.  
  
- `IsBusy`Özelliği, `true` <em>MethodName</em>**zaman uyumsuz** yöntemi çağrıldıktan sonra ve <em>MethodName</em>**Completed** olayı oluşturulduktan önce döndürmelidir. Aksi takdirde, döndürmelidir `false` . <xref:System.ComponentModel.BackgroundWorker>Ve <xref:System.Net.WebClient> bileşenleri, bir özelliği kullanıma sunan sınıfların örnekleridir `IsBusy` .  
  
### <a name="cancellation"></a>İptal  
  
- Mümkünse iptali destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- İptal durumunda, <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> nesnesinde bayrağını ayarlayın <xref:System.ComponentModel.AsyncCompletedEventArgs> .  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir sonuç aldığından emin olun <xref:System.InvalidOperationException> . <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType>Bu doğrulamayı gerçekleştirmek için yöntemini kullanın.  
  
- Bir iptal yöntemine yapılan çağrıların her zaman başarıyla geri dönmesi ve hiçbir zaman özel durum geçirmeyeceğinden emin olun. Genel olarak, bir işlem belirli bir zamanda bir işlemin gerçekten iptal edilebilir olup olmadığı konusunda bilgilendirilmez ve daha önce verilen İptalin başarılı olup olmadığı bildirilmiyor. Ancak, uygulama tamamlanma durumunda bir parçası olduğundan, bir iptal işlemi başarılı olduğunda uygulamaya her zaman bildirim verilir.  
  
- İşlem iptal edildiğinde <em>MethodName</em>**tamamlandı** olayını yükseltin.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve Özel Durumlar  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakalayın ve <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğin değerini bu özel duruma ayarlayın.  
  
### <a name="threading-and-contexts"></a>İş parçacığı oluşturma ve bağlamlar  
 Sınıfınızın doğru çalışması için, istemcinin olay işleyicilerinin ASP.NET ve Windows Forms uygulamaları da dahil olmak üzere, belirtilen uygulama modeli için uygun iş parçacığında veya bağlamda çağrılması önemlidir. Zaman uyumsuz sınıfınızın herhangi bir uygulama modelinde doğru şekilde davrandığından emin olmak için iki önemli yardımcı sınıfı sağlanır: <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager> .  
  
 <xref:System.ComponentModel.AsyncOperationManager>, döndüren bir yöntem sağlar <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> <xref:System.ComponentModel.AsyncOperation> . <em>MethodName</em>**zaman uyumsuz** Yöntem çağrılarınız <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> ve sınıfınız, <xref:System.ComponentModel.AsyncOperation> zaman uyumsuz görevin ömrünü izlemek için döndürülen öğesini kullanır.  
  
 İlerleme durumunu, artımlı sonuçları ve tamamlanmayı istemciye bildirmek için, <xref:System.ComponentModel.AsyncOperation.Post%2A> ve <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> üzerindeki yöntemlerini çağırın <xref:System.ComponentModel.AsyncOperation> . <xref:System.ComponentModel.AsyncOperation>, istemcinin olay işleyicilerinde yapılan çağrıların doğru iş parçacığına veya içeriğe sıralanmasından sorumludur.  
  
> [!NOTE]
> Uygulama modeli ilkesine karşı açıkça gitmek istiyorsanız bu kuralları atlayabilirsiniz, ancak hala olay tabanlı zaman uyumsuz model kullanmanın diğer avantajlarından faydalanabilirsiniz. Örneğin, Windows Forms üzerinde çalışan bir sınıfın ücretsiz olarak iş parçacıklı olmasını isteyebilirsiniz. Geliştiriciler kapsanan kısıtlamaları anlamış olduğu sürece, ücretsiz bir iş parçacıklı sınıf oluşturabilirsiniz. Konsol uygulamaları çağrıların yürütülmesini eşitlemez <xref:System.ComponentModel.AsyncOperation.Post%2A> . Bu, olayların sırada oluşturulmasına neden olabilir `ProgressChanged` . Çağrıların serileştirilmiş yürütülmesini istiyorsanız <xref:System.ComponentModel.AsyncOperation.Post%2A> , bir sınıfı uygulayın ve yükleyebilirsiniz <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> .  
  
 <xref:System.ComponentModel.AsyncOperation>' I kullanma ve zaman uyumsuz işlemlerinizi etkinleştirme hakkında daha fazla bilgi için <xref:System.ComponentModel.AsyncOperationManager> bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz bir şekli destekleyen bir bileşen uygulama](component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Yönergeler  
  
- İdeal olarak, her yöntem çağrısı diğerlerinden bağımsız olmalıdır. Paylaşılan kaynaklarla ilgili bağlantısı önlemeyi kullanmaktan kaçının. Kaynaklar, çağırmaları arasında paylaşılırsa, uygulamanızda uygun bir eşitleme mekanizması sağlamanız gerekir.  
  
- İstemcinin eşitleme uygulaması için gerekli olan tasarımlar önerilmez. Örneğin, bir parametre olarak genel statik nesne alan zaman uyumsuz bir metoda sahip olabilirsiniz; Böyle bir yöntemin birden çok eş zamanlı çağırma verisi bozulmaya veya kilitlenmeleri oluşmasına neden olabilir.  
  
- Birden çok çağırma aşırı yüklemesiyle (İmzada) bir yöntem uygularsanız `userState` , sınıfınızın Kullanıcı durumlarının veya görev kimliklerinin ve bunlara karşılık gelen bekleyen işlemlerin bir koleksiyonunu yönetmesi gerekir. `lock`Çeşitli etkinleştirmeleri koleksiyondaki nesneleri ekleyip kaldırmasına yönelik olan bu koleksiyonun bölgeleriyle korunması gerekir `userState` .  
  
- `CompletedEventArgs`Uygun yerlerde sınıfları yeniden kullanmayı düşünün. Bu durumda, belirtilen bir temsilci ve <xref:System.EventArgs> tür tek bir yönteme bağlı olmadığından, adlandırma yöntem adı ile tutarlı değildir. Ancak, geliştiricilerin ' de bir özellikten alınan değeri dönüştürmeyi zorlamak <xref:System.EventArgs> hiç kabul edilebilir değildir.  
  
- Öğesinden türetilen bir sınıf yazıyorsanız <xref:System.ComponentModel.Component> kendi sınıfınızı uygulamaz ve yüklemeyin <xref:System.Threading.SynchronizationContext> . Uygulama modelleri, bileşen değil, kullanılan denetim <xref:System.Threading.SynchronizationContext> .  
  
- Herhangi bir sıralama için çoklu iş parçacığı kullandığınızda, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız. Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce bkz. [yönetilen Iş parçacığı En Iyi yöntemleri](../threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)
