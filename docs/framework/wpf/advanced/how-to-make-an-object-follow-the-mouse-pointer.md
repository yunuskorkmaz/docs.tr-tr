---
title: "Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma"
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
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1991d2a4b43c679fe7e30f633742e01e281e19b3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="76c41-102">Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76c41-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="76c41-103">Bu örnek, fare işaretçisini ekrandaki getirdiğinde bir nesnenin boyutlarını değiştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76c41-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="76c41-104">Örnek içeren bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturur dosya [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve olay işleyicisi oluşturan bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="76c41-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c41-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="76c41-105">Example</span></span>  
 <span data-ttu-id="76c41-106">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Shapes.Ellipse> içine bir <xref:System.Windows.Controls.StackPanel>ve için olay işleyicisini ekler <xref:System.Windows.UIElement.MouseMove> olay.</span><span class="sxs-lookup"><span data-stu-id="76c41-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="76c41-107">Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.MouseMove> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="76c41-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="76c41-108">Ne zaman fare işaretçisi hareket yüksekliğini ve genişliğini <xref:System.Windows.Shapes.Ellipse> artırılır ve azaltılır.</span><span class="sxs-lookup"><span data-stu-id="76c41-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="76c41-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76c41-109">See Also</span></span>  
 [<span data-ttu-id="76c41-110">Giriş genel bakış</span><span class="sxs-lookup"><span data-stu-id="76c41-110">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
