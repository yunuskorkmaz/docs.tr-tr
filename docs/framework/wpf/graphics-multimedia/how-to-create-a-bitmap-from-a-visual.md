---
title: 'Nasıl yapılır: Bir Görselden Bit Eşlem Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 4735474d00712598cb5e41fad289e8f568d83a48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559772"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="b91af-102">Nasıl yapılır: Bir Görselden Bit Eşlem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b91af-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="b91af-103">Bu örnek, bir bit eşlem nasıl oluşturabileceğinizi gösterir bir <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="b91af-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="b91af-104">A <xref:System.Windows.Media.DrawingVisual> ile işlenen <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="b91af-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="b91af-105"><xref:System.Windows.Media.Visual> Sonra işlenen <xref:System.Windows.Media.Imaging.RenderTargetBitmap> verilen metni bir bit eşlem oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b91af-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b91af-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b91af-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="b91af-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b91af-107">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="b91af-108">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b91af-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="b91af-109">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b91af-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="b91af-110">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="b91af-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
