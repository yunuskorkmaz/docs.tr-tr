---
title: 'Nasıl yapılır: Nesne Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: 7eb562d81bdd8c9187672b31ed08ed6ac27da41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561956"
---
# <a name="how-to-rotate-an-object"></a>Nasıl yapılır: Nesne Döndürme
Bu örnek bir nesnenin nasıl döndürüleceğini gösterir. Örnek ilk oluşturur bir <xref:System.Windows.Media.RotateTransform> ve ardından belirtir, <xref:System.Windows.Media.RotateTransform.Angle%2A> derece cinsinden.  
  
 Aşağıdaki örnek döndüğü bir <xref:System.Windows.Shapes.Polyline> , sol üst köşesindeki 45 derece nesne.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> nesne döndürüldüğü noktasını belirtin. Bu merkez nokta dönüştürülen öğenin koordinat ifade edilir. Varsayılan olarak, döndürme (0,0), sol üst köşesindeki dönüştürmek için nesnenin olduğu uygulanır.  
  
 Sonraki örnek döndüğü bir <xref:System.Windows.Shapes.Polyline> (25,50) noktasına saat yönünde 45 dereceyi nesne.  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Aşağıdaki çizimde uygulama sonuçlarını gösterir bir <xref:System.Windows.Media.Transform> iki nesne için.  
  
 ![farklı merkez nokta 45 derece döndürmeler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dönme 45 derece farklı döndürmek iki nesne merkezleri  
  
 <xref:System.Windows.Shapes.Polyline> Önceki örneklerde olduğu bir <xref:System.Windows.UIElement>. Uyguladığınızda bir <xref:System.Windows.Media.Transform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği bir <xref:System.Windows.UIElement>, kullanabileceğiniz <xref:System.Windows.UIElement.RenderTransformOrigin%2A> noktanız için bir kaynak belirtmek üzere özelliğini her <xref:System.Windows.Media.Transform> öğesine uyguladığınız. Çünkü <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği kullanan koordinatlara göre boyutuna bilmiyorsanız bile öğenin merkezine dönüşüm uygulayabilirsiniz. Daha fazla bilgi ve bir örnek için bkz: [bir dönüşüm tarafından göreli değerlerini kullanarak kaynağını belirtmek](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
