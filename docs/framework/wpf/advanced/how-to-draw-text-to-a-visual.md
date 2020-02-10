---
title: 'Nasıl yapılır: Görsele Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094559"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="ad326-102">Nasıl yapılır: Görsele Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="ad326-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="ad326-103">Aşağıdaki örnek, bir <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> nesnesi kullanarak nasıl metin çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad326-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="ad326-104">Bir çizim bağlamı, bir <xref:System.Windows.Media.DrawingVisual> nesnesinin <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi çağırarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ad326-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="ad326-105">Çizim bağlamına grafik ve metin çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad326-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="ad326-106">Çizim bağlamına metin çizmek için, bir <xref:System.Windows.Media.DrawingContext> nesnesinin <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad326-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="ad326-107">Çizim bağlamına içerik çizmeyi bitirdiğinizde çizim bağlamını kapatmak ve içeriği kalıcı hale getirmek için <xref:System.Windows.Media.DrawingContext.Close%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ad326-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad326-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad326-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="ad326-109">Yukarıdaki kod örneğinin ayıklandığı bütün kod örneği için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span><span class="sxs-lookup"><span data-stu-id="ad326-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span></span>
