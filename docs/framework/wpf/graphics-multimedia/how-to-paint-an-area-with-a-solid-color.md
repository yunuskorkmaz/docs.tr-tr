---
title: 'Nasıl yapılır: Düz Renk ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 7e8e3fa5a379f02c3bb126c17bbe37fc0f3d57cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561338"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Nasıl yapılır: Düz Renk ile bir Alanı Boyama
Düz renk ile alanı boyamak için önceden tanımlanmış sistem fırçası gibi kullanabilir <xref:System.Windows.Media.Brushes.Red%2A> veya <xref:System.Windows.Media.Brushes.Blue%2A>, ya da yeni bir oluşturabilirsiniz <xref:System.Windows.Media.SolidColorBrush> tanımlamak ve kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> alfa, kırmızı, yeşil ve mavi değerleri kullanarak. XAML'de, onaltılık gösterimde kullanarak da bir alanı düz renk ile Boyama.  
  
 Aşağıdaki örnekler boyamak için her bu teknikleri kullanan bir <xref:System.Windows.Shapes.Rectangle> mavi.  
  
## <a name="example"></a>Örnek  
 **Önceden tanımlanmış fırça kullanma**  
  
 Aşağıdaki örnekte önceden tanımlanmış fırça kullanır <xref:System.Windows.Media.Brushes.Blue%2A> dikdörtgen mavi boyamak için.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Onaltılık gösterim kullanılarak**  
  
 Sonraki örnek 8 basamaklı onaltılık gösterim dikdörtgen mavi boyamak için kullanır.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB değerleri kullanma**  
  
 Sonraki örnekte bir <xref:System.Windows.Media.SolidColorBrush> ve açıklar kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> değerlerini mavi renk için ARGB kullanarak.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Renk açıklayan diğer yolları için bkz: <xref:System.Windows.Media.Color> yapısı.  
  
 **İlgili Konular**  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.SolidColorBrush> ve ek örnekler için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) genel bakış.  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.SolidColorBrush> sınıfı. Tam bir örnek için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Brushes>
