---
title: 'Nasıl yapılır: Tuval Oluşturma ve Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: c3ddb5171ca8ded053d56fde26ab86ebc4ae5cb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552850"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="9fcb9-102">Nasıl yapılır: Tuval Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="9fcb9-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="9fcb9-103">Bu örnek nasıl oluşturulacağı ve bir örneğini kullanması gösterir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fcb9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fcb9-104">Example</span></span>  
 <span data-ttu-id="9fcb9-105">Aşağıdaki örnekte iki açıkça konumlandırır <xref:System.Windows.Controls.TextBlock> kullanarak öğeleri <xref:System.Windows.Controls.Canvas.SetTop%2A> ve <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemlerini <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="9fcb9-106">Bu örnek ayrıca atar bir <xref:System.Windows.Controls.Control.Background%2A> rengini `LightSteelBlue` için <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fcb9-107">Kullandığınızda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] konuma <xref:System.Windows.Controls.TextBlock> öğelerini kullanan <xref:System.Windows.Controls.Canvas.Top%2A> ve <xref:System.Windows.Controls.Canvas.Left%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9fcb9-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [<span data-ttu-id="9fcb9-109">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fcb9-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="9fcb9-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9fcb9-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
