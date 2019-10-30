---
title: 'Nasıl yapılır: Bir WDP Görüntüsünü Kodlama ve Kodunu Çözme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WDP encoding [WPF]
- WDP decoding [WPF]
- encoding image formats [WPF]
- decoding WDP images [WPF]
- decoding image formats [WPF]
- encoding WDP images [WPF]
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
ms.openlocfilehash: 8c5c312c7e58d48a865e493c38c3defd3f5f3d1d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040771"
---
# <a name="how-to-encode-and-decode-a-wdp-image"></a>Nasıl yapılır: Bir WDP Görüntüsünü Kodlama ve Kodunu Çözme
Aşağıdaki örneklerde, belirli <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> ve <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> nesneleri kullanılarak bir Microsoft Windows Media fotoğraf görüntüsünün kodunu çözme ve kodlama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir <xref:System.Uri><xref:System.Windows.Media.Imaging.WmpBitmapDecoder> kullanarak bir Windows Media fotoğraf görüntüsünün kodunu nasıl çözebileceğinizi gösterir.  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir <xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>kullanarak Windows Media fotoğraf görüntüsüne nasıl kodlanacağını göstermektedir.  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntülemeye Genel Bakış](imaging-overview.md)
