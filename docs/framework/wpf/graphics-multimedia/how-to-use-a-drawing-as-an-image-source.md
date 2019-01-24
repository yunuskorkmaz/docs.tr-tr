---
title: 'Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 01c8cd65128ce4e78dcbf9e38519091767b7ba2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499281"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Drawing> olarak <xref:System.Windows.Controls.Image.Source%2A> için bir <xref:System.Windows.Controls.Image> denetimi. Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanmak bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizim özelliğini.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> görüntülemek üzere bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek aşağıdaki çıktıyı üretir:  
  
 ![GeometryDrawing iki elips](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Freezable.Freeze%2A>
- [ImageDrawing Kullanarak Görüntü Çizme](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)
- [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze Özniteliği](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
