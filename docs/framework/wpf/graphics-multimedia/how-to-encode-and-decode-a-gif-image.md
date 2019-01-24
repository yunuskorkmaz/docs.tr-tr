---
title: 'Nasıl yapılır: Bir GIF Görüntüsünü Kodlama ve Kodunu Çözme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
ms.openlocfilehash: 9b13ac8021b6f2d25209a89ff2ff9b4bb7531ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562472"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a>Nasıl yapılır: Bir GIF Görüntüsünü Kodlama ve Kodunu Çözme
Aşağıdaki örnekler nasıl kodlanacağını ve bir [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] belirli kullanarak görüntü <xref:System.Windows.Media.Imaging.GifBitmapDecoder> ve <xref:System.Windows.Media.Imaging.GifBitmapEncoder> nesneleri.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl çözüleceğini gösteren bir [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.GifBitmapDecoder> gelen bir <xref:System.IO.FileStream>.  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> içine bir [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
