---
title: WPF Sürüm 4.5'te Yenilikler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 03f785da018cacdec643fa196bdd0c6d5d7c7f70
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325832"
---
# <a name="whats-new-in-wpf-version-45"></a>WPF Sürüm 4.5'te Yenilikler
<a name="introduction"></a> Bu konu, yeni ve geliştirilmiş özellikleri hakkında bilgi içerir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sürüm 4.5.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Şerit denetimi](#ribbon_control)  
  
-   [Gruplandırılmış veri kümelerini büyük görüntüleme performansı geliştirildi](#grouped_virtualization)  
  
-   [VirtualizingPanel için yeni özellikler](#VirtualizingPanel)  
  
-   [Statik özellikler bağlama](#static_properties)  
  
-   [Koleksiyonlar üzerinde olmayan UI iş parçacığı erişme](#xthread_access)  
  
-   [Zaman uyumlu ve zaman uyumsuz olarak verileri doğrulama](#INotifyDataErrorInfo)  
  
-   [Veri bağlama kaynağı otomatik olarak güncelleştiriliyor](#delay)  
  
-   [Bu uygulama ICustomTypeProvider türlerine bağlama](#ICustomTypeProvider)  
  
-   [Bir bağlama ifadesinden veri bağlama bilgileri alınıyor](#binding_state)  
  
-   [İçin geçerli bir DataContext nesne denetleniyor](#DisconnectedSource)  
  
-   [(Canlı şekillendirme) veri değerleri değiştikçe verileri yeniden konumlandırma](#live_shaping)  
  
-   [Bir olay zayıf bir başvuru oluşturmak için gelişmiş destek](#weak_event_pattern)  
  
-   [Dispatcher sınıfı için yeni yöntemler](#async)  
  
-   [Olaylar için biçimlendirme uzantıları](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Şerit denetimi  
 WPF 4.5 ile birlikte gelir bir <xref:System.Windows.Controls.Ribbon.Ribbon> hızlı erişim araç çubuğu, uygulama menüsü ve sekmeler barındıran denetimi.  Daha fazla bilgi için [Şerite Genel Bakış](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Gruplandırılmış veri kümelerini büyük görüntüleme performansı geliştirildi  
 Kullanıcı Arabirimi sanallaştırma, bir alt kümesi olduğunda meydana gelen çok sayıda veri öğelerinin hangi öğelerin ekranda görünür olmasına göre oluşturulan kullanıcı arabirimi (UI) öğeleri. <xref:System.Windows.Controls.VirtualizingPanel> Tanımlar <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> ekli gruplandırılmış veriler için kullanıcı Arabirimi sanallaştırma sağlayan bir özellik.  Gruplandırma veriler hakkında daha fazla bilgi için bkz: nasıl yapılır: Bir görünümde XAML kullanarak verileri sıralama ve grup.  Gruplandırılmış veriler sanallaştırma hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> ekli özellik.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel için yeni özellikler  
  
1. Belirtebileceğiniz olup olmadığını bir <xref:System.Windows.Controls.VirtualizingPanel>, gibi <xref:System.Windows.Controls.VirtualizingStackPanel>, kısmi öğeleri kullanarak görüntüler <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ekli özellik. Varsa <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ayarlanır <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> yalnızca tamamen görünür olan öğeleri görüntüler. Varsa <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ayarlanır <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> kısmen görünür öğeleri görüntüleyebilirsiniz.  
  
2. Önce ve sonra Görünüm penceresinin önbellek boyutu belirtebilirsiniz, <xref:System.Windows.Controls.VirtualizingPanel> kullanarak sanallaştırma <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> ekli özellik.  Önbellek alanı öğeleri olmayan sanallaştırılır görünüm penceresinin altında veya üstünde miktarıdır.  Görünüme kaydırılan gibi kullanıcı Arabirimi öğeleri oluşturmaktan kaçınmak için bir önbellek kullanarak performansı artırabilirsiniz. Böylece uygulama işlemi sırasında yanıt vermemeye değil daha düşük bir öncelikte önbellek doldurulur. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Özelliği tarafından kullanılan ölçü belirler <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Statik özellikler bağlama  
 Statik özelliklere veri bağlama kaynağı olarak kullanabilirsiniz. Statik bir olayı oluşturulursa özelliğinin değeri değiştiğinde veri bağlama altyapısı tanır.  Örneğin, sınıf `SomeClass` adlı statik bir özellik tanımlar `MyProperty`, `SomeClass` olduğu statik bir olayı tanımlayabilir arandığında değerini `MyProperty` değişiklikler.  Statik olay aşağıdaki imzalar birini kullanabilirsiniz.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Bu durumda, sınıf adlı statik bir olay sunan Not *PropertyName* `Changed` Geçiren <xref:System.EventArgs> için olay işleyicisi.  İkinci durumda, sınıf adlı statik bir olay sunan `StaticPropertyChanged` Geçiren <xref:System.ComponentModel.PropertyChangedEventArgs> için olay işleyicisi. Özellik değişikliği bildirimleri her iki yöntemi kullanarak yükseltmek statik özelliği uygulayan bir sınıf seçebilirsiniz.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Koleksiyonlar üzerinde olmayan UI iş parçacığı erişme  
 WPF erişmek ve dışında koleksiyonu oluşturan bir iş parçacığı üzerinde veri koleksiyonları değiştirmenize olanak sağlar.  Bu, bir veritabanı gibi bir dış kaynaktan veri almak ve UI iş parçacığı üzerinde verileri görüntülemek için bir arka plan iş parçacığı kullanmanıza olanak sağlar.  Koleksiyonu değiştirmek için başka bir iş parçacığı kullanarak, kullanıcı arabirimi kullanıcı etkileşimine yanıt verebilecek duruma gelir.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Zaman uyumlu ve zaman uyumsuz olarak verileri doğrulama  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Arabirimi, özel doğrulama kuralları uygulamak ve doğrulama sonuçlarını zaman uyumsuz olarak kullanıma sunmak veri varlık sınıfları sağlar. Bu arabirim, özel hata nesneleri, özellik, çapraz özelliği hataları ve varlık düzeyinde hataları başına birden çok hata da destekler.  Daha fazla bilgi için bkz. <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Veri bağlama kaynağı otomatik olarak güncelleştiriliyor  
 Bir veri kaynağını güncelleştirmek için bir veri bağlamayı kullanırsanız, kullanabileceğiniz <xref:System.Windows.Data.BindingBase.Delay%2A> özelliği bir hedef kaynak güncelleştirmelerinin önce sonra özellik değişiklikleri geçirmek için süreyi belirtin.  Örneğin, sahip olduğunuzu varsayalım. bir <xref:System.Windows.Controls.Slider> olan kendi <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özellik verileri iki yönlü bir veri nesnesinin bir özelliğine bağlı ve <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Bu örnekte, kullanıcı hareket ettirdiğinde <xref:System.Windows.Controls.Slider>, her pikselin kaynak güncelleştirmeleri, <xref:System.Windows.Controls.Slider> taşır.  Kaynak nesne kaydırıcı değeri normalde gerekir. yalnızca kaydırıcının <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değiştirme durdurur.  Kaynak çok sık güncelleştirme önlemek için <xref:System.Windows.Data.BindingBase.Delay%2A> taşıma thumb kestikten sonra belirli bir süre sona erdiğinde kadar'ın kaynak güncelleştirilmemelidir belirtmek için.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Bu uygulama ICustomTypeProvider türlerine bağlama  
 WPF uygulayan nesneler için veri bağlamayı destekleyen <xref:System.Reflection.ICustomTypeProvider>, özel türleri olarak da bilinir.  Özel türler aşağıdaki durumlarda kullanabilirsiniz.  
  
1. Olarak bir <xref:System.Windows.PropertyPath> Veri bağlamada. Örneğin, <xref:System.Windows.Data.Binding.Path%2A> özelliği bir <xref:System.Windows.Data.Binding> özel tür bir özelliğine başvurabilir.  
  
2. Değeri olarak <xref:System.Windows.DataTemplate.DataType%2A> özelliği.  
  
3. Otomatik oluşturulan sütunları belirleyen bir tür olarak bir <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Bir bağlama ifadesinden veri bağlama bilgileri alınıyor  
 Bazı durumlarda, alabilirsiniz <xref:System.Windows.Data.BindingExpression> , bir <xref:System.Windows.Data.Binding> ve kaynak ve hedef nesneler bağlama hakkında bilgi gerekiyor.  Kaynak veya hedef nesne veya ilişkili özelliğin yararlanmanıza olanak tanıyacak için yeni API'ler eklenmiştir.  Olduğunda bir <xref:System.Windows.Data.BindingExpression>, hedef ve kaynak hakkında bilgi almak için aşağıdaki API'leri kullanın.  
  
|Bu bağlama değerini bulmak için|Bu API kullanın|  
|---------------------------------------|------------------|  
|Hedef nesne|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Hedef özelliği|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Kaynak nesne|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Source özelliği|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Olmadığını <xref:System.Windows.Data.BindingExpression> ait bir <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Sahibi bir <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>İçin geçerli bir DataContext nesne denetleniyor  
 Durumlar burada <xref:System.Windows.FrameworkElement.DataContext%2A> içinde bir öğe kapsayıcı bir <xref:System.Windows.Controls.ItemsControl> bağlantısı kesiliyor.  Öğe kapsayıcı bir öğeyi görüntüler kullanıcı Arabirimi öğesidir bir <xref:System.Windows.Controls.ItemsControl>.  Olduğunda bir <xref:System.Windows.Controls.ItemsControl> veriler bir koleksiyona bağlı, her öğe için bir öğe kapsayıcısı oluşturulur. Bazı durumlarda, öğe kapsayıcılarını görsel ağaç'tan kaldırılır. Öğe kapsayıcı kaldırıldı burada iki tipik durumlarda: ne zaman bir öğe temel alınan koleksiyondan kaldırılır ve ne zaman şirket Sanallaştırmanın etkinleştirildiği <xref:System.Windows.Controls.ItemsControl>. Bu gibi durumlarda, <xref:System.Windows.FrameworkElement.DataContext%2A> öğe kapsayıcı özelliği tarafından döndürülen sentinel nesne için ayarlanacak <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> statik özellik.  Denetlemeniz gereken olup olmadığını <xref:System.Windows.FrameworkElement.DataContext%2A> eşittir <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> erişmeden önce nesne <xref:System.Windows.FrameworkElement.DataContext%2A> öğe kapsayıcısı.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>(Canlı şekillendirme) veri değerleri değiştikçe verileri yeniden konumlandırma  
 Veri koleksiyonu gruplandırılmış, sıralar, filtre veya. WPF 4.5 verilerin veri değiştirildiğinde yeniden düzenlenecek olanak tanır. Örneğin, bir uygulamanın kullandığı varsayalım. bir <xref:System.Windows.Controls.DataGrid> listelemek için bir borsa, stocks ve borsa stok değere göre sıralanır. Canlı sıralama stocks üzerinde etkinse <xref:System.Windows.Data.CollectionView>, hisse 's konumda <xref:System.Windows.Controls.DataGrid> hisse değerin daha büyük hale geldiğinde taşır veya küçüktür başka bir stok'ın değeri.   Daha fazla bilgi için <xref:System.ComponentModel.ICollectionViewLiveShaping> arabirimi.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Bir olay zayıf bir başvuru oluşturmak için gelişmiş destek  
 Abonelere olayları içinde ek arabirimi uygulama olmadan katılabilir zayıf olay deseni uygulama artık daha kolay olmasıdır.  Genel <xref:System.Windows.WeakEventManager> sınıfı da zayıf olay deseni adanmış bir katılmak aboneleri sağlar <xref:System.Windows.WeakEventManager> için belirli bir olayı yok.  Daha fazla bilgi için [zayıf olay desenleri](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Dispatcher sınıfı için yeni yöntemler  
 Dispatcher sınıfı zaman uyumlu ve zaman uyumsuz işlemler için yeni yöntemleri tanımlar.  Zaman uyumlu <xref:System.Windows.Threading.Dispatcher.Invoke%2A> alan aşırı yüklemeler yöntemi tanımlayan bir <xref:System.Action> veya <xref:System.Func%601> parametresi. Yeni zaman uyumsuz yöntemin <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, ayrıca alır bir <xref:System.Action> veya <xref:System.Func%601> döndürür ve geri çağırma parametresi olarak bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> Ve <xref:System.Windows.Threading.DispatcherOperation%601> sınıfları tanımlayan bir <xref:System.Threading.Tasks.Task> özelliği.  Çağırdığınızda <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, kullanabileceğiniz `await` ya da anahtar sözcüğüyle <xref:System.Windows.Threading.DispatcherOperation> veya ilişkili <xref:System.Threading.Tasks.Task>. Zaman uyumlu olarak beklemesi gerekiyorsa <xref:System.Threading.Tasks.Task> tarafından döndürülen bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, çağrı <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemi. Çağırma <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> işlemi çağırma iş parçacığı üzerinde sıraya alınan bir kilitlenmeyle neden olur. Kullanma hakkında daha fazla bilgi için bir <xref:System.Threading.Tasks.Task> zaman uyumsuz işlemleri gerçekleştirmek için bkz: [görev Paralelliği (görev paralel kitaplığı)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Olaylar için biçimlendirme uzantıları  
 WPF 4.5 olayları için biçimlendirme uzantıları destekler.  WPF olaylar için kullanılacak bir işaretleme uzantısı tanımlamaz, ancak üçüncü taraflara olayları ile kullanılabilecek bir işaretleme uzantısı oluşturma olanağına sahip olursunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework’teki Yenilikler](../../whats-new/index.md)
