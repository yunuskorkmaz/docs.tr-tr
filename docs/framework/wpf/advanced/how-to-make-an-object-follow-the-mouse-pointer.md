---
title: 'Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: b9b13b4eec3e42744ba2be6031ec841fb5f215e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107321"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="2866c-102">Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2866c-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="2866c-103">Bu örnek, ekranda fare işaretçisi hareket ettirildiğinde nesnenin boyutunu değiştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="2866c-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="2866c-104">Örnek içeren bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan dosya [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve arka plan kod dosyası, olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2866c-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2866c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="2866c-105">Example</span></span>  
 <span data-ttu-id="2866c-106">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Shapes.Ellipse> içine bir <xref:System.Windows.Controls.StackPanel>ve olay işleyicisi ekler <xref:System.Windows.UIElement.MouseMove> olay.</span><span class="sxs-lookup"><span data-stu-id="2866c-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="2866c-107">Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.MouseMove> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2866c-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="2866c-108">Ne zaman fare işaretçisi hareket yüksekliğini ve genişliğini <xref:System.Windows.Shapes.Ellipse> artırılır ve azaltılır.</span><span class="sxs-lookup"><span data-stu-id="2866c-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="2866c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2866c-109">See also</span></span>

- [<span data-ttu-id="2866c-110">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2866c-110">Input Overview</span></span>](input-overview.md)
