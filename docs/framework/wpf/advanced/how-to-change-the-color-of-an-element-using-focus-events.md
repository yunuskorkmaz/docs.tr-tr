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
ms.openlocfilehash: d8d8a3e8b24021cf8a5f916ce3f291a3b66d9411
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543120"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="9f92f-102">Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9f92f-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="9f92f-103">Bu örnek kazanır ve kullanarak odağı kaybettiğinde öğenin rengini değiştirmek nasıl gösterir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olaylar.</span><span class="sxs-lookup"><span data-stu-id="9f92f-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="9f92f-104">Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="9f92f-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f92f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f92f-105">Example</span></span>  
 <span data-ttu-id="9f92f-106">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] iki oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Button> nesneleri ve olay işleyicileri iliştirir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları <xref:System.Windows.Controls.Button> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9f92f-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="9f92f-107">Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="9f92f-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="9f92f-108">Zaman <xref:System.Windows.Controls.Button> kazancı klavye odağı <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> kırmızı değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9f92f-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="9f92f-109">Zaman <xref:System.Windows.Controls.Button> klavye odağı kaybettiğinde <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> beyaza geri değişir.</span><span class="sxs-lookup"><span data-stu-id="9f92f-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="9f92f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f92f-110">See Also</span></span>  
 [<span data-ttu-id="9f92f-111">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9f92f-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
