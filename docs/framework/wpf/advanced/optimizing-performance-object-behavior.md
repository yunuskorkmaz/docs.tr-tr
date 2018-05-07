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
ms.openlocfilehash: 2e1f56dec87de7a22aa8a0bfefe84222d74ba085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-object-behavior"></a>Performansı İyileştirme: Nesne Davranışı
İç davranışını anlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri işlevselliği ve performans arasındaki doğru avantajları yapmanıza yardımcı olur.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Olay işleyicileri nesneler üzerinde nesneleri canlı olabilir  
 Bir nesne, olay geçirdiği temsilci etkili bir şekilde söz konusu nesne başvurusudur. Bu nedenle, olay işleyicileri nesneleri beklenenden daha uzun canlı tutar. Bir nesnenin olayını dinlemek için kayıtlı olan bir nesnenin temizlenmesini gerçekleştirirken nesneyi serbest bırakmadan önce o temsilciyi kaldırmak için gereklidir. Gereksiz nesneleri canlı tutma uygulamanın bellek kullanımını artırır. Bu, özellikle nesne bir mantıksal ağaç veya görsel ağaç kökü olduğunda geçerlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kaynak ve dinleyici arasındaki nesne ömür ilişkilerini izlemenin zor olduğu durumlarda yararlı olabilir olaylar için zayıf olay dinleyici düzenini tanıtır. Var olan bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları bu deseni kullanır. Özel olaylarla nesneleri uyguluyorsanız, bu deseni size kullanımı olabilir. Ayrıntılar için bkz [zayıf olay desenleri](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 CLR Profil Oluşturucu ve çalışma kümesi belirtilen işlemin bellek kullanımı hakkında bilgi sağlayan Görüntüleyicisi, gibi çeşitli araçlar vardır. CLR Profil oluşturucu ayrılmış türleri, ayırma ve çağrı grafikleri, çöp koleksiyonları çeşitli nesli ve sonra yönetilen yığın sonuç durumunu gösteren bir zaman çizgisi histogram dahil olmak üzere ayırma profil çok kullanışlı görünümlerini içerir Bu koleksiyon ve yöntem başına yüklemeleri ve derleme yüklerini gösteren bir çağrı ağacı. Daha fazla bilgi için bkz: [.NET Framework Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Bağımlılık özellikleri ve nesneleri  
 Genel olarak, bir bağımlılık özelliği erişen bir <xref:System.Windows.DependencyObject> erişme daha yavaş değil bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Bir özellik değeri ayarlamak için ek yükü küçük bir performans olsa da, bir değer alma değerinden alma olarak hızlı bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Küçük performansa kaydırma işlemi bağımlılık özellikleri sağlam özellikleri, veri bağlama, animasyon, devralma ve stil gibi destek gerçeğidir. Daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty iyileştirmeleri  
 Uygulamanızda, bağımlılık özellikleri'ni dikkatle tanımlamanız gerekir. Varsa, <xref:System.Windows.DependencyProperty> etkiler, yalnızca işleme diğer meta veri seçenekleri yerine türü meta veri seçeneklerini gibi <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, bu nedenle, meta verileri geçersiz kılarak işaretlemeniz gerekir. Geçersiz kılma veya özellik meta verileri alma hakkında daha fazla bilgi için bkz: [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Ölçüyü geçersiz kılması, düzenlemek ve geçişleri el ile işleme bir özellik değişikliği işleyiciye sahip daha etkili olabilir değilse tüm özellik değişikliklerini gerçekte ölçü etkiler, düzenlemek ve işlenemiyor. Örneğin, yalnızca bir değer kümesi sınırdan daha büyük olduğunda bir arka plan yeniden işlemek karar verebilirsiniz. Bu durumda, değeri kümesi sınırını aşarsa, özellik değiştirme işleyicisi yalnızca işlemeyi geçersiz kılar.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty'yi Devralınabilir yapmak uygun değildir  
 Varsayılan olarak, kayıtlı bağımlılık devralınabilir olmayan özelliklerdir. Ancak, siz açıkça herhangi bir özelliği devralınabilir yapabilirsiniz. Bu yararlı bir özellik olsa da, bir özellik devralınabilir dönüştürme özelliği geçersiz kılma süreyi artırarak performansını etkiler.  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler'ı dikkatli kullanın  
 Arama sırasında <xref:System.Windows.EventManager.RegisterClassHandler%2A> , örnek durumu kaydetmenize olanak tanır işleyicisi performans sorunlarına neden olabilir her örneğinde çağrılır bilmeniz önemlidir. Yalnızca <xref:System.Windows.EventManager.RegisterClassHandler%2A> zaman uygulamanızın gerektirdiği, örnek durumu kaydedin.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Kayıt sırasında DependencyProperty'yi Varsayılan değeri ayarlanamıyor  
 Oluştururken bir <xref:System.Windows.DependencyProperty> varsayılan bir değer gerektiren, bir parametre olarak geçirilen varsayılan meta verileri kullanarak değerini ayarlama <xref:System.Windows.DependencyProperty.Register%2A> yöntemi <xref:System.Windows.DependencyProperty>. Özellik değeri bir oluşturucuda veya bir öğenin her bir örneğinde ayarlamak yerine bu yöntemi kullanın.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Yazmaç Kullanarak PropertyMetadata değerini ayarla  
 Oluştururken bir <xref:System.Windows.DependencyProperty>, ayarı seçeneğiniz <xref:System.Windows.PropertyMetadata> kullanarak <xref:System.Windows.DependencyProperty.Register%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemleri. Nesnenizin çağırmak için statik bir oluşturucuya sahip olabilir ancak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, bu en iyi çözüm değildir ve performansını etkiler. En iyi performans için ayarlanmış <xref:System.Windows.PropertyMetadata> çağrı sırasında <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable nesneleri  
 A <xref:System.Windows.Freezable> , iki durumlu sahip bir nesne özel bir tür: çözülmüş ve dondurulmuş. Nesneleri olabildiğince dondurmak, uygulamanızın performansını artırır ve kendi çalışma kümesinin azaltır. Daha fazla bilgi için bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Her <xref:System.Windows.Freezable> sahip bir <xref:System.Windows.Freezable.Changed> değiştiğinde olayı. Ancak, değişiklik bildirimleri uygulama performans açısından maliyetlidir.  
  
 Aşağıdaki örnek her göz önünde bulundurun <xref:System.Windows.Shapes.Rectangle> aynı kullanan <xref:System.Windows.Media.Brush> nesnesi:  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir olay işleyicisi sağlar <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> geçersiz kılmak için olay <xref:System.Windows.Shapes.Rectangle> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği. Bu durumda, her zaman <xref:System.Windows.Media.SolidColorBrush> tetiklenecek olan kendi <xref:System.Windows.Freezable.Changed> gerekli her biri için geri çağırma işlevi çağırmak için olay <xref:System.Windows.Shapes.Rectangle>— bu geri çağırma işlevi etkinleştirmeleri toplamı zorunlu tuttukları önemli bir performans sorunu. Ayrıca, çok performans eklemek ve uygulamanın bunu yapmak için listenin tamamını gezinmesine olacağından işleyicileri bu noktada kaldırmak için yoğun olur. Uygulama senaryonuz hiçbir zaman değişirse <xref:System.Windows.Media.SolidColorBrush>, bakım maliyetini ödeme <xref:System.Windows.Freezable.Changed> olay işleyicileri gereksiz yere.  
  
 Dondurma bir <xref:System.Windows.Freezable> , artık bildirimleri değiştirmeyi korumada kaynakları harcaması gerektiğinden kendi performansını iyileştirebilir. Aşağıdaki tabloda, basit bir boyutunu gösterilmektedir <xref:System.Windows.Media.SolidColorBrush> zaman kendi <xref:System.Windows.Freezable.IsFrozen%2A> özelliği ayarlanmış `true`, olmadığı karşılaştırıldığında. Bu uygulama için bir fırça varsayar <xref:System.Windows.Shapes.Shape.Fill%2A> on özelliğinin <xref:System.Windows.Shapes.Rectangle> nesneleri.  
  
|**Durum**|**Boyutu**|  
|---------------|--------------|  
|Dondurulmuş <xref:System.Windows.Media.SolidColorBrush>|212 bayt|  
|Olmayan dondurulmuş <xref:System.Windows.Media.SolidColorBrush>|972 bayt|  
  
 Aşağıdaki kod örneği, bu kavramı gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Çözülmüş Freezables üzerinde değiştirilen işleyiciler nesneleri canlı olabilir  
 Bir nesne geçirir temsilci bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olaydır etkili bir şekilde bu nesneye bir başvurusu. Bu nedenle, <xref:System.Windows.Freezable.Changed> olay işleyicileri etkin tutma nesneleri beklenenden daha uzun. Temizleme dinlemek için kayıtlı olan bir nesnenin gerçekleştirirken bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olay, bu nesne serbest bırakmadan önce bu temsilciyi kaldırmak için gerekli.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca <xref:System.Windows.Freezable.Changed> olayları dahili olarak. Örneğin, ele tüm bağımlılık özellikleri <xref:System.Windows.Freezable> için bir değer dinleyecek şekilde <xref:System.Windows.Freezable.Changed> olayları otomatik olarak. <xref:System.Windows.Shapes.Shape.Fill%2A> Geçen özelliği bir <xref:System.Windows.Media.Brush>, bu kavramı gösterir.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 ' In `myBrush` için `myRectangle.Fill`, geri işaret eden bir temsilci <xref:System.Windows.Shapes.Rectangle> nesne eklenir <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> olay. Aşağıdaki kod gerçekte yapmaz yani `myRect` çöp toplama için uygun:  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Bu durumda `myBrush` devam etmenize `myRectangle` canlı ve onu başlatıldığında geri kendisine çağırır kendi <xref:System.Windows.Freezable.Changed> olay. Bu atama Not `myBrush` için <xref:System.Windows.Shapes.Shape.Fill%2A> yeni bir özellik <xref:System.Windows.Shapes.Rectangle> yalnızca başka bir olay işleyicisine ekleyecek `myBrush`.  
  
 Bu tür nesneleri temizlemek için önerilen yol kaldırmaktır <xref:System.Windows.Media.Brush> gelen <xref:System.Windows.Shapes.Shape.Fill%2A> sırayla kaldıracak özelliği <xref:System.Windows.Freezable.Changed> olay işleyicisi.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Kullanıcı arabirimi sanallaştırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca bir çeşitlemesi sağlar <xref:System.Windows.Controls.StackPanel> otomatik olarak "veri bağlama alt içeriğini sanallaştıran" öğesi. Bu bağlamda word sanallaştırmak olarak bir alt nesnelerinin oluşturulduğu çok sayıda veri öğeleri hangi öğelerin ekranda görülebilir olduğuna dayalı bir tekniği anlamına gelir. Hem bellek ve sadece birkaç ekranda belirli bir zamanda olabilir, çok sayıda kullanıcı Arabirimi öğeleri oluşturmak için işlemci bakımından yoğun. <xref:System.Windows.Controls.VirtualizingStackPanel> (tarafından sağlanan işlevsellik aracılığıyla <xref:System.Windows.Controls.VirtualizingPanel>) görünen öğeleri hesaplar ve birlikte çalıştığı <xref:System.Windows.Controls.ItemContainerGenerator> gelen bir <xref:System.Windows.Controls.ItemsControl> (gibi <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>) yalnızca görünür öğeler için oluşturmak için.  
  
 Performansı iyileştirme bu öğeler için görsel nesneler yalnızca oluşturulan veya ekranda görünür durumdaysa Canlı tutulur. Artık denetimin görüntülenebilir alanında olduklarında, görsel nesneler kaldırılabilir. Burada veri nesneleri yerel koleksiyon yerine gerektiği gibi akışla-tüm mevcut olmayan veri sanallaştırma ile karıştırılmamalıdır budur.  
  
 Aşağıdaki tabloda, ekleme ve 5000 işleme süre gösterilmektedir <xref:System.Windows.Controls.TextBlock> öğelerine bir <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.VirtualizingStackPanel>. Bu senaryoda, bir metin dizesi ekleme arasında geçen zamanı ölçümleri temsil <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği bir <xref:System.Windows.Controls.ItemsControl> panel öğelerinin metin dizesini görüntülediğinizde zamana nesnesi.  
  
|**Konak paneli**|**İşleme süresi (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
