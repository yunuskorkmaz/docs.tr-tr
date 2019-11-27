---
title: UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 75c63360eab2cde95698bdaded5c5249a3ca89fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447260"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="ff371-102">UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="ff371-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="ff371-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ff371-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ff371-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="ff371-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ff371-105">Bu konu, bir metin denetiminin içeriği içine katıştırılmış nesneleri göstermek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff371-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff371-106">Katıştırılmış nesneler görüntüleri, köprüleri, düğmeleri, tabloları ya da ActiveX denetimlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ff371-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="ff371-107">Katıştırılmış nesneler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısının alt öğeleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff371-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="ff371-108">Bu, diğer tüm [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleriyle aynı UI Otomasyon ağacı yapısıyla açığa çıkmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff371-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="ff371-109">İşlevsellik, genellikle katıştırılmış nesneler denetim türü için gerekli olan denetim desenleri aracılığıyla sunulur (örneğin, köprüler metin tabanlı olduğundan <xref:System.Windows.Automation.TextPattern>destekleyecektir).</span><span class="sxs-lookup"><span data-stu-id="ff371-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="ff371-110">![Metin kapsayıcısındaki katıştırılmış nesneler.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="ff371-110">![Embedded objects in a text container.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="ff371-111">Metinsel içeriğe sahip bir örnek belge ("tanıyor muydunuz?" ...) ve kod örnekleri için hedef olarak kullanılan iki katıştırılmış nesne (bir Haale ve bir metin köprüsü resmi).</span><span class="sxs-lookup"><span data-stu-id="ff371-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff371-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff371-112">Example</span></span>  
 <span data-ttu-id="ff371-113">Aşağıdaki kod örneği, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısından katıştırılmış nesneler koleksiyonunun nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff371-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="ff371-114">Giriş bölümünde belirtilen örnek belge için iki nesne döndürülür (bir görüntü öğesi ve bir metin öğesi).</span><span class="sxs-lookup"><span data-stu-id="ff371-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff371-115">Görüntü öğesi, genellikle <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "mavi bir Whale") görüntüsünü açıklayan, onunla ilişkilendirilmiş bazı iç metinleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ff371-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="ff371-116">Ancak, görüntü nesnesini kapsayan bir metin aralığı elde edildiğinde, görüntü ne de metin akışında bu açıklayıcı metin döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="ff371-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="ff371-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff371-117">Example</span></span>  
 <span data-ttu-id="ff371-118">Aşağıdaki kod örneği, bir metin aralığının bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içinde katıştırılmış bir nesneden nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff371-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="ff371-119">Alınan metin aralığı, başlangıç uç noktasının izlediği boş bir aralıktır "...</span><span class="sxs-lookup"><span data-stu-id="ff371-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="ff371-120">Hint. (boşluk) "ve bitiş bitiş noktası, katıştırılmış köprüyü temsil eden". "işaretinden önce gelir (giriş bölümünde verilen görüntüde gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="ff371-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="ff371-121">Bu boş bir Aralık olsa da, sıfır olmayan bir span içerdiğinden, bir bozuk aralığı olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="ff371-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff371-122"><xref:System.Windows.Automation.TextPattern> köprü gibi metin tabanlı gömülü bir nesne alabilir; Ancak, tam işlevselliğini göstermek için gömülü nesneden bir ikincil <xref:System.Windows.Automation.TextPattern> alınması gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="ff371-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="ff371-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff371-123">See also</span></span>

- [<span data-ttu-id="ff371-124">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff371-124">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="ff371-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff371-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ff371-126">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="ff371-126">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ff371-127">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="ff371-127">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="ff371-128">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="ff371-128">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
