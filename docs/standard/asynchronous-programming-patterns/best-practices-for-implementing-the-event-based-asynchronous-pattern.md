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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156055"
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
  
- <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfından türetilen <em>MethodName</em>**tamamlandı** olayı için bir <xref:System.EventArgs> sınıfı ve eşlik eden temsilci tanımlayın. Varsayılan sınıf adı <em>MethodName</em>**CompletedEventArgs**biçiminde olmalıdır.  
  
- <xref:System.EventArgs> sınıfının <em>MethodName</em> yönteminin dönüş değerlerine özgü olduğundan emin olun. <xref:System.EventArgs> sınıfını kullandığınızda, geliştiricilerin sonucu saçmasını asla gerektirmemelidir.  
  
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
  
- `void`döndüren metotları döndürmek için bir <xref:System.EventArgs> sınıfı tanımlamayın. Bunun yerine, <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfının bir örneğini kullanın.  
  
- <em>MethodName</em>**tamamlandı** olayını her zaman yükseltdiğinizden emin olun. Bu olay başarıyla tamamlandığında, bir hatada veya İptalde oluşturulmalıdır. Uygulamalar, boşta kaldığı ve tamamlanmanın asla gerçekleşmediği hiçbir durumda hiçbir şekilde karşılaşmamalıdır.  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakalayıp <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliğine yakalanan özel durumu atadığınızdan emin olun.  
  
- Görev tamamlanırken bir hata oluşursa, sonuçlara erişilememelidir. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği `null`olmadığında, <xref:System.EventArgs> yapısındaki herhangi bir özelliğe erişmenin bir özel durum harekete geçirdiğinden emin olun. Bu doğrulamayı gerçekleştirmek için <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> yöntemini kullanın.  
  
- Bir hata olarak zaman aşımı modeli. Zaman aşımı oluştuğunda, <em>MethodName</em>**tamamlandı** olayını yükseltin ve <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliğine bir <xref:System.TimeoutException> atayın.  
  
- Sınıfınız birden çok eşzamanlı çağırmaları destekliyorsa, <em>MethodName</em>**tamamlandı** olayının uygun `userSuppliedState` nesnesini içerdiğinden emin olun.  
  
- <em>MethodName</em>**tamamlandı** olayının uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="simultaneously-executing-operations"></a>Eşzamanlı olarak çalıştırılan Işlemler  
  
- Sınıfınız birden çok eş zamanlı çağrıyı destekliyorsa, bir nesne değerli durum parametresi veya `userSuppliedState`adlı görev KIMLIĞI alan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemeyi tanımlayarak her çağrıyı ayrı olarak izlemek için geliştiriciyi etkinleştirin. Bu parametrenin her zaman <em>MethodName</em>**zaman uyumsuz** yöntemin imzasında son parametre olması gerekir.  
  
- Sınıfınız, nesne değerli durum parametresi veya görev KIMLIĞI alan <em>MethodName</em>**zaman uyumsuz** aşırı yüklemesini TANıMLıYORSA, bu görev kimliğiyle birlikte işlemin ömrünü izlemediğinizden emin olun ve tamamlama işleyicisine geri sağladığınızdan emin olun. Yardım için kullanılabilen yardımcı sınıflar vardır. Eşzamanlılık yönetimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz kalıbı destekleyen bir bileşen uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
- Sınıfınız, durum parametresi olmadan <em>MethodName</em>**zaman uyumsuz** yöntemini tanımlıyorsa ve Çoklu eşzamanlı çağırmaları desteklemiyorsa, önceki <em>MethodName</em>**zaman uyumsuz** çağrının tamamlanmadan önce <em>MethodName</em>**zaman uyumsuz** çağırma denemesinin bir <xref:System.InvalidOperationException>harekete geçirdiğinden emin olun.  
  
- Genel olarak, birden çok bekleyen işlem olması için `userSuppliedState` parametresi olmayan <em>MethodName</em>**zaman uyumsuz** yöntemi birden çok kez çağrıldığında bir özel durum oluşturmaz. Sınıfınız açıkça bu durumu işleyemezse bir özel durum oluşturabilir, ancak geliştiricilerin bu birden fazla ayırt edilemeyen geri çağırmaları işleyebileceğini varsayabilirsiniz  
  
### <a name="accessing-results"></a>Sonuçlara erişme  
  
- Zaman uyumsuz işlemin yürütülmesi sırasında bir hata oluşursa, sonuçlara erişilemeyebilir. <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> `null` <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>tarafından başvurulan özel durumu harekete geçirmediğinde <xref:System.ComponentModel.AsyncCompletedEventArgs> herhangi bir özelliğe erişimi olduğundan emin olun. <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı, bu amaçla <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> yöntemi sağlar.  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir <xref:System.InvalidOperationException> harekete geçirdiğinden emin olun. Bu doğrulamayı gerçekleştirmek için <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
### <a name="progress-reporting"></a>İlerleme raporlaması  
  
- Mümkünse ilerleme raporlamayı destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- Bir **ProgressChanged & lt** veya <em>MethodName</em>**ProgressChanged & lt** olayı uygularsanız, söz konusu işlemin <em>MethodName</em>**olayı oluşturulduktan** sonra belirli bir zaman uyumsuz işlem için oluşturulan bir olay olmadığından emin olun.  
  
- Standart <xref:System.ComponentModel.ProgressChangedEventArgs> Doldurulmakta ise, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> her zaman yüzde olarak yorumlanabileceğinden emin olun. Yüzdenin doğru olması gerekmez, ancak bir yüzdeyi temsil etmelidir. İlerleme raporlama ölçümünüzün yüzde dışında bir şey olması gerekiyorsa, <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfından bir sınıf türetebilir ve <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 0 ' a bırakın. Yüzde dışında bir raporlama ölçümü kullanmaktan kaçının.  
  
- `ProgressChanged` olayının uygun iş parçacığında ve uygulama yaşam döngüsünde uygun zamanda yapıldığından emin olun. Daha fazla bilgi için bkz. Threading ve bağlamları bölümü.  
  
### <a name="isbusy-implementation"></a>Imeşgul uygulama  
  
- Sınıfınız birden çok eş zamanlı çağırma destekliyorsa `IsBusy` özelliğini açığa çıkarın. Örneğin, XML Web hizmeti proxy 'leri, zaman uyumsuz yöntemlerin birden çok eş zamanlı olarak çağırmaları desteklediklerinden bir `IsBusy` özelliği sunmaz.  
  
- `IsBusy` özelliği, <em>MethodName</em>**zaman uyumsuz** yöntemi çağrıldıktan sonra ve <em>methodname</em>**Completed** olayı oluşturulduktan önce `true` döndürmelidir. Aksi takdirde, `false`döndürmelidir. <xref:System.ComponentModel.BackgroundWorker> ve <xref:System.Net.WebClient> bileşenleri, bir `IsBusy` özelliğini kullanıma sunan sınıfların örnekleridir.  
  
### <a name="cancellation"></a>İptal  
  
- Mümkünse iptali destekler. Bu, geliştiricilerin sınıfınızı kullandıklarında daha iyi bir uygulama kullanıcı deneyimi sağlamasına olanak sağlar.  
  
- İptal durumunda, <xref:System.ComponentModel.AsyncCompletedEventArgs> nesnesinde <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> bayrağını ayarlayın.  
  
- Sonuca erişim girişiminin işlemin iptal edildiğini belirten bir <xref:System.InvalidOperationException> harekete geçirdiğinden emin olun. Bu doğrulamayı gerçekleştirmek için <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
- Bir iptal yöntemine yapılan çağrıların her zaman başarıyla geri dönmesi ve hiçbir zaman özel durum geçirmeyeceğinden emin olun. Genel olarak, bir işlem belirli bir zamanda bir işlemin gerçekten iptal edilebilir olup olmadığı konusunda bilgilendirilmez ve daha önce verilen İptalin başarılı olup olmadığı bildirilmiyor. Ancak, uygulama tamamlanma durumunda bir parçası olduğundan, bir iptal işlemi başarılı olduğunda uygulamaya her zaman bildirim verilir.  
  
- İşlem iptal edildiğinde <em>MethodName</em>**tamamlandı** olayını yükseltin.  
  
### <a name="errors-and-exceptions"></a>Hatalar ve Özel Durumlar  
  
- Zaman uyumsuz işlemde oluşan tüm özel durumları yakalayın ve <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinin değerini bu özel duruma ayarlayın.  
  
### <a name="threading-and-contexts"></a>İş parçacığı oluşturma ve bağlamlar  
 Sınıfınızın doğru çalışması için, istemcinin olay işleyicilerinin ASP.NET ve Windows Forms uygulamaları da dahil olmak üzere, belirtilen uygulama modeli için uygun iş parçacığında veya bağlamda çağrılması önemlidir. Zaman uyumsuz sınıfınızın herhangi bir uygulama modelinde doğru şekilde davrandığından emin olmak için iki önemli yardımcı sınıfı sağlanır: <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager>, bir <xref:System.ComponentModel.AsyncOperation>döndüren <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>bir yöntem sağlar. <em>MethodName</em>**zaman uyumsuz** yönteminiz <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> çağırır ve sınıfınız, zaman uyumsuz görevin ömrünü izlemek için döndürülen <xref:System.ComponentModel.AsyncOperation> kullanır.  
  
 İstemciye ilerleme durumunu, artımlı sonuçları ve tamamlamayı raporlamak için <xref:System.ComponentModel.AsyncOperation><xref:System.ComponentModel.AsyncOperation.Post%2A> ve <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> yöntemlerini çağırın. <xref:System.ComponentModel.AsyncOperation>, istemcinin olay işleyicilerindeki çağrıları uygun iş parçacığına veya içeriğe sıralama işleminden sorumludur.  
  
> [!NOTE]
> Uygulama modeli ilkesine karşı açıkça gitmek istiyorsanız bu kuralları atlayabilirsiniz, ancak hala olay tabanlı zaman uyumsuz model kullanmanın diğer avantajlarından faydalanabilirsiniz. Örneğin, Windows Forms üzerinde çalışan bir sınıfın ücretsiz olarak iş parçacıklı olmasını isteyebilirsiniz. Geliştiriciler kapsanan kısıtlamaları anlamış olduğu sürece, ücretsiz bir iş parçacıklı sınıf oluşturabilirsiniz. Konsol uygulamaları <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrılarının yürütülmesini eşitlemez. Bu, `ProgressChanged` olaylarının sırada oluşturulmasına neden olabilir. <xref:System.ComponentModel.AsyncOperation.Post%2A> çağrılarının seri hale getirilmiş yürütmesi varsa, bir <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> sınıfını uygulayın ve yükleyebilirsiniz.  
  
 Zaman uyumsuz işlemlerinizi etkinleştirmek üzere <xref:System.ComponentModel.AsyncOperation> ve <xref:System.ComponentModel.AsyncOperationManager> kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay tabanlı zaman uyumsuz düzene yönelik bir bileşen uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Yönergeler  
  
- İdeal olarak, her yöntem çağrısı diğerlerinden bağımsız olmalıdır. Paylaşılan kaynaklarla ilgili bağlantısı önlemeyi kullanmaktan kaçının. Kaynaklar, çağırmaları arasında paylaşılırsa, uygulamanızda uygun bir eşitleme mekanizması sağlamanız gerekir.  
  
- İstemcinin eşitleme uygulaması için gerekli olan tasarımlar önerilmez. Örneğin, bir parametre olarak genel statik nesne alan zaman uyumsuz bir metoda sahip olabilirsiniz; Böyle bir yöntemin birden çok eş zamanlı çağırma verisi bozulmaya veya kilitlenmeleri oluşmasına neden olabilir.  
  
- Birden çok çağırma aşırı yüklemesiyle (İmzada`userState`) bir yöntem uygularsanız, sınıfınızın Kullanıcı durumları veya görev kimlikleri ve bunlara karşılık gelen bekleyen işlemleri koleksiyonunu yönetmesi gerekir. Çeşitli etkinleştirmeleri koleksiyondaki `userState` nesneleri ekleyip kaldıracağından, bu koleksiyonun `lock` bölgeleriyle korunması gerekir.  
  
- Uygun durumlarda `CompletedEventArgs` sınıfları yeniden kullanmayı düşünün. Bu durumda, belirtilen bir temsilci ve <xref:System.EventArgs> türü tek bir yönteme bağlı olmadığından, adlandırma yöntem adı ile tutarlı değildir. Ancak, geliştiricilerin <xref:System.EventArgs> bir özellikten alınan değeri dönüştürmeyi zorlamak hiçbir şekilde kabul edilemez.  
  
- <xref:System.ComponentModel.Component>türetilen bir sınıf yazıyorsanız kendi <xref:System.Threading.SynchronizationContext> sınıfınızı uygulamaz ve yüklemeyin. Uygulama modelleri, bileşen değil, kullanılan <xref:System.Threading.SynchronizationContext> denetleyin.  
  
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
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
