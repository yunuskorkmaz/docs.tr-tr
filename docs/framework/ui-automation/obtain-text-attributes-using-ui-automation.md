---
title: UI Otomasyonu Kullanarak Metin Özniteliklerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: d4cb9d12e4e2d5a28744e3a238884616a6db8f68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214903"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="f9bca-102">UI Otomasyonu Kullanarak Metin Özniteliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="f9bca-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="f9bca-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f9bca-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f9bca-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f9bca-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f9bca-105">Bu konu nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir metin aralığındaki metin özniteliklerini alma için.</span><span class="sxs-lookup"><span data-stu-id="f9bca-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="f9bca-106">Metin aralığı bir belge içinde metin, ayrık metin seçimi koleksiyonunu veya tüm metin içeriği belgenin bir aralık seçimi giriş işaretini (veya bozuk seçimi) geçerli konumuna karşılık gelebilir.</span><span class="sxs-lookup"><span data-stu-id="f9bca-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9bca-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9bca-107">Example</span></span>  
 <span data-ttu-id="f9bca-108">Aşağıdaki kod örneğinde nasıl alınacağı gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından.</span><span class="sxs-lookup"><span data-stu-id="f9bca-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="f9bca-109"><xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f9bca-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="f9bca-110">Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, sınıfı karşılık gelen yerel nesne modeli erişmek UI Otomasyonu istemci için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bca-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bca-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bca-111">See also</span></span>

- [<span data-ttu-id="f9bca-112">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9bca-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="f9bca-113">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="f9bca-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="f9bca-114">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="f9bca-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="f9bca-115">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9bca-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f9bca-116">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="f9bca-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f9bca-117">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="f9bca-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
