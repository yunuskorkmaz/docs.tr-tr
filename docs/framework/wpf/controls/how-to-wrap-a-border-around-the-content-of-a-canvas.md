---
title: "Nasıl yapılır: Tuval İçeriği Çevresinde Kenarlığı Kaydırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Canvas
- controls [WPF], Border
- Canvas control [WPF], wrapping with Border
- Border control [WPF], wrapping Canvas
ms.assetid: caf0404f-f4e7-484f-9928-5dae1238d8ef
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbcc13512427d02867a50b17aeb75180ede28f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-wrap-a-border-around-the-content-of-a-canvas"></a><span data-ttu-id="ed4a2-102">Nasıl yapılır: Tuval İçeriği Çevresinde Kenarlığı Kaydırma</span><span class="sxs-lookup"><span data-stu-id="ed4a2-102">How to: Wrap a Border Around the Content of a Canvas</span></span>
<span data-ttu-id="ed4a2-103">Bu örnek nasıl kaydırılacağını gösterir bir <xref:System.Windows.Controls.Canvas> öğesi ile bir <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="ed4a2-103">This example shows how to wrap a <xref:System.Windows.Controls.Canvas> element with a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed4a2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed4a2-104">Example</span></span>  
 <span data-ttu-id="ed4a2-105">Aşağıdaki örnekte nasıl görüntüleneceğini gösterir `Hello World!` içinde bir <xref:System.Windows.Controls.Canvas> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ed4a2-105">The following example shows how to display `Hello World!` inside a <xref:System.Windows.Controls.Canvas> element.</span></span> <span data-ttu-id="ed4a2-106"><xref:System.Windows.Controls.Canvas> Öğesi ile kaydırılır bir <xref:System.Windows.Controls.Border> öğesi böylece öğeyi kenarlık özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed4a2-106">The <xref:System.Windows.Controls.Canvas> element is wrapped by a <xref:System.Windows.Controls.Border> element so that a border outlines the element.</span></span>  
  
 [!code-xaml[CanvasHelloWorldBorder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasHelloWorldBorder/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ed4a2-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed4a2-107">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="ed4a2-108">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed4a2-108">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
