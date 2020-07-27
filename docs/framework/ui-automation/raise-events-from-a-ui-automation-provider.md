---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
description: UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren bir örnek görürsünüz. Özel bir düğme denetimi uygulamasında bir UI Otomasyonu olayını başlatır.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 75af4d05172e2417d44f76beab486de5eb3a4ba7
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168104"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="67513-104">UI Otomasyon Sağlayıcıda Olay Tetikleme</span><span class="sxs-lookup"><span data-stu-id="67513-104">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="67513-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="67513-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="67513-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="67513-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="67513-107">Bu konu, bir UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="67513-107">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67513-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="67513-108">Example</span></span>  
 <span data-ttu-id="67513-109">Aşağıdaki örnekte, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel bir düğme denetimi uygulamasında bir olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="67513-109">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="67513-110">Uygulama, bir Kullanıcı Arabirimi Otomasyonu istemci uygulamasının bir düğme tıklamalarını benzetimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="67513-110">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="67513-111">Gereksiz işleme engel olmak için örnek, <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> olayların yapılıp yapılmayacağını görmek için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="67513-111">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="67513-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67513-112">See also</span></span>

- [<span data-ttu-id="67513-113">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67513-113">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
