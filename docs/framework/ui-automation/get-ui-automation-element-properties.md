---
title: UI Otomasyon Öğesi Özelliklerini Alma
description: Bkz. bir UI Otomasyon öğesinin güncel veya önbelleğe alınmış özelliklerinin nasıl alınacağını gösteren yönergeler ve bir örnek.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164101"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="c4952-103">UI Otomasyon Öğesi Özelliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="c4952-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="c4952-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="c4952-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c4952-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c4952-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c4952-106">Bu konu, bir öğenin özelliklerinin nasıl alınacağını gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c4952-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="c4952-107">Geçerli özellik değerini Al</span><span class="sxs-lookup"><span data-stu-id="c4952-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="c4952-108">Hangi <xref:System.Windows.Automation.AutomationElement> özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="c4952-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="c4952-109"><xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>Özellik yapısını çağırın ya da alın <xref:System.Windows.Automation.AutomationElement.Current%2A> ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="c4952-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="c4952-110">Önbelleğe alınmış Özellik değeri alma</span><span class="sxs-lookup"><span data-stu-id="c4952-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="c4952-111">Hangi <xref:System.Windows.Automation.AutomationElement> özelliği almak istediğinizi edinin.</span><span class="sxs-lookup"><span data-stu-id="c4952-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="c4952-112">Özelliği içinde belirtilmiş olmalıdır <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="c4952-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="c4952-113"><xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>Özellik yapısını çağırın ya da alın <xref:System.Windows.Automation.AutomationElement.Cached%2A> ve üyelerinden birindeki değeri alın.</span><span class="sxs-lookup"><span data-stu-id="c4952-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4952-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4952-114">Example</span></span>  
 <span data-ttu-id="c4952-115">Aşağıdaki örnek, öğesinin geçerli özelliklerini almanın çeşitli yollarını gösterir <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="c4952-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="c4952-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4952-116">See also</span></span>

- [<span data-ttu-id="c4952-117">İstemciler İçin UI Otomasyon Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c4952-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="c4952-118">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4952-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="c4952-119">UI Otomasyonda Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="c4952-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
