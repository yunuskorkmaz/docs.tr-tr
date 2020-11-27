---
title: TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme
description: Treedenetçisi sınıfını kullanarak UI Otomasyon öğeleri arasında nasıl gezinmeyi gösteren bir kod örneği görürsünüz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e102e6ce258bef06d1fb44decfa1a3a27384e0bc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261221"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="e9cab-103">TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme</span><span class="sxs-lookup"><span data-stu-id="e9cab-103">Navigate Among UI Automation Elements with TreeWalker</span></span>

> [!NOTE]
> <span data-ttu-id="e9cab-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="e9cab-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e9cab-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e9cab-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e9cab-106">Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , sınıfını kullanarak öğeler arasında gezinmeyi gösteren örnek kodu içerir <xref:System.Windows.Automation.TreeWalker> .</span><span class="sxs-lookup"><span data-stu-id="e9cab-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9cab-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9cab-107">Example</span></span>  

 <span data-ttu-id="e9cab-108">Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kök öğeyi veya masaüstünü bulana kadar ağacı ilerlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9cab-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="e9cab-109">Aşağıdaki öğesi, belirtilen öğenin ana penceresidir.</span><span class="sxs-lookup"><span data-stu-id="e9cab-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="e9cab-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9cab-110">Example</span></span>  

 <span data-ttu-id="e9cab-111">Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> <xref:System.Windows.Forms.TreeView> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim görünümündeki ve etkin olan öğelerin tüm alt ağacını gösteren bir oluşturmak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9cab-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="e9cab-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9cab-112">See also</span></span>

- [<span data-ttu-id="e9cab-113">UI Otomasyon Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="e9cab-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
