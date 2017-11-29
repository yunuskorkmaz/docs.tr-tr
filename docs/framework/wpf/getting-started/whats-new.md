---
title: "&#39; teki WPF sürüm 4. 5'deki yenilikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dc6a35a0ff8586b91ab7d74abc182fa6002f88
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2017
---
# <a name="what39s-new-in-wpf-version-45"></a>&#39; teki WPF sürüm 4. 5'deki yenilikler
<a name="introduction"></a>Bu konu, yeni ve geliştirilmiş özellikler hakkında bilgi içerir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sürüm 4.5.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Şerit denetimi](#ribbon_control)  
  
-   [Büyük görüntülerken, Gelişmiş performans gruplandırılmış veri kümelerini](#grouped_virtualization)  
  
-   [VirtualizingPanel için yeni özellikler](#VirtualizingPanel)  
  
-   [Statik özellikler bağlama](#static_properties)  
  
-   [Koleksiyonlar üzerinde dışı kullanıcı Arabirimi iş parçacığı erişme](#xthread_access)  
  
-   [Zaman uyumlu ve zaman uyumsuz olarak verileri doğrulama](#INotifyDataErrorInfo)  
  
-   [Veri bağlama kaynağını otomatik olarak güncelleştirme](#delay)  
  
-   [Bu uygulama ICustomTypeProvider türlerine bağlama](#ICustomTypeProvider)  
  
-   [Bir bağlama ifadesinden veri bağlama bilgileri alınıyor](#binding_state)  
  
-   [İçin geçerli bir DataContext nesne denetleniyor](#DisconnectedSource)  
  
-   [(Dinamik şekillendirme) verinin değerleri değiştirmek gibi veri yeniden konumlandırma](#live_shaping)  
  
-   [Bir olay zayıf başvuru oluşturma için geliştirilmiş destek](#weak_event_pattern)  
  
-   [Dağıtıcı sınıfı için yeni yöntemler](#async)  
  
-   [Olaylar için işaretleme uzantıları](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Şerit denetimi  
 WPF 4.5 ile birlikte gelen bir <xref:System.Windows.Controls.Ribbon.Ribbon> hızlı erişim araç çubuğu, uygulama menüsü ve sekmeleri barındıran denetim.  Daha fazla bilgi için bkz: [Şerite Genel Bakış](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Büyük görüntülerken, Gelişmiş performans gruplandırılmış veri kümelerini  
 UI sanallaştırma oluşur alt kullanıcı arabirimi (UI) öğeleri çok sayıda veri öğeleri hangi öğelerin ekranda görünür olan bağlı olarak oluşturulan. <xref:System.Windows.Controls.VirtualizingPanel> Tanımlar <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> UI sanallaştırma için gruplandırılmış veri sağlayan özelliği eklenmiş.  Gruplandırma veriler hakkında daha fazla bilgi için bkz: nasıl yapılır: sıralama ve grup verilerini kullanan XAML görünümünde.  Gruplandırılmış veriler sanallaştırma hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> özelliği eklenmiş.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel için yeni özellikler  
  
1.  Belirleyebileceğiniz olup bir <xref:System.Windows.Controls.VirtualizingPanel>, gibi <xref:System.Windows.Controls.VirtualizingStackPanel>, kısmi öğeleri kullanarak görüntüler <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> özelliği eklenmiş. Varsa <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ayarlanır <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> tamamen görünür olan öğeleri yalnızca görüntülenir. Varsa <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ayarlanır <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> kısmen görünür öğeleri görüntüleyebilirsiniz.  
  
2.  Önbellek boyutunu önce ve sonra Görünüm penceresinin belirtebilirsiniz zaman <xref:System.Windows.Controls.VirtualizingPanel> kullanarak sanallaştırılmasını <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> özelliği eklenmiş.  Önbellek alanı öğeleri değil sanallaştırılan görünüm penceresinin altında veya üstünde kullanılabilir.  Görünüme kaydırılan gibi kullanıcı Arabirimi öğeleri oluşturulmasını önlemek için bir önbellek kullanma performansını iyileştirebilir. Böylece uygulama işlemi sırasında yanıt vermemeye değil önbellek daha düşük öncelikli olarak doldurulur. <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Özelliği tarafından kullanılan ölçü belirler <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Statik özellikler bağlama  
 Statik özellikler veri bağlama kaynağı olarak kullanabilirsiniz. Statik bir olay oluşursa özelliğin değeri değiştiğinde veri bağlama altyapısı tanır.  Örneğin, varsa sınıfı `SomeClass` adlı bir statik özellik tanımlar `MyProperty`, `SomeClass` olan statik bir olay tanımlayabilirsiniz ne zaman yükseltilmiş değerini `MyProperty` değişiklikler.  Statik olay aşağıdaki imzalar birini kullanabilirsiniz.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 İlk durumda adlı statik bir olay sınıfı gösterir Not *PropertyName* `Changed` geçen <xref:System.EventArgs> olay işleyicisi.  İkinci durumda, adlı statik bir olay sınıfı gösterir `StaticPropertyChanged` geçen <xref:System.ComponentModel.PropertyChangedEventArgs> olay işleyicisi. Statik özelliği uygulayan bir sınıf, her iki yöntemi kullanarak özellik değişikliği bildirimleri yükseltmek seçebilirsiniz.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Koleksiyonlar üzerinde dışı kullanıcı Arabirimi iş parçacığı erişme  
 WPF erişmek ve iş parçacıkları koleksiyonu oluşturduğunuzda farklı veri koleksiyonlarında değiştirmenize olanak sağlar.  Bu bir veritabanı gibi bir dış kaynaktan veri almak ve kullanıcı Arabirimi iş parçacığı üzerinde verileri görüntülemek için bir arka plan iş parçacığı kullanmanıza olanak sağlar.  Koleksiyon değiştirmek için başka bir iş parçacığı kullanarak, kullanıcı arabiriminiz için kullanıcı etkileşimi yanıt verebilecek duruma gelir.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Zaman uyumlu ve zaman uyumsuz olarak verileri doğrulama  
 <xref:System.ComponentModel.INotifyDataErrorInfo> Arabirimi özel doğrulama kuralları uygulamak ve doğrulama sonuçlarını zaman uyumsuz olarak kullanıma sunmak veri sınıflar sağlar. Bu arabirim, özel hata nesneleri, özellik, çapraz özelliği hataları ve varlık düzeyi hataları başına birden çok hata da destekler.  Daha fazla bilgi için bkz. <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Veri bağlama kaynağını otomatik olarak güncelleştirme  
 Bir veri kaynağını güncelleştirmek için bir veri bağlama kullanırsanız, kullanabileceğiniz <xref:System.Windows.Data.BindingBase.Delay%2A> özelliği bir özellik değişikliklerinden sonra kaynak güncelleştirmelerinin önce hedefte geçirmek için zaman miktarı belirtin.  Örneğin, sahip olduğunuzu varsayın bir <xref:System.Windows.Controls.Slider> olan kendi <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği veri iki yönlü bir veri nesnesi özelliğine bağlı ve <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği ayarlanmış <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Bu örnekte, kullanıcı taşıdığında <xref:System.Windows.Controls.Slider>, her piksel için kaynak güncelleştirmeleri, <xref:System.Windows.Controls.Slider> taşır.  Kaynak nesne genellikle kaydırıcının değer, yalnızca kaydırıcının <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değiştirme durdurur.  Kaynak çok sık güncelleştirilmesini önlemek için kullanmak <xref:System.Windows.Data.BindingBase.Delay%2A> taşıma kaydırma kestikten sonra belirli bir süre sona erdiğinde kadar'ın kaynak güncellenmemelidir belirtmek için.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Bu uygulama ICustomTypeProvider türlerine bağlama  
 WPF veri bağlama uygulayan nesneler için destekleyen <xref:System.Reflection.ICustomTypeProvider>, özel türleri olarak da bilinir.  Aşağıdaki durumlarda özel türler kullanabilirsiniz.  
  
1.  Farklı bir <xref:System.Windows.PropertyPath> Veri bağlamada. Örneğin, <xref:System.Windows.Data.Binding.Path%2A> özelliği bir <xref:System.Windows.Data.Binding> özel türünde bir özellik başvuruda bulunabilir.  
  
2.  Değeri olarak <xref:System.Windows.DataTemplate.DataType%2A> özelliği.  
  
3.  Otomatik oluşturulan sütunları belirleyen bir tür olarak bir <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Bir bağlama ifadesinden veri bağlama bilgileri alınıyor  
 Bazı durumlarda, alabilirsiniz <xref:System.Windows.Data.BindingExpression> , bir <xref:System.Windows.Data.Binding> ve bağlama kaynak ve hedef nesneler hakkında bilgi gerekiyor.  Kaynak veya hedef nesne veya ilişkili özelliği etkinleştirmek için yeni API'ler eklenmiştir.  Olduğunda, bir <xref:System.Windows.Data.BindingExpression>, hedef ve kaynak hakkında bilgi almak için aşağıdaki API'leri kullanın.  
  
|Bağlamanın bu değeri bulmak için|Bu API kullanın|  
|---------------------------------------|------------------|  
|Hedef nesne|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Target özelliği|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Kaynak nesnesi|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Source özelliği|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Olup olmadığını <xref:System.Windows.Data.BindingExpression> ait bir<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Sahibi bir<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>İçin geçerli bir DataContext nesne denetleniyor  
 Durumlar vardır nerede <xref:System.Windows.FrameworkElement.DataContext%2A> bir öğe kapsayıcı bir <xref:System.Windows.Controls.ItemsControl> bağlantısı kesiliyor.  Bir öğe kapsayıcı bir öğeyi görüntüleyen UI öğedir bir <xref:System.Windows.Controls.ItemsControl>.  Zaman bir <xref:System.Windows.Controls.ItemsControl> veriler bir koleksiyona bağlı, bir öğe kapsayıcısı her öğe için oluşturulur. Bazı durumlarda, öğe kapsayıcılarını görsel ağaç kaldırılır. Burada bir öğe kapsayıcısı kaldırılır iki tipik örnekleridir olan bir öğe temel alınan koleksiyonundan zaman kaldırılır ve sanallaştırma üzerinde etkin olduğunda <xref:System.Windows.Controls.ItemsControl>. Bu durumda, <xref:System.Windows.FrameworkElement.DataContext%2A> öğe kapsayıcısı özelliği tarafından döndürülen sentinel nesnesine ayarlanacak <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> statik özelliği.  Denetlemelisiniz olup olmadığını <xref:System.Windows.FrameworkElement.DataContext%2A> eşittir <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> erişmeden önce nesne <xref:System.Windows.FrameworkElement.DataContext%2A> bir öğe kapsayıcısı.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>(Dinamik şekillendirme) verinin değerleri değiştirmek gibi veri yeniden konumlandırma  
 Veri koleksiyonunu gruplandırılmış, sıralanmış, filtre veya kaldırılabilir. WPF 4.5 veri değiştirildiğinde düzenlenmeyecek veri sağlar. Örneğin, bir uygulama kullandığını varsayın bir <xref:System.Windows.Controls.DataGrid> listelemek için hisse senedi stoklar ve hisse stok değerine göre sıralanır. Canlı sıralama hisse üzerinde etkinse, <xref:System.Windows.Data.CollectionView>, stok 's konumda <xref:System.Windows.Controls.DataGrid> hisse senedi değeri büyük hale geldiğinde taşır veya değerinden başka bir stok 's değeri.   Daha fazla bilgi için bkz: <xref:System.ComponentModel.ICollectionViewLiveShaping> arabirimi.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Bir olay zayıf başvuru oluşturma için geliştirilmiş destek  
 Olayları abonelere içinde ek arabirimi uygulama olmadan katılabilmesi için zayıf olay düzeni uygulama artık daha kolay olur.  Genel <xref:System.Windows.WeakEventManager> sınıfı ayrıca ayrılmış bir varsa zayıf olay desende katılmayı aboneleri sağlar <xref:System.Windows.WeakEventManager> için belirli bir olay yok.  Daha fazla bilgi için bkz: [zayıf olay desenleri](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Dağıtıcı sınıfı için yeni yöntemler  
 Dispatcher sınıfı zaman uyumlu ve zaman uyumsuz işlemleri için yeni yöntemleri tanımlar.  Zaman uyumlu <xref:System.Windows.Threading.Dispatcher.Invoke%2A> yöntemi tanımlar Al aşırı bir <xref:System.Action> veya <xref:System.Func%601> parametresi. Yeni zaman uyumsuz yöntem <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, ayrıca alır bir <xref:System.Action> veya <xref:System.Func%601> döndürür ve geri çağırma parametresi olarak bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>.   <xref:System.Windows.Threading.DispatcherOperation> Ve <xref:System.Windows.Threading.DispatcherOperation%601> sınıflarını tanımla bir <xref:System.Threading.Tasks.Task> özelliği.  Çağırdığınızda <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, kullanabileceğiniz `await` ya da anahtar sözcük <xref:System.Windows.Threading.DispatcherOperation> veya ilişkili <xref:System.Threading.Tasks.Task>. Zaman uyumlu olarak bekleyin gerekiyorsa <xref:System.Threading.Tasks.Task> tarafından döndürülen bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>, çağrı <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> genişletme yöntemi. Çağırma <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> işlemi çağıran iş parçacığı üzerinde sıraya alınmış bir kilitlenmeyle neden olur. Kullanma hakkında daha fazla bilgi için bir <xref:System.Threading.Tasks.Task> zaman uyumsuz işlemleri gerçekleştirmek için bkz: [görev Paralelliği (görev paralel kitaplığı)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Olaylar için işaretleme uzantıları  
 WPF 4.5 Biçimlendirme uzantıları olaylarını destekler.  WPF olayları için kullanılacak bir işaretleme uzantısı tanımlamaz, ancak üçüncü tarafların olaylarla kullanılabilecek biçimlendirme uzantısı oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework’teki Yenilikler](../../../../docs/framework/whats-new/index.md)
