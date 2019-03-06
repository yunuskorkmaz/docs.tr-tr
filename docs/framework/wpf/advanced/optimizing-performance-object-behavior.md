---
title: 'Performansı iyileştirme: Nesne Davranışı'
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
ms.openlocfilehash: 5548292480f07fa192985800931f9d0262f2b791
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352691"
---
# <a name="optimizing-performance-object-behavior"></a>Performansı iyileştirme: Nesne Davranışı
İç davranışını anlamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri işlevi ve performans arasında doğru avantajları yapmanıza yardımcı olur.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Olay işleyicileri nesneler üzerinde nesneleri canlı olabilir  
 Bir nesne için kendi olay geçirdiği temsilci etkili bir şekilde bu nesneye bir başvurudur. Bu nedenle, olay işleyicileri nesneleri canlı beklenenden daha uzun tutabilirsiniz. Bir nesnenin olayına dinlemek için kayıtlı olan bir nesne temizleme gerçekleştirirken nesneyi serbest bırakmadan önce bu temsilciyi kaldırmak için gereklidir. Gereksiz nesneleri canlı tutma uygulamanın bellek kullanımı artırır. Bu, özellikle nesne mantıksal ağaç veya görsel ağaç kökünde olduğunda geçerlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kaynak ve dinleyici nesne yaşam süresi ilişkilerini izlemek zor olduğu durumlarda kullanışlı olabilir olaylar için zayıf olay dinleyicisi desen tanıtır. Var olan bazı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları bu deseni kullanır. Özel olaylar nesneleriyle uyguluyorsanız, bu düzen, kullanımı olabilir. Ayrıntılar için bkz [zayıf olay desenleri](weak-event-patterns.md).  
  
 CLR Profiler ve çalışma kümesi belirtilen işlem bellek kullanımı hakkında bilgi sağlayan Görüntüleyicisi, gibi birçok araç vardır. CLR Profiler çok kullanışlı bir histogram ayrılmış türler, ayırma ve çağrı grafikleri, çöp koleksiyonlarının çeşitli nesiller ve sonra yönetilen yığın elde edilen durumunu gösteren bir zaman çizgisi'dahil olmak üzere ayırma profili görünümlerini içerir Bu koleksiyonlar ve yöntem başına yüklemeleri ve derleme yüklerini gösteren bir çağrı ağacı. Daha fazla bilgi için [.NET Framework Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Bağımlılık özellikleri ve nesneler  
 Genel olarak, bir bağımlılık özelliği erişen bir <xref:System.Windows.DependencyObject> erişme daha yavaş değil bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Bir özellik değerini ayarlamak için ek yükü küçük bir performans olsa da, bir değer alma değerini alma olarak hızlı bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özelliği. Küçük bir performans yükü mahsubu bağımlılık özellikleri, veri bağlama, animasyon, devralma ve stil gibi güçlü özellikleri desteklediğini gerçeğidir. Daha fazla bilgi için [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty en iyi duruma getirme  
 Uygulamanızda, bağımlılık özellikleri'ni çok dikkatli bir şekilde tanımlamanız gerekir. Varsa, <xref:System.Windows.DependencyProperty> etkiler, yalnızca işleme diğer meta veri seçenekleri yerine türü meta verileri seçenekleri gibi <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, bu nedenle, meta verileri geçersiz kılarak işaretlemeniz gerekir. Geçersiz kılma veya özellik meta verileri alma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verisi](dependency-property-metadata.md).  
  
 Bir özellik değişiklik işleyici ölçüsü geçersiz, düzenlemek ve geçişleri el ile işlemek için daha verimli olabilir değilse tüm özellik değişiklikleri gerçekten ölçü etkiler, düzenlemek ve işleyin. Örneğin, yalnızca bir değer kümesi sınırdan daha büyük olduğunda yeniden arka plan işlemesi karar verebilirsiniz. Bu durumda, özellik değişiklik işleyicisi yalnızca değer kümesi sınırınızı aştığında işlemeyi geçersiz kılar.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Bir DependencyProperty devralınabilir yapmak uygun değildir  
 Varsayılan olarak, kayıtlı bir bağımlılık özellikleri devralınamaz. Ancak, açıkça herhangi bir özelliği devralınabilir yapabilirsiniz. Bu yararlı bir özellik olsa da, devralınabilir üzere bir özelliğe dönüştürme özelliği geçersiz kılma süreyi artırarak performansını etkiler.  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler'ı dikkatli kullanın  
 Çağrılırken <xref:System.Windows.EventManager.RegisterClassHandler%2A> , örnek durumu kaydetmenize olanak tanır, işleyici performans sorunlarına neden olabilir her örneğinde çağrılır dikkat etmeniz önemlidir. Yalnızca <xref:System.Windows.EventManager.RegisterClassHandler%2A> uygulamanızı gerektirdiğinde, örnek durumu kaydedin.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Kayıt sırasında bir DependencyProperty için varsayılan değer ayarlama  
 Oluştururken bir <xref:System.Windows.DependencyProperty> gerektiren bir varsayılan değer, bir parametre olarak geçirilen varsayılan meta verileri kullanarak ayarlayın <xref:System.Windows.DependencyProperty.Register%2A> yöntemi <xref:System.Windows.DependencyProperty>. Bir oluşturucu ya da her bir öğenin örneğini özellik değerini ayarlamak yerine bu tekniği kullanın.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Yazmaç Kullanarak PropertyMetadata değerini ayarlayın  
 Oluştururken bir <xref:System.Windows.DependencyProperty>, ayarı seçeneğiniz <xref:System.Windows.PropertyMetadata> kullanarak <xref:System.Windows.DependencyProperty.Register%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemleri. Nesnenizin çağırmak için bir statik Oluşturucu sahip, ancak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, bu en iyi çözüm değildir ve performansını etkiler. En iyi performans için ayarlanmış <xref:System.Windows.PropertyMetadata> çağrı sırasında <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable nesneleri  
 A <xref:System.Windows.Freezable> iki durumlu nesnesi özel bir türdür: çözülmüş ve donmuş. Mümkün olduğunda nesneleri dondurma uygulamanızın performansını artırır ve çalışma kümesi azaltır. Daha fazla bilgi için [Freezable nesnelerine genel bakış](freezable-objects-overview.md).  
  
 Her <xref:System.Windows.Freezable> sahip bir <xref:System.Windows.Freezable.Changed> değiştiğinde olayı. Ancak, değişiklik bildirimleri uygulama performans açısından maliyetlidir.  
  
 Aşağıdaki örnek her göz önünde bulundurun <xref:System.Windows.Shapes.Rectangle> ndedir <xref:System.Windows.Media.Brush> nesnesi:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için bir olay işleyicisi sağlar <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> geçersiz kılmak için olay <xref:System.Windows.Shapes.Rectangle> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği. Bu durumda, her zaman <xref:System.Windows.Media.SolidColorBrush> ateşlenmesine sahip kendi <xref:System.Windows.Freezable.Changed> gereken her biri için geri çağırma işlevi çağrılacak olay <xref:System.Windows.Shapes.Rectangle>— bu geri çağırma işlevi etkinleştirmeleri gerekir, önemli bir performans cezası büyük oranda yansıtmaktadır. Ayrıca, çok performans eklemek ve uygulama Bunu yapmak için listenin tamamını geçirmek zorunda olduğundan işleyicileri bu noktada kaldırmak için yoğun olduğundan. Uygulama senaryonuzu hiçbir zaman değişirse <xref:System.Windows.Media.SolidColorBrush>, bakım maliyetini ödeme <xref:System.Windows.Freezable.Changed> olay işleyicileri gereksiz.  
  
 Dondurma bir <xref:System.Windows.Freezable> değişiklik bildirimleri koruma şirket kaynakları harcaması artık gerektiğinden, performansı geliştirebilir. Aşağıdaki tablo basit bir boyutunu gösterir <xref:System.Windows.Media.SolidColorBrush> olduğunda kendi <xref:System.Windows.Freezable.IsFrozen%2A> özelliği `true`, edilmediğinde karşılaştırıldığında. Bu uygulama için bir fırça varsayar <xref:System.Windows.Shapes.Shape.Fill%2A> on özelliği <xref:System.Windows.Shapes.Rectangle> nesneleri.  
  
|**State**|**Boyutu**|  
|---------------|--------------|  
|Dondurulmuş <xref:System.Windows.Media.SolidColorBrush>|212 bayt|  
|Olmayan dondurulmuş <xref:System.Windows.Media.SolidColorBrush>|972 bayt|  
  
 Aşağıdaki kod örneği, bu kavramı gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Çözülmüş Freezable nesneleri değiştirilen işleyicileri nesneleri canlı olabilir  
 Bir nesne geçirir temsilci bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olaydır etkili bir şekilde, bu nesneye bir başvuru. Bu nedenle, <xref:System.Windows.Freezable.Changed> olay işleyicileri etkin tutma nesneleri beklenenden daha uzun. Temizleme dinlemek için kayıtlı olan bir nesnenin gerçekleştirirken bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olayı olduğu nesneyi serbest bırakmadan önce bu temsilciyi kaldırmak için gerekli.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca <xref:System.Windows.Freezable.Changed> olayları dahili olarak. Örneğin, ele tüm bağımlılık özellikleri <xref:System.Windows.Freezable> gibi bir değer dinleyeceği <xref:System.Windows.Freezable.Changed> olayları otomatik olarak. <xref:System.Windows.Shapes.Shape.Fill%2A> Alan, özelliği bir <xref:System.Windows.Media.Brush>, bu kavramı gösterir.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 ' In `myBrush` için `myRectangle.Fill`, geri işaret eden bir temsilci <xref:System.Windows.Shapes.Rectangle> nesne eklenecek <xref:System.Windows.Media.SolidColorBrush> nesnenin <xref:System.Windows.Freezable.Changed> olay. Aşağıdaki kodu gerçekten yapmaz yani `myRect` çöp toplama işlemi için uygun:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Bu durumda `myBrush` hala tutma `myRectangle` etkin tutulan bağlantıyı destekliyorsa ve bunu başlatıldığında geri için çağırır, <xref:System.Windows.Freezable.Changed> olay. İşaretlemediğine dikkat edin `myBrush` için <xref:System.Windows.Shapes.Shape.Fill%2A> yeni bir özellik <xref:System.Windows.Shapes.Rectangle> yalnızca başka bir olay işleyicisine ekler `myBrush`.  
  
 Bu tür nesneler temizlemek için önerilen yöntem kaldırmaktır <xref:System.Windows.Media.Brush> gelen <xref:System.Windows.Shapes.Shape.Fill%2A> sırayla kaldıracak özelliği <xref:System.Windows.Freezable.Changed> olay işleyicisi.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Kullanıcı arabirimi sanallaştırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca bir çeşitlemesi sağlar <xref:System.Windows.Controls.StackPanel> otomatik olarak "sanallaştırır verilere bağlı alt içeriğin" öğesi. Sözcüğü bu bağlamda sanallaştırmak tarafından bir alt nesnelerin oluşturulduğu çok sayıda veri öğelerinin hangi öğelerin ekranda görülebilir olduğuna göre bir teknik ifade eder. Bu, hem bellek ve yalnızca birkaç belirli bir zamanda ekranda olabilir, çok sayıda UI öğesi oluşturmak için işlemci açısından yoğun bir işlemdir. <xref:System.Windows.Controls.VirtualizingStackPanel> (tarafından sağlanan işlevsellik aracılığıyla <xref:System.Windows.Controls.VirtualizingPanel>) görünen öğeler hesaplar ve çalışır <xref:System.Windows.Controls.ItemContainerGenerator> gelen bir <xref:System.Windows.Controls.ItemsControl> (gibi <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>) yalnızca görünür öğeler için oluşturulacak.  
  
 Performans iyileştirme, bu öğeler için görsel nesneler yalnızca oluşturulan veya ekranda görünür durumdaysa Canlı tutulur. Görsel nesneler artık denetim görüntülenebilir alanında olmaları durumunda kaldırılabilir. Nereye veri nesnelerini yerel koleksiyonu yerine gerektiği gibi akışla-tüm mevcut olmayan verileri sanallaştırma ile karıştırılmamalıdır budur.  
  
 Aşağıdaki tablo ekleme ve 5000 işleme geçen süreyi gösterir <xref:System.Windows.Controls.TextBlock> öğelerine bir <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.VirtualizingStackPanel>. Bu senaryoda, ölçümler için bir metin dizesi ekleme arasındaki zamanı temsil eder. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği bir <xref:System.Windows.Controls.ItemsControl> panel öğeleri metin dizesi görüntülediğinizde zamana nesne.  
  
|**Konak paneli**|**İşleme süresi (ms)**|  
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
