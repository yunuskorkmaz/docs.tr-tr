---
title: UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği
description: İstemci uygulamalarının denetimleri ve onlardan veri almasını sağlamak için bir UI Otomasyon sağlayıcısında destek denetim desenlerinin nasıl uygulanacağını anlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 82300499520be6b820b361ebdeb56bbf3716afab
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163505"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="6c8e3-103">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="6c8e3-103">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="6c8e3-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="6c8e3-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6c8e3-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6c8e3-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="6c8e3-106">Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8e3-106">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="6c8e3-107">Destek Denetim desenleri</span><span class="sxs-lookup"><span data-stu-id="6c8e3-107">Support Control Patterns</span></span>

1. <span data-ttu-id="6c8e3-108">Öğesinin, gibi desteklemesi gereken denetim desenleri için uygun arabirimleri uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="6c8e3-108">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="6c8e3-109">Uygulamanızda her denetim arabiriminin uygulamasını içeren nesneyi döndürün<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6c8e3-109">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="6c8e3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c8e3-110">Example</span></span>

<span data-ttu-id="6c8e3-111">Aşağıdaki örnek, <xref:System.Windows.Automation.Provider.ISelectionProvider> tek seçimli bir özel liste kutusu için uygulamasının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c8e3-111">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="6c8e3-112">Üç özellik döndürür ve şu anda seçili öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="6c8e3-112">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="6c8e3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c8e3-113">Example</span></span>

<span data-ttu-id="6c8e3-114">Aşağıdaki örnek, uygulayan sınıfını döndüren uygulamasının bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider> .</span><span class="sxs-lookup"><span data-stu-id="6c8e3-114">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="6c8e3-115">Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, `Nothing` diğer tüm desen tanımlayıcıları için bir null başvurusu (Microsoft Visual Basic .net 'te) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6c8e3-115">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="6c8e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c8e3-116">See also</span></span>

- [<span data-ttu-id="6c8e3-117">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6c8e3-117">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="6c8e3-118">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="6c8e3-118">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
