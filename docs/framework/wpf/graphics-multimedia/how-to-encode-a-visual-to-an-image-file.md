---
title: 'Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545296"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama
Bu örnek <xref:System.Windows.Media.Imaging.RenderTargetBitmap> , ve ' i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>kullanarak <xref:System.Windows.Media.Visual> bir nesnenin görüntü dosyasına nasıl kodlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 , <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.FormattedText> Kullanılarak oluşturulur<xref:System.Windows.Media.Imaging.RenderTargetBitmap>ve ' a işlenir. <xref:System.Windows.Media.Imaging.BitmapImage> İşlenmiş bit eşlem daha sonra yeni bir taşınabilir ağ <xref:System.Windows.Media.Imaging.BitmapFrame> grafikleri (png) dosyası <xref:System.Windows.Media.Imaging.PngBitmapEncoder> oluşturmak üzere öğesine eklenen bir oluşturmak için kullanılır.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 Bu örnekte kullanılmıştır, ancak türetilmiş <xref:System.Windows.Media.Imaging.BitmapEncoder> nesnelerden herhangi biri görüntü dosyasını oluşturmak için kullanılmış olabilir. <xref:System.Windows.Media.Imaging.PngBitmapEncoder>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingContext>
- [Görüntülemeye Genel Bakış](imaging-overview.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [DrawingVisual Nesnelerini Kullanma](using-drawingvisual-objects.md)
