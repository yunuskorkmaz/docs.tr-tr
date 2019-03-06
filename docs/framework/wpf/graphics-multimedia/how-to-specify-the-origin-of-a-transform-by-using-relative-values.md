---
title: 'Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: bdcc17e2d9bf68170c10dd8e35670f3e072a527c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352574"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme
Bu örnekte kaynağını belirtmek için göreli değerlerini kullanmayı gösterir. bir <xref:System.Windows.UIElement.RenderTransform%2A> uygulanan bir <xref:System.Windows.FrameworkElement>.  
  
 Ne zaman döndürmek, ölçeklendirme veya eğriltme bir <xref:System.Windows.FrameworkElement> kullanarak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, varsayılan ayar, öğenin sol üst köşesine dönüşüm uygular. Döndürme, ölçeklendirme veya öğenin Merkezi'nden eğriltme istiyorsanız, öğenin merkezine dönüşümünün merkez ayarlayarak dengeleyebilirsiniz. Ancak, bu çözüm, öğe bildiğiniz gerektirir. Bir öğenin merkezine dönüşüm uygulamak için daha kolay bir yolu ayarlamaktır kendi <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğini (0,5, 0,5) dönüştürme üzerinde orta değer ayarlamak yerine.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde. Örnek bir merkezi belirtmediğinden düğmenin sol üst köşe olan noktası hakkında (0, 0) döndürür. <xref:System.Windows.Media.RotateTransform> Uygulanan <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.  
  
 Aşağıdaki örnek dönüştürme sonucu aşağıda gösterilmektedir.  
  
 ![RenderTransform kullanılarak dönüştürülen düğme](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
RenderTransform özelliği kullanılarak 45 derece saat yönünde bir döndürme  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Aşağıdaki örnekte de kullanan bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde; ancak bu örnekte ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> düğmenin (0,5, 0,5). Sonuç olarak, döndürme merkezini yerine sol üst köşesindeki düğmeyi uygulanır.  
  
 Aşağıdaki örnek dönüştürme sonucu aşağıda gösterilmektedir.  
  
 ![Dönüştürülen ortasından düğme](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
RenderTransform özelliği RenderTransformOrigin'i ile kullanarak 45 derece döndürme (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Dönüştürme hakkında daha fazla bilgi için <xref:System.Windows.FrameworkElement> nesneleri bkz [dönüştüren genel bakış](transforms-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Transform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
