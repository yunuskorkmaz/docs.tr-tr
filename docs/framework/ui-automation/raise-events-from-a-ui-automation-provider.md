---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 1a940cbb99ac068dad6c366520a544035270da3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446880"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="3a6b7-102">UI Otomasyon Sağlayıcıda Olay Tetikleme</span><span class="sxs-lookup"><span data-stu-id="3a6b7-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="3a6b7-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3a6b7-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3a6b7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3a6b7-105">Bu konu, bir UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a6b7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a6b7-106">Example</span></span>  
 <span data-ttu-id="3a6b7-107">Aşağıdaki örnekte, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı özel bir düğme denetimi uygulamasında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="3a6b7-108">Uygulama, bir Kullanıcı Arabirimi Otomasyonu istemci uygulamasının bir düğme tıklamalarını benzetimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="3a6b7-109">Gereksiz işleme engel olmak için örnek, olayların yapılıp yapılmayacağını görmek için <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> denetler.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="3a6b7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a6b7-110">See also</span></span>

- [<span data-ttu-id="3a6b7-111">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3a6b7-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
