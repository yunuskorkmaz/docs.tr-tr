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
ms.openlocfilehash: 4fbb0931ee7d17d4b3264de512353dc75caf070d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543569"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="7d360-102">Nasıl yapılır: Görsele Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="7d360-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="7d360-103">Aşağıdaki örnekte nasıl metne çizileceğini gösterir bir <xref:System.Windows.Media.DrawingVisual> kullanarak bir <xref:System.Windows.Media.DrawingContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7d360-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="7d360-104">Çizim Bağlamı çağrılarak döndürülür <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi bir <xref:System.Windows.Media.DrawingVisual> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7d360-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="7d360-105">Grafikler ve metin çizim bağlamına çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d360-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="7d360-106">Metin çizme bağlamına çizmek için kullanma <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemi bir <xref:System.Windows.Media.DrawingContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7d360-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="7d360-107">Çizim bağlamına çizim içeriği işiniz bittiğinde, çağrı <xref:System.Windows.Media.DrawingContext.Close%2A> çizim bağlamı kapatmak ve içeriği kalıcı hale getirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7d360-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d360-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d360-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="7d360-109">Önceki kod örneğinde ayıklandığı tam kod örnek için bkz [Test kullanarak isabet sınaması örneği isabet](http://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="7d360-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
