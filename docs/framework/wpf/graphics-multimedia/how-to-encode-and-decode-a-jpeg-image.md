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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373796"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="eac3f-102">Nasıl yapılır: Kodlama ve kodunu çözme JPEG resmi</span><span class="sxs-lookup"><span data-stu-id="eac3f-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="eac3f-103">Aşağıdaki örnekler kullanarak belirli bir JPEG görüntüsünü kodlama ve kodunu çözme nasıl <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> ve <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="eac3f-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="eac3f-104">Örnek - bir JPEG görüntüsünü kodunu çözme</span><span class="sxs-lookup"><span data-stu-id="eac3f-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="eac3f-105">Bu örnek, bir JPEG görüntüsünü kullanarak kodu çözülecek gösterilmiştir bir <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> gelen bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="eac3f-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="eac3f-106">Örnek - bir JPEG görüntüsünü kodlama</span><span class="sxs-lookup"><span data-stu-id="eac3f-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="eac3f-107">Bu örnek nasıl kodlanacağını gösterir bir <xref:System.Windows.Media.Imaging.BitmapSource> bir JPEG görüntüsünü kullanarak bir <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="eac3f-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="eac3f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eac3f-108">See also</span></span>

- [<span data-ttu-id="eac3f-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eac3f-109">Imaging Overview</span></span>](imaging-overview.md)
