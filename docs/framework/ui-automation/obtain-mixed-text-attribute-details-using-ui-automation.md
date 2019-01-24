---
title: UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9ff9e1b842caeb81cd2c0f26ea9f733cf2fa9a78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662354"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="0bfb9-102">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="0bfb9-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="0bfb9-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0bfb9-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="0bfb9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0bfb9-105">Bu konu nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin özniteliği ayrıntılarını yayılan birden çok öznitelik değerleri bir metin aralığını elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="0bfb9-106">Metin aralığı bir belge içinde metin, ayrık metin seçimi koleksiyonunu veya tüm metin içeriği belgenin bir aralık seçimi giriş işaretini (veya bozuk seçimi) geçerli konumuna karşılık gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bfb9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bfb9-107">Example</span></span>  
 <span data-ttu-id="0bfb9-108">Aşağıdaki kod örneğinde nasıl alınacağı gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından burada <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> döndürür bir <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> nesne.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="0bfb9-109"><xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="0bfb9-110">Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> sınıfı karşılık gelen yerel nesne modeli erişmek UI Otomasyonu istemci için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfb9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bfb9-111">See also</span></span>
- [<span data-ttu-id="0bfb9-112">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0bfb9-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="0bfb9-113">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="0bfb9-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="0bfb9-114">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="0bfb9-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="0bfb9-115">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0bfb9-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0bfb9-116">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="0bfb9-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0bfb9-117">UI Otomasyonu Kullanarak Metin Özniteliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="0bfb9-117">Obtain Text Attributes Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
