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
ms.openlocfilehash: 0a0a2f2625901f7ee32ba9fe70e71681a1b9ccd3
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545281"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="3c267-102">Nasıl yapılır: Bir PNG Görüntüsünü Kodlama ve Kodunu Çözme</span><span class="sxs-lookup"><span data-stu-id="3c267-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="3c267-103">Aşağıdaki örneklerde, belirli <xref:System.Windows.Media.Imaging.PngBitmapDecoder> ve <xref:System.Windows.Media.Imaging.PngBitmapEncoder> nesneleri kullanarak Taşınabilir Ağ Grafikleri (png) görüntüsünün kodunu çözme ve kodlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c267-103">The following examples show how to decode and encode a Portable Network Graphics (PNG) image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c267-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c267-104">Example</span></span>  
 <span data-ttu-id="3c267-105">Bu örnek, bir ' <xref:System.Windows.Media.Imaging.PngBitmapDecoder> <xref:System.IO.FileStream>den ' a kullanarak bir PNG görüntüsünün kodunu nasıl çözebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c267-105">This example demonstrates how to decode a PNG image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3c267-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c267-106">Example</span></span>  
 <span data-ttu-id="3c267-107">Bu örnek, <xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.PngBitmapEncoder>kullanarak bir PNG görüntüsüne nasıl kodlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c267-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a PNG image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3c267-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c267-108">See also</span></span>

- [<span data-ttu-id="3c267-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c267-109">Imaging Overview</span></span>](imaging-overview.md)
