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
ms.openlocfilehash: ec509a03d95e5f72af0b1f362e253799b07edc1f
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671687"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="451c9-102">Nasıl yapılır: Bir GIF Görüntüsünü Kodlama ve Kodunu Çözme</span><span class="sxs-lookup"><span data-stu-id="451c9-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="451c9-103">Aşağıdaki örneklerde, belirli <xref:System.Windows.Media.Imaging.GifBitmapDecoder> ve <xref:System.Windows.Media.Imaging.GifBitmapEncoder> nesneleri kullanarak bir grafik değişim biçimi (GIF) görüntüsünün kodunu çözme ve kodlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="451c9-103">The following examples show how to decode and encode a Graphics Interchange Format (GIF) image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="451c9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="451c9-104">Example</span></span>  
 <span data-ttu-id="451c9-105">Bu örnek, <xref:System.Windows.Media.Imaging.GifBitmapDecoder> <xref:System.IO.FileStream>öğesinden bir GIF resminin kodunu nasıl çözebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="451c9-105">This example demonstrates how to decode a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="451c9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="451c9-106">Example</span></span>  
 <span data-ttu-id="451c9-107">Bu örnek, <xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.GifBitmapEncoder>kullanarak bir GIF resmine nasıl kodlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="451c9-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="451c9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="451c9-108">See also</span></span>

- [<span data-ttu-id="451c9-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="451c9-109">Imaging Overview</span></span>](imaging-overview.md)
