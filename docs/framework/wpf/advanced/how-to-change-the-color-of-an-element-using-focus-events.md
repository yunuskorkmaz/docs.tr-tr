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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004827"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="ecc3a-102">Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ecc3a-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="ecc3a-103">Bu örnek, <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olaylarını kullanarak odak kazanırsa ve kaybettiğinde bir öğenin renginin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="ecc3a-104">Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve arka plan kod dosyasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc3a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecc3a-105">Example</span></span>  
 <span data-ttu-id="ecc3a-106">Aşağıdaki XAML, iki <xref:System.Windows.Controls.Button> nesnesinden oluşan Kullanıcı arabirimini oluşturur ve <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olaylar için olay işleyicilerini <xref:System.Windows.Controls.Button> nesnelerine ekler.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="ecc3a-107">Aşağıdaki kod arkasında <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="ecc3a-108"><xref:System.Windows.Controls.Button> klavye odağı aldığında, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> kırmızı olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="ecc3a-109"><xref:System.Windows.Controls.Button> klavye odağını kaybettiğinde, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Control.Background%2A> yeniden beyaza dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="ecc3a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecc3a-110">See also</span></span>

- [<span data-ttu-id="ecc3a-111">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ecc3a-111">Input Overview</span></span>](input-overview.md)
