---
title: "Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma"
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
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d5f393d376935f04459e2713e9658c80af6efa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Nasıl yapılır: DataTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek tarafından oluşturulan öğeleri bulmayı gösteren bir <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, var olan bir <xref:System.Windows.Controls.ListBox> bağlı bazı [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri:  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> Aşağıdaki kullanan <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Almak istiyorsanız <xref:System.Windows.Controls.TextBlock> tarafından oluşturulan öğeyi <xref:System.Windows.DataTemplate> belirli bir <xref:System.Windows.Controls.ListBoxItem>, almanız gereken <xref:System.Windows.Controls.ListBoxItem>, bulma <xref:System.Windows.Controls.ContentPresenter> içindeki <xref:System.Windows.Controls.ListBoxItem>ve ardından arama <xref:System.Windows.FrameworkTemplate.FindName%2A> üzerinde <xref:System.Windows.DataTemplate> ayarlı üzerinde <xref:System.Windows.Controls.ContentPresenter>. Aşağıdaki örnekte bu adımların nasıl gerçekleştirileceğini gösterir. Tanıtım amacıyla, bu örnek metin gösteren bir ileti kutusu içeriğini oluşturur <xref:System.Windows.DataTemplate>-oluşturulan metin bloğunun.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Aşağıdaki uygulamasıdır `FindVisualChild`, kullanan <xref:System.Windows.Media.VisualTreeHelper> yöntemleri:  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Bul ControlTemplate oluşturulan öğeleri](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML ad kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
