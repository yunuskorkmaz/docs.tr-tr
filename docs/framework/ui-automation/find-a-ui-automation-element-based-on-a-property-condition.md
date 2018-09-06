---
title: Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4c4f14f79960b98618a4f6a3450b1e1a2c05f731
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786140"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="d704c-102">Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="d704c-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="d704c-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d704c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d704c-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d704c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d704c-105">Bu konu, bir öğenin içine nasıl gösteren kod örneği içerir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç tabanlı belirli bir özellik veya özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d704c-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d704c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d704c-106">Example</span></span>  
 <span data-ttu-id="d704c-107">Aşağıdaki örnekte, bir dizi özellik koşullarına belirtilir ilgilendiğiniz belirli bir öğenin (veya öğeleri) tanımlamak <xref:System.Windows.Automation.AutomationElement> ağaç.</span><span class="sxs-lookup"><span data-stu-id="d704c-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="d704c-108">Bir arama için tüm eşleşen öğeleri ile gerçekleştirilir <xref:System.Windows.Automation.AutomationElement.FindAll%2A> içeren bir dizi yöntem <xref:System.Windows.Automation.AndCondition> eşleşen öğe sayısını sınırlamak için boolean operations.</span><span class="sxs-lookup"><span data-stu-id="d704c-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d704c-109">Gelen ararken <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, yalnızca doğrudan alt öğeleri almak çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d704c-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="d704c-110">Alt öğeleri için arama, yüzlerce veya binlerce büyük olasılıkla bir yığın taşması ile elde edilen öğelerin bile aracılığıyla yineleme.</span><span class="sxs-lookup"><span data-stu-id="d704c-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="d704c-111">Daha düşük bir düzeyde belirli bir öğeyi edinme çalışıyorsanız, uygulama penceresinin veya daha düşük bir düzeyde bir kapsayıcı aramanızı başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d704c-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="d704c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d704c-112">See Also</span></span>  
 [<span data-ttu-id="d704c-113">InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="d704c-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="d704c-114">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="d704c-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="d704c-115">AutomationID Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d704c-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
