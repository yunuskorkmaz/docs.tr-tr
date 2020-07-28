---
title: UI Otomasyon Öğesini Taşıma
description: UI Otomasyonu öğesinin belirtilen ekran konumuna nasıl taşınacağını gösteren örnek koda bakın. Windowdeseni ve TransformPattern Denetim desenlerini kullanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 4c8bec4e6d7a241588a3ab261cb80ce9ac242024
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166145"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="2fa37-104">UI Otomasyon Öğesini Taşıma</span><span class="sxs-lookup"><span data-stu-id="2fa37-104">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="2fa37-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="2fa37-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2fa37-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2fa37-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2fa37-107">Bu örnek, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin belirtilen ekran konumuna nasıl taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fa37-107">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fa37-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2fa37-108">Example</span></span>  
 <span data-ttu-id="2fa37-109">Aşağıdaki örnek, <xref:System.Windows.Automation.WindowPattern> <xref:System.Windows.Automation.TransformPattern> bir Win32 hedef uygulamasını programlama yoluyla ayrık ekran konumlarına taşımak ve izlemek için ve denetim desenlerini kullanır <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent> .</span><span class="sxs-lookup"><span data-stu-id="2fa37-109">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a Win32 target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="2fa37-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fa37-110">See also</span></span>

- [<span data-ttu-id="2fa37-111">Windowmodel örneği</span><span class="sxs-lookup"><span data-stu-id="2fa37-111">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
