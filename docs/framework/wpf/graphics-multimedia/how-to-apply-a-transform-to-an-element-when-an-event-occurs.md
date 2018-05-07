---
title: 'Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: bd50b369666a1b65226b2b7eb6f3d866ec670bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama
Bu örnek nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.ScaleTransform> olay oluştuğunda. Burada gösterilen Dönüşümlerin diğer türleri uygulamak için kullandığınız aynı kavramdır. Dönüşümlerin kullanılabilir türleri hakkında daha fazla bilgi için bkz: <xref:System.Windows.Media.Transform> sınıfı veya [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 Bu iki yoldan biriyle bir öğe için bir dönüşüm uygulayabilirsiniz:  
  
-   Bunu yaparsanız *değil* dönüşümü düzenini etkileyen, kullanmak istediğiniz <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği.  
  
-   Düzen etkilemek için dönüştürme istiyorsanız kullanın <xref:System.Windows.FrameworkElement.LayoutTransform%2A> öğesi özelliği.  
  
 Aşağıdaki örnek uygular bir <xref:System.Windows.Media.ScaleTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> düğmesinin özelliği. Fare düğmesini hareket ettiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliklerini <xref:System.Windows.Media.ScaleTransform> ayarlanır `2`, düğme daha büyük hale gelmesine neden olur. Fare düğmesini devre dışı taşındığında <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ayarlanır `1`, özgün durumuna döndürmek için düğmesine neden olur.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
