---
title: "İş Parçacığı Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f598cecef2d0994692f197df09e9befc39a58723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="threading-model"></a>İş Parçacığı Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Geliştiriciler iş parçacığı kurtarmak için tasarlanmıştır. Sonuç olarak, çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geliştiriciler birden çok iş parçacığı kullanan bir arabirim yazma zorunda kalmaz. Birden çok iş parçacıklı programlar karmaşık ve hata ayıklama zor olduğundan, bunlar tek iş parçacıklı çözümleri bulunduğunda kaçınılmalıdır.  
  
 Geçtiğinden bağımsız ne kadar iyi, ancak Hayır tasarlanmış [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework hiç kurulamayacak sorun her tür için tek iş parçacıklı bir çözüm sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Kapat gelir ancak hala burada birden çok iş parçacığı artırmak durumlarda [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] yanıtlama hızı veya uygulama performans. Bazı arka plan malzeme ele sonra bu kağıt bunlardan bazıları inceler ve bazı alt düzey ayrıntıların tartışması ile sonlanır.  
  

  
> [!NOTE]
>  Bu konuda ele alınmıştır kullanarak iş parçacığı oluşturma <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> zaman uyumsuz çağrılar için yöntem. Ayrıca zaman uyumsuz çağrılar çağırarak yapabileceğiniz <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> ele yöntemi bir <xref:System.Action> veya <xref:System.Func%601> bir parametre olarak.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Yöntemi döndürür bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, sahip olduğu bir <xref:System.Windows.Threading.DispatcherOperation.Task%2A> özelliği. Kullanabileceğiniz `await` ya da anahtar sözcük <xref:System.Windows.Threading.DispatcherOperation> veya ilişkili <xref:System.Threading.Tasks.Task>. Zaman uyumlu olarak bekleyin gerekiyorsa <xref:System.Threading.Tasks.Task> tarafından döndürülen bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, çağrı <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemi.  Çağırma <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bir kilitlenmeyle sonuçlanır. Kullanma hakkında daha fazla bilgi için bir <xref:System.Threading.Tasks.Task> görev Paralelliği zaman uyumsuz işlemleri gerçekleştirmek için bkz.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Yöntemi de ele aşırı sahip bir <xref:System.Action> veya <xref:System.Func%601> bir parametre olarak.  Kullanabileceğiniz <xref:System.Windows.Threading.Dispatcher.Invoke%2A> zaman uyumlu yapma yöntemini çağıran bir temsilci geçirerek <xref:System.Action> veya <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Genel bakış ve dağıtıcı  
 Genellikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar iki iş parçacığı ile başlar: oluşturma ve yönetme için başka bir işleme için bir tane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. İşleme iş parçacığı etkili bir şekilde arka planda gizli olarak çalıştırılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı Giriş alır, olaylarını işleme, ekran boyar ve uygulama kodu çalıştırır. Çoğu uygulama tek kullanımlık [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bazı durumlarda birkaç en iyi yöntem olmasına rağmen iş parçacığı. Biz bu örnek ile daha sonra ele alacağız.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] İş parçacığı sıraları çalışma öğeleri adlı bir nesne içinde bir <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Öncelik temelinde iş öğeleri seçer ve her birinin tamamlanma çalıştırır.  Her [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı en az bir olmalıdır <xref:System.Windows.Threading.Dispatcher>ve her <xref:System.Windows.Threading.Dispatcher> tam olarak bir iş parçacığında iş öğelerini yürütebilir.  
  
 En üst düzeye çıkarmak için esnek ve kullanımı kolay uygulamaları oluşturmak için yeterli olan <xref:System.Windows.Threading.Dispatcher> keserek iş öğeleri küçük üretilen iş. Bu şekilde öğeler hiçbir zaman eskimez <xref:System.Windows.Threading.Dispatcher> işlenmek üzere beklerken sırası. Bir kullanıcı girdisi ve yanıt arasındaki fark edilebilir gecikme rahatsız edebilir.  
  
 Nasıl daha sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları olması büyük işlemlerini işlemek için? Ne kodunuz büyük hesaplama içerir veya bazı uzak sunucudaki veritabanını sorgulama gerekiyor? Genellikle, yanıt bırakarak ayrı bir iş parçacığı büyük işlemi yönetmektir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerde eğilimindedir boş iş parçacığı <xref:System.Windows.Threading.Dispatcher> sırası. Büyük işlemi tamamlandıktan sonra sonuç raporlayabilirsiniz geri [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] görüntülemek için iş parçacığı.  
  
 Geçmişte, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sağlayan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yalnızca oluşturuldukları iş parçacığı tarafından erişilecek öğeleri. Bu tamamlandığında bir arka plan iş parçacığı bazı uzun süre çalışan görev sorumlu bir metin kutusu güncelleştirilemiyor anlamına gelir. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]Bu bütünlüğünü sağlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bileşenleri. Liste kutusu içeriğinin boyama sırasında bir arka plan iş parçacığı tarafından güncelleştirildiyse garip görünebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Bu koordinasyonu zorlayan bir yerleşik karşılıklı dışlama mekanizması vardır. Çoğu sınıflarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilen <xref:System.Windows.Threading.DispatcherObject>. Yapım, adresindeki bir <xref:System.Windows.Threading.DispatcherObject> başvuru depolar <xref:System.Windows.Threading.Dispatcher> şu anda çalışan iş parçacığına bağlı. Uygulamada <xref:System.Windows.Threading.DispatcherObject> oluşturduğu iş parçacığı ile ilişkilendirir. Program yürütme sırasında bir <xref:System.Windows.Threading.DispatcherObject> kendi ortak çağırabilirsiniz <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> yöntemi. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>inceler <xref:System.Windows.Threading.Dispatcher> geçerli iş parçacığı ile ilişkili olan ve kendisine karşılaştırır <xref:System.Windows.Threading.Dispatcher> oluşturma sırasında depolanan başvuru. Bunlar eşleşmiyorsa, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> bir özel durum oluşturur. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>ait her yöntemi başındaki çağrılmaya yönelik bir <xref:System.Windows.Threading.DispatcherObject>.  
  
 Bir iş parçacığı değiştirebilirsiniz yalnızca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], nasıl arka plan iş parçacıkları etkileşim kullanıcıyla? Arka plan iş parçacığı sorabilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] adına üzerinde bir işlemi gerçekleştirmek için iş parçacığı. Bunu bir iş öğesi ile kaydederek yapar <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. <xref:System.Windows.Threading.Dispatcher> Sınıfı, iş öğelerini kaydetme için iki yöntem sağlar: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ve <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Her iki yöntem yürütme için temsilci zamanlayın. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>zaman uyumlu bir çağrı – başka bir deyişle, kadar döndürmez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı gerçekten bittikten temsilci yürütülüyor. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>zaman uyumsuz olarak çağrılır ve hemen döndürür.  
  
 <xref:System.Windows.Threading.Dispatcher> Öğeleri sırasındaki önceliğe göre sıralar. Bir öğe olarak eklerken belirtilen on düzeyi vardır <xref:System.Windows.Threading.Dispatcher> sırası. Bu öncelikleri içinde korunur <xref:System.Windows.Threading.DispatcherPriority> numaralandırması. Hakkında ayrıntılı bilgi <xref:System.Windows.Threading.DispatcherPriority> düzeyleri bulunabilir [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] belgeleri.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Eylem iş parçacıklarında: örnekler  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Uzun süre çalışan hesaplama tek iş parçacıklı bir uygulamayla  
 Çoğu [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] yanıt kullanıcı etkileşimleri olarak oluşturulan olaylar beklenirken boşta kalma zaman büyük bir kısmını harcamanız. Dikkatli programlamayla bu boşta kalma süresi constructively, yanıtlama hızını etkilemeden kullanılabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modeli iş parçacığı içinde yapılmazsa bir işlemi kesmek giriş izin vermez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bu geri dönmek emin olmalısınız anlamına gelir <xref:System.Windows.Threading.Dispatcher> düzenli aralıklarla eski ulaşmadan giriş olaylarını bekleyen işleyemedi.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 ![Asal sayılar ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 Bu basit uygulama, üç, aramasını asal sayılar için yukarı doğru sayar. Kullanıcı tıkladığında **Başlat** arama düğmesini başlar. Program bir asal bulduğunda, kullanıcı arabirimini keşfi ile güncelleştirir. Herhangi bir noktada kullanıcı arama durdurabilirsiniz.  
  
 Basit olmasına rağmen asal sayı araması bazı sorunlar sunan sonsuza kadar gidebilirsiniz.  Biz düğmenin click olay işleyicisi içinde tüm arama işleniyorsa biz hiçbir zaman verirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer olayları işlemek için bir fırsat iş parçacığı. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Giriş veya işlem yanıt verip vermediğini olacaktır iletileri. Hiçbir zaman yeniden çizilmez ve hiçbir zaman düğme tıklamalarına yanıt.  
  
 Ayrı bir iş parçacığı asal sayı araması gerçekleştir, ancak daha sonra eşitleme sorunlarının üstesinden gelmek için ihtiyacımız. Tek iş parçacıklı bir yaklaşım ile biz bulunan büyük asal listeler etiketi doğrudan güncelleştirebilirsiniz.  
  
 Biz yönetilebilir yığınlar halinde hesaplamanın görev bölmeniz, biz düzenli aralıklarla geri dönebilirsiniz <xref:System.Windows.Threading.Dispatcher> ve işlem olayları. Biz verebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeniden çizilmez ve girişini işlemek için bir fırsat.  
  
 İşleme süresini hesaplama ve olay işleme arasında bölmek için en iyi yolu hesaplama yönetmektir <xref:System.Windows.Threading.Dispatcher>. Kullanarak <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi, biz asal sayı denetimlerini zamanlayabilir aynı sıraya [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olayları gelen çizilir. Bizim örneğimizde, aynı anda yalnızca bir tek asal sayı denetimi zamanlayın. Asal sayı kontrolü tamamlandıktan sonra biz sonraki onay hemen zamanlayın. Bu onay bekleyen yalnızca sonra ilerler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olayları işlenmiş.  
  
 ![Dağıtıcı sırası çizimi](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)]Bu mekanizmayı kullanarak yazım denetimi gerçekleştirir. Yazım denetimi boşta kalma süresi kullanarak arka planda gerçekleştirilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Kod bir göz atalım.  
  
 Aşağıdaki örnekte kullanıcı arabirimi oluşturan XAML gösterir.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Aşağıdaki örnek, arka plan kodu gösterir.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 Aşağıdaki örnek, olay işleyicisi gösterir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Üzerinde metnini güncelleştirme yanı sıra <xref:System.Windows.Controls.Button>, bu işleyici, bir temsilci ekleyerek ilk asal sayı onay zamanlama için sorumludur <xref:System.Windows.Threading.Dispatcher> sırası. Bu olay işleyicisi kendi iş tamamlandıktan sonra süre <xref:System.Windows.Threading.Dispatcher> yürütme için bu temsilciyi seçer.  
  
 Daha önce belirtildiği gibi <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> olan <xref:System.Windows.Threading.Dispatcher> üye yürütme için temsilci zamanlamak için kullanılır. Bu durumda, biz seçin <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> öncelik. <xref:System.Windows.Threading.Dispatcher> Yalnızca işlemek için hiçbir önemli olayları olduğunda bu temsilciyi çalıştırır. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yanıt hızını numarası denetleniyor değerinden daha önemlidir. Biz de numarası denetleniyor yordamı temsil eden yeni bir temsilci geçirin.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Bu yöntem, sonraki tek sayı asal olup olmadığını denetler. Asal ise, yöntem doğrudan güncelleştirmeleri `bigPrime` <xref:System.Windows.Controls.TextBlock> keşfi yansıtacak şekilde. Hesaplama bileşeni oluşturmak için kullanılan aynı iş parçacığında oluşturduğumuzdan bunu yapabilirsiniz. Biz seçilen hesaplama için ayrı bir iş parçacığı kullanmak, biz daha karmaşık bir eşitleme mekanizması kullanmanız ve güncelleştirme yürütme gerekirdi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Biz bu durum sonraki gösterir.  
  
 Bu örnek için tam kaynak kodunu için bkz: [Single-Threaded uygulama uzun süre çalışan hesaplama örnek ile](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Bir engelleme işlemi arka plan iş parçacığı ile işleme  
 Grafik uygulamalarında engelleyen işlemlerin işlenmesi zor olabilir. Uygulama Dondur görüneceğinden olay işleyicilerini engelleme yöntemlerini çağıran istemezsiniz. Biz bu işlemleri işlemek için ayrı bir iş parçacığı kullanabilirsiniz, ancak biz bittiğinde, ile eşitlemek sahibiz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] biz doğrudan değiştirilemiyor çünkü iş parçacığı [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] bizim çalışan iş parçacığı gelen. Biz kullanabilirsiniz <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> temsilciler içine eklemek için <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Sonuç olarak, bu temsilciler değiştirme izni ile yürütülür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri.  
  
 Bu örnekte, hava durumu tahmini alan uzaktan yordam çağrısı taklit. Bu çağrıyı yürütmek için ayrı çalışan iş parçacığı kullanırız ve biz bir güncelleştirme yöntemi zamanlama <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tamamlandığında iş parçacığı.  
  
 ![Kullanıcı Arabirimi ekran görüntüsü hava durumu](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.PNG "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Bazı kaydedilmelidir Ayrıntılar verilmiştir.  
  
-   Düğme işleyicisi oluşturma  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Düğmesine tıklandığında, biz saat çizimi görüntülenir ve animasyon başlar. Düğme devre dışı bırakın. Biz çağırma `FetchWeatherFromServer` yeni bir iş parçacığı ve ardından yönteminde dönüş, izin verme <xref:System.Windows.Threading.Dispatcher> hava tahmini toplamak için beklerken olayları işlemek için.  
  
-   Hava getirme  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Örneği basit tutmak için biz gerçekte Ağ bir kodu bu örnekte yok. Bunun yerine, şu dört saniye için uyku moduna yeni iş parçacığını koyarak ağ erişim gecikmesi benzetimi. Bu süre, orijinal olarak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı hala çalıştıran ve olaylara yanıt verme. Bu, size bir animasyonu çalışır ve simge durumuna küçült sol göstermek ve en üst düzeye çıkarmak için düğmeler de çalışmaya devam eder.  
  
 Gecikme tamamlandı ve biz rastgele bizim hava tahmini seçtiyseniz, yeniden rapor zamanı geldi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Çağrı zamanlayarak bunu `UpdateUserInterface` içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parçacığının kullanarak iş parçacığı <xref:System.Windows.Threading.Dispatcher>. Biz bu zamanlanmış yöntem çağrısının hava tanımlayan bir dize geçirin.  
  
-   Güncelleştirme[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Zaman <xref:System.Windows.Threading.Dispatcher> içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığına sahip zaman, zamanlanmış çağrısı yürütür `UpdateUserInterface`. Bu yöntem, saat animasyonu durdurur ve hava durumu tanımlamak için görüntüyü seçer. Bu görüntü görüntüler ve "fetch tahmin" düğmesine geri yükler.  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Birden çok Windows, çoklu iş parçacıkları  
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları birden çok üst düzey windows gerektirir. Tek bir iş parçacığı edilebilir /<xref:System.Windows.Threading.Dispatcher> birleşimi birden çok windows ancak bazen birkaç iş parçacığı yönetmek için daha iyi iş yapın. Bu özellikle ihtimali varsa, Windows'un bir iş parçacığı kullanmasını geçerlidir.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]Explorer bu şekilde çalışır. Her yeni Explorer penceresi özgün işleme ait olduğu, ancak bağımsız bir iş parçacığı denetimi altında oluşturulur.  
  
 Kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> denetim, biz Web sayfalarını görüntüleyebilirsiniz. Basit bir kolayca oluşturabilir [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] değiştirin. Biz önemli özellik ile Başlat: özelliği yeni bir explorer penceresi açın. Kullanıcı, "Yeni Pencere" tıkladığında düğmesi, size bir kopyasını ayrı bir iş parçacığı bizim penceresi başlatın. Bu şekilde, diğer tüm windows uzun süre çalışan veya engelleyici işlemlerinde windows birini kilit olmaz.  
  
 Gerçekte, Web tarayıcısı modeli kendi karmaşık iş parçacığı modeli vardır. Çoğu okuyucuları bilgi sahibi olmanız gerekir çünkü bunu seçtik.  
  
 Aşağıdaki örnek kod gösterir.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Bu kod aşağıdaki iş parçacığı kesimleri en ilginç bize bu bağlamda şunlardır:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Bu yöntem aldığında çağrılan "Yeni Pencere" düğmesine tıklandığında. Yeni bir iş parçacığı oluşturur ve zaman uyumsuz olarak başlatır.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Bu yöntem, yeni bir iş parçacığı için başlangıç noktasıdır. Bu iş parçacığı denetimi altında yeni bir pencere oluşturuyoruz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]otomatik olarak yeni bir oluşturur <xref:System.Windows.Threading.Dispatcher> yeni bir iş parçacığı yönetmek için. Pencerenin işlevsel sağlamak için yapmanız sahip olduğumuz tümüdür başlatmak için <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Teknik Ayrıntılar ve bazı noktalar  
  
### <a name="writing-components-using-threading"></a>İş parçacığı kullanarak bileşen yazma  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Geliştirici Kılavuzu bir bileşen istemcilerine zaman uyumsuz davranışı nasıl getirebilir için bir desen açıklar (bkz [olay tabanlı zaman uyumsuz desene genel bakış](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Örneğin, biz istediğinizi paketlemek varsayın `FetchWeatherFromServer` yeniden kullanılabilir bir bileşenin yönteme. Standart aşağıdaki [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] düzeni, bu aşağıdakine benzer görünecektir.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`bir arka plan iş parçacığı oluşturma gibi daha önce açıklanan teknikleri birini işi zaman uyumsuz olarak yapmak için çağıran iş parçacığı engellemediğini kullanırsınız.  
  
 Bu desenin en önemli parçalarından çağırma *MethodName* `Completed` yöntemini çağıran iş parçacığında *MethodName* `Async` yöntemi ile başlar. Kullanarak bunu yapabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] depolayarak oldukça kolaylıkla <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— ancak ardından grafik olmayan bileşeni yalnızca kullanılabilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları değil, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programlar.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Sınıfı bu adresleri — basitleştirilmiş bir sürümünü olarak düşünün <xref:System.Windows.Threading.Dispatcher> diğer çalışan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de çerçeveleri.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Pompalama iç içe geçmiş  
 Bazen tamamen kilitlemek için uygun olmadığı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Şimdi göz önünde bulundurun <xref:System.Windows.MessageBox.Show%2A> yöntemi <xref:System.Windows.MessageBox> sınıfı. <xref:System.Windows.MessageBox.Show%2A>Kullanıcı Tamam düğmesine tıklar kadar döndürmez. Ancak, bir ileti döngüsü etkileşimli için sahip bir pencere oluşturmaz. Biz kullanıcının Tamam'ı beklerken, özgün uygulama penceresi kullanıcı girişine yanıt vermez. Boyama iletileri işlemek üzere ancak devam eder. Özgün pencere kendisini kapsamdaki ve ortaya yeniden çizer.  
  
 !["Tamam" düğmesini kullanarak MessageBox](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 Bazı iş parçacığı sorumlu ileti kutusu penceresi olması gerekir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ileti kutusu penceresi yalnızca için yeni bir iş parçacığı oluşturabilir, ancak bu iş parçacığı devre dışı bırakılan öğeleri özgün penceresinde boyamak alamadı (karşılıklı dışlama önceki tartışmayı unutmayın). Bunun yerine, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç içe geçmiş bir ileti sistemi işleme kullanır. <xref:System.Windows.Threading.Dispatcher> Sınıfı içerir adlı özel bir yöntem <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, yeni bir ileti döngüsü başlar, ardından uygulamanın geçerli yürütme noktası depolar. İç içe ileti döngüsü sona erdiğinde, yürütme sonra özgün sürdürür <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağırın.  
  
 Bu durumda, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağrısı konumundaki program bağlamda tutar <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, ve arka plan penceresi yeniden çizilmez ve ileti kutusu penceresine girişini işlemek için yeni bir ileti döngüsü başlatır. Kullanıcı Tamam tıklar ve açılır pencereyi temizlediğinde, iç içe döngü çıkar ve denetim sürdürür çağrısından sonra <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Eski yönlendirilmiş olaylar  
 Yönlendirilmiş olay sistemde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları ortaya çıktığında tüm ağaçları bildirir.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Sol fare düğmesini elips basıldığında `handler2` yürütülür. Sonra `handler2` sonlandığında olay iletilir boyunca <xref:System.Windows.Controls.Canvas> kullanan nesne `handler1` işlemesi için. Bu yalnızca olur `handler2` mu açıkça işareti olay nesnesini işlenmiş olarak.  
  
 Mümkünse, `handler2` bu olay işleme süresinin büyük bir bölümünü sürer. `handler2`kullanabilir <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> saat döndürmez bir iç içe ileti döngüsü başlatmak için. Varsa `handler2` bu ileti döngüsü olduğunda işlenmiş olarak olay tamamlamak işareti yok, çok eski olsa da olay ağaca geçirilir.  
  
### <a name="reentrancy-and-locking"></a>Yeniden giriş ve kilitleme  
 Kilitleme mekanizması [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] tam olarak davranır olmayan bir düşünün; bir işlemi tamamen kilit isterken sona için bir iş parçacığı beklediğiniz. Çünkü, yüksek öncelikli iletileri almak ve işlemek iş parçacığı devam eder. Bu kilitlenmeler önlemek ve arabirimleri en düşük düzeyde iyi yanıt vermesi yardımcı olur, ancak Zarif hataları olasılığını tanıtır.  Olmayan herhangi bir şey bu konuda, ancak nadir durumlarda bilmeniz gereken süre büyük çoğunluğu (genellikle içeren [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere iletileri veya COM STA bileşenleri) bu bilerek değer olabilir.  
  
 Geliştiriciler varsayımına altında çalışması nedeniyle, çoğu arabirimleri aklınızda iş parçacığı güvenliği ile oluşturulan değil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiçbir zaman birden çok iş parçacığı tarafından erişilir. Bu durumda, tek iş parçacığı beklenmeyen zamanlarda ortam değişiklikleri yapabilir, bu hatalı neden, efektler <xref:System.Windows.Threading.DispatcherObject> karşılıklı dışlama mekanizması çözmek bekleniyor. Aşağıdaki yarı kodu göz önünde bulundurun:  
  
 ![Yeniden giriş diyagramı iş parçacığı oluşturma](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 Çoğu zaman, en doğru şey, ancak mevcuttur kez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olduğu gibi beklenmeyen yeniden giriş gerçekten sorunlara neden olabilir. Bu nedenle, belirli bir anahtar zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağrıları <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, hangi değişiklikleri kullanmak bu iş parçacığı için kilit yönerge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] normal yerine yeniden giriş serbest kilit [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kilit.  
  
 Bunu neden oldu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] takım seçin Bu davranış? COM STA nesneler ve sonlandırma iş parçacığı ile yapmak vardı. Bir nesne, çöp toplama olduğunda kendi `Finalize` yöntemi çalıştırılır ayrılmış sonlandırıcıyı iş parçacığı üzerinde değil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Okuduğunuzu, sorun, COM STA nesne çünkü oluşturulduğu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı yalnızca atıldı üzerinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Denk mu bir <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (Bu durumda Win32'in kullanarak `SendMessage`). Ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı meşgul, sonlandırıcıyı iş parçacığı durduruldu ve ciddi bellek sızıntısı oluşturan COM STA nesne atılamaz. Bu nedenle [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] takım yapılan yaptıkları gibi çalışmasına kilitleri yapmak için sağlam çağrısı.  
  
 Görev için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biz her yerde yeniden giriş engelleme neden olan bellek sızıntısı yeniden eklenmesiyle olmadan beklenmeyen yeniden giriş önlemek için gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzun süre çalışan hesaplama örnek tek iş parçacıklı uygulamayla](http://go.microsoft.com/fwlink/?LinkID=160038)
