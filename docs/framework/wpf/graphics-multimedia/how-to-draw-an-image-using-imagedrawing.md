---
title: 'Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100164"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="9829a-102">Nasıl yapılır: ImageDrawing Kullanarak Görüntü Çizme</span><span class="sxs-lookup"><span data-stu-id="9829a-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="9829a-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.ImageDrawing> bir görüntü çizin.</span><span class="sxs-lookup"><span data-stu-id="9829a-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="9829a-104">Bir <xref:System.Windows.Media.ImageDrawing> görüntü sağlar bir <xref:System.Windows.Media.ImageSource> ile bir <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, veya <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="9829a-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="9829a-105">Resim çizmek için oluşturduğunuz bir <xref:System.Windows.Media.ImageDrawing> ve kendi <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9829a-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="9829a-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Özellik çizmek için görüntüyü belirtir ve <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> özelliği, her bir görüntü boyutunu ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9829a-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9829a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9829a-107">Example</span></span>  
 <span data-ttu-id="9829a-108">Aşağıdaki örnek, dört kullanarak bileşik çizim oluşturur <xref:System.Windows.Media.ImageDrawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9829a-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="9829a-109">Bu örnek, aşağıdaki görüntüde üretir:</span><span class="sxs-lookup"><span data-stu-id="9829a-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="9829a-110">![Çeşitli DrawingImage nesneleri](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="9829a-110">![Several DrawingImage objects](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="9829a-111">Dört ImageDrawing nesneleri</span><span class="sxs-lookup"><span data-stu-id="9829a-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="9829a-112">Görüntü dosyası olmadan görüntülemek için basit bir yol gösteren bir örnek için <xref:System.Windows.Media.ImageDrawing>, bkz: [görüntü öğesi kullanma](../controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="9829a-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9829a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9829a-113">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [<span data-ttu-id="9829a-114">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9829a-114">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="9829a-115">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9829a-115">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="9829a-116">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="9829a-116">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
