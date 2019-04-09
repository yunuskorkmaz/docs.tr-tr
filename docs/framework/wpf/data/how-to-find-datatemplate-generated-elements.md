---
title: 'Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: de5a4937feabdb4486d9dcf9d5e5bfddd2356690
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089192"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek tarafından oluşturulan öğeleri bulma işlemini gösterir. bir <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir <xref:System.Windows.Controls.ListBox> bağlı bazı [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> Aşağıdaki kullanan <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Almak istiyorsanız <xref:System.Windows.Controls.TextBlock> öğesi tarafından oluşturulan <xref:System.Windows.DataTemplate> belirli bir <xref:System.Windows.Controls.ListBoxItem>, almanız gereken <xref:System.Windows.Controls.ListBoxItem>, bulma <xref:System.Windows.Controls.ContentPresenter> içindeki <xref:System.Windows.Controls.ListBoxItem>ve sonra çağrı <xref:System.Windows.FrameworkTemplate.FindName%2A> üzerinde <xref:System.Windows.DataTemplate> ayarlı üzerinde <xref:System.Windows.Controls.ContentPresenter>. Aşağıdaki örnek, bu adımların nasıl gerçekleştirileceğini gösterir. Tanıtım amacıyla, bu örnek metni gösteren bir ileti kutusu içeriği oluşturur <xref:System.Windows.DataTemplate>-metin bloğu oluşturulur.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Aşağıdaki uygulamasıdır `FindVisualChild`, kullanan <xref:System.Windows.Media.VisualTreeHelper> yöntemleri:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../controls/how-to-find-controltemplate-generated-elements.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [WPF XAML Ad Kapsamları](../advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../advanced/trees-in-wpf.md)
