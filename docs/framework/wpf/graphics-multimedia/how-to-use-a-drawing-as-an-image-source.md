---
title: 'Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769360"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Drawing> olarak <xref:System.Windows.Controls.Image.Source%2A> için bir <xref:System.Windows.Controls.Image> denetimi. Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanmak bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizim özelliğini.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> görüntülemek üzere bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek aşağıdaki çıktıyı üretir:  
  
 ![GeometryDrawing iki elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable.Freeze%2A>
- [ImageDrawing Kullanarak Görüntü Çizme](how-to-draw-an-image-using-imagedrawing.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze Özniteliği](../advanced/presentationoptions-freeze-attribute.md)
