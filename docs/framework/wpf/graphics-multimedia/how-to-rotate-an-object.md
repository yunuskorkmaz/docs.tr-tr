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
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112069"
---
# <a name="how-to-rotate-an-object"></a>Nasıl yapılır: Nesne Döndürme
Bu örnek, bir nesnenin nasıl döndürüldüğünü gösterir. Örnek önce bir <xref:System.Windows.Media.RotateTransform> oluşturur ve sonra <xref:System.Windows.Media.RotateTransform.Angle%2A> derece olarak belirtir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Polyline> nesneyi sol üst köşesinde 45 derece döndürür.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 Nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> döndürüldettiği noktayı belirtin. <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterY%2A> Bu merkez noktası dönüştürülen öğenin koordinat alanında ifade edilir. Varsayılan olarak, döndürme (0,0), dönüştürmek için nesnenin sol üst köşesi olan uygulanır.  
  
 Sonraki örnek, nesneyi <xref:System.Windows.Shapes.Polyline> saat yönünde 45 derece olarak nokta (25,50) döndürür.  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Aşağıdaki resimde iki nesneye a <xref:System.Windows.Media.Transform> uygulamanın sonuçları gösterilmektedir.  
  
 ![Farklı merkez noktaları ile 45 derece rotasyonlar](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Farklı dönme merkezlerinden 45 derece dönen iki nesne  
  
 Önceki <xref:System.Windows.Shapes.Polyline> örneklerde bir <xref:System.Windows.UIElement>. Bir <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> <xref:System.Windows.UIElement>özelliğine a uyguladığınız zaman, öğeye uyguladığınız her <xref:System.Windows.Media.Transform> bir kaynak için bir kaynak belirtmek için <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliği kullanabilirsiniz. Özellik <xref:System.Windows.UIElement.RenderTransformOrigin%2A> göreli koordinatlar kullandığından, boyutunu bilmeseniz bile öğenin merkezine dönüşüm uygulayabilirsiniz. Daha fazla bilgi ve örnek için bkz. [Göreli Değerleri Kullanarak Dönüşümün Kaynağını Belirtin.](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)  
  
 Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Nasıl Dır Konular](transformations-how-to-topics.md)
