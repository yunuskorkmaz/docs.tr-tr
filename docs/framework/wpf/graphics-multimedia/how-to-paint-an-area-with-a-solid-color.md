---
title: 'Nasıl yapılır: Düz Renk ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086851"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Nasıl yapılır: Düz Renk ile bir Alanı Boyama
Düz renk ile bir alanı boyama için önceden tanımlanmış sistem fırça gibi kullanabilirsiniz <xref:System.Windows.Media.Brushes.Red%2A> veya <xref:System.Windows.Media.Brushes.Blue%2A>, ya da yeni bir oluşturabilirsiniz <xref:System.Windows.Media.SolidColorBrush> ve açıklayan kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> alfa, kırmızı, yeşil ve mavi değerleri kullanarak. XAML içinde onaltılık gösterim kullanarak da düz renk ile bir alanı boyama.  
  
 Aşağıdaki örnekler boyamak için her tekniğin kullanan bir <xref:System.Windows.Shapes.Rectangle> mavi.  
  
## <a name="example"></a>Örnek  
 **Önceden tanımlanmış bir fırça kullanma**  
  
 Aşağıdaki örnekte önceden tanımlanmış bir fırçanın kullanan <xref:System.Windows.Media.Brushes.Blue%2A> mavi bir dikdörtgen boyamak için.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Onaltılık gösterim kullanılarak**  
  
 Sonraki örnek, mavi bir dikdörtgen boyamak için 8 basamaklı onaltılık gösterim kullanır.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB değerlerini kullanma**  
  
 Sonraki örnek, oluşturur bir <xref:System.Windows.Media.SolidColorBrush> ve açıklar, <xref:System.Windows.Media.SolidColorBrush.Color%2A> ARGB kullanarak mavi renk için değerler.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Renk açıklayan diğer yolları için bkz. <xref:System.Windows.Media.Color> yapısı.  
  
 **İlgili Konular**  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.SolidColorBrush> ve diğer örnekler [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md) genel bakış.  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.SolidColorBrush> sınıfı. Tam bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brushes>
