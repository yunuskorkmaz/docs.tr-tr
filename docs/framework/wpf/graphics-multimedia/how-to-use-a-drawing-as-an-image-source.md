---
title: "Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e100bc29afb17a37bc0c66621261347bea6d210
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.Drawing> olarak <xref:System.Windows.Controls.Image.Source%2A> için bir <xref:System.Windows.Controls.Image> denetim. Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanın bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve ayarlayın <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizime özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingImage> ve bir <xref:System.Windows.Controls.Image> denetiminin görüntülemek için bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek şu çıkışı üretir:  
  
 ![İki elips GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [ImageDrawing kullanarak resim çizme](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions: Freeze özniteliği](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
