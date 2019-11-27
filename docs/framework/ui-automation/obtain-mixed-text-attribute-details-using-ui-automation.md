---
title: UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 9f2cba1f602cedf3a13bd909b4dc2f1a7b4ab972
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443115"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="31d70-102">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="31d70-102">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="31d70-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="31d70-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="31d70-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="31d70-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="31d70-105">Bu konu, birden çok öznitelik değerini kapsayan bir metin aralığından metin özniteliği ayrıntılarını almak için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="31d70-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="31d70-106">Bir metin aralığı, bir belge içinde giriş işaretinin (veya seçimi kaldırma) geçerli konumuna, bitişik metin seçimine, ayrık metin seçimlerinin bir koleksiyonuna veya bir belgenin tüm metinsel içeriğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="31d70-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31d70-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="31d70-107">Example</span></span>  
 <span data-ttu-id="31d70-108">Aşağıdaki kod örneği, <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> bir <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> nesnesi döndürdüğü bir metin aralığından <xref:System.Windows.Automation.TextPattern.FontNameAttribute> nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31d70-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="31d70-109"><xref:System.Windows.Automation.Text.TextPatternRange> sınıfıyla birlikte <xref:System.Windows.Automation.TextPattern> denetim deseninin temel metin özniteliklerini, özelliklerini ve yöntemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="31d70-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="31d70-110"><xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange>tarafından desteklenmeyen denetime özgü işlevsellik için <xref:System.Windows.Automation.AutomationElement> sınıfı, Kullanıcı Arabirimi Otomasyonu istemcisinin karşılık gelen yerel nesne modeline erişmesi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="31d70-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d70-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31d70-111">See also</span></span>

- [<span data-ttu-id="31d70-112">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31d70-112">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="31d70-113">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="31d70-113">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="31d70-114">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="31d70-114">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="31d70-115">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31d70-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="31d70-116">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="31d70-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="31d70-117">UI Otomasyonu Kullanarak Metin Özniteliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="31d70-117">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
