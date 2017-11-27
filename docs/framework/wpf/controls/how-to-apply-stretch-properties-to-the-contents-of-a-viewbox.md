---
title: "Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama"
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
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6e93c744a8d7c294556e80f0ac4bf1f973ea5c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama
## <a name="example"></a>Örnek  
 Bu örnek değerini değiştirmek nasıl gösterir <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> ve <xref:System.Windows.Controls.Viewbox.Stretch%2A> özelliklerini bir <xref:System.Windows.Controls.Viewbox>.  
  
 İlk örnek kullanan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.Viewbox> öğesi. Atar bir <xref:System.Windows.FrameworkElement.MaxWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400. Örnek Yuvalar bir <xref:System.Windows.Controls.Image> öğesi içinde <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button>için özellik değerlerine karşılık gelen öğeler <xref:System.Windows.Controls.Viewbox.Stretch%2A> ve <xref:System.Windows.Controls.StretchDirection> sıralamaları iç içe uzatma davranışını <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki arka plan kodu dosya tanıtıcıları <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek tanımlar.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>
