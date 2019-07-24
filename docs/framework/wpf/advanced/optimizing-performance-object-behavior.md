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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400472"
---
# <a name="optimizing-performance-object-behavior"></a>Performansı İyileştirme: Nesne Davranışı
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nesnelerin iç davranışını anlamak, işlevsellik ve performans arasındaki doğru avantajları yapmanıza yardımcı olur.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nesneler üzerinde olay Işleyicilerini kaldırma, nesneleri canlı tutmaya devam edebilir  
 Bir nesnenin olayına geçirdiği temsilci, bu nesneye etkin bir şekilde başvurur. Bu nedenle, olay işleyicileri nesneleri beklenenden uzun süre canlı tutabilirler. Bir nesnenin olayını dinlemek için kayıtlı olan bir nesnenin temizlenmesini gerçekleştirirken, nesneyi serbest bırakmadan önce o temsilciyi kaldırmak önemlidir. Gereksiz nesnelerin canlı tutulması, uygulamanın bellek kullanımını artırır. Nesne bir mantıksal ağacın veya görsel ağacın kökü olduğunda bu özellikle doğrudur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Kaynak ve dinleyici arasındaki nesne yaşam süresi ilişkilerinin izlemek zor olduğu durumlarda yararlı olabilecek olaylar için zayıf bir olay dinleyicisi deseninin kullanımını sağlar. Bazı mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaylar bu kalıbı kullanır. Özel olaylar içeren nesneler uyguladığınızda, bu model sizin için kullanılabilir. Ayrıntılar için bkz. [zayıf olay desenleri](weak-event-patterns.md).  
  
 CLR Profiler ve çalışma kümesi Görüntüleyicisi gibi çeşitli araçlar vardır. Bu, belirtilen bir işlemin bellek kullanımı hakkında bilgi sağlar. CLR Profiler, ayrılmış türlerin bir histogramı, ayırma ve çağrı grafikleri dahil olmak üzere ayırma profilinin çok sayıda kullanışlı görünümünü içerir. Bu, çeşitli nesiller atık koleksiyonlarını ve sonrasında yönetilen yığının sonuç durumunu gösteren bir zaman çizgisi içerir Bu koleksiyonlar ve yöntem başına ayırmaları ve derleme yüklerini gösteren bir çağrı ağacı. Daha fazla bilgi için bkz. [.NET Framework Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Bağımlılık özellikleri ve nesneler  
 Genel olarak, bir <xref:System.Windows.DependencyObject> bağımlılık özelliğine erişim bir CLR özelliğine erişmekten daha yavaş değildir. Bir özellik değerini ayarlamaya yönelik küçük bir performans yükü olsa da, bir değeri almak bir CLR özelliğinden değer elde etmek kadar hızlıdır. Küçük performans yükünün mahsuplanması, bağımlılık özelliklerinin veri bağlama, animasyon, devralma ve stil oluşturma gibi güçlü özellikleri desteklemesidir. Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty Iyileştirmeleri  
 Uygulamanızda bağımlılık özelliklerini dikkatle tanımlamanız gerekir. Gibi diğer meta veri seçenekleri <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>yerine yalnızca işleme türü meta veri seçeneklerini etkiliyorsa,metaverilerinigeçersizkılarakbuşekildeişaretlemenizgerekir.<xref:System.Windows.DependencyProperty> Özellik meta verilerini geçersiz kılma veya alma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).  
  
 Tüm özellik değişiklikleri ölçü, düzenleme ve işlemeyi etkilemediği takdirde, bir özellik değişikliği işleyicisinin ölçüyü, düzenlemeyi ve işlemeyi el ile geçersiz kılması daha verimli olabilir. Örneğin, bir arka planı yalnızca bir değer ayarlanan sınırdan daha büyük olduğunda yeniden işlemeye karar verebilirsiniz. Bu durumda, özellik değişikliği işleyiciniz yalnızca değer ayarlanan sınırı aştığında işlemeyi geçersiz kılar.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty devralınabilir hale getirme işlemi ücretsizdir  
 Varsayılan olarak, kayıtlı bağımlılık özellikleri devralınamaz. Ancak, herhangi bir özelliği açıkça devralınabilir yapabilirsiniz. Bu kullanışlı bir özellik olsa da, bir özelliğin devralınabilir olarak dönüştürülmesi, özellik geçersiz kılma süresini artırarak performansı etkiler.  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler 'i dikkatle kullanın  
 Çağırma <xref:System.Windows.EventManager.RegisterClassHandler%2A> işlemi, örnek durumlarınızı kaydetmenize izin verdiğinden, işleyicinin her örnekte çağrıldığından, performans sorunlarına neden olabilecek şekilde farkında olmak önemlidir. Yalnızca uygulamanızın <xref:System.Windows.EventManager.RegisterClassHandler%2A> örnek durumunu kaydetmenizi gerektirdiğinde kullanın.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Kayıt sırasında DependencyProperty için varsayılan değeri ayarlama  
 Varsayılan değer gerektiren <xref:System.Windows.DependencyProperty> bir oluştururken, bir parametresi <xref:System.Windows.DependencyProperty.Register%2A> <xref:System.Windows.DependencyProperty>olarak geçirilen varsayılan meta verileri kullanarak değerini ayarlayın. Bir oluşturucuda veya bir öğenin her örneğindeki özellik değerini ayarlamak yerine bu tekniği kullanın.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register kullanarak PropertyMetadata değerini ayarlama  
 Bir <xref:System.Windows.DependencyProperty>oluştururken, <xref:System.Windows.DependencyProperty.Register%2A> ya <xref:System.Windows.PropertyMetadata> da<xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemlerini kullanarak ayarlama seçeneğiniz vardır. Nesneniz çağırmak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>için bir statik oluşturucuya sahip olsa da, bu en iyi çözüm değildir ve performansı etkiler. En iyi performans için, <xref:System.Windows.PropertyMetadata> <xref:System.Windows.DependencyProperty.Register%2A>çağrısı sırasında öğesini ayarlayın.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable nesneleri  
 <xref:System.Windows.Freezable> , İki durumu olan özel bir nesne türüdür: dondurulmamış ve dondurulmuş. Mümkün olduğunda nesneleri dondurmak, uygulamanızın performansını geliştirir ve çalışma kümesini azaltır. Daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
 Her <xref:System.Windows.Freezable> birinin her <xref:System.Windows.Freezable.Changed> değişiklik yapıldığında oluşan bir olayı vardır. Ancak, değişiklik bildirimleri uygulama performansı açısından maliyetlidir.  
  
 Her birinin <xref:System.Windows.Shapes.Rectangle> aynı <xref:System.Windows.Media.Brush> nesneyi kullandığı aşağıdaki örneği göz önünde bulundurun:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini geçersiz kılmak <xref:System.Windows.Shapes.Rectangle> için <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> olayı için bir olay işleyicisi sağlar. Bu durumda, her seferinde <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.Changed> olayını her tetiklemesi gerektiğinde <xref:System.Windows.Shapes.Rectangle>, bu geri çağırma işlevinin birikmesi, önemli bir performans cezası uygular. Buna ek olarak, bu noktada işleyicileri eklemek ve kaldırmak çok performansa sahiptir çünkü uygulamanın tüm listeyi gezmeleri gerekir. Uygulama senaryonuz hiçbir şekilde hiçbir şekilde değişiklik <xref:System.Windows.Media.SolidColorBrush>görmüyorsa, etkinlik işleyicilerinin gereksiz bir şekilde sürdürülmesi <xref:System.Windows.Freezable.Changed> için ücret ödeirsiniz.  
  
 Değişiklik bildirimlerinin <xref:System.Windows.Freezable> korunmasıyla ilgili kaynakları daha iyi bir şekilde almak zorunda olmadığından, bir değişikliği sürdürmek, performansını iyileştirebilir. Aşağıdaki tabloda, <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.IsFrozen%2A> özelliği özelliği olarak `true`ayarlandığında, ne zaman olduğu ile karşılaştırıldığında bir basit öğesinin boyutu gösterilmektedir. Bu, <xref:System.Windows.Shapes.Shape.Fill%2A> on <xref:System.Windows.Shapes.Rectangle> nesnenin özelliğine bir fırça uygulayan olduğunu varsayar.  
  
|**State**|**Boyutla**|  
|---------------|--------------|  
|Lamadığı<xref:System.Windows.Media.SolidColorBrush>|212 bayt|  
|Dondurulmuş olmayan<xref:System.Windows.Media.SolidColorBrush>|972 bayt|  
  
 Aşağıdaki kod örneği bu kavramı göstermektedir:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Dondurulmamış Freezable nesneleri üzerinde değiştirilen Işleyiciler nesneleri canlı tutamayabilir  
 Bir nesnenin bir <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> nesnenin olayına geçirdiği temsilci, bu nesneye etkin bir şekilde başvurur. Bu nedenle <xref:System.Windows.Freezable.Changed> , olay işleyicileri nesneleri beklenenden uzun süre canlı tutabilirler. <xref:System.Windows.Freezable> Bir<xref:System.Windows.Freezable.Changed> nesnenin olayını dinlemek için kayıtlı olan bir nesnenin temizlenmesini gerçekleştirirken, nesneyi serbest bırakmadan önce o temsilciyi kaldırmak önemlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca <xref:System.Windows.Freezable.Changed> olayları dahili olarak takar. Örneğin, bir değer <xref:System.Windows.Freezable> olarak kullanan tüm bağımlılık özellikleri, <xref:System.Windows.Freezable.Changed> olayları otomatik olarak dinler. ' I<xref:System.Windows.Media.Brush>alan özelliğibukavramıgösterir.<xref:System.Windows.Shapes.Shape.Fill%2A>  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myRectangle.Fill`' A atama `myBrush` üzerinde, nesnesine geri <xref:System.Windows.Shapes.Rectangle> işaret eden bir temsilci <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> olayına eklenecektir. Bu, aşağıdaki kodun gerçekte çöp toplama için uygun `myRect` hale getirmediği anlamına gelir:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Bu durumda `myBrush` , `myRectangle` hala etkin olmaya devam eder ve <xref:System.Windows.Freezable.Changed> olayını harekete çağırdığınızda geri çağırır. Yeni `myBrush` <xref:System.Windows.Shapes.Shape.Fill%2A> bir özelliğine atama, ' ye `myBrush`yalnızca başka bir olay işleyicisi ekleneceğini unutmayın. <xref:System.Windows.Shapes.Rectangle>  
  
 Bu nesne türlerini temizlemek için önerilen yol, <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği içinden <xref:System.Windows.Freezable.Changed> kaldırılacağından olay işleyicisini de kaldırır.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Kullanıcı arabirimi sanallaştırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca, <xref:System.Windows.Controls.StackPanel> veri bağlantılı alt içeriği otomatik olarak "sanallaştırın" bir öğe çeşitlemesi sağlar. Bu bağlamda, sanalbir sözcük, nesnelerin bir alt kümesinin ekranda görünür olduğu çok sayıda veri öğesinden oluşturulduğu bir tekniğe başvurur. Belirli bir zamanda ekranda yalnızca birkaç tane olabilir, çok sayıda UI öğesi oluşturmak için hem bellek hem de işlemci bakımından yoğun bir şekilde yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel>( <xref:System.Windows.Controls.VirtualizingPanel>tarafından sunulan işlevsellik aracılığıyla) görünür öğeleri hesaplar ve ' <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemContainerGenerator> den <xref:System.Windows.Controls.ItemsControl> (veya <xref:System.Windows.Controls.ListView>gibi) ile birlikte çalışarak yalnızca görünür öğeler için öğeleri oluşturur.  
  
 Performans iyileştirmesi olarak, bu öğelerin görsel nesneleri yalnızca ekranda görünür durumdaysa oluşturulur veya etkin tutulur. Artık denetimin görüntülenebilir alanında olmadığında görsel nesneler kaldırılabilir. Bu, veri nesnelerinin, gerekli olduğu gibi akan şekilde yerel koleksiyonda bulunmadığı veri sanallaştırmayla karıştırılmamalıdır.  
  
 Aşağıdaki tabloda, bir <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> ve ' <xref:System.Windows.Controls.VirtualizingStackPanel>a 5000 öğeleri ekleme ve işleme geçen süre gösterilmektedir. Bu senaryoda ölçümler, bir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl> nesnenin özelliğine metin dizesi ekleme arasındaki süreyi, panel öğelerinin metin dizesini görüntülemesi için zaman gösterir.  
  
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
