---
title: UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
description: .NET API 'nin System. Windows. Automation ad alanındaki yönetilen UI Otomasyon sınıflarını kullanarak karışık metin özniteliği ayrıntılarını alın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 111d110be9365c4a58f2bd2b033c1ff4e3a6a95d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903863"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a><span data-ttu-id="4e998-103">UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma</span><span class="sxs-lookup"><span data-stu-id="4e998-103">Obtain Mixed Text Attribute Details Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="4e998-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="4e998-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4e998-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4e998-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4e998-106">Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , birden çok öznitelik değerini kapsayan bir metin aralığından metin özniteliği ayrıntıları elde etmek için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e998-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values.</span></span> <span data-ttu-id="4e998-107">Bir metin aralığı, bir belge içinde giriş işaretinin (veya seçimi kaldırma) geçerli konumuna, bitişik metin seçimine, ayrık metin seçimlerinin bir koleksiyonuna veya bir belgenin tüm metinsel içeriğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4e998-107">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e998-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e998-108">Example</span></span>  
 <span data-ttu-id="4e998-109">Aşağıdaki kod örneği, <xref:System.Windows.Automation.TextPattern.FontNameAttribute> bir nesne döndüren bir metin aralığından nasıl alınacağını gösterir <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> .</span><span class="sxs-lookup"><span data-stu-id="4e998-109">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.</span></span>  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <span data-ttu-id="4e998-110"><xref:System.Windows.Automation.TextPattern>Sınıf ile birlikte bulunan denetim deseninin <xref:System.Windows.Automation.Text.TextPatternRange> temel metin öznitelikleri, özellikleri ve yöntemleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4e998-110">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="4e998-111">Veya tarafından desteklenmeyen denetime özgü işlevsellik için <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.Text.TextPatternRange> , <xref:System.Windows.Automation.AutomationElement> sınıfı, Kullanıcı Arabirimi Otomasyonu istemcisinin karşılık gelen yerel nesne modeline erişmesi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e998-111">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e998-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e998-112">See also</span></span>

- [<span data-ttu-id="4e998-113">UI Otomasyon TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e998-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="4e998-114">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="4e998-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="4e998-115">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="4e998-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="4e998-116">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e998-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4e998-117">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="4e998-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4e998-118">UI Otomasyonu Kullanarak Metin Özniteliklerini Alma</span><span class="sxs-lookup"><span data-stu-id="4e998-118">Obtain Text Attributes Using UI Automation</span></span>](obtain-text-attributes-using-ui-automation.md)
