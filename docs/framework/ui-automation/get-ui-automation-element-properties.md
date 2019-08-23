---
title: UI Otomasyon Öğesi Özelliklerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968959"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="3ad07-102">UI Otomasyon Öğesi Özelliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="3ad07-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="3ad07-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="3ad07-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3ad07-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="3ad07-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3ad07-105">Bu konu, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin özelliklerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ad07-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="3ad07-106">Geçerli özellik değerini Al</span><span class="sxs-lookup"><span data-stu-id="3ad07-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="3ad07-107"><xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="3ad07-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="3ad07-108"><xref:System.Windows.Automation.AutomationElement.Current%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="3ad07-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="3ad07-109">Önbelleğe alınmış Özellik değeri alma</span><span class="sxs-lookup"><span data-stu-id="3ad07-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="3ad07-110"><xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="3ad07-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="3ad07-111">Özelliği içinde <xref:System.Windows.Automation.CacheRequest>belirtilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ad07-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="3ad07-112"><xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="3ad07-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ad07-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ad07-113">Example</span></span>  
 <span data-ttu-id="3ad07-114">Aşağıdaki örnek, öğesinin <xref:System.Windows.Automation.AutomationElement>geçerli özelliklerini almanın çeşitli yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ad07-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="3ad07-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ad07-115">See also</span></span>

- [<span data-ttu-id="3ad07-116">İstemciler İçin UI Otomasyonu Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3ad07-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="3ad07-117">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="3ad07-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="3ad07-118">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="3ad07-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
