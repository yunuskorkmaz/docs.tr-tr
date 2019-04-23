---
title: 'Nasıl yapılır: Bir Görselden Bit Eşlem Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189901"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Nasıl yapılır: Bir Görselden Bit Eşlem Oluşturma
Bu örnek, bir bit eşlem nasıl oluşturabileceğinizi gösterir. bir <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> ile işlenen <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Ardından işlenen <xref:System.Windows.Media.Imaging.RenderTargetBitmap> verilen metnin bir bit eşlem oluşturma.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingContext>
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [DrawingVisual Nesnelerini Kullanma](using-drawingvisual-objects.md)
