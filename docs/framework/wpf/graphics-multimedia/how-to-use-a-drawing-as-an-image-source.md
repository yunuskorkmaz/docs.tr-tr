---
title: 'Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097866"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="5ac7d-102">Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ac7d-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="5ac7d-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Drawing> olarak <xref:System.Windows.Controls.Image.Source%2A> için bir <xref:System.Windows.Controls.Image> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5ac7d-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="5ac7d-104">Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanmak bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizim özelliğini.</span><span class="sxs-lookup"><span data-stu-id="5ac7d-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ac7d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac7d-105">Example</span></span>  
 <span data-ttu-id="5ac7d-106">Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> görüntülemek üzere bir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="5ac7d-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="5ac7d-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5ac7d-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="5ac7d-108">![GeometryDrawing iki elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="5ac7d-108">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="5ac7d-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="5ac7d-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac7d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac7d-110">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="5ac7d-111">ImageDrawing Kullanarak Görüntü Çizme</span><span class="sxs-lookup"><span data-stu-id="5ac7d-111">Draw an Image Using ImageDrawing</span></span>](how-to-draw-an-image-using-imagedrawing.md)
- [<span data-ttu-id="5ac7d-112">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ac7d-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="5ac7d-113">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ac7d-113">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="5ac7d-114">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="5ac7d-114">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
