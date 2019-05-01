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
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001006"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="ca156-102">Nasıl yapılır: Tuval Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="ca156-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="ca156-103">Bu örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ca156-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca156-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca156-104">Example</span></span>  
 <span data-ttu-id="ca156-105">Aşağıdaki örnek iki açıkça konumlandırır <xref:System.Windows.Controls.TextBlock> kullanarak öğeleri <xref:System.Windows.Controls.Canvas.SetTop%2A> ve <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemlerinin <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ca156-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ca156-106">Bu örnek ayrıca atar bir <xref:System.Windows.Controls.Control.Background%2A> rengini `LightSteelBlue` için <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ca156-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca156-107">Kullanırken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] konuma <xref:System.Windows.Controls.TextBlock> öğeleri kullanırsınız <xref:System.Windows.Controls.Canvas.Top%2A> ve <xref:System.Windows.Controls.Canvas.Left%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ca156-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ca156-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca156-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="ca156-109">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ca156-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="ca156-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ca156-110">How-to Topics</span></span>](canvas-how-to-topics.md)
