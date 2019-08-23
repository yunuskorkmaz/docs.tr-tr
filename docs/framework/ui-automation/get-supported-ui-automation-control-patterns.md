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
ms.openlocfilehash: 8987526a572d3c9a239885407c19bd1ad3674f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968989"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="4df2d-102">Desteklenen UI Otomasyon Denetim Düzenlerini Alma</span><span class="sxs-lookup"><span data-stu-id="4df2d-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="4df2d-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="4df2d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4df2d-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4df2d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4df2d-105">Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4df2d-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="4df2d-106">Tüm denetim desenlerini al</span><span class="sxs-lookup"><span data-stu-id="4df2d-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="4df2d-107"><xref:System.Windows.Automation.AutomationElement> İlgilendiğiniz denetim düzenlerini alın.</span><span class="sxs-lookup"><span data-stu-id="4df2d-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="4df2d-108">Öğesinden <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> tüm denetim desenlerini almak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="4df2d-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4df2d-109">İstemcinin kullanmamaları <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="4df2d-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="4df2d-110">Bu yöntem, var olan her denetim deseninin dahili <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> olarak çağırdığı için performans ciddi bir şekilde etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="4df2d-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="4df2d-111">Mümkünse, bir istemci ilgilendiğiniz önemli desenleri <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df2d-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="4df2d-112">Belirli bir denetim deseninin elde edileceği</span><span class="sxs-lookup"><span data-stu-id="4df2d-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="4df2d-113"><xref:System.Windows.Automation.AutomationElement> İlgilendiğiniz denetim düzenlerini alın.</span><span class="sxs-lookup"><span data-stu-id="4df2d-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="4df2d-114">Belirli <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> model için bir çağrı yapın veya sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="4df2d-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="4df2d-115">Bu yöntemler benzerdir, ancak model bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="4df2d-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df2d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4df2d-116">Example</span></span>  
 <span data-ttu-id="4df2d-117">Aşağıdaki örnek bir liste öğesi <xref:System.Windows.Automation.AutomationElement> için alır ve bu öğeden bir <xref:System.Windows.Automation.SelectionItemPattern> alır.</span><span class="sxs-lookup"><span data-stu-id="4df2d-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="4df2d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df2d-118">See also</span></span>

- [<span data-ttu-id="4df2d-119">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="4df2d-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
