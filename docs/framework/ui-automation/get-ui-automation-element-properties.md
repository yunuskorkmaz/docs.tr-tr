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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73678433692f5532f712f0d2c7a3c5bf138a87b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405583"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="a526f-102">UI Otomasyon Öğesi Özelliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="a526f-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="a526f-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a526f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a526f-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a526f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a526f-105">Bu konuda, özelliklerini almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="a526f-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="a526f-106">Geçerli bir özellik değeri Al</span><span class="sxs-lookup"><span data-stu-id="a526f-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="a526f-107">Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz, özelliği.</span><span class="sxs-lookup"><span data-stu-id="a526f-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="a526f-108">Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ya da almak <xref:System.Windows.Automation.AutomationElement.Current%2A> özelliği yapısı ve get üyeleri birinden değeri.</span><span class="sxs-lookup"><span data-stu-id="a526f-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="a526f-109">Önbelleğe alınan özellik değerini alın</span><span class="sxs-lookup"><span data-stu-id="a526f-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="a526f-110">Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz, özelliği.</span><span class="sxs-lookup"><span data-stu-id="a526f-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="a526f-111">Özelliği, belirtilmiş olmalıdır <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="a526f-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="a526f-112">Çağrı <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ya da almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği yapısı ve get üyeleri birinden değeri.</span><span class="sxs-lookup"><span data-stu-id="a526f-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a526f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a526f-113">Example</span></span>  
 <span data-ttu-id="a526f-114">Aşağıdaki örnek, geçerli özelliklerini almak için çeşitli yollar gösterir bir <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="a526f-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="a526f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a526f-115">See Also</span></span>  
 [<span data-ttu-id="a526f-116">İstemciler İçin UI Otomasyonu Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a526f-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="a526f-117">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="a526f-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="a526f-118">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="a526f-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
