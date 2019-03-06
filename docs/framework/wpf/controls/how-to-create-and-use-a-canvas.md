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
ms.openlocfilehash: 13ed32195621350284530da78544e026ed341658
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360387"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="99b15-102">Nasıl yapılır: Tuval Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="99b15-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="99b15-103">Bu örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="99b15-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99b15-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="99b15-104">Example</span></span>  
 <span data-ttu-id="99b15-105">Aşağıdaki örnek iki açıkça konumlandırır <xref:System.Windows.Controls.TextBlock> kullanarak öğeleri <xref:System.Windows.Controls.Canvas.SetTop%2A> ve <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemlerinin <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="99b15-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="99b15-106">Bu örnek ayrıca atar bir <xref:System.Windows.Controls.Control.Background%2A> rengini `LightSteelBlue` için <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="99b15-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b15-107">Kullanırken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] konuma <xref:System.Windows.Controls.TextBlock> öğeleri kullanırsınız <xref:System.Windows.Controls.Canvas.Top%2A> ve <xref:System.Windows.Controls.Canvas.Left%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="99b15-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="99b15-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99b15-108">See also</span></span>
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="99b15-109">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99b15-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="99b15-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="99b15-110">How-to Topics</span></span>](canvas-how-to-topics.md)
