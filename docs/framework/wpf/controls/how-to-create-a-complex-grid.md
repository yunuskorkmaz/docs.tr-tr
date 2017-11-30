---
title: "Nasıl yapılır: Karmaşık Kılavuz Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c0008a7379feefd9b3fe719f85b3205a72fb51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-complex-grid"></a>Nasıl yapılır: Karmaşık Kılavuz Oluşturma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Grid> aylık takvim gibi görünen bir düzen oluşturmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanarak sekiz sıra ve sekiz sütun tanımlar <xref:System.Windows.Controls.RowDefinition> ve <xref:System.Windows.Controls.ColumnDefinition> sınıfları. Kullandığı <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> ile birlikte ekli özelliklerini, <xref:System.Windows.Shapes.Rectangle> çeşitli sütunları ve satırları arka dolgu öğeleri. Bu tasarım, birden fazla öğe her hücresinde olabileceğinden bir <xref:System.Windows.Controls.Grid>, ilkesine birbirinden <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Documents.Table>.  
  
 Örnek dikey gradyanlar kullanır <xref:System.Windows.Shapes.Shape.Fill%2A> görsel sunumu ve takvimin okunabilirliğini artırmak için satırlar ve sütunlar. Biçimlendirilmiş <xref:System.Windows.Controls.TextBlock> öğeleri tarih ve haftanın günleri temsil eder. <xref:System.Windows.Controls.TextBlock>öğeleri kesinlikle yerleştirilir kendi hücrelerde kullanarak <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ve uygulama için stil içinde tanımlanan hizalama özelliklerini.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Boyama düz renklerle ve gradyan genel bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tablo genel bakış](../../../../docs/framework/wpf/advanced/table-overview.md)
