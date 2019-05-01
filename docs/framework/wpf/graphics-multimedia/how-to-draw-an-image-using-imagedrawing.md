---
title: 'Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947611"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.ImageDrawing> bir görüntü çizin. Bir <xref:System.Windows.Media.ImageDrawing> görüntü sağlar bir <xref:System.Windows.Media.ImageSource> ile bir <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, veya <xref:System.Windows.Media.Visual>. Resim çizmek için oluşturduğunuz bir <xref:System.Windows.Media.ImageDrawing> ve kendi <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özellikleri. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Özellik çizmek için görüntüyü belirtir ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özelliği, her bir görüntü boyutunu ve konumunu belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dört kullanarak bileşik çizim oluşturur <xref:System.Windows.Media.ImageDrawing> nesneleri. Bu örnek, aşağıdaki görüntüde üretir:  
  
 ![Çeşitli DrawingImage nesneleri](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Dört ImageDrawing nesneleri  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Görüntü dosyası olmadan görüntülemek için basit bir yol gösteren bir örnek için <xref:System.Windows.Media.ImageDrawing>, bkz: [görüntü öğesi kullanma](../controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze Özniteliği](../advanced/presentationoptions-freeze-attribute.md)
