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
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646427"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek, bir <xref:System.Windows.DataTemplate>. tarafından oluşturulan öğeleri nasıl bulabileceğinizi gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bazı <xref:System.Windows.Controls.ListBox> XML verilerine bağlı bir tane vardır:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Aşağıdakileri <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>kullanır:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Belirli bir öğe <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.DataTemplate> tarafından oluşturulan eleman <xref:System.Windows.Controls.ListBoxItem>almak istiyorsanız , <xref:System.Windows.Controls.ListBoxItem>almak gerekir <xref:System.Windows.Controls.ContentPresenter> , <xref:System.Windows.Controls.ListBoxItem>içinde bulmak <xref:System.Windows.FrameworkTemplate.FindName%2A> , <xref:System.Windows.DataTemplate> ve sonra <xref:System.Windows.Controls.ContentPresenter>bu ayarlanır . Aşağıdaki örnek, bu adımların nasıl gerçekleştirilir gösteriş yapılacağını gösterir. Bu örnek, gösterim amacıyla oluşturulan metin bloğunun metin <xref:System.Windows.DataTemplate>içeriğini gösteren bir ileti kutusu oluşturur.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Yöntemleri kullanan `FindVisualChild` <xref:System.Windows.Media.VisualTreeHelper> uygulama aşağıdaki gibidir:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../controls/how-to-find-controltemplate-generated-elements.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML Ad Kapsamları](../advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../advanced/trees-in-wpf.md)
