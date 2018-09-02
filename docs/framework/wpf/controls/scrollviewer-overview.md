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
ms.openlocfilehash: 4c9a2e8cf64f18f3e8614912759a4a6eb01d4823
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463136"
---
# <a name="scrollviewer-overview"></a>ScrollViewer Genel Bakışı
Bir kullanıcı arabiriminde içeriği genellikle bir bilgisayar ekranının ekran alandan daha büyük. <xref:System.Windows.Controls.ScrollViewer> Denetim içeriğinin gezinmeye olanak sağlamak için kolay bir yol sağlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu konu tanıtır <xref:System.Windows.Controls.ScrollViewer> öğesi ve çeşitli kullanım örnekleri sağlar.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer denetimi  
 Kaydırma sağlayan önceden tanımlanmış iki öğe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar: <xref:System.Windows.Controls.Primitives.ScrollBar> ve <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Denetimini kapsülleyen yatay ve dikey <xref:System.Windows.Controls.Primitives.ScrollBar> öğeleri ve içerik kapsayıcı (gibi bir <xref:System.Windows.Controls.Panel> öğesi) kaydırılabilir bir alanda başka görünür öğeler görüntülemek için. Kullanmak için özel bir nesne derlemelidir <xref:System.Windows.Controls.Primitives.ScrollBar> içerik kaydırma için öğesi. Ancak, kullanabileceğiniz <xref:System.Windows.Controls.ScrollViewer> öğesi kendisi ile bileşik denetim olduğundan kapsülleyen <xref:System.Windows.Controls.Primitives.ScrollBar> işlevselliği.  
  
 <xref:System.Windows.Controls.ScrollViewer> Denetimi, fare ve klavye komutlarına yanıt verir ve içeriği önceden belirlenmiş artışlarla kaydırmak için çok sayıda yöntem tanımlar. Kullanabileceğiniz <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> olay değişikliği algılamak üzere bir <xref:System.Windows.Controls.ScrollViewer> durumu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> yalnızca tek bir alt öğe genellikle olabilir bir <xref:System.Windows.Controls.Panel> barındırabilir öğesi bir <xref:System.Windows.Controls.Panel.Children%2A> öğelerinin koleksiyonu. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Özelliği tanımlayan tek bir alt öğesi <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fiziksel vs. Mantıksal kaydırma  
 Fiziksel kaydırma içeriği kaydırmak için önceden belirlenmiş bir fiziksel artışla genellikle piksel cinsinden bildirilen değer tarafından kullanılır. Mantıksal kaydırma mantıksal ağaçta bir sonraki öğeye ilerlemek için kullanılır. Fiziksel kaydırma varsayılan davranıştır kaydırma çoğu <xref:System.Windows.Controls.Panel> öğeleri. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Her iki tür kaydırma destekler.  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo arabirimi  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Arabirimi temsil eder, ana kaydırma bölgesinde bir <xref:System.Windows.Controls.ScrollViewer> veya denetim türetilmiş. Kayan özellikleri ve yöntemleri tarafından uygulanan arabirimi tanımlar <xref:System.Windows.Controls.Panel> mantıksal birim yerine fiziksel bir artış kaydırma gerektiren öğeler. Örneği atama <xref:System.Windows.Controls.Primitives.IScrollInfo> türetilmiş için <xref:System.Windows.Controls.Panel> ve sonra kaydırma yöntemlerini kullanma, bir alt koleksiyonu yerine piksel artış sonraki mantıksal birim kaydırmak için kullanışlı bir yol sağlar. Varsayılan olarak, <xref:System.Windows.Controls.ScrollViewer> denetimi, fiziksel birimlerle kaydırma destekler.  
  
 <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.VirtualizingStackPanel> her ikisini de uygulamak <xref:System.Windows.Controls.Primitives.IScrollInfo> ve mantıksal kaydırma yerel olarak destekler. Bu yerel olarak mantıksal kaydırma desteği düzen denetimleri için hala kaydırma fiziksel konak sarmalama tarafından elde edebileceğiniz <xref:System.Windows.Controls.Panel> öğesinde bir <xref:System.Windows.Controls.ScrollViewer> ve ayarı <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> özelliğini `false`.  
  
 Aşağıdaki kod örneği bir örneğini nasıl gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> için bir <xref:System.Windows.Controls.StackPanel> ve içerik kaydırma yöntemlerini kullanma (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) arabirim tarafından tanımlanan.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Tanımlama ve bir ScrollViewer öğesi kullanma  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ScrollViewer> bazı metinleri ve bir dikdörtgen içeren bir pencere içinde. <xref:System.Windows.Controls.Primitives.ScrollBar> yalnızca gerekli olduklarında öğeleri görünür. Penceresini yeniden boyutlandırdığınızda <xref:System.Windows.Controls.Primitives.ScrollBar> öğeleri görünür ve, güncelleştirilmiş değerleri nedeniyle kaybolmasını <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> ve <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> özellikleri.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>ScrollViewer stil oluşturma  
 Windows Presentation Foundation'da tüm denetimler gibi <xref:System.Windows.Controls.ScrollViewer> denetimin varsayılan işleme davranışını değiştirmek üzere biçimlendirilebilir. Denetim stili hakkında ek bilgi için bkz. [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Kullanılabilir belgeler  
 Belge içeriği için kaydırma alternatif sayfalandırma destekleyen bir belge kapsayıcı seçmektir. <xref:System.Windows.Documents.FlowDocument> bir görüntüleme denetimine gibi barındırılması için tasarlanmıştır ve belgeler için <xref:System.Windows.Controls.FlowDocumentPageViewer>, barındırılmak kaydırmayı önleme birden çok sayfa. <xref:System.Windows.Controls.DocumentViewer> bir çözüm sağlar <xref:System.Windows.Documents.FixedDocument> görüntüleme alanının dışındaki içeriği görüntülemek için geleneksel kaydırma kullanan içerik.  
  
 Belge biçimleri ve sunum seçenekleri hakkında ek bilgi için bkz. [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Kaydırma Görüntüleyicisi oluşturma](https://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Denetimler](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
