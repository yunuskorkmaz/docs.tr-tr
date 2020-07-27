---
title: İş Parçacığı Modeli
description: Windows Presentation Foundation uygulamanızda birden çok iş parçacığına ihtiyacınız olabilecek durumlar hakkında bilgi edinin. Tek iş parçacıklı çözümler tercih edilir.
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
ms.openlocfilehash: 9b67b6ea2896e9e6fec57dee8d1013d54fab03fc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166378"
---
# <a name="threading-model"></a>İş Parçacığı Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], iş parçacığı zorluklarından geliştiricilerin kaydedileceği şekilde tasarlanmıştır. Sonuç olarak, geliştiricilerin çoğunluğu birden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fazla iş parçacığı kullanan bir arabirim yazmak zorunda kalmaz. Çok iş parçacıklı programlar karmaşık olduğu ve hata ayıklamanın zor olduğu için, tek iş parçacıklı çözümler olduğunda bu, kaçınılmalıdır.

 Bununla birlikte ne kadar iyi mimari olduğuna bakılmaksızın, hiçbir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] çerçeve her bir sorun için tek iş parçacıklı bir çözüm sağlayacaktır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yakın zamanda gelir, ancak birden çok iş parçacığının [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] yanıt hızını veya uygulama performansını artıran durumlar vardır. Bu şekilde, bazı arka plan malzemeleri ele alındıktan sonra bu durum, bu durumların bazılarını araştırır ve daha sonra bazı alt düzey ayrıntıların bir tartışmasına göre sonlanır.

> [!NOTE]
> Bu konuda, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> zaman uyumsuz çağrılar için yöntemi kullanılarak iş parçacığı ele alınmaktadır. Ayrıca, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> bir <xref:System.Action> veya parametresi olarak kullanan yöntemini çağırarak zaman uyumsuz çağrılar yapabilirsiniz <xref:System.Func%601> .  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>Yöntemi, <xref:System.Windows.Threading.DispatcherOperation> özelliği olan bir veya döndürür <xref:System.Windows.Threading.DispatcherOperation%601> <xref:System.Windows.Threading.DispatcherOperation.Task%2A> . `await`Anahtar sözcüğünü ya da ilişkili ile kullanabilirsiniz <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Threading.Tasks.Task> . Veya tarafından döndürülen için eşzamanlı olarak beklemeniz gerekiyorsa <xref:System.Threading.Tasks.Task> <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> , <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemini çağırın.  Çağırmak <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> kilitlenmeye neden olur. Zaman uyumsuz işlemleri gerçekleştirmek için kullanma hakkında daha fazla bilgi için <xref:System.Threading.Tasks.Task> bkz. Görev Paralelliği.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>Bu yöntemde, bir <xref:System.Action> veya parametresi olarak bir veya olarak alan aşırı yüklemeleri de vardır <xref:System.Func%601> .  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>Yöntemini, bir temsilciyi geçirerek zaman uyumlu çağrılar yapmak için kullanabilirsiniz <xref:System.Action> <xref:System.Func%601> .

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>Genel bakış ve dağıtıcı
 Genellikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar iki iş parçacığı ile başlar: bir, işleme ve bir diğeri yönetmek için bir diğeri [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . İşlem parçacığı, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı girişi aldığında, olayları işlerken, ekranı boyayıp uygulama kodunu çalıştırdığında, arka planda gizli olarak çalışır. Birçok uygulama tek bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı kullanır, ancak bazı durumlarda en iyi şekilde kullanılır. Bunu daha sonra bir örnekle tartışacağız.

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]İş parçacığı, adlı bir nesne içindeki iş öğelerini sıralar <xref:System.Windows.Threading.Dispatcher> . , <xref:System.Windows.Threading.Dispatcher> İş öğelerini öncelik temelinde seçer ve her birini tamamlamada çalıştırır.  Her [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında en az bir tane olmalıdır <xref:System.Windows.Threading.Dispatcher> ve her biri <xref:System.Windows.Threading.Dispatcher> iş öğelerini tam olarak bir iş parçacığında yürütebilirler.

 Kullanıcı dostu uygulamalar oluşturma eli, <xref:System.Windows.Threading.Dispatcher> iş öğelerini küçük tutarak aktarım hızını en üst düzeye çıkarabilmesini sağlar. Bu şekilde öğeler, <xref:System.Windows.Threading.Dispatcher> işlenmek üzere bekleyen sırada hiç kullanılmıyor. Giriş ve yanıt arasındaki perceivable gecikmesi bir kullanıcıyı rahatsız edebilir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Uygulamalar, büyük işlemleri işlemek için nasıl kullanılır? Kodunuz büyük bir hesaplama içeriyorsa veya bir veritabanını bir uzak sunucuda sorgulamak için ihtiyaç duyuyorsa ne olacak? Genellikle, yanıt ayrı bir iş parçacığında büyük işlemi idare etmek ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığını kuyruktaki öğelere eğilme etmek için serbest bırakır <xref:System.Windows.Threading.Dispatcher> . Büyük işlem tamamlandığında, sonuçları [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] görüntülenmek üzere iş parçacığına rapor edebilir.

 Tarihsel olarak, Windows [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelere yalnızca kendilerini oluşturan iş parçacığından erişilmesine izin verir. Bu, uzun süre çalışan bazı görevlerden sorumlu bir arka plan iş parçacığının, tamamlandığında bir metin kutusunu güncelleştiremeyeceği anlamına gelir. Windows, bileşenleri bütünlüğünü sağlamak için bunu yapar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bir liste kutusu, içeriği boyama sırasında arka plan iş parçacığı tarafından güncellendiyse tuhaf görünebilir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu koordinasyonu zorlayan yerleşik bir karşılıklı dışlama mekanizmasına sahiptir. İçindeki sınıfların çoğu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilir <xref:System.Windows.Threading.DispatcherObject> . Oluşturma sırasında, <xref:System.Windows.Threading.DispatcherObject> <xref:System.Windows.Threading.Dispatcher> o anda çalışan iş parçacığına bağlı bir başvuru depolar. Aslında, <xref:System.Windows.Threading.DispatcherObject> kendisini oluşturan iş parçacığıyla ilişkilendirir. Program yürütme sırasında, bir <xref:System.Windows.Threading.DispatcherObject> ortak <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> yöntemini çağırabilir. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A><xref:System.Windows.Threading.Dispatcher>geçerli iş parçacığıyla ilişkili olduğunu inceler ve <xref:System.Windows.Threading.Dispatcher> oluşturma sırasında saklanan başvuruyla karşılaştırır. Eşleşmiyorsa <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> bir özel durum oluşturur. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>, bir öğesine ait her yöntemin başlangıcında çağrılmalıdır <xref:System.Windows.Threading.DispatcherObject> .

 Yalnızca bir iş parçacığı değişiklik yapabiliyorsanız [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , arka plan iş parçacıkları kullanıcıyla nasıl etkileşebilir? Bir arka plan iş parçacığı, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığının adına bir işlem gerçekleştirmesini isteyebilir. İş parçacığını iş parçacığı ile kaydederek bunu yapar <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . <xref:System.Windows.Threading.Dispatcher>Sınıfı, iş öğelerini kaydetmek için iki yöntem sağlar: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ve <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> . Her iki yöntem de bir temsilciyi yürütmeye zamanlar. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>zaman uyumlu bir çağrıdır; diğer bir deyişle, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı gerçekten temsilciyi yürütmeyi bitirene kadar döndürmez. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>zaman uyumsuzdur ve hemen döndürür.

 <xref:System.Windows.Threading.Dispatcher>Öğeleri sırasıyla sırasına göre sıralar. Kuyruğa bir öğe eklenirken belirtilen on düzey vardır <xref:System.Windows.Threading.Dispatcher> . Bu öncelikler <xref:System.Windows.Threading.DispatcherPriority> numaralandırmada tutulur. Düzeyler hakkında ayrıntılı bilgi <xref:System.Windows.Threading.DispatcherPriority> Windows SDK belgelerinde bulunabilir.

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>İşlemdeki iş parçacıkları: örnekler

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Uzun süre çalışan bir hesaplama ile tek Iş parçacıklı bir uygulama
 Çoğu grafik kullanıcı arabirimi (Gua), kullanıcı etkileşimlerine yanıt olarak oluşturulan olayları beklerken zaman içindeki büyük bir bölümü harcamaktadır. Dikkatli bir programlamayla bu boşta kalma süresi, ' nin yanıt hızını etkilemeden oluşturulabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . İş parçacığı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modeli, girişin iş parçacığında meydana gelen bir işlemi kesmesine izin vermez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bu, <xref:System.Windows.Threading.Dispatcher> bekleyen giriş olaylarını eski olmadan işlemek için düzenli aralıklarla geri döndiğinizden emin olmanız gerektiği anlamına gelir.

 Aşağıdaki örneği inceleyin:

 ![Asal sayıların iş parçacığı gösteren ekran görüntüsü.](./media/threading-model/threading-prime-numbers.png)

 Bu basit uygulama, üç ' dan yukarı doğru sayılır, asal sayılar için arama yapılır. Kullanıcı **Başlat** düğmesine tıkladığında arama başlar. Program bir ana bulduğunda, Kullanıcı arabirimini bulma işlemi ile güncelleştirir. Herhangi bir noktada Kullanıcı aramayı durdurabilir.

 Yeterince basit olsa da, asal sayı araması sonsuza kadar devam eder ve bu da bazı zorluklar sunar.  Düğmenin tıklama olayı işleyicisi içinde tüm aramayı ele aldık, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığına diğer olayları işleme şansı vermeiyoruz. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Giriş veya işlem iletilerine yanıt veremezse. Hiçbir şekilde yeniden boyanır ve düğme tıklamalarına hiç yanıt vermez.

 Ana sayı aramasını ayrı bir iş parçacığında ele geçirebilir, ancak eşitleme sorunlarıyla uğraşmanız gerekir. Tek iş parçacıklı bir yaklaşımla, bulunan en büyük ana alanı listeleyen etiketi doğrudan güncelleştirebiliriz.

 Hesaplama görevini yönetilebilir parçalara ayırdık, düzenli aralıklarla <xref:System.Windows.Threading.Dispatcher> ve işlem olaylarına geri dönebiliriz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Girişi yeniden çizmeyi ve işlemeyi sağlayacak bir fırsat verebiliriz.

 Hesaplama ve olay işleme arasındaki işleme süresini bölmenin en iyi yolu, ' dan hesaplamayı yönetmekdir <xref:System.Windows.Threading.Dispatcher> . <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>Yöntemini kullanarak, ana sayı denetimlerini olayların çizildiği sırada zamanlayabiliriz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bizim örneğimizde, aynı anda yalnızca tek bir ana sayı denetimi zamanladık. Asal sayı denetimi tamamlandıktan sonra sonraki denetimi hemen zamanlıyoruz. Bu denetim yalnızca bekleyen olaylar işlendikten sonra devam eder [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

 ![Dağıtıcı kuyruğunu gösteren ekran görüntüsü.](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word, bu mekanizmayı kullanarak yazım denetimi gerçekleştirir. Yazım denetimi, iş parçacığının boşta kalma süresi kullanılarak arka planda yapılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Şimdi koda göz atalım.

 Aşağıdaki örnek, Kullanıcı arabirimini oluşturan XAML 'yi gösterir.

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 Aşağıdaki örnek, arka plan kodunu gösterir.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 Aşağıdaki örnek, için olay işleyicisini gösterir <xref:System.Windows.Controls.Button> .

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 Bu işleyicinin, içindeki metni güncelleştirmesinin yanı sıra, <xref:System.Windows.Controls.Button> kuyruğa bir temsilci ekleyerek ilk asal sayı denetiminin planlanmasından sorumludur <xref:System.Windows.Threading.Dispatcher> . Bu olay işleyicisi işini tamamladıktan sonra, <xref:System.Windows.Threading.Dispatcher> yürütme için bu temsilciyi seçer.

 Daha önce bahsedildiği gibi, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> <xref:System.Windows.Threading.Dispatcher> bir temsilciyi yürütmeye zamanlamak için kullanılan üye. Bu durumda öncelik ' i seçeceğiz <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> . <xref:System.Windows.Threading.Dispatcher>Bu temsilciyi yalnızca işlemek için önemli bir olay olmadığında yürütecektir. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Yanıt verme sayısı, sayı denetlenmeden daha önemlidir. Ayrıca, sayı denetimi yordamını temsil eden yeni bir temsilci geçiririz.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 Bu yöntem, sonraki tek sayının asal olup olmadığını denetler. Asal ise, yöntemi, `bigPrime` <xref:System.Windows.Controls.TextBlock> bulmayı yansıtacak şekilde doğrudan öğesini güncelleştirir. Bu, hesaplamayı, bileşeni oluşturmak için kullanılan aynı iş parçacığında gerçekleştiğinden, bunu yapabiliriz. Hesaplama için ayrı bir iş parçacığı kullanmayı seçtik, daha karmaşık bir eşitleme mekanizması kullanmak ve güncelleştirmeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığında yürütmek istiyoruz. Bu durumu daha sonra göstereceğiz.

 Bu örneğe ilişkin tam kaynak kodu için, [uzun süre çalışan hesaplama örneğiyle tek Iş parçacıklı uygulamaya](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication) bakın

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Bir arka plan Iş parçacığı ile engelleyici Işlemi işleme
 Grafik uygulamada engelleme işlemlerini işleme zor olabilir. Uygulama dondurmak için göründüğünden olay işleyicilerinden engelleme yöntemlerini çağırmak istemiyorum. Bu işlemleri işlemek için ayrı bir iş parçacığı kullanabiliriz, ancak işiniz bittiğinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığından doğrudan GUI 'yi değiştiremedik için iş parçacığıyla eşitliyoruz. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> İş parçacığının içine temsilciler eklemek için veya kullanabilirsiniz <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Sonuç olarak, bu Temsilciler öğeleri değiştirme izniyle yürütülür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

 Bu örnekte, hava durumu tahminini alan bir uzak yordam çağrısını taklit ediyoruz. Bu çağrıyı yürütmek için ayrı bir çalışan iş parçacığı kullanıyoruz ve <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bitirtiğimiz sırada iş parçacığında bir güncelleştirme yöntemi zamanladık.

 ![Hava durumu Kullanıcı arabirimini gösteren ekran görüntüsü.](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 Aşağıda, belirtime bazı ayrıntılar verilmiştir.

- Düğme Işleyicisi oluşturma

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 Düğmeye tıklandığında saat çizimi görüntülenir ve canlandırarak başlayın. Düğmeyi devre dışı bıraktık. `FetchWeatherFromServer`Yöntemi yeni bir iş parçacığında çağırır ve sonra geri döntiğimiz için <xref:System.Windows.Threading.Dispatcher> Hava durumu tahminini toplamayı beklerken olayları işlemesini sağlar.

- Hava durumu getiriliyor

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 Şeyleri basit tutmak için, bu örnekte aslında hiçbir ağ kodu yoktur. Bunun yerine, yeni iş parçacığını dört saniye boyunca uykuya yerleştirerek ağ erişimi gecikmesi benzetimi yapılır. Bu süre içinde, özgün [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı çalışmaya devam eder ve olaylara yanıt verir. Bunu göstermek için, çalışan bir animasyon kalmadı ve simge durumuna küçült ve büyüt düğmeleri de çalışmaya devam eder.

 Gecikme bittiğinde ve hava durumu tahminimizi gelişigüzel bir şekilde seçtiğimiz zaman, iş parçacığına yeniden rapor veririz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bu, iş parçacığı tarafından iş parçacığında öğesine bir çağrı zamanlayarak yapılır `UpdateUserInterface` [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Threading.Dispatcher> . Bu zamanlanmış yöntem çağrısına hava durumunu açıklayan bir dize geçiririz.

- Güncelleştirme[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] İş parçacığında zaman olduğunda, zamanlanan çağrısını yürütür `UpdateUserInterface` . Bu yöntem saat animasyonunu durdurup hava durumunu tanımlayacak bir görüntü seçer. Bu görüntüyü görüntüler ve "tahmin getirme" düğmesini geri yükler.

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>Birden çok pencere, birden çok Iş parçacığı
 Bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar birden çok üst düzey pencere gerektirir. Birden çok pencere yönetmek için bir Iş parçacığı/birleşim için mükemmel bir kabul edilebilir <xref:System.Windows.Threading.Dispatcher> , ancak bazen birkaç iş parçacığı daha iyi bir iş olur. Bu durum özellikle, bir Windows 'un iş parçacığını tekeline alacak herhangi bir şansınız varsa geçerlidir.

 Windows Gezgini bu biçimde çalışmaktadır. Her yeni Gezgin penceresi orijinal işleme aittir, ancak bağımsız bir iş parçacığının denetimi altında oluşturulur.

 Bir denetim kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> Web sayfalarını görüntüleriz. Kolayca basit bir Internet Explorer yerine kolayca oluşturabiliyoruz. Önemli bir özellik ile başlıyoruz: yeni bir Gezgin penceresi açma özelliği. Kullanıcı "yeni pencere" düğmesine tıkladığında, ayrı bir iş parçacığında penceremizin kopyasını başladık. Bu şekilde, Windows 'un birindeki uzun süreli veya engelleyici işlemler diğer tüm pencereleri kilitlemez.

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

 Bu yöntem, yeni iş parçacığının başlangıç noktasıdır. Bu iş parçacığının denetimi altında yeni bir pencere oluşturacağız. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Threading.Dispatcher>yeni iş parçacığını yönetmek için otomatik olarak yeni bir oluşturur. Tüm bunları, pencereyi başlatmak için yapmanız gerekir <xref:System.Windows.Threading.Dispatcher> .

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>Teknik ayrıntılar ve geçmiş noktaları

### <a name="writing-components-using-threading"></a>Iş parçacığı kullanarak bileşen yazma
 Microsoft .NET Framework Geliştirici Kılavuzu, bir bileşenin istemcilerine zaman uyumsuz davranış sergileme şeklini gösteren bir model tanımlar (bkz. [olay tabanlı zaman uyumsuz düzene genel bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Örneğin, `FetchWeatherFromServer` yöntemi yeniden kullanılabilir, grafik olmayan bir bileşene paketlemek istediğinizi varsayalım. Standart Microsoft .NET Framework deseninin ardından bu, aşağıdaki gibi görünür.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync`, bir arka plan iş parçacığı oluşturma gibi daha önce açıklanan tekniklerin birini kullanarak, çağrıyı zaman uyumsuz olarak işler, çağıran iş parçacığını engeller.

 Bu düzenin en önemli bölümlerinden biri, *MethodName* `Completed` Ile başlamak için *MethodName* yöntemini çağıran aynı iş parçacığında MethodName metodunu çağırıyor `Async` . Bunu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] depolayarak oldukça kolay bir şekilde yapabilirsiniz, <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> ancak grafik olmayan bileşen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms veya ASP.net programlarında değil yalnızca uygulamalarda kullanılabilir.

 <xref:System.Windows.Threading.DispatcherSynchronizationContext>Sınıfı bu ihtiyacı ele <xref:System.Windows.Threading.Dispatcher> alınmaktadır. Bu, diğer çerçeveler ile birlikte da bilinen basitleştirilmiş bir sürümü olarak düşünün [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>İç içe pompalama
 Bazen iş parçacığının tamamen kilitlenmesinden mümkün değildir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Sınıfın yöntemini ele alalım <xref:System.Windows.MessageBox.Show%2A> <xref:System.Windows.MessageBox> . <xref:System.Windows.MessageBox.Show%2A>Kullanıcı Tamam düğmesine tıklaana kadar döndürmez. Ancak, etkileşimli olması için ileti döngüsüne sahip olması gereken bir pencere oluşturur. Kullanıcının Tamam 'a tıklamasını beklerken, özgün uygulama penceresi Kullanıcı girişine yanıt vermez. Ancak, boyama iletilerini işlemeye devam eder. Özgün pencere, kapsandığınızda ve gösterildiğinde kendisini yeniden çizer.

 ![Tamam düğmesi ile MessageBox gösteren ekran görüntüsü](./media/threading-model/threading-message-loop.png)

 Bazı iş parçacıklarının ileti kutusu penceresinde bir ücret olması gerekir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yalnızca ileti kutusu penceresi için yeni bir iş parçacığı oluşturulabilir, ancak bu iş parçacığı özgün penceredeki devre dışı bırakılmış öğeleri boyayamadı (karşılıklı dışlamanın önceki tartışmasını hatırlayın). Bunun yerine, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iç içe geçmiş bir ileti işleme sistemi kullanır. <xref:System.Windows.Threading.Dispatcher>Sınıfı <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> , bir uygulamanın geçerli yürütme noktasını depolayan, sonra yeni bir ileti döngüsü Başlatan adlı özel bir yöntemi içerir. İç içe geçmiş ileti döngüsü tamamlandığında, yürütme özgün çağrıdan sonra devam eder <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> .

 Bu durumda, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> çağrısında program bağlamını korur <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> ve arka plan penceresini yeniden boyamak ve ileti kutusu penceresine girişi işlemek için yeni bir ileti döngüsü başlatır. Kullanıcı Tamam ' ı tıklattığında ve açılır pencereyi temizlediğinde, iç içe geçmiş döngü çıkar ve çağrısından sonra devam eder <xref:System.Windows.MessageBox.Show%2A> .

### <a name="stale-routed-events"></a>Eski yönlendirilmiş olaylar
 İçindeki yönlendirilmiş olay sistemi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Olaylar oluşturulduğunda tüm ağaçlara bildirir.

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 Elips üzerinde sol fare düğmesine basıldığında `handler2` yürütülür. `handler2`Tamamlandıktan sonra olay, <xref:System.Windows.Controls.Canvas> işlemek için kullanılan nesnesine geçirilir `handler1` . Bu yalnızca `handler2` olay nesnesini açıkça işlenmiş olarak işaretlemediğinde gerçekleşir.

 `handler2`Bu olayı işlemek çok uzun sürecek. `handler2`<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, saat döndürmeyen bir iç içe ileti döngüsünü başlatmak için kullanabilir. `handler2`Bu ileti döngüsü tamamlandığında olayı işlenmiş olarak işaretlemeirse, etkinlik çok eski olsa bile ağaca geçirilir.

### <a name="reentrancy-and-locking"></a>Yeniden giriş ve kilitleme
 Ortak dil çalışma zamanının (CLR) kilitleme mekanizması tam olarak tek bir şekilde davranmayabilir; bir kilit istenirken bir iş parçacığının işlemi tamamen durdurmasından kaynaklanabilir. Gerçekte, iş parçacığı yüksek öncelikli iletileri almaya ve işlemeye devam eder. Bu, kilitlenmeleri önlemeye yardımcı olur ve arabirimlerin düşük ölçüde yanıt vermesini sağlar, ancak hafif hatalara yönelik olasılığı ortaya çıkarır.  Bu sürenin büyük çoğunluğunda, bununla ilgili herhangi bir şey bilmeniz gerekmez, ancak nadir koşullarda (genellikle Win32 pencere iletilerini veya COM STA bileşenlerini içeren) Bu durum yararlı olabilir.

 Çoğu arabirim, iş parçacığı güvenliği göz önünde bulundurularak derlenmez çünkü geliştiriciler bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tarafından hiç bir iş parçacığı tarafından hiçbir şekilde erişilmediği varsayılarak çalışır. Bu durumda, bu tek iş parçacığı beklenmedik zamanlarda çevresel değişiklikler yapabilir ve bu da <xref:System.Windows.Threading.DispatcherObject> karşılıklı dışlama mekanizmasının çözülenmesinin beklenen etkileri olur. Aşağıdaki sözde kodu göz önünde bulundurun:

 ![İş parçacığı yeniden girişi gösteren diyagram.](./media/threading-model/threading-reentrancy.png "Threadingreentrance")

 Çoğu zaman doğru şeydir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu tür beklenmeyen yeniden giriş sorunları sorunlara neden olabileceği zamanlar vardır. Bu nedenle, belirli anahtar süreleriyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırır <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A> , bu iş parçacığının kilit yönergesini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her zamanki clr kilidi yerine yeniden giriş, serbest bir kilit kullanacak şekilde değiştirir.

 Bu nedenle, CLR ekibi neden bu davranışı seçmişmidir? COM STA nesneleri ve sonlandırma iş parçacığı ile yapması gerekiyordu. Bir nesne atık olarak toplandığında, `Finalize` yöntemi iş parçacığı değil, ayrılmış Sonlandırıcı iş parçacığında çalıştırılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . İş parçacığı üzerinde oluşturulan bir COM STA nesnesi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yalnızca iş parçacığı üzerinde atıyacağından, bu da sorunu çıkarmaktadır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . CLR, bir öğesinin eşdeğerini yapar <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (Bu örnekte Win32's kullanarak `SendMessage` ). Ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iş parçacığı meşgulse, Sonlandırıcı iş parçacığı durduruldu ve com STA nesnesi atılamaz ve bu da ciddi bir bellek sızıntısı oluşturur. Bu nedenle, CLR ekibi kilitleri yapmak için zor çağrıyı yaptığı gibi çalışır.

 İçin görevi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bellek sızıntısını yeniden bildirmeden beklenmedik bir şekilde yeniden giriş yapmaktan kaçınmaktır. bu nedenle her yerde yeniden giriş yapmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uzun süre çalışan hesaplama örneği olan tek Iş parçacıklı uygulama](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)
