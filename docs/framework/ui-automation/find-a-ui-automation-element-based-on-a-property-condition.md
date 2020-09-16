---
title: Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
description: Özellik koşulunu temel alan UI Otomasyonu öğesi bulun. Belirli bir özelliği veya özellikleri temel alan UI Otomasyon ağacı içindeki bir öğeyi bulun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 112f38d6bef726f92dbf13da70b88732929175dd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557690"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="f506c-104">Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="f506c-104">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="f506c-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="f506c-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f506c-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f506c-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f506c-107">Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] belirli bir özellik veya özelliklere göre ağaç içindeki bir öğenin nasıl bulunacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="f506c-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f506c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f506c-108">Example</span></span>  
 <span data-ttu-id="f506c-109">Aşağıdaki örnekte, ağaçta ilgilendiğiniz belirli bir öğeyi (veya öğeleri) tanımlayan bir özellik koşulları kümesi belirtilmiştir <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="f506c-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="f506c-110">Daha sonra eşleşen <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> öğelerin sayısını sınırlamak için bir dizi Boole işlemi içeren yöntemiyle, tüm eşleşen öğeler için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="f506c-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f506c-111">' Dan arama yaparken <xref:System.Windows.Automation.AutomationElement.RootElement%2A> , yalnızca doğrudan alt öğe edinmeyi denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f506c-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="f506c-112">Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f506c-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="f506c-113">Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f506c-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="f506c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f506c-114">See also</span></span>

- <span data-ttu-id="f506c-115">[Invokemodel ve ExpandCollapsePattern menü öğesi örneği](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f506c-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="f506c-116">UI Otomasyon Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="f506c-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="f506c-117">AutomationID Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f506c-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
