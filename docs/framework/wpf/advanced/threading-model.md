---
title: İş Parçacığı Modeli
ms.date: 03/30/2017
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
ms.openlocfilehash: 0bcb0e7369345aaae39d99a005a07304aaad7043
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62036471"
---
# <a name="threading-model"></a>İş Parçacığı Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Geliştiriciler, iş parçacığı kurtarmak için tasarlanmıştır. Sonuç olarak, çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geliştiriciler birden fazla iş parçacığı kullanan bir arabirim yazma zorunda kalmaz. Çoklu iş parçacığı kullanan programları, karmaşık ve hata ayıklama zor olduğundan, bunlar çözümleri tek iş parçacıklı bulunduğunda kaçınılmalıdır.  
  
 Olursa olsun ne kadar iyi, ancak Hayır desteklemesi için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework hiç sorun her tür için tek iş parçacıklı bir çözüm sağlayabilir olacaktır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kapat, gelen vardır, ancak yine de burada birden çok iş parçacığı geliştirmek durumlarda [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] yanıtlama hızı veya uygulama performans. Bu yazıda, bazı arka plan malzeme görüştükten sonra bu durumlardan bazıları inceler ve bazı alt düzey ayrıntıları Serileştirmenin burada sona eriyor.  

> [!NOTE]
>  Bu konuda ele alınmıştır kullanarak iş parçacığı <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> zaman uyumsuz çağrılar için yöntemi. Zaman uyumsuz çağrıları çağrı yaparak da yapabilirsiniz <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Al yönteminin bir <xref:System.Action> veya <xref:System.Func%601> bir parametre olarak.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Yöntemi döndürür bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, sahip olduğu bir <xref:System.Windows.Threading.DispatcherOperation.Task%2A> özelliği. Kullanabileceğiniz `await` ya da anahtar sözcüğüyle <xref:System.Windows.Threading.DispatcherOperation> veya ilişkili <xref:System.Threading.Tasks.Task>. Zaman uyumlu olarak beklemesi gerekiyorsa <xref:System.Threading.Tasks.Task> tarafından döndürülen bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, çağrı <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemi.  Çağırma <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bir kilitlenmeyle neden olur. Kullanma hakkında daha fazla bilgi için bir <xref:System.Threading.Tasks.Task> görev Paralelliği zaman uyumsuz işlemleri gerçekleştirmek için bkz.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Yöntemi alan aşırı yüklemeler de sahip bir <xref:System.Action> veya <xref:System.Func%601> bir parametre olarak.  Kullanabileceğiniz <xref:System.Windows.Threading.Dispatcher.Invoke%2A> zaman uyumlu hale getirmek için yöntemini çağıran bir temsilci geçirerek <xref:System.Action> veya <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Genel bakış ve dağıtıcı  
 Genellikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları ile iki iş parçacığı başlangıç: oluşturma ve yönetme için başka bir işleme için bir tane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. İşleme iş parçacığı etkili bir şekilde arka planda gizli olarak çalıştırılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı girişini alır, olayları işler, ekran boyar ve uygulama kodu çalıştırır. Çoğu uygulama tek kullanımlık [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bazı durumlarda birkaç kullanmak en iyisidir ancak, iş parçacığı. Bu örnek ile daha sonra açıklayacağız.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] İş parçacığı kuyruklarına iş öğeleri adı verilen bir nesne içinde bir <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Öncelikli olarak iş öğeleri seçer ve her birinin tamamlanma çalıştırır.  Her [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı en az bir sahip olmalıdır <xref:System.Windows.Threading.Dispatcher>ve her <xref:System.Windows.Threading.Dispatcher> iş öğelerini tam olarak bir iş parçacığında yürütebilirsiniz.  
  
 Hızlı, kullanışlı uygulamalar oluşturmak için püf noktası en üst düzeye çıkarmaktır <xref:System.Windows.Threading.Dispatcher> tutarak iş öğelerini küçük aktarım hızı. Bu şekilde öğeleri hiçbir zaman oturan eski Al <xref:System.Windows.Threading.Dispatcher> kuyruk işleme için bekleniyor. Bir kullanıcı girişi ve yanıt arasındaki fark edilebilir gecikme rahatsız edebilir.  
  
 Daha sonra nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] büyük işlemlerini gereken uygulamaları? Ne kodunuzu içeren geniş bir hesaplama veya bazı uzak sunucuda bir veritabanını sorgulama gerekiyor? Genellikle, yanıt bırakarak ayrı bir iş parçacığı büyük işlem yönetmektir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerinde eğilimindedir boş iş parçacığı <xref:System.Windows.Threading.Dispatcher> kuyruk. Büyük işlem tamamlandığında, sonuç bildirebilirsiniz geri [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] görüntülemek için iş parçacığı.  
  
 Tarihsel olarak, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sağlayan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturuldukları yalnızca iş parçacığı tarafından erişilecek öğeleri. Başka bir deyişle, bir arka plan iş parçacığı sorumlu bazı uzun süre çalışan görev sona erdiğinde bir metin kutusu güncelleştirilemiyor. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bütünlüğünü sağlamak için bunu yapar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bileşenleri. Liste kutusu içeriğinin boyama sırasında bir arka plan iş parçacığı tarafından güncelleştirildiyse garip görünebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu koordinasyonu zorlayan bir yerleşik karşılıklı dışlama mekanizması vardır. Çoğu sınıflarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilen <xref:System.Windows.Threading.DispatcherObject>. Oluşturma sırasında bir <xref:System.Windows.Threading.DispatcherObject> başvuru depolar <xref:System.Windows.Threading.Dispatcher> çalışmakta olan iş parçacığına bağlı. Aslında, <xref:System.Windows.Threading.DispatcherObject> oluşturduğu iş parçacığı ile ilişkilendirir. Programın yürütülmesi sırasında bir <xref:System.Windows.Threading.DispatcherObject> kendi ortak çağırabilirsiniz <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> yöntemi. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> inceler <xref:System.Windows.Threading.Dispatcher> kendisine karşılaştırır ve geçerli iş parçacığıyla ilişkilendirilmiş <xref:System.Windows.Threading.Dispatcher> yapım sırasında depolanan başvuru. Bunlar eşleşmiyorsa, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> bir özel durum oluşturur. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> başında ait her bir yöntemin çağrılması amaçlanmıştır bir <xref:System.Windows.Threading.DispatcherObject>.  
  
 Yalnızca tek bir iş parçacığı değiştirebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], nasıl arka plan iş parçacığı etkileşim kullanıcıyla? Arka plan iş parçacığı sorabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kendi adına bir işlemi gerçekleştirmek için iş parçacığı. Bunu bir iş öğesi ile kaydederek yapar <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. <xref:System.Windows.Threading.Dispatcher> Sınıfı iş öğelerini kaydetmek için iki yöntem sunar: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ve <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Her iki yöntem yürütme için bir temsilci zamanlayın. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> zaman uyumlu bir çağrı – diğer bir deyişle, kadar döndürmüyor [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aslında iş parçacığı tamamlandıktan temsilciyi çalıştırıyor. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> zaman uyumsuz ve hemen döndürür.  
  
 <xref:System.Windows.Threading.Dispatcher> Öğeleri sırasındaki önceliğe göre sıralar. Öğe eklenirken belirtilen on düzeyi vardır <xref:System.Windows.Threading.Dispatcher> kuyruk. İçinde bu öncelikleri korunur <xref:System.Windows.Threading.DispatcherPriority> sabit listesi. Hakkında ayrıntılı bilgi <xref:System.Windows.Threading.DispatcherPriority> düzeyleri bulunabilir [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] belgeleri.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Eylem iş parçacıkları: Örnekleri  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Uzun süre çalışan hesaplamalar ile tek iş parçacıklı bir uygulama  
 Çoğu [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] büyük bölümünü boşta Kullanıcı etkileşimlerine karşılık oluşturulan olaylar için beklenirken zaman ayırın. Dikkatli programlamayla bu boşta kalma süresi constructively, yanıtlama hızını etkilemeden kullanılabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İş parçacığı modeli giriş olarak gerçekleştirilecek bir işlemi kesmek izin vermez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Geri dönmek emin olmalıdır yani <xref:System.Windows.Threading.Dispatcher> düzenli aralıklarla bekleyen eski ulaşmadan giriş olayları işlenecek.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
 ![Asal sayıları iş parçacığı gösteren ekran görüntüsü.](./media/threading-model/threading-prime-numbers.png)  
  
 Bu basit uygulama, üç, aramasını asal sayıları için yukarı doğru sayar. Kullanıcı tıkladığında **Başlat** arama düğmesini başlar. Program bir asal bulduğunda, kullanıcı arabirimi keşfi ile güncelleştirir. Herhangi bir noktada, kullanıcı arama durdurabilirsiniz.  
  
 Basit olmasına rağmen asal sayı arama bazı sorunlar sunan sonsuza kadar çıkabilir.  Biz düğmenin click olay işleyicisi içindeki tüm arama işleniyorsa, biz hiçbir zaman verirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer olayları işlemek için bir fırsat iş parçacığı. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Giriş veya işlem yanıt veremeyebilir iletileri. Hiçbir zaman repaint ve hiç düğme tıklamalarına yanıt verme.  
  
 Biz asal sayı ayrı bir iş parçacığı aramasını, ancak ardından biz eşitleme sorunlarla başa çıkmak gerekir. Tek iş parçacıklı bir yaklaşımla size doğrudan bulunan büyük asal listeler etiket güncelleştirebilirsiniz.  
  
 Biz yönetilebilir öbeklere hesaplama görevi bölmeniz, biz düzenli aralıklarla geri dönerek <xref:System.Windows.Threading.Dispatcher> ve olay işleme. Size [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] repaint ve giriş işlemek için bir fırsat.  
  
 İşlem süresi hesaplama ve olay işleme arasında bölmek için en iyi yolu, hesaplama yönetmektir <xref:System.Windows.Threading.Dispatcher>. Kullanarak <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi, biz asal sayı denetimlerini zamanlayabilirsiniz aynı sıra [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gelen olayları çizilmiştir. Bizim örneğimizde, biz yalnızca bir tek asal sayı denetimi birer birer zamanlayın. Asal sayı onay tamamlandıktan sonra biz sonraki denetim hemen zamanlayın. Bu denetim yalnızca sonra bekleyen geçer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olayları işlenmiş.  
  
 ![Dağıtıcı sıranın gösteren ekran görüntüsü.](./media/threading-model/threading-dispatcher-queue.png)  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] Bu mekanizma kullanılarak yazım denetimi gerçekleştirir. Yazım denetimi boşta kalma süresi'ni kullanarak arka planda gerçekleştirilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Kod bir göz atalım.  
  
 Aşağıdaki örnek kullanıcı arabirimi oluşturan XAML gösterir.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Aşağıdaki örnek, arka plan kod gösterir.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 Aşağıdaki örnekte olay işleyicisi <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Üzerinde metnini güncelleştirme yanı sıra <xref:System.Windows.Controls.Button>, bu işleyici, ilk asal sayı onay zamanlama için bir temsilciye ekleyerek sorumludur <xref:System.Windows.Threading.Dispatcher> kuyruk. Bu olay işleyicisi, kendi iş tamamlandıktan sonra süre <xref:System.Windows.Threading.Dispatcher> yürütme için bu temsilciyi seçer.  
  
 Daha önce de belirttiğimiz gibi <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> olduğu <xref:System.Windows.Threading.Dispatcher> üye yürütme için bir temsilci zamanlamak için kullanılır. Bu durumda, Seçtiğimiz <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> öncelik. <xref:System.Windows.Threading.Dispatcher> İşlemek için önemli olay olduğunda bu temsilciyi çalıştırır. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yanıt verme hızını sayı denetlemekten daha önemlidir. Biz de numarası denetleniyor yordamı temsil eden yeni bir metot temsilcisi geçirin.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Bu yöntem, asal sonraki tek sayı olup olmadığını denetler. Asal ise, yöntem doğrudan güncelleştirmeleri `bigPrime` <xref:System.Windows.Controls.TextBlock> keşfi yansıtacak şekilde. Hesaplama bileşeni oluşturmak için kullanılan aynı iş parçacığında gerçekleştirilmekte olduğundan bunu yapabilirsiniz. Ki seçilen hesaplama için ayrı bir iş parçacığı kullanmak, size daha karmaşık bir eşitleme mekanizmasının kullanılması ve güncelleştirme yürütme gerekirdi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Biz bu durum sonraki kazandırabileceğinizi göstereceğiz.  
  
 Bu örnek için tam kaynak kodunu görmek [uzun süre çalışan hesaplama örneğiyle Single-Threaded uygulama](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Engelleyici bir işlemi bir arka plan iş parçacığı ile işleme  
 Bir grafik uygulaması engelleme işlemleri işleme zor olabilir. Uygulama donmuş gözükeceği engelleme yöntemleri olay işleyicilerini çağırmanızı istemezsiniz. Bu işlemleri işlemek için ayrı bir iş parçacığı kullanabiliriz, ancak işimiz bittiğinde, ile eşitlemek sahibiz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] biz doğrudan değişiklik yapamazsınız çünkü iş parçacığı [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] bizim çalışan iş parçacığından. Kullanabiliriz <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> temsilciler içine eklenecek <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Sonuç olarak, bu temsilcileri değiştirme iznine yürütülecek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri.  
  
 Bu örnekte biz hava durumu tahminini alan bir uzak yordam çağrısı taklit. Bu çağrı yürütmek için ayrı iş parçacığı kullanıyoruz ve biz de bir güncelleştirme yöntemi zamanlama <xref:System.Windows.Threading.Dispatcher> , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tamamlandığında iş parçacığı.  
  
 ![UI hava durumu gösteren ekran görüntüsü.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Not ayrıntıları bazıları aşağıda verilmiştir.  
  
- Düğme işleyicisi oluşturma  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Düğme tıklandığında, biz saat çizimi görüntülenir ve animasyon başlar. Düğmeyi devre dışı bırakın. Biz çağırma `FetchWeatherFromServer` yöntemi yeni bir iş parçacığı ve ardından size dönüş izin <xref:System.Windows.Threading.Dispatcher> hava durumu tahminini toplamak için beklerken olayları işlemek için.  
  
- Hava durumu getirilirken  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Basit bir anlatım gözetildiği, biz aslında ağ herhangi bir kodu bu örnekte gerekmez. Bunun yerine, biz dört saniye için uyku moduna yeni iş parçacığını koyarak ağ erişimi gecikmesini benzetimi. Zaman, özgün [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı hala çalıştığından ve olaylarına yanıt verme. Bu, size bir animasyonu çalışır ve simge durumuna küçült bırakmış olabilirsiniz göstermek ve en üst düzeye çıkarmak için düğmeler de çalışmaya devam.  
  
 Gecikme tamamlandıktan ve bizim hava durumu tahminini rastgele seçtik geri rapor için zaman olur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bir çağrı zamanlayarak bunu `UpdateUserInterface` içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak bu iş parçacığının iş parçacığı <xref:System.Windows.Threading.Dispatcher>. Biz bu zamanlanmış yöntem çağrısına hava durumunu açıklayan bir dize geçirin.  
  
- Güncelleştirme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Zaman <xref:System.Windows.Threading.Dispatcher> içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı zaman sahiptir, zamanlanmış çağrısı yürütür `UpdateUserInterface`. Bu yöntem, saat animasyonu durdurur ve hava durumu tanımlamak için bir görüntü seçer. Bu görüntü görüntüler ve "getirme tahmin" düğmesini geri yükler.  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Birden çok Windows, birden çok iş parçacığı  
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar birden çok üst düzey pencerelere gerektirir. Tek bir iş parçacığı edilebilir /<xref:System.Windows.Threading.Dispatcher> birden çok windows, ancak bazen birden çok iş parçacığı yönetileceğini birleşimi daha iyi iş yapın. Bu özellikle ihtimali varsa, bir windows iş parçacığını tekeline geçerlidir.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Gezgini bu şekilde çalışır. Her yeni Gezgini penceresi özgün işleme ait olduğu, ancak bunu bağımsız bir iş parçacığı denetimi altında oluşturulur.  
  
 Kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> denetimi, Web sayfaları görüntüleriz. Basit bir kolayca oluşturabiliriz [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] değiştirin. Biz önemli bir özelliği ile Başlat: yeni bir Gezgini penceresi açmak için yeteneği. Kullanıcı, "Yeni Pencere" tıkladığında düğmesi, biz bir kopyasını ayrı bir iş parçacığı bizim penceresi başlatın. Bu şekilde, diğer tüm windows uzun süreli veya engelleme işlemleri windows biriyle kilitlenmez.  
  
 Gerçekte, kendi karmaşık iş parçacığı modeli Web tarayıcı modeline sahiptir. Çoğu okuyucularına tanıyor olmalıdır çünkü bunu seçtik.  
  
 Aşağıdaki örnek kod gösterir.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Bu kod aşağıdaki iş parçacığı bölümleri en ilginç bize bu bağlamda şunlardır:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Bu yöntem olduğunda çağrılır "Yeni Pencere" düğmesine tıklandığında. Bu, yeni bir iş parçacığı oluşturur ve zaman uyumsuz olarak başlatır.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Bu yöntem, yeni iş parçacığı için başlangıç noktasıdır. Bu iş parçacığı denetimi altında yeni bir pencere oluştururuz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] otomatik olarak yeni bir oluşturur <xref:System.Windows.Threading.Dispatcher> yeni iş parçacığını yönetmek için. Biz penceresi işlevsel hale getirmek için yapmanız gereken tek şey başlatmak için <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Teknik Ayrıntılar ve bazı noktalar  
  
### <a name="writing-components-using-threading"></a>İş parçacığı kullanan bileşen yazma  
 Microsoft .NET Framework Geliştirici Kılavuzu için zaman uyumsuz davranış istemcilerine bir bileşeni nasıl ortaya koyabileceğiniz bir deseni açıklar (bkz [olay tabanlı zaman uyumsuz desene genel bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Örneği için paketlenecek istedik varsayalım `FetchWeatherFromServer` yeniden kullanılabilir bir bileşenin içine yöntemi. Standart Microsoft .NET Framework desenini, bunun aşağıdaki gibi görünür.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` bir arka plan iş parçacığı oluşturma gibi daha önce açıklanan olan tekniklerle biri zaman uyumsuz olarak yapması için çağıran iş parçacığını engellemeyen kullanırsınız.  
  
 Bu düzenin en önemli parçalarından çağırır *MethodName* `Completed` yöntemi çağıran iş parçacığında *MethodName* `Async` ile başlamak için yöntemi. Kullanarak bunu yapabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] depolayarak oldukça bir kolayca <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— ancak ardından grafik olmayan bileşeni yalnızca içinde kullanılabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları değil [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programlar.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Sınıfı bu adresleri — basitleştirilmiş bir sürümünü olarak düşünebilirsiniz <xref:System.Windows.Threading.Dispatcher> diğer çalışan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] çerçeveleri de.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>İç içe pompalama  
 Bazen tamamen kilitlemek için uygun değil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Düşünelim <xref:System.Windows.MessageBox.Show%2A> yöntemi <xref:System.Windows.MessageBox> sınıfı. <xref:System.Windows.MessageBox.Show%2A> Kullanıcı Tamam düğmesine tıklayana kadar döndürmüyor. Ancak, bir ileti döngüsü etkileşimli olması gereken bir pencere oluşturur. Özgün uygulama penceresi şu kullanıcı için Tamam'a tıklayın beklerken, kullanıcı girişine yanıt vermiyor. Boyama iletileri işlemek ancak devam eder. Özgün penceresinde kendisi kapsamında ve ortaya çıktığı zaman yeniden çizer.  
  
 ![Tamam düğmesi ile bir MessageBox gösteren ekran görüntüsü](./media/threading-model/threading-message-loop.png)  
  
 Bazı iş parçacığı ileti kutusu penceresi sorumlu olması gerekir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ileti kutusu penceresi için yeni bir iş parçacığı oluşturabilirsiniz, ancak bu iş parçacığı özgün penceresinde devre dışı bırakılan öğeleri boyama veremeyebilir (karşılıklı dışlama önceki tartışmayı unutmayın). Bunun yerine, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç içe geçmiş ileti işleme sistemi kullanır. <xref:System.Windows.Threading.Dispatcher> Sınıfı olarak adlandırılan özel bir yöntem içerir <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, ardından depoladığı uygulamanın geçerli yürütme noktasını yeni bir ileti döngüsü başlatır. İç içe geçmiş ileti döngüsü sona erdiğinde, sonra özgün yürütmeyi devam ettirir <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağırın.  
  
 Bu durumda, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağrısı program bağlamında tutar <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, ve arka plan penceresi repaint ve ileti kutusu penceresi giriş işlemek için yeni bir ileti döngüsü başlatır. Kullanıcı Tamam'ı tıklattığında açılan penceresini temizler, iç içe geçmiş döngüsünden çıkıp denetimi devam ettirir çağrısından sonra <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Eski yönlendirilmiş olaylar  
 Yönlendirilmiş olay sistemde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları oluştuğunda tüm ağaçları bildirir.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Elips farenin sol düğmesine basıldığında `handler2` yürütülür. Sonra `handler2` bittiğinde, olay geçirildiğinde boyunca <xref:System.Windows.Controls.Canvas> kullanan nesne `handler1` işlemek için. Yalnızca böyle `handler2` mu açıkça işareti olay nesnesiyle işlenmiş olarak.  
  
 Mümkünse, `handler2` bu olay işleme süresi büyük ölçüde götürür. `handler2` kullanabilir <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> saatliğine döndürmüyor bir iç içe geçmiş ileti döngüsü başlatmak için. Varsa `handler2` çok eski olsa da, olay ağacın geçirilir, bu ileti döngüsü olduğunda, işlenmiş olarak olay tamamlamak işareti yok.  
  
### <a name="reentrancy-and-locking"></a>Yeniden giriş ve kilitleme  
 Kilitleme mekanizması [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] tam olarak davranmaya olmayan bir Imagine; bir işlemi tamamen kilit isterken sona ermesi için bir iş parçacığı beklediğiniz. Yüksek öncelikli iletileri almak ve işlemek üzere çünkü iş parçacığı devam eder. Bu kilitlenmeleri önlemek ve arabirimleri en düşük düzeyde esnek olun yardımcı olur, ancak küçük hatalar için olasılık sunar.  Yoksa bilmeniz gereken her şey bu konuda, ancak nadir koşullarda süre büyük çoğunluğu (genellikle içeren [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere iletileri veya COM STA bileşenleri) bu bilerek değer olabilir.  
  
 Çoğu arabirimleri ile iş parçacığı güvenliği aklınızda almayan geliştiriciler varsayım altında çalıştığından, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiçbir zaman birden fazla iş parçacığı tarafından erişilebilir. Bu durumda, tek bir iş parçacığı beklenmeyen zamanlarda ortam değişiklikleri yapabilir, bu hatalı neden, efektler <xref:System.Windows.Threading.DispatcherObject> karşılıklı dışlama mekanizması çözmek gereken. Aşağıdaki sözde kod göz önünde bulundurun:  
  
 ![Yeniden giriş iş parçacığı gösteren diyagram. ](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 Çoğu zaman doğru şeyi olan, ancak bazı durumlarda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] burada beklenmeyen tür yeniden giriş gerçekten sorunlara neden olabilir. Bu nedenle, belirli bir anahtar zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağrıları <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, hangi değişiklikleri kullanılacak iş parçacığı için kilit yönerge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerine yeniden giriş ücretsiz kilit [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kilit.  
  
 Bunu neden oldu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] takım'ı seçin, bu davranışı? COM STA nesneleri ve sonlandırma iş parçacığı ile gereken buydu. Bir nesnenin çöp olarak toplanacak, olduğunda kendi `Finalize` yöntemi çalıştırılır adanmış bir sonlandırıcı iş parçacığı üzerinde değil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. İzindeki sorun, bir COM STA nesnesi olduğundan oluşturulduğu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı yalnızca elden üzerinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Denk mu bir <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (Bu durumda Win32'ın kullanarak `SendMessage`). Ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] meşgul iş parçacığı Sonlandırıcı iş parçacığı durduruldu ve ciddi bir bellek sızıntısı oluşturan COM STA nesne atılamaz. Bu nedenle [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] team yapılmış yaptıkları tümleştirmeleri kilitleri yapmak zor çağrısı.  
  
 Görev için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biz her yerde yeniden giriş engelleme neden olan bellek sızıntısı yeniden eklenmesiyle olmadan beklenmeyen yeniden giriş önlemek içindir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uzun süre çalışan hesaplama örneğiyle tek iş parçacıklı uygulama](https://go.microsoft.com/fwlink/?LinkID=160038)
