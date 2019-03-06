---
title: 'Nasıl yapılır: Bir BMP Görüntüsünü Kodlama ve Kodunu Çözme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: 5aee77ab70c6a24846967b01bbb458ba4cdbe970
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379633"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a>Nasıl yapılır: Bir BMP Görüntüsünü Kodlama ve Kodunu Çözme
Aşağıdaki örnekler nasıl kodlanacağını ve bir [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] belirli kullanarak görüntü <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> ve <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> nesneleri.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl çözüleceğini gösteren bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> gelen bir <xref:System.Uri>.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> içine bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntülemeye Genel Bakış](imaging-overview.md)
