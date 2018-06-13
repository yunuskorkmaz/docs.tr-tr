---
title: 'Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562296"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="81d66-102">Nasıl yapılır: Çizimi Görüntü Kaynağı Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="81d66-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="81d66-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.Drawing> olarak <xref:System.Windows.Controls.Image.Source%2A> için bir <xref:System.Windows.Controls.Image> denetim.</span><span class="sxs-lookup"><span data-stu-id="81d66-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="81d66-104">Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanın bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve ayarlayın <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizime özelliği.</span><span class="sxs-lookup"><span data-stu-id="81d66-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81d66-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="81d66-105">Example</span></span>  
 <span data-ttu-id="81d66-106">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingImage> ve bir <xref:System.Windows.Controls.Image> denetiminin görüntülemek için bir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="81d66-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="81d66-107">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="81d66-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="81d66-108">![İki elips GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="81d66-108">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="81d66-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="81d66-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="81d66-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81d66-110">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="81d66-111">ImageDrawing Kullanarak Görüntü Çizme</span><span class="sxs-lookup"><span data-stu-id="81d66-111">Draw an Image Using ImageDrawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [<span data-ttu-id="81d66-112">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="81d66-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="81d66-113">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="81d66-113">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="81d66-114">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="81d66-114">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
