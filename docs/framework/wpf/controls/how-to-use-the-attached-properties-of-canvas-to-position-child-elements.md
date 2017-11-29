---
title: "Nasıl yapılır: Alt Öğeleri Konumlandırmak için Tuvalin Ekli Özelliklerini Kullanma"
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
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85ee852c868f26937494d5d340d2db4210224754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="4f87f-102">Nasıl yapılır: Alt Öğeleri Konumlandırmak için Tuvalin Ekli Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4f87f-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="4f87f-103">Bu örnek, iliştirilmiş özelliklerini kullanmak gösterilmiştir <xref:System.Windows.Controls.Canvas> alt öğeleri konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="4f87f-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f87f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f87f-104">Example</span></span>  
 <span data-ttu-id="4f87f-105">Aşağıdaki örnek, dört ekler <xref:System.Windows.Controls.Button> öğeler alt öğelerin üst öğesi olarak <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="4f87f-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="4f87f-106">Her alt öğe, farklı bir ekli özelliğini temsil eden <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, ve <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f87f-106">Each child element represents a distinct attached property of <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span> <span data-ttu-id="4f87f-107">Her <xref:System.Windows.Controls.Button> göre üst konumlandırılmış <xref:System.Windows.Controls.Canvas> ve atanan özellik değerine göre.</span><span class="sxs-lookup"><span data-stu-id="4f87f-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4f87f-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f87f-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="4f87f-109">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4f87f-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="4f87f-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="4f87f-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="4f87f-111">Ekli özellikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="4f87f-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
