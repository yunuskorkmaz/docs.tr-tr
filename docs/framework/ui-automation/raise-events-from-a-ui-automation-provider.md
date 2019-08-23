---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: c973d6ddba498f4bdab4be764a4be6bff1cacf9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966368"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="e4ed4-102">UI Otomasyon Sağlayıcıda Olay Tetikleme</span><span class="sxs-lookup"><span data-stu-id="e4ed4-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="e4ed4-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e4ed4-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e4ed4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e4ed4-105">Bu konu, bir UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ed4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4ed4-106">Example</span></span>  
 <span data-ttu-id="e4ed4-107">Aşağıdaki örnekte, özel bir düğme [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimi uygulamasında bir olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="e4ed4-108">Uygulama, bir Kullanıcı Arabirimi Otomasyonu istemci uygulamasının bir düğme tıklamalarını benzetimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="e4ed4-109">Gereksiz işleme engel olmak için örnek, olayların <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> yapılıp yapılmayacağını görmek için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="e4ed4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-110">See also</span></span>

- [<span data-ttu-id="e4ed4-111">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4ed4-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
