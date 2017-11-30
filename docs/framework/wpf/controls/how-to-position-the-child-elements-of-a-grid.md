---
title: "Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma"
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
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dbe0bcb5d3c46edcb97410e00832f1b9d6205b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma
Bu örnekte get ve set üzerinde tanımlanan yöntemlerinin nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir üst tanımlar <xref:System.Windows.Controls.Grid> öğesi (`grid1`) üç sütun ve üç satır vardır. Bir alt <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) eklenen <xref:System.Windows.Controls.Grid> sütun konumu sıfır'da, konumu sıfır satır. <xref:System.Windows.Controls.Button>öğeleri yeniden konumlandırmak için çağrılan yöntemleri temsil eden <xref:System.Windows.Shapes.Rectangle> öğesi içinde <xref:System.Windows.Controls.Grid>. Bir kullanıcı bir düğmesine tıkladığında, ilgili yöntem etkinleştirilir.  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki arka plan kodu örnek yöntemleri işler, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları Yükselt. Bu yöntem çağrıları örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğelerini alma dizesi olarak yeni özellik değerlerinin çıktısını almak için yöntemleri.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
