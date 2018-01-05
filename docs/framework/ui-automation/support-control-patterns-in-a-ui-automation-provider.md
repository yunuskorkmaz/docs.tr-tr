---
title: "UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9e85aa2fe36ad6fab59ae071a662755219ccbbb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="6359d-102">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="6359d-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="6359d-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6359d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6359d-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6359d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6359d-105">Bu konu, böylece istemci uygulamaları denetimleri işlemek ve bunları Veri Al UI Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerini uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6359d-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="6359d-106">Denetim düzenleri desteği</span><span class="sxs-lookup"><span data-stu-id="6359d-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="6359d-107">Öğe, gibi desteklemesi gereken denetim düzenleri için uygun arabirimlerini <xref:System.Windows.Automation.Provider.IInvokeProvider> için <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="6359d-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="6359d-108">Her denetim arabirimi uygulamanızda uygulanmasını içeren nesneyi döndürür<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6359d-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="6359d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6359d-109">Example</span></span>  
 <span data-ttu-id="6359d-110">Aşağıdaki örnek uygulaması gösterir <xref:System.Windows.Automation.Provider.ISelectionProvider> tek seçim özel liste kutusu için.</span><span class="sxs-lookup"><span data-stu-id="6359d-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="6359d-111">Üç özellikleri döndürür ve şu anda seçili öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="6359d-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="6359d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6359d-112">Example</span></span>  
 <span data-ttu-id="6359d-113">Aşağıdaki örnek uygulaması gösterir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> uygulayan sınıf döndüren <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span><span class="sxs-lookup"><span data-stu-id="6359d-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="6359d-114">Çoğu liste kutusu denetimleri diğer desenleri de, ancak bu örnek bir null başvuru destekleyecektir (`Nothing` içinde [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) için diğer tüm düzeni tanımlayıcıları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6359d-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="6359d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6359d-115">See Also</span></span>  
 [<span data-ttu-id="6359d-116">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6359d-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="6359d-117">Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="6359d-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
