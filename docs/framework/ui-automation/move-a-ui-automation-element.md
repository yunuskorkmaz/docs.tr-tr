---
title: UI Otomasyon Öğesini Taşıma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cb239adc6dfb11c83fb983a41ea40ad8bf714038
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562584"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="bbccc-102">UI Otomasyon Öğesini Taşıma</span><span class="sxs-lookup"><span data-stu-id="bbccc-102">Move a UI Automation Element</span></span>
> [!NOTE]
>  <span data-ttu-id="bbccc-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bbccc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bbccc-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bbccc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bbccc-105">Bu örnek nasıl taşınacağı gösterir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] belirtilen ekran konum öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbccc-105">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbccc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbccc-106">Example</span></span>  
 <span data-ttu-id="bbccc-107">Aşağıdaki örnekte <xref:System.Windows.Automation.WindowPattern> ve <xref:System.Windows.Automation.TransformPattern> denetim desenlerini program aracılığıyla taşıma bir [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] hedef uygulama ayrık ekran konumlarına ve izleme <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span><span class="sxs-lookup"><span data-stu-id="bbccc-107">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="bbccc-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbccc-108">See Also</span></span>  
 [<span data-ttu-id="bbccc-109">WindowPattern'ı örneği</span><span class="sxs-lookup"><span data-stu-id="bbccc-109">WindowPattern Sample</span></span>](https://msdn.microsoft.com/library/598b695c-8baf-406e-bbfb-2a1c7842a1de)
