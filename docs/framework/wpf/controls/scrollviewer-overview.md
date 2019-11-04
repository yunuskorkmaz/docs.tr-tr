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
ms.openlocfilehash: 993f3c861cbead88df3503eb01f18e5d1f69e2d8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458428"
---
# <a name="scrollviewer-overview"></a>ScrollViewer Genel Bakışı
Bir kullanıcı arabirimindeki içerikler genellikle bilgisayar ekranının görüntüleme alanından daha büyüktür. <xref:System.Windows.Controls.ScrollViewer> denetimi, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarda içerik kaydırmayı etkinleştirmek için kullanışlı bir yol sağlar. Bu konuda <xref:System.Windows.Controls.ScrollViewer> öğesi tanıtılmakta ve birkaç kullanım örneği sunulmaktadır.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer denetimi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda kaydırmayı etkinleştiren önceden tanımlanmış iki öğe vardır: <xref:System.Windows.Controls.Primitives.ScrollBar> ve <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> denetimi, kaydırılabilir bir alanda diğer görünür öğeleri göstermek için yatay ve dikey <xref:System.Windows.Controls.Primitives.ScrollBar> öğelerini ve bir içerik kapsayıcısını (<xref:System.Windows.Controls.Panel> öğesi gibi) kapsüller. İçerik kaydırma için <xref:System.Windows.Controls.Primitives.ScrollBar> öğesini kullanmak üzere özel bir nesne derlemeniz gerekir. Ancak, <xref:System.Windows.Controls.Primitives.ScrollBar> işlevselliğini kapsülleyen bir bileşik denetim olduğundan, <xref:System.Windows.Controls.ScrollViewer> öğesini kendisi kullanabilirsiniz.  
  
 <xref:System.Windows.Controls.ScrollViewer> denetimi hem fare hem de klavye komutlarına yanıt verir ve içeriği önceden belirlenmiş artışlarla kaydırmak için çeşitli yöntemler tanımlar. <xref:System.Windows.Controls.ScrollViewer> durumundaki bir değişikliği algılamak için <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> olayını kullanabilirsiniz.  
  
 Bir <xref:System.Windows.Controls.ScrollViewer> yalnızca bir alt öğe olabilir, genellikle öğelerin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonunu barındırabileceğiniz bir <xref:System.Windows.Controls.Panel> öğesidir. <xref:System.Windows.Controls.ContentPresenter.Content%2A> özelliği, <xref:System.Windows.Controls.ScrollViewer>tek alt öğesini tanımlar.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fiziksel ve mantıksal kaydırma  
 Fiziksel kaydırma, genellikle piksel olarak belirtilen bir değere göre önceden belirlenmiş fiziksel artışa göre içerik kaydırmak için kullanılır. Mantıksal kaydırma, mantıksal ağaçtaki bir sonraki öğeye kaydırmak için kullanılır. Fiziksel kaydırma, çoğu <xref:System.Windows.Controls.Panel> öğesi için varsayılan kaydırma davranışıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her iki kaydırma türünü destekler.  
  
#### <a name="the-iscrollinfo-interface"></a>Icrollinınfo arabirimi  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi, bir <xref:System.Windows.Controls.ScrollViewer> ya da türetilmiş denetim içindeki ana kaydırma bölgesini temsil eder. Arabirim, fiziksel bir artış yerine mantıksal birim tarafından kaydırmayı gerektiren <xref:System.Windows.Controls.Panel> öğeleri tarafından uygulanabilen kaydırma özelliklerini ve yöntemleri tanımlar. Bir <xref:System.Windows.Controls.Primitives.IScrollInfo> örneğini türetilmiş bir <xref:System.Windows.Controls.Panel> atama ve sonra kaydırma yöntemlerini kullanma, piksel artışı yerine alt koleksiyondaki bir sonraki mantıksal birime kaydırmak için kullanışlı bir yol sağlar. <xref:System.Windows.Controls.ScrollViewer> denetimi varsayılan olarak fiziksel birimlere göre kaydırmayı destekler.  
  
 <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.VirtualizingStackPanel> her ikisi de <xref:System.Windows.Controls.Primitives.IScrollInfo> uygular ve mantıksal kaydırmayı yerel olarak destekler. Mantıksal kaydırmayı yerel olarak destekleyen düzen denetimlerinde, ana bilgisayar <xref:System.Windows.Controls.Panel> öğesini bir <xref:System.Windows.Controls.ScrollViewer> sarmalayarak ve <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> özelliğini `false`olarak ayarlayarak fiziksel kaydırmaya devam edebilirsiniz.  
  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Controls.Primitives.IScrollInfo> örneğinin bir <xref:System.Windows.Controls.StackPanel> nasıl alınacağını ve arabirim tarafından tanımlanan içerik kaydırma yöntemlerini (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer Öğesi tanımlama ve kullanma  
 Aşağıdaki örnek, bir pencerede metin ve dikdörtgen içeren bir <xref:System.Windows.Controls.ScrollViewer> oluşturur. <xref:System.Windows.Controls.Primitives.ScrollBar> öğeler yalnızca gerekli olduklarında görünür. Pencereyi yeniden boyutlandırdığınızda, <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> ve <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> özelliklerinin güncelleştirilmiş değerleri nedeniyle <xref:System.Windows.Controls.Primitives.ScrollBar> öğeleri görünür ve kaybolur.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>ScrollViewer Stillendirme  
 Windows Presentation Foundation tüm denetimleri gibi, denetimin varsayılan işleme davranışını değiştirmek için <xref:System.Windows.Controls.ScrollViewer> Stillenebilir. Denetim stili hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Belgeleri sayfalayarak  
 Belge içeriği için, kaydırmaya alternatif olarak, sayfalandırmayı destekleyen bir belge kapsayıcısı seçmeniz gerekir. <xref:System.Windows.Documents.FlowDocument>, birden çok sayfada içerik sayfalandırmayı destekleyen <xref:System.Windows.Controls.FlowDocumentPageViewer>gibi bir görüntüleme denetimi içinde barındırılmak üzere tasarlanan belgeler için, kaydırma ihtiyacını önler. <xref:System.Windows.Controls.DocumentViewer>, içeriği görüntüleme alanı bölgesi dışında görüntülemek için geleneksel kaydırmayı kullanan <xref:System.Windows.Documents.FixedDocument> içeriğini görüntülemeye yönelik bir çözüm sağlar.  
  
 Belge biçimleri ve sunum seçenekleri hakkında daha fazla bilgi için bkz. [WPF Içindeki belgeler](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Nasıl yapılır: kaydırma Görüntüleyicisi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)
- [ScrollBar Stilleri ve Şablonları](scrollbar-styles-and-templates.md)
- [Denetimler](../advanced/optimizing-performance-controls.md)
