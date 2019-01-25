---
title: 'Nasıl yapılır: Kodlama ve kodunu çözme JPEG resmi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: db42411f71e2934f3e5f86a06f434da220f1882e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603514"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a>Nasıl yapılır: Kodlama ve kodunu çözme JPEG resmi

Aşağıdaki örnekler kullanarak belirli bir JPEG görüntüsünü kodlama ve kodunu çözme nasıl <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> ve <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> nesneleri.  
  
## <a name="example---decode-a-jpeg-image"></a>Örnek - bir JPEG görüntüsünü kodunu çözme

Bu örnek, bir JPEG görüntüsünü kullanarak kodu çözülecek gösterilmiştir bir <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> gelen bir <xref:System.IO.FileStream>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a>Örnek - bir JPEG görüntüsünü kodlama

Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> bir JPEG görüntüsünü kullanarak bir <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
