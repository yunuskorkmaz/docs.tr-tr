---
title: UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
description: Bir parçadaki bir öğe için UI Otomasyon sağlayıcısında gezintiyi nasıl etkinleştireceğinizi gösteren bir örnek okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168493"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="9d383-103">UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9d383-103">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="9d383-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="9d383-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9d383-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9d383-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9d383-106">Bu konu, bir parçadaki bir öğe için UI Otomasyon sağlayıcısında gezintiyi nasıl etkinleştireceğinizi gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="9d383-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d383-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d383-107">Example</span></span>  
 <span data-ttu-id="9d383-108">Aşağıdaki örnek kod, <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> liste içindeki bir liste öğesi için uygular.</span><span class="sxs-lookup"><span data-stu-id="9d383-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="9d383-109">Üst öğe liste kutusu öğesidir ve eşdüzey öğeler liste koleksiyonundaki diğer öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="9d383-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="9d383-110">Yöntemi, `null` `Nothing` geçerli olmayan yönler için (Visual Basic olarak) döndürür; bu durumda, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild> öğesi alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9d383-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="9d383-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d383-111">See also</span></span>

- [<span data-ttu-id="9d383-112">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d383-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="9d383-113">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="9d383-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
