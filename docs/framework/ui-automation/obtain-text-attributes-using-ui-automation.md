---
title: "UI Otomasyonu Kullanarak Metin Özniteliklerini Alma"
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
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 099ce10a5c0f05e95652f3d384628d4d2fac8208
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="53752-102">UI Otomasyonu Kullanarak Metin Özniteliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="53752-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="53752-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="53752-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="53752-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="53752-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="53752-105">Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin özniteliklerini metin aralığından elde edilir.</span><span class="sxs-lookup"><span data-stu-id="53752-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="53752-106">Bir metin aralığını geçerli konumunu şapka (veya bozuk seçimi) için bir belge içinde metin, ayrık metin seçimleri koleksiyonu veya bir belgenin tüm metin içeriği bitişik seçimi karşılık gelebilir.</span><span class="sxs-lookup"><span data-stu-id="53752-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53752-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="53752-107">Example</span></span>  
 <span data-ttu-id="53752-108">Aşağıdaki kod örneğinde elde etme gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından.</span><span class="sxs-lookup"><span data-stu-id="53752-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="53752-109"><xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="53752-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="53752-110">Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, sınıf karşılık gelen yerel nesne modeline erişmek UI Otomasyon istemcisi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="53752-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53752-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53752-111">See Also</span></span>  
 [<span data-ttu-id="53752-112">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53752-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="53752-113">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="53752-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="53752-114">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="53752-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="53752-115">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53752-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="53752-116">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="53752-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="53752-117">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="53752-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
