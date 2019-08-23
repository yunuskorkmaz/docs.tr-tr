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
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964230"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="f03fa-102">Nasıl yapılır: Tuval Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="f03fa-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="f03fa-103">Bu örnek, <xref:System.Windows.Controls.Canvas>bir örneğinin nasıl oluşturulacağını ve kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f03fa-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f03fa-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03fa-104">Example</span></span>  
 <span data-ttu-id="f03fa-105">Aşağıdaki <xref:System.Windows.Controls.TextBlock> örnek, <xref:System.Windows.Controls.Canvas.SetTop%2A> ve <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemlerini kullanarakikiöğeyiaçıkçakonumlandırır.<xref:System.Windows.Controls.Canvas></span><span class="sxs-lookup"><span data-stu-id="f03fa-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="f03fa-106">Örnek, <xref:System.Windows.Controls.Control.Background%2A> `LightSteelBlue` 'abir<xref:System.Windows.Controls.Canvas>rengi de atar.</span><span class="sxs-lookup"><span data-stu-id="f03fa-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f03fa-107">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Öğeleri konumlandırmak <xref:System.Windows.Controls.TextBlock> için kullandığınızda, <xref:System.Windows.Controls.Canvas.Top%2A> ve <xref:System.Windows.Controls.Canvas.Left%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f03fa-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f03fa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03fa-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="f03fa-109">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f03fa-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="f03fa-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f03fa-110">How-to Topics</span></span>](canvas-how-to-topics.md)
