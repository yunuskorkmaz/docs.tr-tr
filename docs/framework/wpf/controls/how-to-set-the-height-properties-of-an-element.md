---
title: "Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama"
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
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ae66e60375cfbc45a4f1e8834b6420bc5c0b70a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama
## <a name="example"></a>Örnek  
 Bu örnek görsel olarak işleme davranışı dört yüksekliği ile ilgili özelliklerin arasındaki farklar gösterilmektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Sınıfı, bir öğenin yüksekliği özelliklerini tanımlayan dört özelliği sunar. Bu dört özellikleri çakışabilir ve bunu yaptıklarında, önceliklidir değeri şu şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinHeight%2A> değer önceliklidir <xref:System.Windows.FrameworkElement.MaxHeight%2A> sırayla önceliklidir değeri <xref:System.Windows.FrameworkElement.Height%2A> değeri. Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualHeight%2A>salt okunurdur ve gerçek yükseklik düzen işlemine ile etkileşim tarafından belirlendiği şekilde bildirir.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler çizin bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) bir alt öğesi olarak <xref:System.Windows.Controls.Canvas>. Yükseklik özelliklerini değiştirebilirsiniz bir <xref:System.Windows.Shapes.Rectangle> bir dizi kullanarak <xref:System.Windows.Controls.ListBox> özellik değerlerini temsil eden öğeleri <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, ve <xref:System.Windows.FrameworkElement.Height%2A>. Bu şekilde, her özelliğin önceliği görsel olarak görüntülenir.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Aşağıdaki arka plan kodu örnekleri olayları işlemek, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayını başlatır. Her işleyici girdisinden alan <xref:System.Windows.Controls.ListBox>, değer olarak ayrıştırır bir <xref:System.Double>ve değeri belirtilen yükseklik ilgili özellik için geçerlidir. Yükseklik değerleri de bir dizeye dönüştürülür ve çeşitli yazılmış <xref:System.Windows.Controls.TextBlock> öğelerine (Bu öğelerin tanımları seçilen XAML'de gösterilmez).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Tam bir örnek için bkz: [yükseklik özellikleri örneği](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Bir öğenin genişlik özelliklerini ayarlama](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Yükseklik özellikleri örneği](http://go.microsoft.com/fwlink/?LinkID=159993)
