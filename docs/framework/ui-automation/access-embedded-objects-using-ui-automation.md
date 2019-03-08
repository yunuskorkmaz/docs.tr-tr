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
ms.openlocfilehash: df4925fc534d8c601060f1218be75a0a674579c0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680210"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="7e44e-102">UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="7e44e-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="7e44e-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7e44e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7e44e-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="7e44e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7e44e-105">Bu konu başlığı altında gösterilir nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir metin denetiminin içeriğini katıştırılmış nesneleri göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e44e-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e44e-106">Katıştırılmış nesneler içerebilir görüntüleri, köprüleri, düğmeler, tablolar veya ActiveX denetimlerini.</span><span class="sxs-lookup"><span data-stu-id="7e44e-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="7e44e-107">Katıştırılmış nesneler alt değerlendirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e44e-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="7e44e-108">Bu aynı UI Otomasyonu ağaç yapısı olarak diğer tüm aracılığıyla kullanıma olanak tanıyan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7e44e-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="7e44e-109">İşlevleri, buna genellikle katıştırılmış nesneleri denetim türüne göre gerekli denetim desenleri aracılığıyla gösterilir (köprü metin tabanlı olduğundan, örneğin, destekleyecek <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="7e44e-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="7e44e-110">![Bir metin kapsayıcı katıştırılmış nesneler. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="7e44e-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="7e44e-111">Bir örnek belge ile metinsel içeriği ("yaptığınız biliyor?" ...) ve kod örnekleri için bir hedef olarak kullanılan iki katıştırılmış nesneler (bir Whale'ı ve bir köprü bir resim).</span><span class="sxs-lookup"><span data-stu-id="7e44e-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e44e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e44e-112">Example</span></span>  
 <span data-ttu-id="7e44e-113">Aşağıdaki kod örneği, katıştırılmış nesneler koleksiyonunu içinden almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e44e-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="7e44e-114">Giriş sağlanan örnek belge için iki nesne (bir görüntü öğesi ve bir metin öğesi) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7e44e-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e44e-115">Görüntü öğesi, genellikle görüntünün açıklayan ilişkili bazı iç metin olmalıdır, <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "bir mavi whale.").</span><span class="sxs-lookup"><span data-stu-id="7e44e-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="7e44e-116">Ancak, görüntünün ne bu açıklayıcı metin resim nesnesi kapsayan bir metin aralığını alındığında, metin akışında döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7e44e-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="7e44e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e44e-117">Example</span></span>  
 <span data-ttu-id="7e44e-118">Aşağıdaki kod örneği, bir metin aralığı içinde katıştırılmış bir nesne almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e44e-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="7e44e-119">Alınan metin boş bir aralığın başlangıç uç noktası aşağıdaki "... yere aralığı</span><span class="sxs-lookup"><span data-stu-id="7e44e-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="7e44e-120">Okyanusu. (boşluk) "ve kapatma bitiş uç nokta önündeki". "(giriş sağlanan görüntü gösterildiği gibi) katıştırılmış köprüyü temsil eden.</span><span class="sxs-lookup"><span data-stu-id="7e44e-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="7e44e-121">Bu boş bir aralığın olsa da, sıfır olmayan bir aralık olduğundan, bozuk bir aralık olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="7e44e-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e44e-122"><xref:System.Windows.Automation.TextPattern> bir metin tabanlı katıştırılmış nesne köprü gibi alabilirsiniz; Ancak, ikincil <xref:System.Windows.Automation.TextPattern> tam işlevselliğini kullanıma sunmak için katıştırılmış nesneden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e44e-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="7e44e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e44e-123">See also</span></span>
- [<span data-ttu-id="7e44e-124">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e44e-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="7e44e-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e44e-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7e44e-126">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="7e44e-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7e44e-127">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="7e44e-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="7e44e-128">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="7e44e-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
