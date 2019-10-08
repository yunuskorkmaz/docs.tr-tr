---
title: 'Nasıl yapılır: bir nesnenin fare Işaretçisini Izlemesini sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005073"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a><span data-ttu-id="0949c-102">Nasıl yapılır: bir nesnenin fare Işaretçisini Izlemesini sağlama</span><span class="sxs-lookup"><span data-stu-id="0949c-102">How to: Make an Object Follow the Mouse Pointer</span></span>
<span data-ttu-id="0949c-103">Bu örnek, fare işaretçisi ekranda taşırken bir nesnenin boyutlarının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0949c-103">This example shows how to change the dimensions of an object when the mouse pointer moves on the screen.</span></span>  
  
 <span data-ttu-id="0949c-104">Örnek, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' i ve olay işleyicisini oluşturan arka plan kod dosyasını oluşturan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="0949c-104">The example includes an [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] and a code-behind file that creates the event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0949c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0949c-105">Example</span></span>  
 <span data-ttu-id="0949c-106">Aşağıdaki XAML, <xref:System.Windows.Controls.StackPanel> içindeki bir <xref:System.Windows.Shapes.Ellipse> ' den oluşan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' ı oluşturur ve <xref:System.Windows.UIElement.MouseMove> olayına yönelik olay işleyicisini ekler.</span><span class="sxs-lookup"><span data-stu-id="0949c-106">The following XAML creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], which consists of an <xref:System.Windows.Shapes.Ellipse> inside of a <xref:System.Windows.Controls.StackPanel>, and attaches the event handler for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 <span data-ttu-id="0949c-107">Aşağıdaki kod arkasında <xref:System.Windows.UIElement.MouseMove> olay işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0949c-107">The following code behind creates the <xref:System.Windows.UIElement.MouseMove> event handler.</span></span>  <span data-ttu-id="0949c-108">Fare işaretçisi taşırken, <xref:System.Windows.Shapes.Ellipse> ' ın yüksekliği ve genişliği artar ve azalır.</span><span class="sxs-lookup"><span data-stu-id="0949c-108">When the mouse pointer moves, the height and the width of the <xref:System.Windows.Shapes.Ellipse> are increased and decreased.</span></span>  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a><span data-ttu-id="0949c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0949c-109">See also</span></span>

- [<span data-ttu-id="0949c-110">Girişe genel bakış</span><span class="sxs-lookup"><span data-stu-id="0949c-110">Input Overview</span></span>](input-overview.md)
