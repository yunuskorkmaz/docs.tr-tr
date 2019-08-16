---
title: 'Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545296"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="0c296-102">Nasıl yapılır: Görüntü Dosyası İçine Bir Görseli Kodlama</span><span class="sxs-lookup"><span data-stu-id="0c296-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="0c296-103">Bu örnek <xref:System.Windows.Media.Imaging.RenderTargetBitmap> , ve ' i <xref:System.Windows.Media.Imaging.PngBitmapEncoder>kullanarak <xref:System.Windows.Media.Visual> bir nesnenin görüntü dosyasına nasıl kodlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c296-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c296-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c296-104">Example</span></span>  
 <span data-ttu-id="0c296-105">, <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.FormattedText> Kullanılarak oluşturulur<xref:System.Windows.Media.Imaging.RenderTargetBitmap>ve ' a işlenir. <xref:System.Windows.Media.Imaging.BitmapImage></span><span class="sxs-lookup"><span data-stu-id="0c296-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="0c296-106">İşlenmiş bit eşlem daha sonra yeni bir taşınabilir ağ <xref:System.Windows.Media.Imaging.BitmapFrame> grafikleri (png) dosyası <xref:System.Windows.Media.Imaging.PngBitmapEncoder> oluşturmak üzere öğesine eklenen bir oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c296-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new Portable Network Graphics (PNG) file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="0c296-107">Bu örnekte kullanılmıştır, ancak türetilmiş <xref:System.Windows.Media.Imaging.BitmapEncoder> nesnelerden herhangi biri görüntü dosyasını oluşturmak için kullanılmış olabilir. <xref:System.Windows.Media.Imaging.PngBitmapEncoder></span><span class="sxs-lookup"><span data-stu-id="0c296-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c296-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c296-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="0c296-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c296-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="0c296-110">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c296-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="0c296-111">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c296-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
