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
ms.openlocfilehash: 67f37dfe1fe63f2130646cb227fec855ccc7bf75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042599"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="8448c-102">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="8448c-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="8448c-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8448c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8448c-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8448c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="8448c-105">Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.</span><span class="sxs-lookup"><span data-stu-id="8448c-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="8448c-106">Destek Denetim desenleri</span><span class="sxs-lookup"><span data-stu-id="8448c-106">Support Control Patterns</span></span>

1. <span data-ttu-id="8448c-107">Öğesinin, <xref:System.Windows.Automation.Provider.IInvokeProvider> <xref:System.Windows.Automation.InvokePattern>gibi desteklemesi gereken denetim desenleri için uygun arabirimleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8448c-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="8448c-108">Uygulamanızda her denetim arabiriminin uygulamasını içeren nesneyi döndürün<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8448c-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="8448c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8448c-109">Example</span></span>

<span data-ttu-id="8448c-110">Aşağıdaki örnek, tek seçimli bir özel <xref:System.Windows.Automation.Provider.ISelectionProvider> liste kutusu için uygulamasının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8448c-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="8448c-111">Üç özellik döndürür ve şu anda seçili öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="8448c-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="8448c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8448c-112">Example</span></span>

<span data-ttu-id="8448c-113">Aşağıdaki örnek, uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider>sınıfını döndüren uygulamasının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8448c-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="8448c-114">Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, diğer tüm desen tanımlayıcıları için`Nothing` bir null başvurusu (Microsoft Visual Basic .net 'te) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8448c-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="8448c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8448c-115">See also</span></span>

- [<span data-ttu-id="8448c-116">UI Otomasyonu Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8448c-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="8448c-117">Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="8448c-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
