---
title: ScrollViewer Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186981"
---
# <a name="scrollviewer-overview"></a>ScrollViewer Genel Bakışı
Kullanıcı arabirimindeki içerik genellikle bilgisayar ekranının görüntü alanından daha büyüktür. Denetim, <xref:System.Windows.Controls.ScrollViewer> uygulamalarda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriğin kaydırılmasını etkinleştirmek için kullanışlı bir yol sağlar. Bu konu öğeyi <xref:System.Windows.Controls.ScrollViewer> tanıtır ve çeşitli kullanım örnekleri sağlar.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>ScrollViewer Denetimi  
 Uygulamalarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kaydırmayı sağlayan iki önceden tanımlanmış <xref:System.Windows.Controls.Primitives.ScrollBar> öğe <xref:System.Windows.Controls.ScrollViewer>vardır: ve . Denetim, <xref:System.Windows.Controls.ScrollViewer> kaydırılabilir bir alanda <xref:System.Windows.Controls.Primitives.ScrollBar> diğer görünür öğeleri görüntülemek için <xref:System.Windows.Controls.Panel> yatay ve dikey öğeleri ve bir içerik kapsayıcısını (öğe gibi) saklar. İçerik kaydırma için <xref:System.Windows.Controls.Primitives.ScrollBar> öğeyi kullanmak için özel bir nesne oluşturmanız gerekir. Ancak, <xref:System.Windows.Controls.Primitives.ScrollBar> işlevselliği <xref:System.Windows.Controls.ScrollViewer> kapsülleyen bir bileşik denetim olduğundan, öğeyi tek başına kullanabilirsiniz.  
  
 Denetim <xref:System.Windows.Controls.ScrollViewer> hem fare hem de klavye komutlarına yanıt verir ve içeriği önceden belirlenmiş artışlarla kaydırmak için çok sayıda yöntem tanımlar. <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> Bir <xref:System.Windows.Controls.ScrollViewer> durumda bir değişiklik algılamak için olay kullanabilirsiniz.  
  
 A <xref:System.Windows.Controls.ScrollViewer> yalnızca bir alt öğesi <xref:System.Windows.Controls.Panel> olabilir, genellikle <xref:System.Windows.Controls.Panel.Children%2A> bir öğe koleksiyonu barındırabilir bir öğe. Özellik, <xref:System.Windows.Controls.ContentPresenter.Content%2A> <xref:System.Windows.Controls.ScrollViewer>tek alt özelliği tanımlar.  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Fiziksel ve Mantıksal Kaydırma  
 Fiziksel kaydırma, içeriği önceden belirlenmiş bir fiziksel artışla, genellikle pikselolarak bildirilen bir değerle kaydırmak için kullanılır. Mantıksal kaydırma, mantıksal ağaçtaki bir sonraki öğeye kaydırmak için kullanılır. Fiziksel kaydırma çoğu <xref:System.Windows.Controls.Panel> öğe için varsayılan kaydırma davranışıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]her iki kaydırma türünü de destekler.  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo Arabirimi  
 Arabirim, <xref:System.Windows.Controls.Primitives.IScrollInfo> bir <xref:System.Windows.Controls.ScrollViewer> veya türetilmiş denetim içindeki ana kaydırma bölgesini temsil eder. Arabirim, fiziksel bir artış yerine mantıksal birim <xref:System.Windows.Controls.Panel> tarafından kaydırılması gereken öğeler tarafından uygulanabilen kaydırma özelliklerini ve yöntemleri tanımlar. Türetilmiş <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.IScrollInfo> bir örneğini ve kaydırma yöntemlerini kullanarak bir örneğini kullanmak, piksel artışyerine bir alt koleksiyondaki bir sonraki mantıksal birime kaydırmanın yararlı bir yolunu sağlar. Varsayılan olarak, <xref:System.Windows.Controls.ScrollViewer> denetim fiziksel birimler tarafından kaydırma destekler.  
  
 <xref:System.Windows.Controls.StackPanel>ve <xref:System.Windows.Controls.VirtualizingStackPanel> hem <xref:System.Windows.Controls.Primitives.IScrollInfo> uygulamak ve yerel mantıksal kaydırma destekler. Mantıksal kaydırmayı yerel olarak destekleyen düzen denetimleri için, ana bilgisayar <xref:System.Windows.Controls.Panel> öğesini <xref:System.Windows.Controls.ScrollViewer> bir'e sararak ve <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> özelliği .'e `false`ayarlayarak fiziksel kaydırma elde edebilirsiniz.  
  
 Aşağıdaki kod örneği, <xref:System.Windows.Controls.Primitives.IScrollInfo> bir örneğinin nasıl <xref:System.Windows.Controls.StackPanel> kullanılacağını ve arabirim<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>tarafından tanımlanan içerik kaydırma yöntemlerini (ve) nasıl kullanılacağını gösterir.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer Öğesini Tanımlama ve Kullanma  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ScrollViewer> bazı metin ve dikdörtgen içeren bir pencere oluşturur. <xref:System.Windows.Controls.Primitives.ScrollBar>öğeleri yalnızca gerekli olduğunda görünür. Pencereyi yeniden boyutlandırdığınızda, <xref:System.Windows.Controls.Primitives.ScrollBar> öğeler ve özelliklerin <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> güncelleştirilmiş değerleri nedeniyle öğeler görünür ve <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> kaybolur.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>ScrollViewer'ı Şekillendirme  
 Windows Sunu Temeli'ndeki <xref:System.Windows.Controls.ScrollViewer> tüm denetimler gibi, denetimin varsayılan oluşturma davranışını değiştirmek için stillandırılabilir. Denetim stili hakkında daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Paginating Belgeler  
 Belge içeriği için kaydırmanın alternatifi, pagination destekleyen bir belge kapsayıcısı seçmektir. <xref:System.Windows.Documents.FlowDocument>bir görüntüleme denetimi içinde barındırılacak şekilde tasarlanmış <xref:System.Windows.Controls.FlowDocumentPageViewer>belgeler içindir, gibi , birden çok sayfa arasında içeriği paginating destekler, kaydırma ihtiyacını önlemek. <xref:System.Windows.Controls.DocumentViewer>içeriği görüntü alanının dışında görüntülemek için geleneksel kaydırma özelliğini kullanan içeriği görüntülemek <xref:System.Windows.Documents.FixedDocument> için bir çözüm sağlar.  
  
 Belge biçimleri ve sunu seçenekleri hakkında daha fazla bilgi için [WPF'deki Belgeler'e](../advanced/documents-in-wpf.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Nasıl Yapılsın: Kaydırma Görüntüleyici Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)
- [ScrollBar Stilleri ve Şablonları](scrollbar-styles-and-templates.md)
- [Denetimler](../advanced/optimizing-performance-controls.md)
