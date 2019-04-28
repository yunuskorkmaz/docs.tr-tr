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
ms.openlocfilehash: 93e0fba4288ba3231bfed45252bdaa78892d008c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610055"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="94fd1-102">UI Otomasyon Öğesi Özelliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="94fd1-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="94fd1-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="94fd1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="94fd1-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="94fd1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="94fd1-105">Bu konu başlığı altında özelliklerini alma işlemi gösterilmektedir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="94fd1-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="94fd1-106">Geçerli bir özellik değeri Al</span><span class="sxs-lookup"><span data-stu-id="94fd1-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="94fd1-107">Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz özelliği.</span><span class="sxs-lookup"><span data-stu-id="94fd1-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="94fd1-108">Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ABD'deki <xref:System.Windows.Automation.AutomationElement.Current%2A> özelliği yapısı ve get üyelerini birinden değer.</span><span class="sxs-lookup"><span data-stu-id="94fd1-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="94fd1-109">Önbelleğe alınan özellik değer alma</span><span class="sxs-lookup"><span data-stu-id="94fd1-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="94fd1-110">Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz özelliği.</span><span class="sxs-lookup"><span data-stu-id="94fd1-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="94fd1-111">Özelliği içinde belirtilen gerekir <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="94fd1-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="94fd1-112">Çağrı <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ABD'deki <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği yapısı ve get üyelerini birinden değer.</span><span class="sxs-lookup"><span data-stu-id="94fd1-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94fd1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="94fd1-113">Example</span></span>  
 <span data-ttu-id="94fd1-114">Aşağıdaki örnek, geçerli özelliklerini almak için çeşitli yollar gösterir. bir <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="94fd1-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="94fd1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94fd1-115">See also</span></span>

- [<span data-ttu-id="94fd1-116">İstemciler İçin UI Otomasyonu Özellikleri</span><span class="sxs-lookup"><span data-stu-id="94fd1-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="94fd1-117">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="94fd1-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="94fd1-118">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="94fd1-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
