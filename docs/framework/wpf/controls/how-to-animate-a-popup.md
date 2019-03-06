---
title: 'Nasıl yapılır: Açılan Pencereye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: ed5edf298e59d6a9adddc03fc21de1900c7ee8e9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372847"
---
# <a name="how-to-animate-a-popup"></a>Nasıl yapılır: Açılan Pencereye Animasyon Ekleme
Bu örnek animasyon uygulamak için iki yolunu gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Primitives.PopupAnimation> bir değere <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, hangi nedenleri <xref:System.Windows.Controls.Primitives.Popup> göründüğünde "açma için".  
  
 Döndürmek için <xref:System.Windows.Controls.Primitives.Popup>, bu örnekte atar bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği <xref:System.Windows.Controls.Canvas>, alt öğesi olan <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Örnek dönüştürme düzgün çalışması ayarlamanız gerekir <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini `true`. Ayrıca, <xref:System.Windows.FrameworkElement.Margin%2A> üzerinde <xref:System.Windows.Controls.Canvas> içerik için yeterli alan belirtmelidir <xref:System.Windows.Controls.Primitives.Popup> döndürmek için.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 Aşağıdaki örnekte gösterildiği nasıl bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gerçekleşen olay olduğunda bir <xref:System.Windows.Controls.Button> tıklandığında Tetikleyicileri <xref:System.Windows.Media.Animation.Storyboard> animasyon başlar.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [Nasıl Yapılır Konuları](popup-how-to-topics.md)
- [Açılan Pencereye Genel Bakış](popup-overview.md)
