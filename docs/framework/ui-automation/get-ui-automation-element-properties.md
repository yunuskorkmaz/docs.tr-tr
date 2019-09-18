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
ms.openlocfilehash: 158ebf29bb504dd11f9e8416011226fc5846873e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043607"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="6316f-102">UI Otomasyon Öğesi Özelliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="6316f-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="6316f-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6316f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6316f-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6316f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6316f-105">Bu konu, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin özelliklerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6316f-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="6316f-106">Geçerli özellik değerini Al</span><span class="sxs-lookup"><span data-stu-id="6316f-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="6316f-107"><xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="6316f-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="6316f-108"><xref:System.Windows.Automation.AutomationElement.Current%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="6316f-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="6316f-109">Önbelleğe alınmış Özellik değeri alma</span><span class="sxs-lookup"><span data-stu-id="6316f-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="6316f-110"><xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="6316f-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="6316f-111">Özelliği içinde <xref:System.Windows.Automation.CacheRequest>belirtilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6316f-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="6316f-112"><xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="6316f-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6316f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6316f-113">Example</span></span>  
 <span data-ttu-id="6316f-114">Aşağıdaki örnek, öğesinin <xref:System.Windows.Automation.AutomationElement>geçerli özelliklerini almanın çeşitli yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6316f-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="6316f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6316f-115">See also</span></span>

- [<span data-ttu-id="6316f-116">İstemciler İçin UI Otomasyonu Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6316f-116">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="6316f-117">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="6316f-117">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="6316f-118">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="6316f-118">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
