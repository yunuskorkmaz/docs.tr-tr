---
title: 'Performansı İyileştirme: Nesne Davranışı'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094494"
---
# <a name="optimizing-performance-object-behavior"></a>Performansı İyileştirme: Nesne Davranışı
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerinin iç davranışını anlamak, işlevsellik ve performans arasındaki doğru avantajları yapmanıza yardımcı olur.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nesneler üzerinde olay Işleyicilerini kaldırma, nesneleri canlı tutmaya devam edebilir  
 Bir nesnenin olayına geçirdiği temsilci, bu nesneye etkin bir şekilde başvurur. Bu nedenle, olay işleyicileri nesneleri beklenenden uzun süre canlı tutabilirler. Bir nesnenin olayını dinlemek için kayıtlı olan bir nesnenin temizlenmesini gerçekleştirirken, nesneyi serbest bırakmadan önce o temsilciyi kaldırmak önemlidir. Gereksiz nesnelerin canlı tutulması, uygulamanın bellek kullanımını artırır. Nesne bir mantıksal ağacın veya görsel ağacın kökü olduğunda bu özellikle doğrudur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kaynak ve dinleyici arasındaki nesne yaşam süresi ilişkilerinin izlemek zor olduğu durumlarda faydalı olabilecek olaylar için zayıf bir olay dinleyicisi deseninin kullanımını sağlar. Bazı mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları bu kalıbı kullanır. Özel olaylar içeren nesneler uyguladığınızda, bu model sizin için kullanılabilir. Ayrıntılar için bkz. [zayıf olay desenleri](weak-event-patterns.md).  
  
 CLR Profiler ve çalışma kümesi Görüntüleyicisi gibi çeşitli araçlar vardır. Bu, belirtilen bir işlemin bellek kullanımı hakkında bilgi sağlar. CLR Profiler, ayrılmış türlerin bir histogramı, ayırma ve çağrı grafikleri dahil olmak üzere ayırma profilinin çok sayıda kullanışlı görünümünü içerir. Bu, çeşitli nesiller atık koleksiyonlarını ve sonrasında yönetilen yığının sonuç durumunu gösteren bir zaman çizgisi içerir Bu koleksiyonlar ve yöntem başına ayırmaları ve derleme yüklerini gösteren bir çağrı ağacı. Daha fazla bilgi için bkz. [performans](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Bağımlılık özellikleri ve nesneler  
 Genel olarak, bir <xref:System.Windows.DependencyObject> bağımlılık özelliğine erişilmesi bir CLR özelliğine erişmekten daha yavaş değildir. Bir özellik değerini ayarlamaya yönelik küçük bir performans yükü olsa da, bir değeri almak bir CLR özelliğinden değer elde etmek kadar hızlıdır. Küçük performans yükünün mahsuplanması, bağımlılık özelliklerinin veri bağlama, animasyon, devralma ve stil oluşturma gibi güçlü özellikleri desteklemesidir. Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty Iyileştirmeleri  
 Uygulamanızda bağımlılık özelliklerini dikkatle tanımlamanız gerekir. <xref:System.Windows.DependencyProperty>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>gibi diğer meta veri seçenekleri yerine yalnızca işleme türü meta veri seçeneklerini etkiliyorsa, meta verilerini geçersiz kılarak onu bu şekilde işaretlemeniz gerekir. Özellik meta verilerini geçersiz kılma veya alma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).  
  
 Tüm özellik değişiklikleri ölçü, düzenleme ve işlemeyi etkilemediği takdirde, bir özellik değişikliği işleyicisinin ölçüyü, düzenlemeyi ve işlemeyi el ile geçersiz kılması daha verimli olabilir. Örneğin, bir arka planı yalnızca bir değer ayarlanan sınırdan daha büyük olduğunda yeniden işlemeye karar verebilirsiniz. Bu durumda, özellik değişikliği işleyiciniz yalnızca değer ayarlanan sınırı aştığında işlemeyi geçersiz kılar.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty devralınabilir hale getirme işlemi ücretsizdir  
 Varsayılan olarak, kayıtlı bağımlılık özellikleri devralınamaz. Ancak, herhangi bir özelliği açıkça devralınabilir yapabilirsiniz. Bu kullanışlı bir özellik olsa da, bir özelliğin devralınabilir olarak dönüştürülmesi, özellik geçersiz kılma süresini artırarak performansı etkiler.  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler 'i dikkatle kullanın  
 <xref:System.Windows.EventManager.RegisterClassHandler%2A> çağrıldığında, örnek durumlarınızı kaydetmenize izin vermek için, işleyicinin her örnekte çağrıldığından, performans sorunlarına neden olabilecek farkında olmak önemlidir. Yalnızca uygulamanız örneğin durumunu kaydetmenizi gerektirdiğinde <xref:System.Windows.EventManager.RegisterClassHandler%2A> kullanın.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Kayıt sırasında DependencyProperty için varsayılan değeri ayarlama  
 Varsayılan değer gerektiren bir <xref:System.Windows.DependencyProperty> oluştururken, değeri, <xref:System.Windows.DependencyProperty><xref:System.Windows.DependencyProperty.Register%2A> yöntemine parametre olarak geçirilen varsayılan meta verileri kullanarak ayarlayın. Bir oluşturucuda veya bir öğenin her örneğindeki özellik değerini ayarlamak yerine bu tekniği kullanın.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register kullanarak PropertyMetadata değerini ayarlama  
 <xref:System.Windows.DependencyProperty>oluştururken, <xref:System.Windows.DependencyProperty.Register%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemlerinden birini kullanarak <xref:System.Windows.PropertyMetadata> ayarlama seçeneğiniz vardır. Nesneniz <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>çağırmak için bir statik oluşturucuya sahip olsa da, bu en iyi çözüm değildir ve performansı etkiler. En iyi performans için, <xref:System.Windows.DependencyProperty.Register%2A>çağrısı sırasında <xref:System.Windows.PropertyMetadata> ayarlayın.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable nesneleri  
 <xref:System.Windows.Freezable>, iki durumu olan özel bir nesne türüdür: dondurulmamış ve dondurulmuş. Mümkün olduğunda nesneleri dondurmak, uygulamanızın performansını geliştirir ve çalışma kümesini azaltır. Daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
 Her <xref:System.Windows.Freezable> her değiştiğinde oluşan bir <xref:System.Windows.Freezable.Changed> olayı vardır. Ancak, değişiklik bildirimleri uygulama performansı açısından maliyetlidir.  
  
 Her <xref:System.Windows.Shapes.Rectangle> aynı <xref:System.Windows.Media.Brush> nesnesini kullandığı aşağıdaki örneği göz önünde bulundurun:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], varsayılan olarak, <xref:System.Windows.Shapes.Rectangle> nesnesinin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini geçersiz kılmak için <xref:System.Windows.Media.SolidColorBrush> nesnesinin <xref:System.Windows.Freezable.Changed> olayına bir olay işleyicisi sağlar. Bu durumda, <xref:System.Windows.Freezable.Changed> <xref:System.Windows.Media.SolidColorBrush> her bir <xref:System.Windows.Shapes.Rectangle>için geri çağırma işlevini çağırması gerekir, bu geri çağırma işlevinin birikmesi önemli bir performans cezası uygular. Buna ek olarak, bu noktada işleyicileri eklemek ve kaldırmak çok performansa sahiptir çünkü uygulamanın tüm listeyi gezmeleri gerekir. Uygulama senaryonuz <xref:System.Windows.Media.SolidColorBrush>hiçbir şekilde değiştirdiyse, <xref:System.Windows.Freezable.Changed> olay işleyicilerini gereksiz şekilde sürdürme maliyeti ödeirsiniz.  
  
 Bir <xref:System.Windows.Freezable> dondurmak, artık değişiklik bildirimlerinin korunmasıyla ilgili kaynakları daha iyi bir şekilde sağlaması gerekmediği için performansını iyileştirebilir. Aşağıdaki tabloda, <xref:System.Windows.Freezable.IsFrozen%2A> özelliği `true`olarak ayarlandığında, ne zaman olmadığı ile karşılaştırıldığında basit bir <xref:System.Windows.Media.SolidColorBrush> boyutu gösterilmektedir. Bu, on <xref:System.Windows.Shapes.Rectangle> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğine bir fırça uygulamayı varsayar.  
  
|**Durum**|**Boyut**|  
|---------------|--------------|  
|Dondurulmuş <xref:System.Windows.Media.SolidColorBrush>|212 bayt|  
|Dondurulmuş olmayan <xref:System.Windows.Media.SolidColorBrush>|972 bayt|  
  
 Aşağıdaki kod örneği bu kavramı göstermektedir:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Dondurulmamış Freezable nesneleri üzerinde değiştirilen Işleyiciler nesneleri canlı tutamayabilir  
 Bir nesnenin <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olayına geçirdiği temsilci, bu nesneye etkin bir şekilde başvurur. Bu nedenle, <xref:System.Windows.Freezable.Changed> olay işleyicileri nesneleri beklenenden daha uzun süre canlı tutabilirler. <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olayını dinlemek için kayıtlı olan bir nesnenin temizlenmesini gerçekleştirirken, nesneyi serbest bırakmadan önce o temsilciyi kaldırmak önemlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, <xref:System.Windows.Freezable.Changed> olaylarını dahili olarak takar. Örneğin, bir değer olarak <xref:System.Windows.Freezable> kullanan tüm bağımlılık özellikleri, olayları otomatik olarak <xref:System.Windows.Freezable.Changed> dinler. <xref:System.Windows.Media.Brush>alan <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, bu kavramı gösterir.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myBrush` `myRectangle.Fill`atamada <xref:System.Windows.Shapes.Rectangle> nesnesine işaret eden bir temsilci <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> olayına eklenecektir. Bu, aşağıdaki kodun çöp toplama için uygun `myRect` gerçekten yapmayacağı anlamına gelir:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Bu durumda `myBrush` hala `myRectangle` canlı tutmaya devam eder ve <xref:System.Windows.Freezable.Changed> olayını tetiklendiğinde buna geri çağrı yapılır. Yeni bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğine `myBrush` atamanın, `myBrush`'ye başka bir olay işleyicisi ekleneceğini unutmayın.  
  
 Bu nesne türlerini temizlemek için önerilen yol, <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinden kaldırılacağından <xref:System.Windows.Freezable.Changed> olay işleyicisini de kaldıracaktır.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Kullanıcı arabirimi sanallaştırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, veri bağlantılı alt içeriği otomatik olarak "sanallaştırır" <xref:System.Windows.Controls.StackPanel> öğesinin bir varyasyonunu sağlar. Bu bağlamda, sanalbir sözcük, nesnelerin bir alt kümesinin ekranda görünür olduğu çok sayıda veri öğesinden oluşturulduğu bir tekniğe başvurur. Belirli bir zamanda ekranda yalnızca birkaç tane olabilir, çok sayıda UI öğesi oluşturmak için hem bellek hem de işlemci bakımından yoğun bir şekilde yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel> (<xref:System.Windows.Controls.VirtualizingPanel>tarafından sunulan işlevler aracılığıyla) görünür öğeleri hesaplar ve bir <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ItemContainerGenerator> ile (<xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>gibi) çalışarak yalnızca görünür öğeler için öğeleri oluşturur.  
  
 Performans iyileştirmesi olarak, bu öğelerin görsel nesneleri yalnızca ekranda görünür durumdaysa oluşturulur veya etkin tutulur. Artık denetimin görüntülenebilir alanında olmadığında görsel nesneler kaldırılabilir. Bu, veri nesnelerinin, gerekli olduğu gibi akan şekilde yerel koleksiyonda bulunmadığı veri sanallaştırmayla karıştırılmamalıdır.  
  
 Aşağıdaki tabloda, 5000 <xref:System.Windows.Controls.TextBlock> öğeleri <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.VirtualizingStackPanel>ekleme ve işleme geçen süre gösterilmektedir. Bu senaryoda ölçümler, bir metin dizesini bir <xref:System.Windows.Controls.ItemsControl> nesnesinin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğine ekleme arasındaki süreyi, panel öğelerinin metin dizesini görüntülemesi için zaman gösterir.  
  
|**Ana bilgisayar paneli**|**İşleme süresi (MS)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
