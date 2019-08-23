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
ms.openlocfilehash: 83e54da5fdb75e3da44009ec700102d6bd7ae5e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937962"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="aa95e-102">UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="aa95e-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="aa95e-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="aa95e-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="aa95e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="aa95e-105">Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir metin denetiminin içeriği içine katıştırılmış nesneleri ortaya çıkarmak için nasıl kullanılabilecekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa95e-106">Katıştırılmış nesneler görüntüleri, köprüleri, düğmeleri, tabloları ya da ActiveX denetimlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="aa95e-107">Katıştırılmış nesneler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısının alt öğeleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="aa95e-108">Bu, diğer [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] tüm öğeler ile aynı UI Otomasyon ağacı yapısıyla açığa çıkmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa95e-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="aa95e-109">İşlevsellik, genellikle katıştırılmış nesneler denetim türü için gerekli olan denetim desenleri aracılığıyla gösterilir (örneğin, köprüler, metin tabanlı <xref:System.Windows.Automation.TextPattern>olduğundan).</span><span class="sxs-lookup"><span data-stu-id="aa95e-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="aa95e-110">![Metin kapsayıcısındaki katıştırılmış nesneler.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="aa95e-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="aa95e-111">Metinsel içeriğe sahip bir örnek belge ("tanıyor muydunuz?" ...) ve kod örnekleri için hedef olarak kullanılan iki katıştırılmış nesne (bir Haale ve bir metin köprüsü resmi).</span><span class="sxs-lookup"><span data-stu-id="aa95e-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa95e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa95e-112">Example</span></span>  
 <span data-ttu-id="aa95e-113">Aşağıdaki kod örneği, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içinden katıştırılmış nesneler koleksiyonunun nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="aa95e-114">Giriş bölümünde belirtilen örnek belge için iki nesne döndürülür (bir görüntü öğesi ve bir metin öğesi).</span><span class="sxs-lookup"><span data-stu-id="aa95e-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa95e-115">Görüntü öğesi, görüntüyü açıklayan, genellikle <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "mavi bir Whale"), onunla ilişkilendirilmiş bir iç metin içermelidir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="aa95e-116">Ancak, görüntü nesnesini kapsayan bir metin aralığı elde edildiğinde, görüntü ne de metin akışında bu açıklayıcı metin döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="aa95e-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="aa95e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa95e-117">Example</span></span>  
 <span data-ttu-id="aa95e-118">Aşağıdaki kod örneği, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içindeki katıştırılmış bir nesneden bir metin aralığının nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="aa95e-119">Alınan metin aralığı, başlangıç uç noktasının izlediği boş bir aralıktır "...</span><span class="sxs-lookup"><span data-stu-id="aa95e-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="aa95e-120">Hint. (boşluk) "ve bitiş bitiş noktası, katıştırılmış köprüyü temsil eden". "işaretinden önce gelir (giriş bölümünde verilen görüntüde gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="aa95e-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="aa95e-121">Bu boş bir Aralık olsa da, sıfır olmayan bir span içerdiğinden, bir bozuk aralığı olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="aa95e-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa95e-122"><xref:System.Windows.Automation.TextPattern>köprü gibi metin tabanlı katıştırılmış bir nesne alabilir; Ancak, tam işlevselliğini <xref:System.Windows.Automation.TextPattern> göstermek için, ikincil nesnenin gömülü nesneden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa95e-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="aa95e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa95e-123">See also</span></span>

- [<span data-ttu-id="aa95e-124">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa95e-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="aa95e-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa95e-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="aa95e-126">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="aa95e-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="aa95e-127">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="aa95e-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="aa95e-128">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="aa95e-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
