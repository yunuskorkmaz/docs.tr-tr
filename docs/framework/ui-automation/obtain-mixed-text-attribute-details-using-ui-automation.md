---
title: "UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma"
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
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0588ec764aabf5aa0e88477838d949a294f3064e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="bf251-102">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="bf251-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="bf251-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bf251-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bf251-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bf251-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bf251-105">Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin özniteliği ayrıntılarını birden çok öznitelik değerleri yayılan bir metin aralığından elde edilir.</span><span class="sxs-lookup"><span data-stu-id="bf251-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="bf251-106">Bir metin aralığını geçerli konumunu şapka (veya bozuk seçimi) için bir belge içinde metin, ayrık metin seçimleri koleksiyonu veya bir belgenin tüm metin içeriği bitişik seçimi karşılık gelebilir.</span><span class="sxs-lookup"><span data-stu-id="bf251-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf251-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf251-107">Example</span></span>  
 <span data-ttu-id="bf251-108">Aşağıdaki kod örneğinde elde etme gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından nerede <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> döndürür bir <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bf251-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="bf251-109"><xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bf251-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="bf251-110">Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> sınıfı, karşılık gelen yerel nesne modeline erişmek UI otomasyon istemci için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf251-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf251-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf251-111">See Also</span></span>  
 [<span data-ttu-id="bf251-112">UI Otomasyon textpattern öğesine genel bakış</span><span class="sxs-lookup"><span data-stu-id="bf251-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="bf251-113">UI Otomasyonu kullanarak metin kutusuna içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="bf251-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="bf251-114">UI Otomasyonu kullanarak metin bulma ve vurgulama</span><span class="sxs-lookup"><span data-stu-id="bf251-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="bf251-115">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="bf251-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="bf251-116">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="bf251-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="bf251-117">UI Otomasyonu kullanarak metin özniteliklerini alma</span><span class="sxs-lookup"><span data-stu-id="bf251-117">Obtain Text Attributes Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
