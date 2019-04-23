---
title: 'Nasıl yapılır: Bir PNG Görüntüsünü Kodlama ve Kodunu Çözme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
ms.openlocfilehash: 46d4a7ffbfe7a6a620c26447cce30f3a0bd35adc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090861"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="bba7a-102">Nasıl yapılır: Bir PNG Görüntüsünü Kodlama ve Kodunu Çözme</span><span class="sxs-lookup"><span data-stu-id="bba7a-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="bba7a-103">Aşağıdaki örnekler nasıl kodlanacağını ve bir [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] belirli kullanarak görüntü <xref:System.Windows.Media.Imaging.PngBitmapDecoder> ve <xref:System.Windows.Media.Imaging.PngBitmapEncoder> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="bba7a-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba7a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bba7a-104">Example</span></span>  
 <span data-ttu-id="bba7a-105">Bu örnek nasıl çözüleceğini gösteren bir [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.PngBitmapDecoder> gelen bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="bba7a-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bba7a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bba7a-106">Example</span></span>  
 <span data-ttu-id="bba7a-107">Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> içine bir [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] kullanarak görüntü bir <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="bba7a-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bba7a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba7a-108">See also</span></span>

- [<span data-ttu-id="bba7a-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bba7a-109">Imaging Overview</span></span>](imaging-overview.md)
