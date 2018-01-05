---
title: "Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d1d504ca056f35fe8716b299ec73f45648bb3d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="21d4c-102">Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="21d4c-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="21d4c-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="21d4c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="21d4c-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="21d4c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="21d4c-105">Bu konu, bir öğenin içine bulun gösteren kod örneği içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç dayalı belirli bir özellik veya özellikleri.</span><span class="sxs-lookup"><span data-stu-id="21d4c-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21d4c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="21d4c-106">Example</span></span>  
 <span data-ttu-id="21d4c-107">Aşağıdaki örnekte, bir dizi özellik koşulları belirtilir ilgi belirli bir öğenin (veya öğeleri) tanımlamak <xref:System.Windows.Automation.AutomationElement> ağacı.</span><span class="sxs-lookup"><span data-stu-id="21d4c-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="21d4c-108">İle eşleşen tüm öğeleri için bir arama sonra gerçekleştirilen <xref:System.Windows.Automation.AutomationElement.FindAll%2A> bir dizi içerir yöntemi <xref:System.Windows.Automation.AndCondition> eşleşen öğe sayısını sınırlamak için boolean işlemleri.</span><span class="sxs-lookup"><span data-stu-id="21d4c-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21d4c-109">Gelen ararken <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, sadece doğrudan alt edinmeye.</span><span class="sxs-lookup"><span data-stu-id="21d4c-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="21d4c-110">Alt öğeleri için bir arama yüzlerce veya binlerce büyük olasılıkla bir yığın taşması kaynaklanan öğelerinin bile yinelemek.</span><span class="sxs-lookup"><span data-stu-id="21d4c-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="21d4c-111">Belirli bir öğenin alt düzeyde edinme çalışıyorsanız, Uygulama penceresinden veya daha düşük düzeydeki bir kapsayıcı aramanızı başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21d4c-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="21d4c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21d4c-112">See Also</span></span>  
 [<span data-ttu-id="21d4c-113">InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="21d4c-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="21d4c-114">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="21d4c-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="21d4c-115">AutomationID Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="21d4c-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
