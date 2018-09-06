---
title: UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 98fcc601979579719d0133a081dcd9c111bb7fe0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863496"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="a52a8-102">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="a52a8-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="a52a8-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a52a8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a52a8-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a52a8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a52a8-105">Bu konuda, böylece istemci uygulamaları denetimleri işlemenizi ve onlardan veri almak, UI Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerini uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a52a8-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="a52a8-106">Denetim düzenleri desteği</span><span class="sxs-lookup"><span data-stu-id="a52a8-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="a52a8-107">Öğe, gibi desteklemelidir denetim desenleri için uygun arabirimi uygulayan <xref:System.Windows.Automation.Provider.IInvokeProvider> için <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="a52a8-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="a52a8-108">Uygulamanızı her denetim arabiriminin uygulamanızda içeren nesneyi döndürür <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a52a8-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="a52a8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a52a8-109">Example</span></span>  
 <span data-ttu-id="a52a8-110">Aşağıdaki örnek bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.ISelectionProvider> tek seçimli özel liste kutusu için.</span><span class="sxs-lookup"><span data-stu-id="a52a8-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="a52a8-111">Bu üç özellik döndürür ve şu anda seçili öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="a52a8-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="a52a8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a52a8-112">Example</span></span>  
 <span data-ttu-id="a52a8-113">Aşağıdaki örnek bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> uygulayan sınıf döndüren <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="a52a8-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="a52a8-114">Çoğu liste kutusu denetimleri diğer desenleri de ancak bu örnekte bir null başvuru destekleyecektir (`Nothing` Microsoft Visual Basic. NET'te) için diğer tüm düzeni tanımlayıcıları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a52a8-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="a52a8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a52a8-115">See Also</span></span>  
 [<span data-ttu-id="a52a8-116">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a52a8-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="a52a8-117">Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="a52a8-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
