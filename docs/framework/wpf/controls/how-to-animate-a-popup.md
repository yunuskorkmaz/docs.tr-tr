---
title: 'Nasıl yapılır: Açılan Pencereye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 05b84eea7fe983340ebb8c5cdb20ff39eb2f0858
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Açılan Pencereye Genel Bakış](../../../../docs/framework/wpf/controls/popup-overview.md)
