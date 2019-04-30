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
ms.openlocfilehash: 973b9267eaef5d55176633ee80a1dc7f8b043909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698999"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama
Bu örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> bir olay gerçekleştiğinde. Burada gösterilen diğer tür dönüştürmeleri uygulamak için kullandığınız aynı kavramdır. Dönüşümlerin kullanılabilir türleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.Transform> sınıfı veya [dönüştüren genel bakış](transforms-overview.md).  
  
 Bu iki yöntemden biriyle öğeye dönüşüm uygulayabilirsiniz:  
  
- Bunu yaparsanız *değil* dönüşümü düzenini etkiler, kullanmak istediğiniz <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.  
  
- Düzen etkileyen dönüşüm istiyorsanız kullanın <xref:System.Windows.FrameworkElement.LayoutTransform%2A> öğesinin özelliği.  
  
 Aşağıdaki örnek geçerli bir <xref:System.Windows.Media.ScaleTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> düğmesinin özelliği. Düğme üzerinde fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliklerini <xref:System.Windows.Media.ScaleTransform> ayarlandığından `2`, düğmeyi daha büyük hale gelmesine neden olur. Düğmeyi, fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ayarlandığından `1`, özgün boyutuna döndürmek için düğmeyi neden olur.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
- [Yönlendirilmiş Olaylara Genel Bakış](../advanced/routed-events-overview.md)
