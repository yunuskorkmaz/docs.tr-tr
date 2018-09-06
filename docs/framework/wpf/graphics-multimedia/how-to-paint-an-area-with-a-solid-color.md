---
title: 'Nasıl yapılır: Düz Renk ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 017c685139979ec3aa411be6e6b5fdf0e91657de
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799232"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Nasıl yapılır: Düz Renk ile bir Alanı Boyama
Düz renk ile bir alanı boyama için önceden tanımlanmış sistem fırça gibi kullanabilirsiniz <xref:System.Windows.Media.Brushes.Red%2A> veya <xref:System.Windows.Media.Brushes.Blue%2A>, ya da yeni bir oluşturabilirsiniz <xref:System.Windows.Media.SolidColorBrush> ve açıklayan kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> alfa, kırmızı, yeşil ve mavi değerleri kullanarak. XAML içinde onaltılık gösterim kullanarak da düz renk ile bir alanı boyama.  
  
 Aşağıdaki örnekler boyamak için her tekniğin kullanan bir <xref:System.Windows.Shapes.Rectangle> mavi.  
  
## <a name="example"></a>Örnek  
 **Önceden tanımlanmış bir fırça kullanma**  
  
 Aşağıdaki örnekte önceden tanımlanmış bir fırçanın kullanan <xref:System.Windows.Media.Brushes.Blue%2A> mavi bir dikdörtgen boyamak için.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Onaltılık gösterim kullanılarak**  
  
 Sonraki örnek, mavi bir dikdörtgen boyamak için 8 basamaklı onaltılık gösterim kullanır.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB değerlerini kullanma**  
  
 Sonraki örnek, oluşturur bir <xref:System.Windows.Media.SolidColorBrush> ve açıklar, <xref:System.Windows.Media.SolidColorBrush.Color%2A> ARGB kullanarak mavi renk için değerler.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Renk açıklayan diğer yolları için bkz. <xref:System.Windows.Media.Color> yapısı.  
  
 **İlgili Konular**  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.SolidColorBrush> ve diğer örnekler [düz renkler ve gradyanlar genel bakış boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) genel bakış.  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.SolidColorBrush> sınıfı. Tam bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Brushes>
