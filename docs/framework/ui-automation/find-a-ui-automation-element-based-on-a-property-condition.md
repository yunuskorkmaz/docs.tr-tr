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
ms.openlocfilehash: 24c236e3d577fd4c9844546b04eefeee9eaf1de8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965151"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="01f10-102">Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="01f10-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="01f10-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="01f10-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="01f10-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="01f10-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="01f10-105">Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] belirli bir özellik veya özelliklere göre ağaç içindeki bir öğenin nasıl bulunacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="01f10-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f10-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="01f10-106">Example</span></span>  
 <span data-ttu-id="01f10-107">Aşağıdaki örnekte, <xref:System.Windows.Automation.AutomationElement> ağaçta ilgilendiğiniz belirli bir öğeyi (veya öğeleri) tanımlayan bir özellik koşulları kümesi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01f10-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="01f10-108">Daha sonra eşleşen öğelerin sayısını sınırlamak için bir <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> dizi Boole işlemi içeren yöntemiyle, tüm eşleşen öğeler için arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="01f10-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01f10-109"><xref:System.Windows.Automation.AutomationElement.RootElement%2A>' Dan arama yaparken, yalnızca doğrudan alt öğe edinmeyi denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="01f10-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="01f10-110">Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="01f10-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="01f10-111">Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01f10-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="01f10-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f10-112">See also</span></span>

- <span data-ttu-id="01f10-113">[Invokemodel ve ExpandCollapsePattern menü öğesi örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="01f10-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="01f10-114">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="01f10-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
- [<span data-ttu-id="01f10-115">AutomationID Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="01f10-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
