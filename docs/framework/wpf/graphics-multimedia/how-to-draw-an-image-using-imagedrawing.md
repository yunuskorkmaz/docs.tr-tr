---
title: 'Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 2c7771f841fb3b600d4790eb4d484b0a09c45dd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.ImageDrawing> resim çizmek için. Bir <xref:System.Windows.Media.ImageDrawing> görüntü etkinleştirir bir <xref:System.Windows.Media.ImageSource> ile bir <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, veya <xref:System.Windows.Media.Visual>. Resim çizmek için oluşturduğunuz bir <xref:System.Windows.Media.ImageDrawing> ve kendi <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özellikleri. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Özelliği çizmek için resmi belirtir ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özelliği, her görüntü boyutunu ve konumunu belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dört kullanarak bileşik çizim oluşturur <xref:System.Windows.Media.ImageDrawing> nesneleri. Bu örnek, aşağıdaki resimde üretir:  
  
 ![Çeşitli DrawingImage nesneleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Dört ImageDrawing nesnesi  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Bir görüntü dosyası olmadan görüntülemek için basit bir yol gösteren bir örnek için <xref:System.Windows.Media.ImageDrawing>, bkz: [resim öğesi kullanma](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze Özniteliği](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
