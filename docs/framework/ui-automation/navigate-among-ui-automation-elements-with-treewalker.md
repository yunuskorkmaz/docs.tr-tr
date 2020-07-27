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
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168014"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="36457-103">TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme</span><span class="sxs-lookup"><span data-stu-id="36457-103">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="36457-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="36457-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="36457-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="36457-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="36457-106">Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , sınıfını kullanarak öğeler arasında gezinmeyi gösteren örnek kodu içerir <xref:System.Windows.Automation.TreeWalker> .</span><span class="sxs-lookup"><span data-stu-id="36457-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36457-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="36457-107">Example</span></span>  
 <span data-ttu-id="36457-108">Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kök öğeyi veya masaüstünü bulana kadar ağacı ilerlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="36457-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="36457-109">Aşağıdaki öğesi, belirtilen öğenin ana penceresidir.</span><span class="sxs-lookup"><span data-stu-id="36457-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="36457-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="36457-110">Example</span></span>  
 <span data-ttu-id="36457-111">Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> <xref:System.Windows.Forms.TreeView> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim görünümündeki ve etkin olan öğelerin tüm alt ağacını gösteren bir oluşturmak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="36457-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="36457-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36457-112">See also</span></span>

- [<span data-ttu-id="36457-113">UI Otomasyon Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="36457-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
