---
title: Desteklenen UI Otomasyon Denetim Düzenlerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435644"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="800bb-102">Desteklenen UI Otomasyon Denetim Düzenlerini Alma</span><span class="sxs-lookup"><span data-stu-id="800bb-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="800bb-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="800bb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="800bb-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="800bb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="800bb-105">Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="800bb-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="800bb-106">Tüm denetim desenlerini al</span><span class="sxs-lookup"><span data-stu-id="800bb-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="800bb-107">Denetim desenlerini ilgilendiğiniz <xref:System.Windows.Automation.AutomationElement> alın.</span><span class="sxs-lookup"><span data-stu-id="800bb-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="800bb-108">Öğeden tüm denetim desenlerini almak için <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="800bb-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="800bb-109">İstemcinin <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>kullanmamaları önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="800bb-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="800bb-110">Bu yöntem, var olan her denetim deseninin dahili <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırdığı için performans ciddi bir şekilde etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="800bb-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="800bb-111">Mümkünse, bir istemci ilgilendiğiniz önemli desenler için <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="800bb-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="800bb-112">Belirli bir denetim deseninin elde edileceği</span><span class="sxs-lookup"><span data-stu-id="800bb-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="800bb-113">Denetim desenlerini ilgilendiğiniz <xref:System.Windows.Automation.AutomationElement> alın.</span><span class="sxs-lookup"><span data-stu-id="800bb-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="800bb-114">Belirli bir kalıbı sorgulamak için <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="800bb-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="800bb-115">Bu yöntemler benzerdir, ancak model bulunmazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="800bb-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="800bb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="800bb-116">Example</span></span>  
 <span data-ttu-id="800bb-117">Aşağıdaki örnek, bir liste öğesi için bir <xref:System.Windows.Automation.AutomationElement> alır ve bu öğeden bir <xref:System.Windows.Automation.SelectionItemPattern> edinir.</span><span class="sxs-lookup"><span data-stu-id="800bb-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="800bb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="800bb-118">See also</span></span>

- [<span data-ttu-id="800bb-119">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="800bb-119">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
