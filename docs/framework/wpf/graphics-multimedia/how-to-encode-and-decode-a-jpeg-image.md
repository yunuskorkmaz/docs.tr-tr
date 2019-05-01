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
ms.openlocfilehash: 0f64ef8537f22ea996cbcf274885de1f3968267a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947517"
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

- [Görüntülemeye Genel Bakış](imaging-overview.md)
