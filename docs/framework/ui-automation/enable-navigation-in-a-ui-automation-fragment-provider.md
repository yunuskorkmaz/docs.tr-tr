---
title: UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 6410a0f8a991f1dc21a298972182ec630723f627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932606"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="129d4-102">UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="129d4-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="129d4-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="129d4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="129d4-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="129d4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="129d4-105">Bu konu, bir parçadaki bir öğe için UI Otomasyon sağlayıcısında gezintiyi nasıl etkinleştireceğinizi gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="129d4-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="129d4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="129d4-106">Example</span></span>  
 <span data-ttu-id="129d4-107">Aşağıdaki örnek kod, liste <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> içindeki bir liste öğesi için uygular.</span><span class="sxs-lookup"><span data-stu-id="129d4-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="129d4-108">Üst öğe liste kutusu öğesidir ve eşdüzey öğeler liste koleksiyonundaki diğer öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="129d4-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="129d4-109">Yöntemi, geçerli `null` olmayan`Nothing` yönler için (Visual Basic olarak) döndürür <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ; bu durumda, ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>öğesi alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="129d4-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="129d4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="129d4-110">See also</span></span>

- [<span data-ttu-id="129d4-111">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="129d4-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="129d4-112">Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="129d4-112">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
