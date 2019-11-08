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
ms.openlocfilehash: 22544b3bf2acf6e397f2ad5ae3de576bf491bd2b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740731"
---
# <a name="threading-model"></a>İş Parçacığı Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], geliştiricilerin iş parçacığı zorluklarından kaydedileceği şekilde tasarlanmıştır. Sonuç olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geliştiricilerin çoğunluğu birden fazla iş parçacığı kullanan bir arabirim yazmak zorunda kalmaz. Çok iş parçacıklı programlar karmaşık olduğu ve hata ayıklamanın zor olduğu için, tek iş parçacıklı çözümler olduğunda bu, kaçınılmalıdır.  
  
 Ancak, ne kadar iyi bir şekilde uygun olduğuna bakılmaksızın, hiçbir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] çerçevesi her bir sorun için tek iş parçacıklı bir çözüm sağlayacaktır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yakın, ancak birden çok iş parçacığının [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] yanıt verme hızını veya uygulama performansını geliştirmediği durumlar vardır. Bu şekilde, bazı arka plan malzemeleri ele alındıktan sonra bu durum, bu durumların bazılarını araştırır ve daha sonra bazı alt düzey ayrıntıların bir tartışmasına göre sonlanır.  

> [!NOTE]
> Bu konuda, zaman uyumsuz çağrılar için <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi kullanılarak iş parçacığı ele alınmaktadır. Ayrıca, bir <xref:System.Action> veya <xref:System.Func%601> parametre olarak kullanan <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> yöntemini çağırarak zaman uyumsuz çağrılar yapabilirsiniz.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> yöntemi, <xref:System.Windows.Threading.DispatcherOperation.Task%2A> özelliğine sahip <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>döndürür. `await` anahtar sözcüğünü <xref:System.Windows.Threading.DispatcherOperation> ya da ilişkili <xref:System.Threading.Tasks.Task>kullanabilirsiniz. Bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>tarafından döndürülen <xref:System.Threading.Tasks.Task> için zaman uyumlu olarak beklemeniz gerekiyorsa, <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemini çağırın.  <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> çağırmak kilitlenmeye neden olur. Zaman uyumsuz işlemleri gerçekleştirmek için <xref:System.Threading.Tasks.Task> kullanma hakkında daha fazla bilgi için bkz. Görev Paralelliği.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> yönteminde, bir <xref:System.Action> veya <xref:System.Func%601> parametre olarak alan aşırı yüklemeleri de vardır.  Bir temsilci, <xref:System.Action> veya <xref:System.Func%601>geçirerek zaman uyumlu çağrılar yapmak için <xref:System.Windows.Threading.Dispatcher.Invoke%2A> yöntemini kullanabilirsiniz.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Genel bakış ve dağıtıcı  
 Genellikle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar iki iş parçacığı ile başlar: bir diğeri, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yönetmek için işleme ve bir diğeri. İşleme iş parçacığı, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı girişi aldığında, olayları işlerken, ekranı boyayıp uygulama kodunu çalıştırdığında arka planda gizli olarak çalışır. Birçok uygulama tek bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı kullanır, ancak bazı durumlarda en iyi şekilde kullanılır. Bunu daha sonra bir örnekle tartışacağız.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı, <xref:System.Windows.Threading.Dispatcher>adlı bir nesne içindeki iş öğelerini sıralar. <xref:System.Windows.Threading.Dispatcher>, iş öğelerini öncelik temelinde seçer ve her birini tamamlamaya çalışır.  Her [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında en az bir <xref:System.Windows.Threading.Dispatcher>olmalı ve her <xref:System.Windows.Threading.Dispatcher> iş öğelerini tam olarak bir iş parçacığında yürütebilirler.  
  
 Kullanıcı dostu uygulamalar oluşturma eli, iş öğelerini küçük tutarak <xref:System.Windows.Threading.Dispatcher> aktarım hızını en üst düzeye çıkarabilmesini sağlar. Bu şekilde öğeler, işlenmek üzere bekleyen <xref:System.Windows.Threading.Dispatcher> kuyrukta hiç kullanılmıyor. Giriş ve yanıt arasındaki perceivable gecikmesi bir kullanıcıyı rahatsız edebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar büyük işlemleri nasıl işleymelidir? Kodunuz büyük bir hesaplama içeriyorsa veya bir veritabanını bir uzak sunucuda sorgulamak için ihtiyaç duyuyorsa ne olacak? Genellikle, yanıt ayrı bir iş parçacığında büyük işlemi işleymaktır ve bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığını <xref:System.Windows.Threading.Dispatcher> sırasındaki öğelere eğilimli olarak bırakır. Büyük işlem tamamlandığında, sonuçları görüntülenmek üzere [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığına rapor edebilir.  
  
 Tarihsel olarak, Windows [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerine yalnızca kendilerini oluşturan iş parçacığından erişilmesine izin verir. Bu, uzun süre çalışan bazı görevlerden sorumlu bir arka plan iş parçacığının, tamamlandığında bir metin kutusunu güncelleştiremeyeceği anlamına gelir. Windows, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bileşenlerinin bütünlüğünü sağlamak için bunu yapar. Bir liste kutusu, içeriği boyama sırasında arka plan iş parçacığı tarafından güncellendiyse tuhaf görünebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu koordinasyonu zorlayan yerleşik bir karşılıklı dışlama mekanizmasına sahiptir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu sınıf <xref:System.Windows.Threading.DispatcherObject>türetilir. Oluşturma sırasında <xref:System.Windows.Threading.DispatcherObject>, çalışmakta olan iş parçacığına bağlı <xref:System.Windows.Threading.Dispatcher> bir başvuru depolar. Aslında <xref:System.Windows.Threading.DispatcherObject>, kendisini oluşturan iş parçacığıyla ilişkilendirir. Program yürütme sırasında, <xref:System.Windows.Threading.DispatcherObject> ortak <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metodunu çağırabilir. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>, geçerli iş parçacığıyla ilişkili <xref:System.Windows.Threading.Dispatcher> inceler ve oluşturma sırasında saklanan <xref:System.Windows.Threading.Dispatcher> başvurusuyla karşılaştırır. Eşleşmiyorsa, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> bir özel durum oluşturur. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>, bir <xref:System.Windows.Threading.DispatcherObject>ait her yöntemin başlangıcında çağrılması amaçlanmıştır.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yalnızca bir iş parçacığı değiştirebilir, arka plan iş parçacıkları kullanıcıyla nasıl etkileşime geçebilir? Arka plan iş parçacığı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığından adına bir işlem gerçekleştirmesini isteyebilir. Bu, bir iş öğesini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığının <xref:System.Windows.Threading.Dispatcher> kaydederek yapar. <xref:System.Windows.Threading.Dispatcher> sınıfı, iş öğelerini kaydetmek için iki yöntem sunar: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ve <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Her iki yöntem de bir temsilciyi yürütmeye zamanlar. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> zaman uyumlu bir çağrıdır; diğer bir deyişle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı gerçekten temsilciyi yürütmeyi bitirene kadar döndürmez. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> zaman uyumsuzdur ve hemen döndürülür.  
  
 <xref:System.Windows.Threading.Dispatcher>, sırasındaki öğeleri önceliğe göre sıralar. <xref:System.Windows.Threading.Dispatcher> kuyruğuna bir öğe eklenirken belirtime gereken on düzey vardır. Bu öncelikler <xref:System.Windows.Threading.DispatcherPriority> numaralandırmasında tutulur. <xref:System.Windows.Threading.DispatcherPriority> düzeyler hakkında ayrıntılı bilgi Windows SDK belgelerinde bulunabilir.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>İşlemdeki iş parçacıkları: örnekler  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Uzun süre çalışan bir hesaplama ile tek Iş parçacıklı bir uygulama  
 Çoğu grafik kullanıcı arabirimi (Gua), kullanıcı etkileşimlerine yanıt olarak oluşturulan olayları beklerken zaman içindeki büyük bir bölümü harcamaktadır. Dikkatli bir programlamayla bu boşta kalma süresi, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yanıt hızını etkilemeden oluşturulabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli, girişin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında meydana gelen bir işlemi kesmesine izin vermez. Bu, bekleyen giriş olaylarını eski olmadan işlemek için <xref:System.Windows.Threading.Dispatcher> düzenli aralıklarla geri döndürtığınızdan emin olmanız gerektiği anlamına gelir.  
  
 Aşağıdaki örneği göz önünde bulundurun:  
  
 ![Asal sayıların iş parçacığı gösteren ekran görüntüsü.](./media/threading-model/threading-prime-numbers.png)  
  
 Bu basit uygulama, üç ' dan yukarı doğru sayılır, asal sayılar için arama yapılır. Kullanıcı **Başlat** düğmesine tıkladığında arama başlar. Program bir ana bulduğunda, Kullanıcı arabirimini bulma işlemi ile güncelleştirir. Herhangi bir noktada Kullanıcı aramayı durdurabilir.  
  
 Yeterince basit olsa da, asal sayı araması sonsuza kadar devam eder ve bu da bazı zorluklar sunar.  Düğmenin tıklama olayı işleyicisi içinde tüm aramayı ele aldık, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığına diğer olayları işleme şansı vermeiyoruz. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] giriş veya işlem iletilerine yanıt veremezse. Hiçbir şekilde yeniden boyanır ve düğme tıklamalarına hiç yanıt vermez.  
  
 Ana sayı aramasını ayrı bir iş parçacığında ele geçirebilir, ancak eşitleme sorunlarıyla uğraşmanız gerekir. Tek iş parçacıklı bir yaklaşımla, bulunan en büyük ana alanı listeleyen etiketi doğrudan güncelleştirebiliriz.  
  
 Hesaplama görevini yönetilebilir parçalara ayırdık, düzenli aralıklarla <xref:System.Windows.Threading.Dispatcher> ve olayları işleyecek şekilde geri dönebiliriz. Girişi yeniden boyamak ve işlemek için bir fırsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verebiliriz.  
  
 Hesaplama ve olay işleme arasındaki işleme süresini bölmenin en iyi yolu <xref:System.Windows.Threading.Dispatcher>hesaplamayı yönetmekdir. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> yöntemi kullanılarak, ana sayı denetimlerini [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olaylarının çizildiği sırada zamanlayabilirsiniz. Bizim örneğimizde, aynı anda yalnızca tek bir ana sayı denetimi zamanladık. Asal sayı denetimi tamamlandıktan sonra sonraki denetimi hemen zamanlıyoruz. Bu denetim yalnızca bekleyen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olayları işlendikten sonra devam eder.  
  
 ![Dağıtıcı kuyruğunu gösteren ekran görüntüsü.](./media/threading-model/threading-dispatcher-queue.png)  
  
 Microsoft Word, bu mekanizmayı kullanarak yazım denetimi gerçekleştirir. Yazım denetimi, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığının boşta kalma süresi kullanılarak arka planda yapılır. Şimdi koda göz atalım.  
  
 Aşağıdaki örnek, Kullanıcı arabirimini oluşturan XAML 'yi gösterir.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Aşağıdaki örnek, arka plan kodunu gösterir.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Controls.Button>için olay işleyicisi gösterilmektedir.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 <xref:System.Windows.Controls.Button>metnin güncelleştirilmesinin yanı sıra, bu işleyici, <xref:System.Windows.Threading.Dispatcher> kuyruğuna bir temsilci ekleyerek ilk asal sayı denetimini zamanlamaktan sorumludur. Bu olay işleyicisi işini tamamladıktan sonra, <xref:System.Windows.Threading.Dispatcher> yürütülmek üzere bu temsilciyi seçer.  
  
 Daha önce bahsedildiği gibi <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>, bir temsilciyi yürütmeye zamanlamak için kullanılan <xref:System.Windows.Threading.Dispatcher> üyesidir. Bu durumda <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> önceliğini seçeceğiz. <xref:System.Windows.Threading.Dispatcher> bu temsilciyi yalnızca işlemek için önemli bir olay olmadığında yürütecektir. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yanıt verme sayısı, sayı denetlemeden daha önemlidir. Ayrıca, sayı denetimi yordamını temsil eden yeni bir temsilci geçiririz.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Bu yöntem, sonraki tek sayının asal olup olmadığını denetler. Asal ise Yöntem, bulmayı yansıtmak için `bigPrime`<xref:System.Windows.Controls.TextBlock> doğrudan güncelleştirir. Bu, hesaplamayı, bileşeni oluşturmak için kullanılan aynı iş parçacığında gerçekleştiğinden, bunu yapabiliriz. Hesaplama için ayrı bir iş parçacığı kullanmayı seçtik, daha karmaşık bir eşitleme mekanizması kullanmak ve güncelleştirmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında yürütmek istiyoruz. Bu durumu daha sonra göstereceğiz.  
  
 Bu örneğe ilişkin tam kaynak kodu için, [uzun süre çalışan hesaplama örneğiyle tek Iş parçacıklı uygulamaya](https://go.microsoft.com/fwlink/?LinkID=160038) bakın  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Bir arka plan Iş parçacığı ile engelleyici Işlemi işleme  
 Grafik uygulamada engelleme işlemlerini işleme zor olabilir. Uygulama dondurmak için göründüğünden olay işleyicilerinden engelleme yöntemlerini çağırmak istemiyorum. Bu işlemleri işlemek için ayrı bir iş parçacığı kullanabiliriz, ancak işiniz bittiğinde, GUI 'yi çalışan iş parçacığından doğrudan değiştireemdiğimiz için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığıyla eşitliyoruz. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığının <xref:System.Windows.Threading.Dispatcher> içine temsilciler eklemek için <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> kullanabilirsiniz. Sonuç olarak, bu Temsilciler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri değiştirme izniyle yürütülür.  
  
 Bu örnekte, hava durumu tahminini alan bir uzak yordam çağrısını taklit ediyoruz. Bu çağrıyı yürütmek için ayrı bir çalışan iş parçacığı kullanıyoruz ve tamamlandığımızda [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığının <xref:System.Windows.Threading.Dispatcher> bir güncelleştirme yöntemi zamanladık.  
  
 ![Hava durumu Kullanıcı arabirimini gösteren ekran görüntüsü.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Aşağıda, belirtime bazı ayrıntılar verilmiştir.  
  
- Düğme Işleyicisi oluşturma  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Düğmeye tıklandığında saat çizimi görüntülenir ve canlandırarak başlayın. Düğmeyi devre dışı bıraktık. Yeni bir iş parçacığında `FetchWeatherFromServer` yöntemini çağırdık ve sonra geri dönediğimiz için, hava durumu tahminini toplamayı beklerken <xref:System.Windows.Threading.Dispatcher> olayları işlemesini sağlar.  
  
- Hava durumu getiriliyor  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Şeyleri basit tutmak için, bu örnekte aslında hiçbir ağ kodu yoktur. Bunun yerine, yeni iş parçacığını dört saniye boyunca uykuya yerleştirerek ağ erişimi gecikmesi benzetimi yapılır. Bu süre içinde, özgün [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı çalışmaya devam eder ve olaylara yanıt verir. Bunu göstermek için, çalışan bir animasyon kalmadı ve simge durumuna küçült ve büyüt düğmeleri de çalışmaya devam eder.  
  
 Gecikme bittiğinde ve hava durumu tahminimizi rastgele seçtiğimiz zaman, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığına yeniden rapor vereceğiz. Bunu, iş parçacığı <xref:System.Windows.Threading.Dispatcher>kullanarak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında `UpdateUserInterface` bir çağrı zamanlayarak yapacağız. Bu zamanlanmış yöntem çağrısına hava durumunu açıklayan bir dize geçiririz.  
  
- [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] güncelleştiriliyor  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığındaki <xref:System.Windows.Threading.Dispatcher> zamanı olduğunda, `UpdateUserInterface`zamanlanan çağrısını yürütür. Bu yöntem saat animasyonunu durdurup hava durumunu tanımlayacak bir görüntü seçer. Bu görüntüyü görüntüler ve "tahmin getirme" düğmesini geri yükler.  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Birden çok pencere, birden çok Iş parçacığı  
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar birden çok üst düzey pencere gerektirir. Birden çok pencere yönetmek için bir Iş parçacığı/<xref:System.Windows.Threading.Dispatcher> birleşimi için mükemmel bir kabul edilebilir, ancak bazen birkaç iş parçacığı daha iyi bir iş olur. Bu durum özellikle, bir Windows 'un iş parçacığını tekeline alacak herhangi bir şansınız varsa geçerlidir.  
  
 Windows Gezgini bu biçimde çalışmaktadır. Her yeni Gezgin penceresi orijinal işleme aittir, ancak bağımsız bir iş parçacığının denetimi altında oluşturulur.  
  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Frame> denetimi kullanarak Web sayfalarını görüntüleriz. Kolayca basit bir Internet Explorer yerine kolayca oluşturabiliyoruz. Önemli bir özellik ile başlıyoruz: yeni bir Gezgin penceresi açma özelliği. Kullanıcı "yeni pencere" düğmesine tıkladığında, ayrı bir iş parçacığında penceremizin kopyasını başladık. Bu şekilde, Windows 'un birindeki uzun süreli veya engelleyici işlemler diğer tüm pencereleri kilitlemez.  
  
 Gerçekte, Web tarayıcısı modelinin karmaşık iş parçacığı modeli vardır. Çoğu okuyucuları tanımak gerektiğinden, bunu seçtik.  
  
 Aşağıdaki örnek kodu gösterir.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Bu kodun aşağıdaki iş parçacığı kesimleri, bu bağlamda bizimle ilgili en ilginç bir koddur:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Bu yöntem, "yeni pencere" düğmesine tıklandığında çağrılır. Yeni bir iş parçacığı oluşturur ve zaman uyumsuz olarak başlatır.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Bu yöntem, yeni iş parçacığının başlangıç noktasıdır. Bu iş parçacığının denetimi altında yeni bir pencere oluşturacağız. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yeni bir iş parçacığını yönetmek için otomatik olarak yeni bir <xref:System.Windows.Threading.Dispatcher> oluşturur. Her şey, pencerenin işlevsel olmasını sağlamak için <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Teknik ayrıntılar ve geçmiş noktaları  
  
### <a name="writing-components-using-threading"></a>Iş parçacığı kullanarak bileşen yazma  
 Microsoft .NET Framework Geliştirici Kılavuzu, bir bileşenin istemcilerine zaman uyumsuz davranış sergileme şeklini gösteren bir model tanımlar (bkz. [olay tabanlı zaman uyumsuz düzene genel bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Örneğin, `FetchWeatherFromServer` yöntemini yeniden kullanılabilir, grafik olmayan bir bileşene paketlemek istediğimiz varsayın. Standart Microsoft .NET Framework deseninin ardından bu, aşağıdaki gibi görünür.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`, bir arka plan iş parçacığı oluşturma gibi daha önce açıklanan tekniklerin birini kullanarak, çağrıyı zaman uyumsuz olarak işler, çağıran iş parçacığını engellemiyor.  
  
 Bu düzenin en önemli bölümlerinden biri, ile başlamak için *methodname*`Async` yöntemini çağıran aynı Iş parçacığında *MethodName*`Completed` yöntemini çağırmaktadır. Bunu, <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>depolayarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oldukça kolay bir şekilde yapabilirsiniz ancak grafik olmayan bileşen yalnızca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda kullanılabilir, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] veya ASP.NET programlarında kullanılamaz.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> sınıfı bu gereksinimi giderir. Bu, diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] çerçeveleri ile de birlikte çalışarak Basitleştirilmiş <xref:System.Windows.Threading.Dispatcher> bir sürümü olarak düşünün.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>İç içe pompalama  
 Bazen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığını tamamen kilitlemek uygun değildir. <xref:System.Windows.MessageBox> sınıfının <xref:System.Windows.MessageBox.Show%2A> yöntemini ele alalım. <xref:System.Windows.MessageBox.Show%2A>, Kullanıcı Tamam düğmesine tıklaana kadar dönmez. Ancak, etkileşimli olması için ileti döngüsüne sahip olması gereken bir pencere oluşturur. Kullanıcının Tamam 'a tıklamasını beklerken, özgün uygulama penceresi Kullanıcı girişine yanıt vermez. Ancak, boyama iletilerini işlemeye devam eder. Özgün pencere, kapsandığınızda ve gösterildiğinde kendisini yeniden çizer.  
  
 ![Tamam düğmesi ile MessageBox gösteren ekran görüntüsü](./media/threading-model/threading-message-loop.png)  
  
 Bazı iş parçacıklarının ileti kutusu penceresinde bir ücret olması gerekir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yalnızca ileti kutusu penceresi için yeni bir iş parçacığı oluşturabilir, ancak bu iş parçacığı özgün penceredeki devre dışı bırakılmış öğeleri boyayamadı (karşılıklı dışlamanın önceki tartışmasını hatırlayın). Bunun yerine, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç içe geçmiş bir ileti işleme sistemi kullanır. <xref:System.Windows.Threading.Dispatcher> sınıfı, bir uygulamanın geçerli yürütme noktasını depolayan <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>adlı özel bir yöntemi içerir ve sonra yeni bir ileti döngüsü başlatır. İç içe geçmiş ileti döngüsü tamamlandığında, yürütme özgün <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağrısından sonra devam eder.  
  
 Bu durumda, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> <xref:System.Windows.MessageBox>çağrısında program bağlamını korur.<xref:System.Windows.MessageBox.Show%2A>ve arka plan penceresini yeniden boyamak ve ileti kutusu penceresine girişi işlemek için yeni bir ileti döngüsü başlatır. Kullanıcı Tamam ' ı tıklattığında ve açılır pencereyi temizlediğinde, iç içe geçmiş döngü çıkar ve <xref:System.Windows.MessageBox.Show%2A>çağrısından sonra devam eder.  
  
### <a name="stale-routed-events"></a>Eski yönlendirilmiş olaylar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ' deki yönlendirilmiş olay sistemi, olaylar oluşturulduğunda tüm ağaçları bilgilendirir.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Elips üzerinde sol fare düğmesine basıldığında `handler2` yürütülür. `handler2` tamamlandıktan sonra olay, işlemek için `handler1` kullanan <xref:System.Windows.Controls.Canvas> nesnesine geçirilir. Bu yalnızca `handler2` olay nesnesini açıkça işlenmiş olarak işaretlemediğinde gerçekleşir.  
  
 `handler2`, bu olayı işlemek için harika bir süre sürer. `handler2`, saat döndürmeyen bir iç içe ileti döngüsünü başlatmak için <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> kullanabilir. Bu ileti döngüsü tamamlandığında olayı işlenmiş olarak işaretlemeirse, etkinlik çok eski olsa bile ağaca geçirilir. `handler2`  
  
### <a name="reentrancy-and-locking"></a>Yeniden giriş ve kilitleme  
 Ortak dil çalışma zamanının (CLR) kilitleme mekanizması tam olarak tek bir şekilde davranmayabilir; bir kilit istenirken bir iş parçacığının işlemi tamamen durdurmasından kaynaklanabilir. Gerçekte, iş parçacığı yüksek öncelikli iletileri almaya ve işlemeye devam eder. Bu, kilitlenmeleri önlemeye yardımcı olur ve arabirimlerin düşük ölçüde yanıt vermesini sağlar, ancak hafif hatalara yönelik olasılığı ortaya çıkarır.  Bu sürenin büyük çoğunluğunda, bununla ilgili herhangi bir şey bilmeniz gerekmez, ancak nadir koşullarda (genellikle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere iletilerini veya COM STA bileşenlerini içeren) Bu durum farkında olabilir.  
  
 Çoğu arabirim, iş parçacığı güvenliği göz önünde bulundurularak derlenmez çünkü geliştiriciler bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] birden fazla iş parçacığı tarafından hiçbir şekilde erişilmediği varsayılarak çalışır. Bu durumda, bu tek iş parçacığı beklenmedik zamanlarda çevresel değişiklikler yapabilir ve bu durum, <xref:System.Windows.Threading.DispatcherObject> karşılıklı dışlama mekanizmasının çözülmesinin gerekmemesine neden olur. Aşağıdaki sözde kodu göz önünde bulundurun:  
  
 ![İş parçacığı yeniden girişi gösteren diyagram.](./media/threading-model/threading-reentrancy.png "Threadingreentrance")  
  
 Çoğu zaman doğru bir şeydir, ancak bu, beklenmeyen yeniden giriş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sorunlara neden olabilecek zamanlar vardır. Bu nedenle, belirli bir anahtar süreleriyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu iş parçacığının kilit yönergesini, olağan CLR kilidi yerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeniden giriş ve serbest bir kilit kullanacak şekilde değiştiren <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>çağırır.  
  
 Bu nedenle, CLR ekibi neden bu davranışı seçmişmidir? COM STA nesneleri ve sonlandırma iş parçacığı ile yapması gerekiyordu. Bir nesne atık olarak toplandığında, `Finalize` yöntemi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı değil, ayrılmış Sonlandırıcı iş parçacığında çalıştırılır. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı üzerinde oluşturulan bir COM STA nesnesi yalnızca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı üzerinde atıyacağından, bu sorun oluşur. CLR, bir <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> eşdeğerini yapar (Bu durumda Win32's `SendMessage`kullanılarak). Ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı meşgulse, Sonlandırıcı iş parçacığı durduruldu ve COM STA nesnesi atılamaz ve bu da ciddi bir bellek sızıntısı oluşturur. Bu nedenle, CLR ekibi kilitleri yapmak için zor çağrıyı yaptığı gibi çalışır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görevi, Bellek sızıntısını yeniden bildirmeden beklenmedik bir şekilde yeniden giriş yapmaktan kaçınmaktır. bu nedenle her yerde yeniden giriş yapmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uzun süre çalışan hesaplama örneği olan tek Iş parçacıklı uygulama](https://go.microsoft.com/fwlink/?LinkID=160038)
