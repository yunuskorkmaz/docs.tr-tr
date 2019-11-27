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
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446823"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="9aef6-102">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="9aef6-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="9aef6-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9aef6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9aef6-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9aef6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="9aef6-105">Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.</span><span class="sxs-lookup"><span data-stu-id="9aef6-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="9aef6-106">Destek Denetim desenleri</span><span class="sxs-lookup"><span data-stu-id="9aef6-106">Support Control Patterns</span></span>

1. <span data-ttu-id="9aef6-107">Öğenin desteklemesi gereken denetim desenleri için, <xref:System.Windows.Automation.InvokePattern>için <xref:System.Windows.Automation.Provider.IInvokeProvider> gibi uygun arabirimleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9aef6-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="9aef6-108"><xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType> uygulamanızda her denetim arabiriminin uygulamanızı içeren nesneyi döndürün</span><span class="sxs-lookup"><span data-stu-id="9aef6-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="9aef6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aef6-109">Example</span></span>

<span data-ttu-id="9aef6-110">Aşağıdaki örnek, tek seçimli bir özel liste kutusu için <xref:System.Windows.Automation.Provider.ISelectionProvider> bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aef6-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="9aef6-111">Üç özellik döndürür ve şu anda seçili öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="9aef6-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="9aef6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aef6-112">Example</span></span>

<span data-ttu-id="9aef6-113">Aşağıdaki örnek, <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulayan sınıfını döndüren <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aef6-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="9aef6-114">Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, diğer tüm desen tanımlayıcıları için bir null başvurusu (Microsoft Visual Basic .NET 'te`Nothing`) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9aef6-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="9aef6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aef6-115">See also</span></span>

- [<span data-ttu-id="9aef6-116">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9aef6-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="9aef6-117">Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="9aef6-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
