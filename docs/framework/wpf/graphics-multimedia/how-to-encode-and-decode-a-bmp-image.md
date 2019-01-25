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
ms.openlocfilehash: dfdadfb7175342199099a1549008197b8d42551c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530716"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a><span data-ttu-id="37f28-102">Nasıl yapılır: Bir BMP Görüntüsünü Kodlama ve Kodunu Çözme</span><span class="sxs-lookup"><span data-stu-id="37f28-102">How to: Encode and Decode a BMP Image</span></span>
<span data-ttu-id="37f28-103">Aşağıdaki örnekler nasıl kodlanacağını ve bir [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] belirli kullanarak görüntü <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> ve <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="37f28-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37f28-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="37f28-104">Example</span></span>  
 <span data-ttu-id="37f28-105">Bu örnek nasıl çözüleceğini gösteren bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> gelen bir <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="37f28-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="37f28-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="37f28-106">Example</span></span>  
 <span data-ttu-id="37f28-107">Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> içine bir [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="37f28-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] image using a <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="37f28-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37f28-108">See also</span></span>
- [<span data-ttu-id="37f28-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37f28-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
