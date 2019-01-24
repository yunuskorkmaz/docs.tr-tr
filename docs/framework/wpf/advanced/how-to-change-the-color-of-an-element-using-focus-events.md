---
title: 'Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: ad5ba8490f4b98512d539f5ae9c72b03333aca69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547020"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="67e70-102">Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="67e70-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="67e70-103">Bu örnek, kazançlar ve odağından kullanarak öğenin rengini değiştirme gösterir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları.</span><span class="sxs-lookup"><span data-stu-id="67e70-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="67e70-104">Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="67e70-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e70-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="67e70-105">Example</span></span>  
 <span data-ttu-id="67e70-106">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] iki oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Button> nesneleri ve ekler için olay işleyicileri <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları <xref:System.Windows.Controls.Button> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="67e70-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="67e70-107">Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="67e70-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="67e70-108">Zaman <xref:System.Windows.Controls.Button> klavye odağı kazandığında <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> kırmızıya değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="67e70-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="67e70-109">Zaman <xref:System.Windows.Controls.Button> klavye odağından <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> beyaz olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="67e70-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="67e70-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e70-110">See also</span></span>
- [<span data-ttu-id="67e70-111">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67e70-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
