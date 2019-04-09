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
ms.openlocfilehash: f55862722c6062c5353fc3b1ab8569d4759ac342
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157293"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="f174c-102">Desteklenen UI Otomasyon Denetim Düzenlerini Alma</span><span class="sxs-lookup"><span data-stu-id="f174c-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="f174c-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f174c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f174c-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f174c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f174c-105">Bu konuda, Denetim düzeni nesnelerden alma işlemi gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f174c-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="f174c-106">Tüm denetim düzenleri elde</span><span class="sxs-lookup"><span data-stu-id="f174c-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="f174c-107">Alma <xref:System.Windows.Automation.AutomationElement> , Denetim desenleri ilgilendiğiniz.</span><span class="sxs-lookup"><span data-stu-id="f174c-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="f174c-108">Çağrı <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> öğesinden tüm denetim desenlerini alma için.</span><span class="sxs-lookup"><span data-stu-id="f174c-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f174c-109">Bir istemci değil kullanmanızı önemle tavsiye edilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="f174c-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="f174c-110">Performans ciddi bir şekilde etkilenecek bu yöntem çağrısı <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> mevcut her denetim düzeni için dahili olarak.</span><span class="sxs-lookup"><span data-stu-id="f174c-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="f174c-111">Mümkünse, bir istemci çağırmalıdır <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ilgilendiğiniz anahtar desenleri için.</span><span class="sxs-lookup"><span data-stu-id="f174c-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="f174c-112">Bir özel denetim düzeni alın</span><span class="sxs-lookup"><span data-stu-id="f174c-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="f174c-113">Alma <xref:System.Windows.Automation.AutomationElement> , Denetim desenleri ilgilendiğiniz.</span><span class="sxs-lookup"><span data-stu-id="f174c-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="f174c-114">Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> sorgulamak için belirli bir desen.</span><span class="sxs-lookup"><span data-stu-id="f174c-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="f174c-115">Bu yöntemler benzerdir ancak deseni bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> özel durum harekete ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="f174c-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f174c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f174c-116">Example</span></span>  
 <span data-ttu-id="f174c-117">Aşağıdaki örnek alır bir <xref:System.Windows.Automation.AutomationElement> bir liste öğesi için ve edinir bir <xref:System.Windows.Automation.SelectionItemPattern> bu öğeden.</span><span class="sxs-lookup"><span data-stu-id="f174c-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="f174c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f174c-118">See also</span></span>

- [<span data-ttu-id="f174c-119">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="f174c-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
