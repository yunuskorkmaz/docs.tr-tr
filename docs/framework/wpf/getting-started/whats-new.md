---
title: WPF Sürüm 4.5'te Yenilikler
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746925"
---
# <a name="whats-new-in-wpf-version-45"></a>WPF Sürüm 4.5'te Yenilikler
<a name="introduction"></a>Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sürüm 4,5 ' deki yeni ve gelişmiş özellikler hakkında bilgiler içerir.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Şerit denetimi](#ribbon_control)  
  
- [Büyük ölçekli veri kümeleri görüntülenirken performans artırıldı](#grouped_virtualization)  
  
- [VirtualizingPanel için yeni özellikler](#VirtualizingPanel)  
  
- [Statik özelliklere bağlama](#static_properties)  
  
- [Kullanıcı arabirimi olmayan Iş parçacıklarında koleksiyonlara erişme](#xthread_access)  
  
- [Eşzamanlı ve zaman uyumsuz olarak verileri doğrulama](#INotifyDataErrorInfo)  
  
- [Veri bağlamasının kaynağını otomatik olarak güncelleştirme](#delay)  
  
- [ICustomTypeProvider 'ı uygulayan türlere bağlama](#ICustomTypeProvider)  
  
- [Bağlama ifadesinden veri bağlama bilgilerini alma](#binding_state)  
  
- [Geçerli bir DataContext nesnesi denetleniyor](#DisconnectedSource)  
  
- [Verilerin değerleri değiştiğinde verileri yeniden konumlandırma (canlı şekillendirme)](#live_shaping)  
  
- [Bir olaya zayıf bir başvuru kurmak için geliştirilmiş destek](#weak_event_pattern)  
  
- [Dağıtıcı sınıfı için yeni Yöntemler](#async)  
  
- [Olaylar için biçimlendirme uzantıları](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Şerit denetimi  
 WPF 4,5, hızlı erişim araç çubuğu, uygulama menüsü ve sekmeler barındıran bir <xref:System.Windows.Controls.Ribbon.Ribbon> denetimiyle birlikte sunulur.  Daha fazla bilgi için [şeride genel bakış](/visualstudio/vsto/ribbon-overview)bölümüne bakın.  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Büyük ölçekli veri kümeleri görüntülenirken performans artırıldı  
 Kullanıcı arabirimi (UI) öğelerinden oluşan bir alt küme, ekranda görünür öğeleri temel alan daha fazla sayıda veri öğesinden oluşturulduğunda, UI Sanallaştırması oluşur. <xref:System.Windows.Controls.VirtualizingPanel>, gruplanmış veriler için UI sanallaştırmayı sağlayan <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> iliştirilmiş özelliği tanımlar.  Verileri gruplandırma hakkında daha fazla bilgi için bkz. nasıl yapılır: XAML 'de görünüm kullanarak verileri sıralama ve gruplama.  Gruplanmış verileri sanallaştırıp hakkında daha fazla bilgi için <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> Ekli özelliğine bakın.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel için yeni özellikler  
  
1. <xref:System.Windows.Controls.VirtualizingStackPanel>gibi bir <xref:System.Windows.Controls.VirtualizingPanel>, <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> iliştirilmiş özelliği kullanarak kısmi öğeleri görüntüleyip görüntülemediğini belirtebilirsiniz. <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> <xref:System.Windows.Controls.ScrollUnit.Item>olarak ayarlanırsa <xref:System.Windows.Controls.VirtualizingPanel> yalnızca tamamen görünür olan öğeleri görüntüler. <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> <xref:System.Windows.Controls.ScrollUnit.Pixel>olarak ayarlanırsa, <xref:System.Windows.Controls.VirtualizingPanel> kısmen görünür öğeleri görüntüleyebilir.  
  
2. <xref:System.Windows.Controls.VirtualizingPanel>, <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> iliştirilmiş özelliğini kullanarak sanallaştırırken, görünüm penceresinin önüne ve arkasına önbelleğin boyutunu belirtebilirsiniz.  Önbellek, öğelerin sanallaştırılmamış olan görünüm penceresinin üzerinde veya altında yer alan miktarıdır.  Bir önbellek kullanarak, görünümde kaydırılabilecekleri Kullanıcı arabirimi öğeleri oluşturulmasını önlemek performansı iyileştirebilir. Önbellek, işlem sırasında yanıt vermemeye devam edebilmesi için daha düşük bir önceliğe doldurulur. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> özelliği, <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>tarafından kullanılan ölçüm birimini belirler.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Statik özelliklere bağlama  
 Statik özellikleri bir veri bağlamanın kaynağı olarak kullanabilirsiniz. Veri bağlama altyapısı, statik bir olay ortaya çıktığında özelliğin değerinin ne zaman değişeceğinin algılar.  Örneğin, sınıfı `SomeClass` `MyProperty`adlı statik bir özellik tanımlıyorsa `SomeClass` `MyProperty` değeri değiştiğinde oluşturulan statik bir olay tanımlayabilir.  Statik olay, aşağıdaki imzaların birini kullanabilir.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 İlk durumda, sınıfının, olay işleyicisine <xref:System.EventArgs> geçiren *PropertyName*`Changed` adlı statik bir olay kullanıma sunduğunu unutmayın.  İkinci durumda, sınıfı, <xref:System.ComponentModel.PropertyChangedEventArgs> olay işleyicisine geçiren `StaticPropertyChanged` adlı statik bir olay gösterir. Statik özelliği uygulayan bir sınıf, her iki yöntemi kullanarak özellik değişikliği bildirimleri kullanmayı seçebilir.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Kullanıcı arabirimi olmayan Iş parçacıklarında koleksiyonlara erişme  
 WPF, koleksiyon oluşturenden farklı iş parçacıklarında veri koleksiyonlarına erişmenize ve bunları değiştirmenize olanak sağlar.  Bu, bir veritabanı gibi bir dış kaynaktan veri almak için bir arka plan iş parçacığı kullanmanızı ve verileri Kullanıcı arabirimi iş parçacığında görüntülemenizi sağlar.  Koleksiyonu değiştirmek için başka bir iş parçacığı kullanarak Kullanıcı arabiriminiz kullanıcı etkileşimine yanıt vermeye devam eder.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Eşzamanlı ve zaman uyumsuz olarak verileri doğrulama  
 <xref:System.ComponentModel.INotifyDataErrorInfo> arabirimi, veri varlık sınıflarının özel doğrulama kuralları uygulamasına ve doğrulama sonuçlarının zaman uyumsuz olarak kullanıma sunulmasına olanak sağlar. Bu arabirim Ayrıca özel hata nesnelerini, özellik başına birden çok hatayı, çapraz Özellik hatalarını ve varlık düzeyindeki hataları destekler.  Daha fazla bilgi için bkz. <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Veri bağlamasının kaynağını otomatik olarak güncelleştirme  
 Bir veri kaynağını güncelleştirmek için veri bağlama kullanırsanız, kaynak güncelleştirmelerden önce hedefteki Özellik değişikliklerinden sonra geçmesi gereken süreyi belirtmek için <xref:System.Windows.Data.BindingBase.Delay%2A> özelliğini kullanabilirsiniz.  Örneğin, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özellik verileri bir veri nesnesinin özelliğine iki yönlü bir <xref:System.Windows.Controls.Slider> sahip olduğunuzu ve <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğinin <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>olarak ayarlandığını varsayalım.  Bu örnekte, Kullanıcı <xref:System.Windows.Controls.Slider>taşırken <xref:System.Windows.Controls.Slider> taşınan her bir piksel için kaynak güncellenir.  Kaynak nesne, genellikle kaydırıcının <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değiştirmeyi durdurulduğunda kaydırıcının değerine ihtiyaç duyuyor.  Kaynağın çok sık güncelleştirilmesini engellemek için <xref:System.Windows.Data.BindingBase.Delay%2A> kullanarak, parmak izi hareket ettikten sonra belirli bir süre geçtikten sonra kaynağın güncelleştirilmemelidir.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>ICustomTypeProvider 'ı uygulayan türlere bağlama  
 WPF, özel türler olarak da bilinen <xref:System.Reflection.ICustomTypeProvider>uygulayan nesnelere veri bağlamayı destekler.  Aşağıdaki durumlarda özel türleri kullanabilirsiniz.  
  
1. Bir veri bağlamasında <xref:System.Windows.PropertyPath> olarak. Örneğin, bir <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.Binding.Path%2A> özelliği özel bir türün özelliğine başvurabilir.  
  
2. <xref:System.Windows.DataTemplate.DataType%2A> özelliğinin değeri olarak.  
  
3. <xref:System.Windows.Controls.DataGrid>otomatik olarak oluşturulan sütunları belirleyen bir tür olarak.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Bağlama ifadesinden veri bağlama bilgilerini alma  
 Belirli durumlarda, bir <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.BindingExpression> alabilir ve bağlamanın kaynak ve hedef nesneleriyle ilgili bilgilere ihtiyaç duyabilirsiniz.  Kaynak veya hedef nesne ya da ilişkili özelliği almanızı sağlamak için yeni API 'Ler eklenmiştir.  Bir <xref:System.Windows.Data.BindingExpression>olduğunda, hedef ve kaynak hakkında bilgi almak için aşağıdaki API 'Leri kullanın.  
  
|Bağlamanın bu değerini bulmak için|Bu API 'YI kullan|  
|---------------------------------------|------------------|  
|Hedef nesne|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Target özelliği|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Kaynak nesne|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Source özelliği|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Data.BindingExpression> bir <xref:System.Windows.Data.BindingGroup> ait olup olmadığı|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Data.BindingGroup> sahibi|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Geçerli bir DataContext nesnesi denetleniyor  
 Bir <xref:System.Windows.Controls.ItemsControl> bir öğe kapsayıcısının <xref:System.Windows.FrameworkElement.DataContext%2A> bağlantısı kesildiğinde oluşan durumlar vardır.  Öğe kapsayıcısı, bir <xref:System.Windows.Controls.ItemsControl>öğe görüntüleyen UI öğesidir.  Bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyona veri bağlandığında, her öğe için bir öğe kapsayıcısı oluşturulur. Bazı durumlarda, öğe kapsayıcıları görsel ağaçtan kaldırılır. Bir öğe kapsayıcısının kaldırıldığı iki tipik durum, temel koleksiyondan bir öğe kaldırıldığında ve <xref:System.Windows.Controls.ItemsControl>sanallaştırma etkinleştirildiğinde. Bu durumlarda, öğe kapsayıcısının <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği, <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> static özelliği tarafından döndürülen Sentinel nesnesine ayarlanır.  Bir öğe kapsayıcısının <xref:System.Windows.FrameworkElement.DataContext%2A> erişmeden önce <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> nesnesine eşit olup olmadığını denetlemeniz gerekir.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Verilerin değerleri değiştiğinde verileri yeniden konumlandırma (canlı şekillendirme)  
 Bir veri koleksiyonu gruplandırılabilir, sıralanabilir veya filtrelenebilir. WPF 4,5, verilerin değiştirildiği sırada verilerin yeniden düzenlenmesini sağlar. Örneğin, bir uygulamanın stok pazarında hisse senetleri listelemek için <xref:System.Windows.Controls.DataGrid> kullandığını ve hisse senetleri stok değerine göre sıralandığını varsayalım. Canlı sıralama, hisse senedi ' <xref:System.Windows.Data.CollectionView>etkin hale gelirse, hisse senedi değeri başka bir hisse senedinin değerinden daha büyük veya daha az olduğunda, <xref:System.Windows.Controls.DataGrid> bir hisse senedi.   Daha fazla bilgi için <xref:System.ComponentModel.ICollectionViewLiveShaping> arabirimine bakın.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Bir olaya zayıf bir başvuru kurmak için geliştirilmiş destek  
 Olaylara abone olan aboneler ek bir arabirim uygulamadan bu uygulamaya katılabildiğinden, zayıf olay deseninin uygulanması artık daha kolay olur.  Genel <xref:System.Windows.WeakEventManager> sınıfı ayrıca, belirli bir olay için adanmış bir <xref:System.Windows.WeakEventManager> yoksa, abonelerin zayıf olay düzenine katılmasını sağlar.  Daha fazla bilgi için bkz. [zayıf olay desenleri](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Dağıtıcı sınıfı için yeni Yöntemler  
 Dağıtıcı sınıfı, zaman uyumlu ve zaman uyumsuz işlemler için yeni Yöntemler tanımlar.  Zaman uyumlu <xref:System.Windows.Threading.Dispatcher.Invoke%2A> yöntemi, bir <xref:System.Action> veya <xref:System.Func%601> parametresi alan aşırı yüklemeleri tanımlar. <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>yeni zaman uyumsuz yöntem, geri çağırma parametresi olarak bir <xref:System.Action> veya <xref:System.Func%601> alır ve bir <xref:System.Windows.Threading.DispatcherOperation> ya da <xref:System.Windows.Threading.DispatcherOperation%601>döndürür.   <xref:System.Windows.Threading.DispatcherOperation> ve <xref:System.Windows.Threading.DispatcherOperation%601> sınıfları bir <xref:System.Threading.Tasks.Task> özelliği tanımlar.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>çağırdığınızda, `await` anahtar sözcüğünü <xref:System.Windows.Threading.DispatcherOperation> ya da ilişkili <xref:System.Threading.Tasks.Task>kullanabilirsiniz. Bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>tarafından döndürülen <xref:System.Threading.Tasks.Task> için zaman uyumlu olarak beklemeniz gerekiyorsa, <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemini çağırın. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> çağrısı, işlem çağıran bir iş parçacığında sıraya alınmışsa kilitlenmeyle sonuçlanır. Zaman uyumsuz işlemleri gerçekleştirmek için <xref:System.Threading.Tasks.Task> kullanma hakkında daha fazla bilgi için bkz. [Görev Paralelliği (görev paralel kitaplığı)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Olaylar için biçimlendirme uzantıları  
 WPF 4,5, olaylar için biçimlendirme uzantılarını destekler.  WPF, olaylar için kullanılmak üzere bir işaretleme uzantısı tanımlamaz, ancak üçüncü taraflar olaylarla kullanılabilecek bir işaretleme uzantısı oluşturabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework’teki Yenilikler](../../whats-new/index.md)
