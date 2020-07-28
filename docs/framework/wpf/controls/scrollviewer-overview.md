---
title: ScrollViewer Genel Bakışı
description: Windows Presentation Foundation uygulamalarında içerik kaydırmayı sağlayan ScrollViewer denetimi hakkında bilgi edinin. Bkz. kullanım örnekleri.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1ef680bb004315a2b523814714d5533535d044e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164642"
---
# <a name="scrollviewer-overview"></a>ScrollViewer Genel Bakışı
Bir kullanıcı arabirimindeki içerikler genellikle bilgisayar ekranının görüntüleme alanından daha büyüktür. <xref:System.Windows.Controls.ScrollViewer>Denetim, uygulamalarda içerik kaydırmayı etkinleştirmek için kullanışlı bir yol sağlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Bu konu, <xref:System.Windows.Controls.ScrollViewer> öğesini tanıtır ve birkaç kullanım örneği sağlar.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>ScrollViewer denetimi  
 Uygulamalarda kaydırmayı etkinleştiren önceden tanımlanmış iki öğe vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : <xref:System.Windows.Controls.Primitives.ScrollBar> ve <xref:System.Windows.Controls.ScrollViewer> . <xref:System.Windows.Controls.ScrollViewer>Bu denetim, <xref:System.Windows.Controls.Primitives.ScrollBar> <xref:System.Windows.Controls.Panel> kaydırılabilir bir alanda diğer görünür öğeleri göstermek için yatay ve dikey öğeleri ve bir içerik kapsayıcısını (bir öğe gibi) kapsüller. İçerik kaydırma için öğesini kullanmak üzere özel bir nesne derlemeniz gerekir <xref:System.Windows.Controls.Primitives.ScrollBar> . Ancak, <xref:System.Windows.Controls.ScrollViewer> işlevselliği kapsülleyen bir bileşik denetim olduğundan, öğesini kendisi de kullanabilirsiniz <xref:System.Windows.Controls.Primitives.ScrollBar> .  
  
 <xref:System.Windows.Controls.ScrollViewer>Denetim hem fare hem de klavye komutlarına yanıt verir ve içeriği önceden belirlenmiş artışlarla kaydırmak için çeşitli yöntemler tanımlar. <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>Olayı, bir durumdaki değişikliği algılamak için kullanabilirsiniz <xref:System.Windows.Controls.ScrollViewer> .  
  
 Yalnızca bir alt öğesi olabilir <xref:System.Windows.Controls.ScrollViewer> , genellikle bir öğe <xref:System.Windows.Controls.Panel> koleksiyonunu barındırabileceğiniz bir öğedir <xref:System.Windows.Controls.Panel.Children%2A> . <xref:System.Windows.Controls.ContentPresenter.Content%2A>Özelliği, öğesinin tek alt öğesini tanımlar <xref:System.Windows.Controls.ScrollViewer> .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Fiziksel ve mantıksal kaydırma  
 Fiziksel kaydırma, genellikle piksel olarak belirtilen bir değere göre önceden belirlenmiş fiziksel artışa göre içerik kaydırmak için kullanılır. Mantıksal kaydırma, mantıksal ağaçtaki bir sonraki öğeye kaydırmak için kullanılır. Fiziksel kaydırma, çoğu öğe için varsayılan kaydırma davranışıdır <xref:System.Windows.Controls.Panel> . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Her iki kaydırma türünü destekler.  
  
#### <a name="the-iscrollinfo-interface"></a>Icrollinınfo arabirimi  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>Arabirim, veya türetilmiş bir denetim içindeki ana kaydırma bölgesini temsil eder <xref:System.Windows.Controls.ScrollViewer> . Arabirim, <xref:System.Windows.Controls.Panel> fiziksel bir artış yerine mantıksal birim tarafından kaydırmayı gerektiren öğeler tarafından uygulanabilen kaydırma özelliklerini ve yöntemleri tanımlar. Öğesinin bir örneğini <xref:System.Windows.Controls.Primitives.IScrollInfo> türetilmiş öğesine atama <xref:System.Windows.Controls.Panel> ve sonra kaydırma yöntemlerini kullanma, piksel artışı yerine bir alt koleksiyonda bir sonraki mantıksal birime kaydırmak için kullanışlı bir yol sağlar. Varsayılan olarak, <xref:System.Windows.Controls.ScrollViewer> Denetim fiziksel birimlere göre kaydırmayı destekler.  
  
 <xref:System.Windows.Controls.StackPanel>ve <xref:System.Windows.Controls.VirtualizingStackPanel> her ikisi de <xref:System.Windows.Controls.Primitives.IScrollInfo> mantıksal kaydırmayı uygular ve yerel olarak destekler. Mantıksal kaydırmayı yerel olarak destekleyen düzen denetimlerinde, ana bilgisayar <xref:System.Windows.Controls.Panel> öğesini bir içinde sarmalayarak <xref:System.Windows.Controls.ScrollViewer> ve <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> özelliğini olarak ayarlayarak fiziksel kaydırmaya devam edebilirsiniz `false` .  
  
 Aşağıdaki kod örneği, bir örneğinin öğesine nasıl ekleneceğini <xref:System.Windows.Controls.Primitives.IScrollInfo> <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> arabirim tarafından tanımlanan içerik kaydırma yöntemlerini (ve) kullanmayı gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> .  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer Öğesi tanımlama ve kullanma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.ScrollViewer> metin ve dikdörtgen içeren bir pencerede oluşturur. <xref:System.Windows.Controls.Primitives.ScrollBar>öğeler yalnızca gerekli olduklarında görünür. Pencereyi yeniden boyutlandırdığınızda, <xref:System.Windows.Controls.Primitives.ScrollBar> ve özelliklerinin güncelleştirilmiş değerleri nedeniyle öğeler görünür ve kaybolur <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> .  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>ScrollViewer Stillendirme  
 Windows Presentation Foundation içindeki tüm denetimler gibi, <xref:System.Windows.Controls.ScrollViewer> denetimin varsayılan işleme davranışını değiştirmek için stil oluşturulabilir. Denetim stili hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Belgeleri sayfalayarak  
 Belge içeriği için, kaydırmaya alternatif olarak, sayfalandırmayı destekleyen bir belge kapsayıcısı seçmeniz gerekir. <xref:System.Windows.Documents.FlowDocument>, gibi bir görüntüleme denetimi içinde barındırılmak üzere tasarlanan, gibi <xref:System.Windows.Controls.FlowDocumentPageViewer> birden çok sayfada içerik sayfalandırmayı destekleyen, kaydırma ihtiyacını engelleyen belgeler içindir. <xref:System.Windows.Controls.DocumentViewer>içeriği görüntülemek için <xref:System.Windows.Documents.FixedDocument> , görüntüleme alanının bölgesi dışındaki içeriği görüntülemek için geleneksel kaydırmayı kullanan bir çözüm sağlar.  
  
 Belge biçimleri ve sunum seçenekleri hakkında daha fazla bilgi için bkz. [WPF Içindeki belgeler](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Nasıl yapılır: kaydırma Görüntüleyicisi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF'deki Belgeler](../advanced/documents-in-wpf.md)
- [ScrollBar Stilleri ve Şablonları](scrollbar-styles-and-templates.md)
- [Denetimler](../advanced/optimizing-performance-controls.md)
