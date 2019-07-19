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
ms.openlocfilehash: 7d3520a1b1913fe68fedb0ea9d76cc138ed661c4
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331723"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a>Nasıl yapılır: Bir BMP Görüntüsünü Kodlama ve Kodunu Çözme
Aşağıdaki örneklerde, belirli <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> ve <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> nesneleri kullanarak bir bit eşlem (BMP) görüntüsünün kodunu çözme ve kodlama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, ' <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> <xref:System.Uri>den ' a kullanarak bir BMP görüntüsünün kodunu nasıl çözebileceğinizi gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>kullanarak bir BMP görüntüsüne nasıl kodlanacağını gösterir.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntülemeye Genel Bakış](imaging-overview.md)
