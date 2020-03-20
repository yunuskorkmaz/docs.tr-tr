---
title: 'Nasıl yapılır: Düz Renk ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849528"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Nasıl yapılır: Düz Renk ile bir Alanı Boyama
Bir <xref:System.Windows.Media.Brushes.Red%2A> alanı düz renkle boyamak için, <xref:System.Windows.Media.Brushes.Blue%2A>önceden tanımlanmış bir sistem fırçası kullanabilir <xref:System.Windows.Media.SolidColorBrush> veya yeni <xref:System.Windows.Media.SolidColorBrush.Color%2A> bir yeni oluşturabilir ve alfa, kırmızı, yeşil ve mavi değerleri kullanarak tanımlayabilirsiniz. XAML'de, heksidecimal gösterim kullanarak düz renkli bir alanı da boyayabilirsiniz.  
  
 Aşağıdaki örnekler, mavi boyamak <xref:System.Windows.Shapes.Rectangle> için bu tekniklerin her birini kullanır.  
  
## <a name="example"></a>Örnek  
 **Önceden Tanımlanmış Fırça Kullanma**  
  
 Aşağıdaki örnekte, dikdörtgen mavisini boyamak için önceden tanımlanmış fırça <xref:System.Windows.Media.Brushes.Blue%2A> kullanır.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Hexadecimal Gösterim kullanma**  
  
 Sonraki örnek, dikdörtgen mavisini boyamak için 8 basamaklı heksadedesmal gösterim kullanır.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB Değerlerini Kullanma**  
  
 Sonraki örnek bir <xref:System.Windows.Media.SolidColorBrush> oluşturur ve <xref:System.Windows.Media.SolidColorBrush.Color%2A> mavi renk için ARGB değerlerini kullanarak açıklar.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Rengi açıklamanın diğer yolları için <xref:System.Windows.Media.Color> yapıya bakın.  
  
 **İlgili Konular**  
  
 Hakkında <xref:System.Windows.Media.SolidColorBrush> daha fazla bilgi ve ek örnekler [için, Düz Renkler ve Degradelere Genel Bakış ile Resim](painting-with-solid-colors-and-gradients-overview.md) bölümüne bakın.  
  
 Bu kod örneği, <xref:System.Windows.Media.SolidColorBrush> sınıf için sağlanan daha büyük bir örneğin bir parçasıdır. Numunenin tamamı için [Fırçalar Örneğine](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brushes>
