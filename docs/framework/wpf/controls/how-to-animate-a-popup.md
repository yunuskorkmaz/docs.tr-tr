---
title: "Nasıl yapılır: Açılan Pencereye Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 276c1a54cfdddcde84c0702f4e84f1dc6174bbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-popup"></a>Nasıl yapılır: Açılan Pencereye Animasyon Ekleme
Bu örnek, animasyon için iki yol gösterir. bir <xref:System.Windows.Controls.Primitives.Popup> denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Primitives.PopupAnimation> değerini özelliğine <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, hangi nedenler <xref:System.Windows.Controls.Primitives.Popup> görüntülendiğinde "bileşenini için".  
  
 Döndürmek için <xref:System.Windows.Controls.Primitives.Popup>, bu örnek atar bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği <xref:System.Windows.Controls.Canvas>, alt öğesi olan olduğu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Dönüştürme düzgün çalışması örnek ayarlamalısınız <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğine `true`. Ayrıca, <xref:System.Windows.FrameworkElement.Margin%2A> üzerinde <xref:System.Windows.Controls.Canvas> içerik için yeterli alan belirtmelidir <xref:System.Windows.Controls.Primitives.Popup> döndürmek için.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 Aşağıdaki örnekte gösterildiği nasıl bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> oluşur olay olduğunda bir <xref:System.Windows.Controls.Button> tıklandığında, Tetikleyicileri <xref:System.Windows.Media.Animation.Storyboard> animasyonu başlatır.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Açılan genel bakış](../../../../docs/framework/wpf/controls/popup-overview.md)
