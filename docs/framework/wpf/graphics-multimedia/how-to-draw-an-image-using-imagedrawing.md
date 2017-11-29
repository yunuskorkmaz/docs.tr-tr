---
title: "Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d975d33bb3c102e5294d78dc76d8136ab521953
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="1d72a-102">Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme</span><span class="sxs-lookup"><span data-stu-id="1d72a-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="1d72a-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.ImageDrawing> resim çizmek için.</span><span class="sxs-lookup"><span data-stu-id="1d72a-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="1d72a-104">Bir <xref:System.Windows.Media.ImageDrawing> görüntü etkinleştirir bir <xref:System.Windows.Media.ImageSource> ile bir <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, veya <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="1d72a-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="1d72a-105">Resim çizmek için oluşturduğunuz bir <xref:System.Windows.Media.ImageDrawing> ve kendi <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1d72a-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="1d72a-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Özelliği çizmek için resmi belirtir ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özelliği, her görüntü boyutunu ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d72a-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d72a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d72a-107">Example</span></span>  
 <span data-ttu-id="1d72a-108">Aşağıdaki örnek, dört kullanarak bileşik çizim oluşturur <xref:System.Windows.Media.ImageDrawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1d72a-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="1d72a-109">Bu örnek, aşağıdaki resimde üretir:</span><span class="sxs-lookup"><span data-stu-id="1d72a-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="1d72a-110">![Çeşitli DrawingImage nesneleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="1d72a-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="1d72a-111">Dört ImageDrawing nesnesi</span><span class="sxs-lookup"><span data-stu-id="1d72a-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="1d72a-112">Bir görüntü dosyası olmadan görüntülemek için basit bir yol gösteren bir örnek için <xref:System.Windows.Media.ImageDrawing>, bkz: [resim öğesi kullanma](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="1d72a-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d72a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d72a-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="1d72a-114">Çizim nesnelerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1d72a-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="1d72a-115">Freezable nesnelere genel bakış</span><span class="sxs-lookup"><span data-stu-id="1d72a-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="1d72a-116">PresentationOptions: Freeze özniteliği</span><span class="sxs-lookup"><span data-stu-id="1d72a-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
