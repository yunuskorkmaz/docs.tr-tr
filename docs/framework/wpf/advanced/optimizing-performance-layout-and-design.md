---
title: 'Performansı iyileştirme: Düzen ve Tasarım'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: a18cc364d625cc98f77e63b0f361980ef574e8a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611890"
---
# <a name="optimizing-performance-layout-and-design"></a>Performansı iyileştirme: Düzen ve Tasarım
Tasarımı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen hesaplama ve nesne başvurularını doğrulama gereksiz yük oluşturarak uygulama performansını etkileyebilir. Nesneleri, oluşumunu özellikle, çalışma zamanında uygulamanızın performans özelliklerine etkileyebilir.  
  
 Bu konu, bu alanlarda performans önerileri sağlar.  
  
## <a name="layout"></a>Düzen  
 "Düzen geçişi" terimi ölçme ve üyelerinin düzenleme işlemi açıklanır bir <xref:System.Windows.Controls.Panel>-türetilen nesne koleksiyonunu ve bunların ekranda çizim. Düzen geçişi matematiksel olarak yoğun bir işlemdir; öğelerinin koleksiyondaki sayıda büyük sayısının hesaplamaların gerekli. Bir alt her zaman örneğin <xref:System.Windows.UIElement> nesne koleksiyonundaki konumuna değişiklikleri, yeni bir düzen sistemi geçişi tetikleme olasılığına sahiptir. Nesne özellikleri ve düzeni davranışı arasındaki yakın ilişkileri nedeniyle düzen sistemi çağırabilirsiniz olayların türünü anlamak önemlidir. Uygulamanızın mümkün olduğunca düzenini gereksiz tüm çağrıları geçirmek azaltarak daha iyi sonuç verecektir.  
  
 Düzen sistemi, bir koleksiyondaki her bir alt üyesi için iki geçiş yapar: bir ölçü geçişi ve düzenleme geçişi. Her alt nesne geçersiz kılınan kendi uygulamasını sağlar <xref:System.Windows.UIElement.Measure%2A> ve <xref:System.Windows.UIElement.Arrange%2A> kendi özel düzen davranışı sağlamak için yöntemleri. En basit şekliyle, düzen, bir öğenin yeniden boyutlandırılmış konumlandırılmış ve ekranda çizilmiş müşteri adayları bir özyinelemeli sistemidir.  
  
- Bir alt <xref:System.Windows.UIElement> nesne, çekirdek özellikleri sağlayarak düzen işlemine başlar.  
  
- Nesnenin <xref:System.Windows.FrameworkElement> boyutu gibi ilişkili özellikleri <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A>, değerlendirilir.  
  
- <xref:System.Windows.Controls.Panel>-belirli bir mantıksal uygulandığı gibi <xref:System.Windows.Controls.DockPanel.Dock%2A> özelliği <xref:System.Windows.Controls.DockPanel>, veya <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliği <xref:System.Windows.Controls.StackPanel>.  
  
- İçerik düzenleme veya tüm alt nesneleri ölçüldükten sonra konumlandırılmış.  
  
- Alt nesneler koleksiyonunun ekrana çizilir.  
  
 Aşağıdaki eylemlerden herhangi birini meydana gelirse düzeni geçiş işlemi tekrar çağrılır:  
  
- Bir alt nesnesi, koleksiyona eklenir.  
  
- A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> alt nesneye uygulanır.  
  
- <xref:System.Windows.UIElement.UpdateLayout%2A> Yöntemi, alt nesne için çağrılır.  
  
- Geçişleri düzenleme veya ölçü etkileyen meta verileri ile işaretlenmiş bir bağımlılık özelliğinin değeri için bir değişiklik olduğunda.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Mümkün olduğunda en verimli panelini kullanın  
 Düzen işleminin doğrudan, düzen davranışını karmaşıklığı <xref:System.Windows.Controls.Panel>-türetilmiş öğeleri kullanırsınız. Örneğin, bir <xref:System.Windows.Controls.Grid> veya <xref:System.Windows.Controls.StackPanel> denetimi çok daha fazla işlevsellik sağlayan bir <xref:System.Windows.Controls.Canvas> denetimi. Bu işlev daha büyük bir artış fiyat performans maliyetleri daha büyük bir artış olur. Ancak, İşlevler gerekmiyorsa, bir <xref:System.Windows.Controls.Grid> denetimi sağlar, kullanmanız gerektiğini daha az maliyetli alternatifleri gibi bir <xref:System.Windows.Controls.Canvas> veya özel bir paneli.  
  
 Daha fazla bilgi için [panellere genel bakış](../controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Bir RenderTransform değiştirmek yerine güncelleştir  
 Güncelleştirme olabilir bir <xref:System.Windows.Media.Transform> değeri olarak değiştirmek yerine bir <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Bu, özellikle animasyon içeren senaryolarda geçerlidir. Mevcut bir güncelleştirerek <xref:System.Windows.Media.Transform>, gereksiz Düzen hesaplamasını başlatma kaçının.  
  
### <a name="build-your-tree-top-down"></a>Ağaç yukarıdan aşağıya oluşturun  
 Bir düğüm eklendiğinde veya mantıksal ağacından kaldırıldı özelliği geçersiz kılmalar düğümün üst ve alt öğeleri üzerinde oluşturulur. Sonuç olarak, yukarıdan aşağıya yapım deseni zaten doğrulanmış düğümlerdeki kılınması maliyetini önlemek için her zaman gelmelidir. Aşağıdaki tablo, yürütme hızını yukarıdan aşağıya aşağıdan yukarıya, tek bir 150 düzeyden bulunduğu ağaç karşı ağacı oluşturma arasındaki farkı gösterir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.DockPanel> her düzeyde.  
  
|**Eylem**|**Ağaç (ms) oluşturma**|**İşleme — ağaç (ms) oluşturmayı içerir**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Aşağıdan yukarıya|366|454|  
|Yukarıdan aşağıya|11|96|  
  
 Aşağıdaki kod örneği, ağaç yukarıdan aşağı oluşturma işlemini gösterir.  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Mantıksal ağacı hakkında daha fazla bilgi için bkz. [WPF içinde ağaçlar](trees-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
- [Düzen](layout.md)
