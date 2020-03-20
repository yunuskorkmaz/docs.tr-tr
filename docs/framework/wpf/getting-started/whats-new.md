---
title: WPF Sürüm 4.5'te Yenilikler
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174712"
---
# <a name="whats-new-in-wpf-version-45"></a>WPF Sürüm 4.5'te Yenilikler
<a name="introduction"></a>Bu konu, sürüm 4.5'teki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yeni ve geliştirilmiş özellikler hakkında bilgi içerir.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Şerit kontrolü](#ribbon_control)  
  
- [Büyük gruplanmış veri kümeleri görüntülerken geliştirilmiş performans](#grouped_virtualization)  
  
- [VirtualizingPanel için yeni özellikler](#VirtualizingPanel)  
  
- [Statik özelliklere bağlanma](#static_properties)  
  
- [UI olmayan iş parçacıklarındaki koleksiyonlara erişim](#xthread_access)  
  
- [Eşzamanlı ve Eşzamanlı olarak verileri doğrulama](#INotifyDataErrorInfo)  
  
- [Veri bağlama kaynağının otomatik olarak güncelleştirilmesi](#delay)  
  
- [ICustomTypeProvider uygulayan türlere bağlama](#ICustomTypeProvider)  
  
- [Bağlayıcı bir ifadeden veri bağlama bilgileri alma](#binding_state)  
  
- [Geçerli bir DataContext nesnesi için denetleme](#DisconnectedSource)  
  
- [Verilerin değerleri değiştikçe verileri yeniden konumlandırma (Canlı şekillendirme)](#live_shaping)  
  
- [Bir Etkinliğe Zayıf Bir Başvuru Oluşturmak için Geliştirilmiş Destek](#weak_event_pattern)  
  
- [Dispatcher sınıfı için yeni yöntemler](#async)  
  
- [Etkinlikler için Biçimlendirme Uzantıları](#events_markup_extenions)  
  
<a name="ribbon_control"></a>
## <a name="ribbon-control"></a>Şerit kontrolü  
 WPF 4.5, <xref:System.Windows.Controls.Ribbon.Ribbon> Hızlı Erişim Araç Çubuğu, Uygulama Menüsü ve sekmeleri barındıran bir denetime sahip gemiler.  Daha fazla bilgi için [Şerite Genel Bakış'a](/visualstudio/vsto/ribbon-overview)bakın.  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Büyük gruplanmış veri kümeleri görüntülerken geliştirilmiş performans  
 Kullanıcı arabirimi (UI) öğelerinin bir alt kümesi, ekranda görünen öğelere dayalı olarak daha fazla sayıda veri öğesinden oluşturulduğunda Kullanıcı Arabirimi sanallaştırması oluşur. Gruplanmış <xref:System.Windows.Controls.VirtualizingPanel> veriler <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> için UI Sanallaştırmasağlayan ekli özelliği tanımlar.  Verileri gruplandırma hakkında daha fazla bilgi için bkz: XAML'de Görünümü Kullanarak Verileri Sıralama ve Gruplandırma.  Gruplanmış verileri sanallaştırma hakkında daha <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> fazla bilgi için ekteki özelliğe bakın.  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>VirtualizingPanel için yeni özellikler  
  
1. Ekli <xref:System.Windows.Controls.VirtualizingPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>özelliği kullanarak <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> kısmi öğeleri gösterip görüntülemediğini belirtebilirsiniz. <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> Ayarlanmışsa, <xref:System.Windows.Controls.VirtualizingPanel> yalnızca tamamen görünür öğeleri <xref:System.Windows.Controls.ScrollUnit.Item>görüntüler. <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> Ayarlanmışsa, <xref:System.Windows.Controls.VirtualizingPanel> kısmen görünen öğeleri görüntüleyebilirsiniz. <xref:System.Windows.Controls.ScrollUnit.Pixel>  
  
2. Ekteki özelliği kullanarak sanallaştırıldığında <xref:System.Windows.Controls.VirtualizingPanel> görüntü bağlantı noktasından önce ve sonra önbelleğin boyutunu belirtebilirsiniz. <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A>  Önbellek, öğelerin sanallaştırılmayan görünüm portunun üstündeki veya altındaki alan miktarıdır.  Görüntüye kaydırılırken UI öğeleri oluşturmamak için önbellek kullanmak performansı artırabilir. Uygulamanın işlem sırasında yanıt vermemesi için önbellek daha düşük bir öncelikte doldurulur. Özellik, <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> '. tarafından <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>kullanılan ölçü birimini belirler.  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>Statik özelliklere bağlanma  
 Statik özellikleri veri bağlama kaynağı olarak kullanabilirsiniz. Statik bir olay yükseltildiğinde, veri bağlama altyapısı özelliğin değerinin ne zaman değiştiğini tanır.  `SomeClass` Örneğin, sınıf `MyProperty`, adlı statik bir `SomeClass` özellik tanımlarsa, `MyProperty` değişikliklerin değeri yükseltildiğinde yükseltilen statik bir olay tanımlayabilir.  Statik olay aşağıdaki imzalardan birini kullanabilir.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 İlk durumda, sınıfın olay işleyicisine geçen <xref:System.EventArgs> *PropertyName* `Changed` adlı statik bir olayı ortaya çıkardığını unutmayın.  İkinci durumda, sınıf olay işleyicisi `StaticPropertyChanged` geçer <xref:System.ComponentModel.PropertyChangedEventArgs> adlı statik bir olay ortaya çıkarır. Statik özelliği uygulayan bir sınıf, her iki yöntemi kullanarak özellik değiştirme bildirimlerini yükseltmeyi seçebilir.  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>UI olmayan iş parçacıklarındaki koleksiyonlara erişim  
 WPF, koleksiyonu oluşturan iş parçacıkları dışındaki iş parçacıklarındaki veri koleksiyonlarına erişmenizi ve değiştirmenizi sağlar.  Bu, veritabanı gibi harici bir kaynaktan veri almak ve UI iş parçacığındaki verileri görüntülemek için bir arka plan iş parçacığı kullanmanıza olanak tanır.  Koleksiyonu değiştirmek için başka bir iş parçacığı kullanarak, kullanıcı arabiriminiz kullanıcı etkileşimine yanıt vermeye devam eder.  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>Eşzamanlı ve Eşzamanlı olarak verileri doğrulama  
 Arabirim, <xref:System.ComponentModel.INotifyDataErrorInfo> veri varlık sınıflarının özel doğrulama kurallarını uygulamasına ve doğrulama sonuçlarını eşzamanlı olarak ortaya çıkarmasını sağlar. Bu arabirim ayrıca özel hata nesnelerini, özellik başına birden çok hatayı, çapraz özellik hatalarını ve varlık düzeyindeki hataları da destekler.  Daha fazla bilgi için bkz. <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Veri bağlama kaynağının otomatik olarak güncelleştirilmesi  
 Bir veri kaynağını güncelleştirmek için bir veri bağlama <xref:System.Windows.Data.BindingBase.Delay%2A> kullanırsanız, kaynak güncelleştirmeden önce hedefteki özellik değiştikten sonra geçmek için bir süre belirtmek için özelliği kullanabilirsiniz.  Örneğin, bir veri <xref:System.Windows.Controls.Slider> nesnesinin <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliğine iki yönlü bağlı olan bir özellik verisi olduğunu ve özelliğin <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> . <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>  Bu örnekte, kullanıcı <xref:System.Windows.Controls.Slider> <xref:System.Windows.Controls.Slider> hareket ettiği her piksel için kaynak güncelleştirmeleri taşır.  Kaynak nesne genellikle kaydırıcının değerine yalnızca kaydırıcının <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değişmesi durduğunda gerekir.  Kaynağın çok sık güncelleştirilmesini <xref:System.Windows.Data.BindingBase.Delay%2A> önlemek için, başparmağın hareket etmesi durduktan sonra belirli bir süre geçtikçe kaynağın güncelleştirilmemesi gerektiğini belirtmek için kullanın.  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>ICustomTypeProvider uygulayan türlere bağlama  
 WPF, özel türler olarak <xref:System.Reflection.ICustomTypeProvider>da bilinen nesneleri uygulayan verilere bağlamayı destekler.  Aşağıdaki durumlarda özel türleri kullanabilirsiniz.  
  
1. Bir <xref:System.Windows.PropertyPath> veri bağlama olarak. Örneğin, <xref:System.Windows.Data.Binding.Path%2A> bir <xref:System.Windows.Data.Binding> özelliği özel bir tür bir özellik başvuru olabilir.  
  
2. Özelliğin <xref:System.Windows.DataTemplate.DataType%2A> değeri olarak.  
  
3. Otomatik olarak oluşturulan sütunları belirleyen bir <xref:System.Windows.Controls.DataGrid>tür olarak.  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Bağlayıcı bir ifadeden veri bağlama bilgileri alma  
 Bazı durumlarda, a <xref:System.Windows.Data.BindingExpression> <xref:System.Windows.Data.Binding> ve kaynak ve bağlama hedef nesneleri hakkında bilgi gerekir alabilirsiniz.  Kaynak veya hedef nesneyi veya ilişkili özelliği alabilmeniz için yeni API'ler eklendi.  Hedef <xref:System.Windows.Data.BindingExpression>ve kaynak hakkında bilgi almak için aşağıdaki API'leri kullanın.  
  
|Bağlamanın bu değerini bulmak için|Bu API'yi kullanın|  
|---------------------------------------|------------------|  
|Hedef nesne|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Hedef özellik|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Kaynak nesne|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Kaynak özelliği|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Bir <xref:System.Windows.Data.BindingExpression> ait olup olmadığını<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|Bir sahibi<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>Geçerli bir DataContext nesnesi için denetleme  
 Bir öğe <xref:System.Windows.FrameworkElement.DataContext%2A> kapsayıcısının <xref:System.Windows.Controls.ItemsControl> bağlantısının kesildiği durumlar vardır.  Madde kapsayıcısı, bir öğeyi bir <xref:System.Windows.Controls.ItemsControl>.'de görüntüleyen UI öğesidir  Bir <xref:System.Windows.Controls.ItemsControl> koleksiyona bağlı bir veri olduğunda, her öğe için bir madde kapsayıcısı oluşturulur. Bazı durumlarda, öğe kapsayıcıları görsel ağaçtan kaldırılır. Bir öğe kapsayıcıkaldırıldı iki tipik durumlarda bir öğe altta yatan koleksiyondan kaldırılır ve <xref:System.Windows.Controls.ItemsControl>sanallaştırma etkinleştirildiğinde . Bu gibi durumlarda, madde kapsayıcısının <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> statik özellik tarafından döndürülen sentinel nesneye ayarlanır.  Bir öğe kapsayıcısına <xref:System.Windows.FrameworkElement.DataContext%2A> erişmeden <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> <xref:System.Windows.FrameworkElement.DataContext%2A> önce nesnenin nesneye eşit olup olmadığını denetlemeniz gerekir.  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Verilerin değerleri değiştikçe verileri yeniden konumlandırma (Canlı şekillendirme)  
 Veri koleksiyonu gruplandırılabilir, sıralanabilir veya filtrelenebilir. WPF 4.5, veriler değiştirildiğinde verilerin yeniden düzenlenmesini sağlar. Örneğin, bir uygulamanın borsadaki hisse senetlerini listelemek için a <xref:System.Windows.Controls.DataGrid> kullandığını ve hisse senetlerinin hisse senedi değerine göre sıralendiğini varsayalım. Hisse senetlerinde canlı sıralama <xref:System.Windows.Data.CollectionView>etkinse, hisse senedinin <xref:System.Windows.Controls.DataGrid> değeri başka bir hisse senedinin değerinden büyük veya daha az olduğunda hisse senedinin hareketteki konumu.   Daha fazla bilgi <xref:System.ComponentModel.ICollectionViewLiveShaping> için arabirime bakın.  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Bir Etkinliğe Zayıf Bir Başvuru Oluşturmak için Geliştirilmiş Destek  
 Etkinliklere abone ler ek bir arabirim uygulamadan katılabildiklerinden, zayıf olay deseni uygulama artık daha kolay.  Genel <xref:System.Windows.WeakEventManager> sınıf, belirli bir olay için özel <xref:System.Windows.WeakEventManager> bir durum yoksa, abonelerin zayıf olay desenine katılmalarını da sağlar.  Daha fazla bilgi için [Zayıf Olay Desenleri'ne](../advanced/weak-event-patterns.md)bakın.  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Dispatcher sınıfı için yeni yöntemler  
 Dispatcher sınıfı senkron ve eşzamanlı işlemler için yeni yöntemler tanımlar.  Senkron <xref:System.Windows.Threading.Dispatcher.Invoke%2A> yöntem, bir <xref:System.Action> veya <xref:System.Func%601> parametre alan aşırı yüklemeleri tanımlar. Yeni <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>asynchronous yöntemi, ayrıca <xref:System.Action> bir <xref:System.Func%601> veya geri arama parametresi olarak alır ve bir <xref:System.Windows.Threading.DispatcherOperation> veya <xref:System.Windows.Threading.DispatcherOperation%601>döndürür .   Ve <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> sınıflar bir <xref:System.Threading.Tasks.Task> özelliği tanımlar.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>Aradiğinizde, anahtar kelimeyi `await` aşağıdaki lerle <xref:System.Windows.Threading.DispatcherOperation> birlikte <xref:System.Threading.Tasks.Task>kullanabilirsiniz. A <xref:System.Windows.Threading.DispatcherOperation> veya tarafından <xref:System.Windows.Threading.DispatcherOperation%601>döndürülen için <xref:System.Threading.Tasks.Task> eşzamanlı olarak beklemeniz gerekiyorsa, uzantı yöntemini <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> arayın. Arama <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> iş parçacığı üzerinde işlem sıraya dizilirse, arama kilitlenmeyle sonuçlanır. Eşkenar meyniişlemleri gerçekleştirmek için a <xref:System.Threading.Tasks.Task> kullanma hakkında daha fazla bilgi için Görev [Paralelliği (Görev Paralel Kitaplığı)](../../../standard/parallel-programming/task-based-asynchronous-programming.md)bakın.  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>Etkinlikler için Biçimlendirme Uzantıları  
 WPF 4.5 olaylar için biçimlendirme uzantılarını destekler.  WPF olaylar için kullanılacak bir biçimlendirme uzantısı tanımlamasa da, üçüncü taraflar olaylarla birlikte kullanılabilecek bir biçimlendirme uzantısı oluşturabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çerçevesinde Yenilikler](../../whats-new/index.md)
