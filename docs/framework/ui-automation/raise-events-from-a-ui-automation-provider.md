---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 3deb4c6716d83af4b05e15b5b8a4b89e28317406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138703"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="ac8d7-102">UI Otomasyon Sağlayıcıda Olay Tetikleme</span><span class="sxs-lookup"><span data-stu-id="ac8d7-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="ac8d7-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ac8d7-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ac8d7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ac8d7-105">Bu konu, bir olayı bir UI Otomasyonu sağlayıcısı gösteren kod örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8d7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac8d7-106">Example</span></span>  
 <span data-ttu-id="ac8d7-107">Aşağıdaki örnekte, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı, özel bir düğme denetimini uygulamasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="ac8d7-108">Uygulama düğmesi tıklamasından benzetimini yapmak UI otomasyon istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="ac8d7-109">Örnek denetler gereksiz işleme engel olmak için <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> olayları harekete Geçirilmemesi gereken olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="ac8d7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8d7-110">See also</span></span>

- [<span data-ttu-id="ac8d7-111">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac8d7-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
