---
title: "Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0a1ff9de1f5ddfdabbf7af7fef5f78046c14f8ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama
Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Visual> kullanarak bir görüntü dosyası içine nesne bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.DrawingVisual> Kullanılarak oluşturulan bir <xref:System.Windows.Media.Imaging.BitmapImage> ve <xref:System.Windows.Media.FormattedText> için işlenen bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. İşlenen bit eşlem sonra oluşturmak için kullanılan bir <xref:System.Windows.Media.Imaging.BitmapFrame> için eklenen <xref:System.Windows.Media.Imaging.PngBitmapEncoder> yeni [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] dosya.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> Bu örnek ancak herhangi bir türetilmiş kullanılan <xref:System.Windows.Media.Imaging.BitmapEncoder> nesneleri kullanılabilirdi görüntü dosyası oluşturmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingContext>  
 [Görüntü oluşturmaya genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [DrawingVisual nesnelerini kullanma](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
