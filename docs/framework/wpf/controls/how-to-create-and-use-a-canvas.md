---
title: "Nasıl yapılır: Tuval Oluşturma ve Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8925b9b6cd6cea1a29592f591f9c1c89d32d49e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="8f9f9-102">Nasıl yapılır: Tuval Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="8f9f9-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="8f9f9-103">Bu örnek nasıl oluşturulacağı ve bir örneğini kullanması gösterir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8f9f9-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f9f9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f9f9-104">Example</span></span>  
 <span data-ttu-id="8f9f9-105">Aşağıdaki örnekte iki açıkça konumlandırır <xref:System.Windows.Controls.TextBlock> kullanarak öğeleri <xref:System.Windows.Controls.Canvas.SetTop%2A> ve <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemlerini <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8f9f9-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="8f9f9-106">Bu örnek ayrıca atar bir <xref:System.Windows.Controls.Control.Background%2A> rengini `LightSteelBlue` için <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="8f9f9-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f9f9-107">Kullandığınızda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] konuma <xref:System.Windows.Controls.TextBlock> öğelerini kullanan <xref:System.Windows.Controls.Canvas.Top%2A> ve <xref:System.Windows.Controls.Canvas.Left%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="8f9f9-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8f9f9-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f9f9-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [<span data-ttu-id="8f9f9-109">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8f9f9-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="8f9f9-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8f9f9-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
