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
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362870"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="bf0c4-102">Nasıl yapılır: Bir Görselden Bit Eşlem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf0c4-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="bf0c4-103">Bu örnek, bir bit eşlem nasıl oluşturabileceğinizi gösterir. bir <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="bf0c4-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="bf0c4-104">A <xref:System.Windows.Media.DrawingVisual> ile işlenen <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="bf0c4-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="bf0c4-105"><xref:System.Windows.Media.Visual> Ardından işlenen <xref:System.Windows.Media.Imaging.RenderTargetBitmap> verilen metnin bir bit eşlem oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bf0c4-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0c4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf0c4-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="bf0c4-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf0c4-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="bf0c4-108">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bf0c4-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="bf0c4-109">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bf0c4-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="bf0c4-110">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bf0c4-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
