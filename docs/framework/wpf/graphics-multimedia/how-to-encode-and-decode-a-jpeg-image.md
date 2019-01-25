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
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="68f2c-102">Nasıl yapılır: Kodlama ve kodunu çözme JPEG resmi</span><span class="sxs-lookup"><span data-stu-id="68f2c-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="68f2c-103">Aşağıdaki örnekler kullanarak belirli bir JPEG görüntüsünü kodlama ve kodunu çözme nasıl <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> ve <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="68f2c-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="68f2c-104">Örnek - bir JPEG görüntüsünü kodunu çözme</span><span class="sxs-lookup"><span data-stu-id="68f2c-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="68f2c-105">Bu örnek, bir JPEG görüntüsünü kullanarak kodu çözülecek gösterilmiştir bir <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> gelen bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="68f2c-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="68f2c-106">Örnek - bir JPEG görüntüsünü kodlama</span><span class="sxs-lookup"><span data-stu-id="68f2c-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="68f2c-107">Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> bir JPEG görüntüsünü kullanarak bir <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="68f2c-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="68f2c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68f2c-108">See also</span></span>

- [<span data-ttu-id="68f2c-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="68f2c-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
