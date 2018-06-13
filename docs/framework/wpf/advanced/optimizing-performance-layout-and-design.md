---
title: 'Performansı İyileştirme: Düzen ve Tasarım'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 9c9921e664d69038480e73ee6779ca9e48b81c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547842"
---
# <a name="optimizing-performance-layout-and-design"></a>Performansı İyileştirme: Düzen ve Tasarım
Tasarımını, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama Düzen hesaplama ve nesne başvuruları doğrulama gereksiz ek yük oluşturarak kendi performansını etkileyebilir. Özellikle, çalışma zamanında nesneleri yapımı uygulamanızın performans özellikleri etkileyebilir.  
  
 Bu konu, bu alanlarda performans önerileri sağlar.  
  
## <a name="layout"></a>Düzen  
 "Düzen geçişi" terimi ölçme ve üyeleri düzenleme işlemi açıklanır bir <xref:System.Windows.Controls.Panel>-nesnenin koleksiyonunu ve bunların ekranda çizimini türetilmiş. Düzen geçişi matematiksel yoğunluklu bir işlemdir — koleksiyondaki alt büyük sayısını büyük gerekli hesaplamaların sayısı. Bir alt her zaman örneğin, <xref:System.Windows.UIElement> koleksiyondaki nesnenin konumunu değiştirdiğinde, düzen sistemi tarafından yeni bir geçişi tetikleme olasılığı vardır. Nesne özellikleri ve düzeni davranışı arasında yakın ilişki nedeniyle düzen sistemi çağırabileceği olayların türünü anlamak önemlidir. Uygulamanızı mümkün olduğunca düzeninin gereksiz tüm çağrılarını iletmek azaltarak daha iyi performans gösterir.  
  
 Bir koleksiyondaki her alt üyesi için iki geçiş düzen sistemi tamamlar: bir ölçü geçişi ve bir düzenleme geçişi. Her bir alt nesne, kendi geçersiz kılınan uygulamasını sağlar <xref:System.Windows.UIElement.Measure%2A> ve <xref:System.Windows.UIElement.Arrange%2A> kendi belirli düzen davranışını sağlamak için yöntemleri. En basit şekliyle, Düzen sistemidir, bir öğenin yeniden boyutlandırılmış konumlandırılmış ve ekranda çizilmiş götüren bir özyinelemeli.  
  
-   Bir alt <xref:System.Windows.UIElement> nesnesi, çekirdek özellikleri ölçülerek düzen işlemine başlar.  
  
-   Nesnenin <xref:System.Windows.FrameworkElement> boyutu gibi ilişkili özellikleri <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A>, değerlendirilir.  
  
-   <xref:System.Windows.Controls.Panel>-belirli mantığı uygulandığı gibi <xref:System.Windows.Controls.DockPanel.Dock%2A> özelliği <xref:System.Windows.Controls.DockPanel>, veya <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliği <xref:System.Windows.Controls.StackPanel>.  
  
-   İçerik düzenlenmiş veya tüm alt nesneleri ölçülen sonra konumlandırıldı.  
  
-   Alt nesne koleksiyonundaki ekran çizilir.  
  
 Aşağıdaki eylemlerden herhangi birini oluşursa düzeni geçiş işlemi yeniden çağrılır:  
  
-   Bir alt nesne koleksiyona eklenir.  
  
-   A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> alt nesneye uygulanır.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> Yöntemi, alt nesne için çağrılır.  
  
-   Bir değişiklik geçişleri düzenleme veya ölçü etkileyen meta verileri ile işaretlenmiş bir bağımlılık özelliğinin değerine olduğunda.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Mümkün olduğunda en verimli panelini kullanın  
 Düzen işleminin doğrudan, düzen davranışını karmaşıklığı <xref:System.Windows.Controls.Panel>-öğelerin türetilmiş. Örneğin, bir <xref:System.Windows.Controls.Grid> veya <xref:System.Windows.Controls.StackPanel> denetim çok daha fazla işlevsellik sağlayan bir <xref:System.Windows.Controls.Canvas> denetim. Fiyat işlevselliği büyük bu artış performans maliyetleri büyük bir artış olur. Ancak, işlevselliği ihtiyacınız yoksa, bir <xref:System.Windows.Controls.Grid> denetimi sağlar, kullanmanız gereken daha az maliyetli alternatifleri gibi bir <xref:System.Windows.Controls.Canvas> veya özel bir panel.  
  
 Daha fazla bilgi için bkz: [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Güncelleştirme yerine RenderTransform'u değiştirme  
 Güncelleştirme olabilir bir <xref:System.Windows.Media.Transform> değeri olarak değiştirerek yerine bir <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Bu, özellikle animasyon içeren senaryolarda geçerlidir. Var olan güncelleştirerek <xref:System.Windows.Media.Transform>, gereksiz Düzen hesaplamasını başlatmaktan kaçınırsınız.  
  
### <a name="build-your-tree-top-down"></a>Ağaç üstten alta oluşturun  
 Bir düğüm eklenen ya da mantıksal ağacından kaldırılan özellik geçersiz kılmalar düğümün üst ve tüm alt öğelerini oluşturulur. Sonuç olarak, üstten alta yapım deseni önceden doğrulanmış düğümleri geçersiz kılınması maliyetini önlemek için her zaman gelmelidir. Aşağıdaki tabloda bir ağaç yukarıdan aşağı alt ağaç, tek bir tıklatmayla 150 düzeyden olduğu yukarı karşı oluşturma arasındaki yürütme hızı farkı gösterilir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.DockPanel> her düzeyde.  
  
|**Eylem**|**Ağaç (ms) oluşturma**|**İşleme — ağaç (ms) oluşturmayı içerir**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Aşağıdan yukarıya|366|454|  
|Yukarıdan aşağıya|11|96|  
  
 Aşağıdaki kod örneğinde nasıl aşağı ağaç top oluşturulacağını gösterir.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Mantıksal ağacının hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)
