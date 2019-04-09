---
title: 'Nasıl yapılır: Bir TIFF Görüntüsünü Kodlama ve Kodunu Çözme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
ms.openlocfilehash: 0b2b638d3aa81e48a1378794435d59da1b323aa2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107438"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="5321d-102">Nasıl yapılır: Bir TIFF Görüntüsünü Kodlama ve Kodunu Çözme</span><span class="sxs-lookup"><span data-stu-id="5321d-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="5321d-103">Aşağıdaki örnekler nasıl kodlanacağını ve bir [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] belirli kullanarak görüntü <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> ve <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5321d-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5321d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5321d-104">Example</span></span>  
 <span data-ttu-id="5321d-105">Bu örnek nasıl çözüleceğini gösteren bir [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> gelen bir <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="5321d-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="5321d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5321d-106">Example</span></span>  
 <span data-ttu-id="5321d-107">Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> içine bir [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="5321d-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5321d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5321d-108">See also</span></span>

- [<span data-ttu-id="5321d-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5321d-109">Imaging Overview</span></span>](imaging-overview.md)
