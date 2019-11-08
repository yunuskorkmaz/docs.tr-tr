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
ms.openlocfilehash: 2cb3d73574cd207c0e06abe15f6a953a67cd5c78
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733434"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek, bir <xref:System.Windows.DataTemplate>tarafından oluşturulan öğelerin nasıl bulunacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bazı XML verilerine bağlanan bir <xref:System.Windows.Controls.ListBox> vardır:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> aşağıdaki <xref:System.Windows.DataTemplate>kullanır:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Belirli bir <xref:System.Windows.Controls.ListBoxItem><xref:System.Windows.DataTemplate> tarafından oluşturulan <xref:System.Windows.Controls.TextBlock> öğesini almak istiyorsanız, <xref:System.Windows.Controls.ListBoxItem>almanız, bu <xref:System.Windows.Controls.ContentPresenter> içindeki <xref:System.Windows.Controls.ListBoxItem>bulmanız ve ardından üzerinde ayarlanan <xref:System.Windows.FrameworkTemplate.FindName%2A> üzerinde <xref:System.Windows.DataTemplate> çağırmanız gerekir. Bu <xref:System.Windows.Controls.ContentPresenter>. Aşağıdaki örnek, bu adımların nasıl gerçekleştirileceğini gösterir. Tanıtım amacıyla bu örnek, <xref:System.Windows.DataTemplate>tarafından oluşturulan metin bloğunun metin içeriğini gösteren bir ileti kutusu oluşturur.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Aşağıda, <xref:System.Windows.Media.VisualTreeHelper> yöntemlerini kullanan `FindVisualChild`uygulamasıdır:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma](../controls/how-to-find-controltemplate-generated-elements.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML Ad Kapsamları](../advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../advanced/trees-in-wpf.md)
