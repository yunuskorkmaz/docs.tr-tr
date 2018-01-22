---
title: "ScrollViewer Genel Bakışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7317bade85641d7d055facabcf7103b945609583
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="scrollviewer-overview"></a>ScrollViewer Genel Bakışı
Bir kullanıcı arabirimi içinde içerik genellikle bilgisayar ekranın görüntü alanından daha büyüktür. <xref:System.Windows.Controls.ScrollViewer> Denetim içeriğinin kaydırma etkinleştirmek için kullanışlı bir yöntem sunar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu konu tanıtır <xref:System.Windows.Controls.ScrollViewer> öğesi ve birkaç kullanım örnekleri sağlar.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer denetimi  
 Kaydırmayı etkinleştiren önceden tanımlanmış iki öğe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar: <xref:System.Windows.Controls.Primitives.ScrollBar> ve <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Denetim yalıtır yatay ve dikey <xref:System.Windows.Controls.Primitives.ScrollBar> öğelerini ve içerik kapsayıcı (gibi bir <xref:System.Windows.Controls.Panel> öğesi) kaydırılabilir bir alanında diğer görünür öğeleri görüntülemek için. Kullanmak için özel bir nesne oluşturmanız <xref:System.Windows.Controls.Primitives.ScrollBar> içerik kaydırma öğesi. Ancak, kullanabileceğiniz <xref:System.Windows.Controls.ScrollViewer> öğesi kendi başına bir bileşik denetim olduğundan yalıtır <xref:System.Windows.Controls.Primitives.ScrollBar> işlevselliği.  
  
 <xref:System.Windows.Controls.ScrollViewer> Denetimi fare ve klavye komutlarına yanıt verir ve içeriği önceden belirlenmiş artışlarla kaydırmak çok sayıda yöntem tanımlar. Kullanabileceğiniz <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> değişikliği algılamak için olay bir <xref:System.Windows.Controls.ScrollViewer> durumu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> yalnızca tek bir alt öğe genellikle olabilir bir <xref:System.Windows.Controls.Panel> barındırabilir öğesi bir <xref:System.Windows.Controls.Panel.Children%2A> öğeleri koleksiyonu. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Özelliği tanımlar tek alt <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fiziksel vs. Mantıksal kaydırma  
 Fiziksel kaydırma içeriği kaydırmak için önceden belirlenmiş fiziksel artışla genellikle piksel cinsinden bildirilmiş bir değer tarafından kullanılır. Mantıksal kaydırma mantıksal ağacının bir sonraki öğeye kaydırmak için kullanılır. Fiziksel kaydırma olan çoğu için varsayılan kaydırma davranışını <xref:System.Windows.Controls.Panel> öğeleri. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Her iki tür kaydırma destekler.  
  
#### <a name="the-iscrollinfo-interface"></a>The IScrollInfo Interface  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Arabirimi ana kaydırma bölgesini temsil eden bir <xref:System.Windows.Controls.ScrollViewer> veya denetim türetilmiş. Kayan özellikleri ve yöntemleri tarafından uygulanan arabirimi tanımlar <xref:System.Windows.Controls.Panel> mantıksal birim yerine fiziksel bir artış kaydırma gerektiren öğeler. Örneği atama <xref:System.Windows.Controls.Primitives.IScrollInfo> türetilmiş için <xref:System.Windows.Controls.Panel> ve kaydırma yöntemlerini kullanarak bir alt koleksiyona yerine piksel artış sonraki mantıksal birime kaydırmak için kullanışlı bir yol sağlar. Varsayılan olarak, <xref:System.Windows.Controls.ScrollViewer> denetimi, fiziksel birimlerle kaydırmayı destekler.  
  
 <xref:System.Windows.Controls.StackPanel>ve <xref:System.Windows.Controls.VirtualizingStackPanel> her ikisini de uygulamak <xref:System.Windows.Controls.Primitives.IScrollInfo> ve mantıksal kaydırmayı yerel olarak destekler. Bu yerel destek mantıksal kaydırma düzen denetimleri için halen fiziksel ana bilgisayar kaydırma tarafından kaydırma elde edebilirsiniz <xref:System.Windows.Controls.Panel> öğesinde bir <xref:System.Windows.Controls.ScrollViewer> ve ayarı <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> özelliğine `false`.  
  
 Aşağıdaki kod örneğinde örneği yayınlanamıyor gösterilmiştir <xref:System.Windows.Controls.Primitives.IScrollInfo> için bir <xref:System.Windows.Controls.StackPanel> ve içerik kaydırma yöntemlerinin (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) arabirim tarafından tanımlanan.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Tanımlama ve ScrollViewer öğesini kullanma  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.ScrollViewer> bir pencerede bazı metinleri ve bir dikdörtgen içerir. <xref:System.Windows.Controls.Primitives.ScrollBar>öğeleri yalnızca gerekli olduklarında görünür. Pencereyi yeniden boyutlandırdığınızda <xref:System.Windows.Controls.Primitives.ScrollBar> öğeleri görünür ve kaybolur, güncelleştirilmiş değerleri nedeniyle <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> ve <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> özellikleri.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>ScrollViewer'a stil ekleme  
 Windows Presentation Foundation içindeki tüm denetimler gibi <xref:System.Windows.Controls.ScrollViewer> denetimi varsayılan işleme davranışını değiştirmek için stili. Denetim stil hakkında ek bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Belgeleri sayfa numaralandırma  
 Belgenin içeriği için kaydırma alternatif sayfalandırma destekleyen bir belge kapsayıcı seçmektir. <xref:System.Windows.Documents.FlowDocument>bir görüntüleme denetimine gibi barındırılması için tasarlanmış belgeler için <xref:System.Windows.Controls.FlowDocumentPageViewer>, barındırılmak kaydırmayı önleme birden çok sayfa. <xref:System.Windows.Controls.DocumentViewer>İzleme için bir çözüm sağlar <xref:System.Windows.Documents.FixedDocument> görüntü alanının dışındaki içeriği görüntülemek için geleneksel kaydırmayı kullanan içerik.  
  
 Belge biçimleri ve sunu seçenekleri hakkında ek bilgi için bkz: [WPF belgelerde](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Bir kaydırma Görüntüleyicisi oluşturma](http://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Denetimler](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
