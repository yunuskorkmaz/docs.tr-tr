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
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187070"
---
# <a name="optimizing-performance-object-behavior"></a>Performansı İyileştirme: Nesne Davranışı
Nesnelerin içsel davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] anlamak, işlevsellik ve performans arasında doğru dengeleri başarasınız yardımcı olur.  

<a name="Not_Removing_Event_Handlers"></a>
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Nesnelerdeki Olay İşleyicilerinin Kaldırılmaması Nesneleri Canlı Tutabilir  
 Bir nesnenin olayına geçtiği temsilci, etkili bir şekilde o nesneye bir başvurudur. Bu nedenle, olay işleyicileri nesneleri beklenenden daha uzun süre canlı tutabilir. Bir nesnenin olayını dinlemek için kaydedilmiş bir nesneyi temizleme yaparken, nesneyi bırakmadan önce bu temsilciyi kaldırmak önemlidir. Gereksiz nesneleri canlı tutmak, uygulamanın bellek kullanımını artırır. Bu, özellikle nesne mantıksal bir ağacın veya görsel bir ağacın kökü olduğunda geçerlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kaynak ve dinleyici arasındaki nesne yaşam boyu ilişkilerinin izlenmesinin zor olduğu durumlarda yararlı olabilecek olaylar için zayıf bir olay dinleyici sseni deseni sunar. Varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bazı olaylar bu deseni kullanır. Özel olayları olan nesneleri uyguluyorsanız, bu desen sizin için kullanılabilir. Ayrıntılar için [Zayıf Olay Desenleri'ne](weak-event-patterns.md)bakın.  
  
 CLR Profiler ve Çalışma Kümesi Görüntüleyici gibi, belirli bir işlemin bellek kullanımı hakkında bilgi sağlayan çeşitli araçlar vardır. CLR Profiler tahsis profili çok yararlı görünümleri bir dizi içerir, ayrılan türleri bir histogram dahil, tahsisat ve çağrı grafikleri, çeşitli nesillerin çöp toplama gösteren bir zaman çizgisi ve sonra yönetilen yığının ortaya çıkan durumu bu koleksiyonları ve yöntem başına ayırmaları ve montaj yüklerini gösteren bir çağrı ağacı. Daha fazla bilgi için [Performans'a](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10))bakın.  
  
<a name="DPs_and_Objects"></a>
## <a name="dependency-properties-and-objects"></a>Bağımlılık Özellikleri ve Nesneleri  
 Genel olarak, bir <xref:System.Windows.DependencyObject> bağımlılık özelliğine erişmek, bir CLR özelliğine erişmekten daha yavaş değildir. Bir özellik değerini ayarlamak için küçük bir performans yükü olsa da, değer almak bir CLR özelliğinden değer almak kadar hızlıdır. Küçük performans genel ini dengeleme, bağımlılık özelliklerinin veri bağlama, animasyon, devralma ve stil oluşturma gibi sağlam özellikleri desteklemesidir. Daha fazla bilgi için [bkz.](dependency-properties-overview.md)  
  
### <a name="dependencyproperty-optimizations"></a>BağımlılıkÖzellik Optimizasyonları  
 Uygulamanızdaki bağımlılık özelliklerini çok dikkatli bir şekilde tanımlamalısınız. Etkileriniz, <xref:System.Windows.DependencyProperty> meta <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>verilerini geçersiz kılarak bu tür olarak işaretlemeniz gerekir. Özellik meta verilerini geçersiz kılma veya alma hakkında daha fazla bilgi için Bkz. [Bağımlılık Özelliği Meta verileri.](dependency-property-metadata.md)  
  
 Tüm özellik değişiklikleri gerçekten ölçü, düzenlemek ve işlemek etkilemezse, bir özellik değişikliği işleyicisinin ölçüleri geçersiz kılması, düzenleme ve işleme geçişlerini el ile işlemesi daha verimli olabilir. Örneğin, bir arka planı yalnızca bir değer ayarlanmış bir sınırdan büyük olduğunda yeniden oluşturmaya karar verebilirsiniz. Bu durumda, özellik değişikliği işleyiciniz yalnızca değer ayarlanan sınırı aştığında işlemegeçersiz olur.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Bağımlılık Özelliğinin Devralınabilir Hale Getirilmesi Ücretsiz Değildir  
 Varsayılan olarak, kayıtlı bağımlılık özellikleri devredilemez. Ancak, herhangi bir özelliği açıkça devralınabilir hale getirebilirsiniz. Bu yararlı bir özellik olsa da, bir özelliği devralınabilir olarak dönüştürmek, özellik geçersiz liği için süreyi artırarak performansı etkiler.  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler'ı Dikkatle Kullanın  
 Arama, <xref:System.Windows.EventManager.RegisterClassHandler%2A> örnek durumunuzu kaydetmenize olanak sağlarken, işleyicinin her örnekte çağrıldığını ve bu nedenle performans sorunlarına neden olabileceğini unutmayın. Yalnızca <xref:System.Windows.EventManager.RegisterClassHandler%2A> uygulamanız örnek durumunuzu kaydetmenizi gerektirdiğinde kullanın.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Kayıt Sırasında Bağımlılık Özelliğinin Varsayılan Değerini Ayarlama  
 Varsayılan değer <xref:System.Windows.DependencyProperty> gerektiren bir değer oluştururken, varsayılan meta verileri kullanarak değeri <xref:System.Windows.DependencyProperty.Register%2A> bir parametre olarak geçirilen yöntemine <xref:System.Windows.DependencyProperty>ayarlayın. Bir oluşturucuda veya bir öğenin her örneğinde özellik değerini ayarlamak yerine bu tekniği kullanın.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register'ı kullanarak PropertyMetaveri Değerini ayarlama  
 Bir <xref:System.Windows.DependencyProperty>, kullanarak <xref:System.Windows.PropertyMetadata> <xref:System.Windows.DependencyProperty.Register%2A> ya da <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemleri ayarlama seçeneğiniz vardır. Nesnenizin çağıracağı <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>statik bir oluşturucu olabilir, ancak bu en uygun çözüm değildir ve performansı etkileyecektir. En iyi performans <xref:System.Windows.PropertyMetadata> için, arama <xref:System.Windows.DependencyProperty.Register%2A>sırasında ayarlayın.  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Serbest Nesneler  
 A, <xref:System.Windows.Freezable> iki durum olan özel bir nesne türüdür: çözülmüş ve dondurulmuş. Nesneleri mümkün olduğunca dondurma, uygulamanızın performansını artırır ve çalışma kümesini azaltır. Daha fazla bilgi için [Freezable Objects Genel Bakış'a](freezable-objects-overview.md)bakın.  
  
 Her <xref:System.Windows.Freezable> biri <xref:System.Windows.Freezable.Changed> değiştiğinde yükseltilen bir olay aşar. Ancak, değişiklik bildirimleri uygulama performansı açısından maliyetlidir.  
  
 Her birinin <xref:System.Windows.Shapes.Rectangle> aynı <xref:System.Windows.Media.Brush> nesneyi kullandığı aşağıdaki örneği göz önünde bulundurun:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak, nesnenin <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.Changed> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini geçersiz kılabilmesi için nesnenin olayı için bir olay işleyicisi sağlar. Bu durumda, her <xref:System.Windows.Media.SolidColorBrush> olay yangın <xref:System.Windows.Freezable.Changed> için her zaman her <xref:System.Windows.Shapes.Rectangle>biri için geri arama işlevi çağırmak için gereklidir —bu geri arama işlevi çağrılarıbirikimi önemli bir performans cezası empoze. Buna ek olarak, uygulama bunu yapmak için tüm liste çapraz olurdu bu noktada işleyicileri eklemek ve kaldırmak için çok performans yoğundur. Uygulama senaryonuz hiçbir <xref:System.Windows.Media.SolidColorBrush>zaman değişiklik göstermezse, <xref:System.Windows.Freezable.Changed> olay işleyicilerini gereksiz yere koruma maliyetini ödersiniz.  
  
 Değişiklik <xref:System.Windows.Freezable> bildirimlerini korumak için artık kaynak harcaması gerekmediğinden, a'yı dondurmak performansını artırabilir. Aşağıdaki tablo, <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.IsFrozen%2A> özelliği ayarlandığında basit bir boyutu `true`gösterir , ne zaman değil göre. Bu, on <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> nesnenin özelliğine bir fırça uyguladığımı varsayar.  
  
|**Durum**|**Boyut**|  
|---------------|--------------|  
|Dondurulmuş<xref:System.Windows.Media.SolidColorBrush>|212 Bayt|  
|Dondurulmamış<xref:System.Windows.Media.SolidColorBrush>|972 Bayt|  
  
 Aşağıdaki kod örneği bu kavramı gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Dondurulmamış Freezables Üzerinde Değiştirilen İşleyiciler Nesneleri Canlı Tutabilir  
 Bir nesnenin bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olayına geçtiği temsilci, bu nesneye etkili bir şekilde başvurur. Bu <xref:System.Windows.Freezable.Changed> nedenle, olay işleyicileri nesneleri beklenenden daha uzun süre canlı tutabilir. Bir <xref:System.Windows.Freezable> nesnenin <xref:System.Windows.Freezable.Changed> olayını dinlemek için kaydedilmiş bir nesneyi temizleme yaparken, nesneyi bırakmadan önce bu temsilciyi kaldırmak önemlidir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ayrıca olayları <xref:System.Windows.Freezable.Changed> dahili olarak bağlar. Örneğin, değer olarak kabul <xref:System.Windows.Freezable> edilen tüm bağımlılık <xref:System.Windows.Freezable.Changed> özellikleri olayları otomatik olarak dinler. Bir <xref:System.Windows.Shapes.Shape.Fill%2A> alır <xref:System.Windows.Media.Brush>özelliği, bu kavramı göstermektedir.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Atamada , `myBrush` `myRectangle.Fill` <xref:System.Windows.Shapes.Rectangle> nesneye işaret eden bir temsilci nesnenin <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.Changed> olayına eklenir. Bu, aşağıdaki kodun çöp `myRect` toplama için gerçekten uygun olmadığı anlamına gelir:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Bu durumda `myBrush` hala `myRectangle` canlı tutuyor ve <xref:System.Windows.Freezable.Changed> olay ateşler zaman ona geri arayacak. Yeni <xref:System.Windows.Shapes.Rectangle> bir `myBrush` `myBrush` <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği atama sadece başka bir olay işleyicisi ekleyeceğiz unutmayın.  
  
 Bu tür nesneleri temizlemenin önerilen yolu, olay <xref:System.Windows.Media.Brush> işleyicisini <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Freezable.Changed> kaldıran özelliği kaldırmaktır.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>Kullanıcı Arabirimi Sanallaştırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ayrıca, verilere bağlı <xref:System.Windows.Controls.StackPanel> alt içeriği otomatik olarak "sanallaştıran" öğenin bir varyasyonunu sağlar. Bu bağlamda, sanallaştırma sözcüğü, öğelerin ekranda görünür olduğu daha fazla sayıda veri öğesinden bir nesne alt kümesinin oluşturulduğu bir tekniği ifade eder. Belirli bir anda ekranda yalnızca birkaç kişi olabilirken, hem bellek hem de işlemci açısından çok sayıda UI öğesi oluşturmak yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel>(tarafından <xref:System.Windows.Controls.VirtualizingPanel>sağlanan işlevsellik yoluyla) görünür öğeleri <xref:System.Windows.Controls.ItemContainerGenerator> hesaplar <xref:System.Windows.Controls.ItemsControl> ve <xref:System.Windows.Controls.ListBox> yalnızca görünür öğeler için öğeler oluşturmak için bir (gibi veya) <xref:System.Windows.Controls.ListView>ile çalışır.  
  
 Performans optimizasyonu olarak, bu öğelerin görsel nesneleri yalnızca ekranda görünürse oluşturulur veya canlı tutulur. Denetimin görüntülenebilir alanında artık değilken, görsel nesneler kaldırılabilir. Bu, veri nesnelerinin tüm yerel koleksiyonda bulunmadığı ve gerektiği gibi akışlandığı veri sanallaştırmasıyla karıştırılmamalıdır.  
  
 Aşağıdaki tabloda, a ve a'ya <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>5000 öğe ekleyerek ve işleyen geçen süreyi gösterir. Bu senaryoda, ölçümler, bir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl> nesnenin özelliğine bir metin dizesi eklemek arasındaki süreyi, panel öğelerinin metin dizesini görüntülediğinde gösterir.  
  
|**Ev sahibi paneli**|**İşleme süresi (ms)**|  
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
