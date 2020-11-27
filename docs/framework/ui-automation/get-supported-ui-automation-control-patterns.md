---
title: Desteklenen UI Otomasyon Denetim Düzenlerini Alma
description: UI Otomasyon öğelerinden desteklenen denetim deseninin nesnelerinin nasıl alınacağını gösteren bir örnek okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 68abe272e91c40932aba5bcf99394c4a8f815c53
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276457"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="c73c6-103">Desteklenen UI Otomasyon Denetim Düzenlerini Alma</span><span class="sxs-lookup"><span data-stu-id="c73c6-103">Get Supported UI Automation Control Patterns</span></span>

> [!NOTE]
> <span data-ttu-id="c73c6-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="c73c6-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c73c6-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c73c6-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c73c6-106">Bu konu, öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c73c6-106">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="c73c6-107">Tüm denetim desenlerini al</span><span class="sxs-lookup"><span data-stu-id="c73c6-107">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="c73c6-108"><xref:System.Windows.Automation.AutomationElement>İlgilendiğiniz denetim düzenlerini alın.</span><span class="sxs-lookup"><span data-stu-id="c73c6-108">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="c73c6-109"><xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>Öğesinden tüm denetim desenlerini almak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="c73c6-109">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c73c6-110">İstemcinin kullanmamaları önemle önerilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> .</span><span class="sxs-lookup"><span data-stu-id="c73c6-110">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="c73c6-111">Bu yöntem, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> var olan her denetim deseninin dahili olarak çağırdığı için performans ciddi bir şekilde etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="c73c6-111">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="c73c6-112">Mümkünse, bir istemci <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ilgilendiğiniz önemli desenleri çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c73c6-112">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="c73c6-113">Belirli bir denetim deseninin elde edileceği</span><span class="sxs-lookup"><span data-stu-id="c73c6-113">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="c73c6-114"><xref:System.Windows.Automation.AutomationElement>İlgilendiğiniz denetim düzenlerini alın.</span><span class="sxs-lookup"><span data-stu-id="c73c6-114">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="c73c6-115"><xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> Belirli bir model için bir çağrı yapın veya sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="c73c6-115">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="c73c6-116">Bu yöntemler benzerdir, ancak model bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="c73c6-116">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c73c6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="c73c6-117">Example</span></span>  

 <span data-ttu-id="c73c6-118">Aşağıdaki örnek bir <xref:System.Windows.Automation.AutomationElement> liste öğesi için alır ve bu öğeden bir alır <xref:System.Windows.Automation.SelectionItemPattern> .</span><span class="sxs-lookup"><span data-stu-id="c73c6-118">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="c73c6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c73c6-119">See also</span></span>

- [<span data-ttu-id="c73c6-120">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="c73c6-120">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
