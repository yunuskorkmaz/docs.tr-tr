---
title: "Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d975d33bb3c102e5294d78dc76d8136ab521953
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions: Freeze özniteliği](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
