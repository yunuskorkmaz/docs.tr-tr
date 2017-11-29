---
title: "UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme"
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
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0f417acd3440c224db06ca4034c23a1cd6eb395e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="a451f-102">UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="a451f-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="a451f-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a451f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a451f-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a451f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a451f-105">Bu konuda gösterilmektedir nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin denetiminin içeriğine katıştırılmış nesneler kullanıma sunmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a451f-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a451f-106">Katıştırılmış nesneler içerebilir görüntüleri, köprüler, düğmeleri, tablolar veya ActiveX denetimleri.</span><span class="sxs-lookup"><span data-stu-id="a451f-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="a451f-107">Katıştırılmış nesneler alt olarak kabul edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a451f-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="a451f-108">Bu aynı UI Otomasyonu ağaç yapısını diğer tüm aracılığıyla gösterilmesine izin veren [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a451f-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="a451f-109">İşlevselliği, buna karşılık, genellikle katıştırılmış nesneler denetim türü tarafından gerekli denetim düzenleri aracılığıyla gösterilir (örneğin, köprü metin tabanlı olduğundan destekledikleri <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="a451f-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="a451f-110">![Katıştırılmış nesneler metin kapsayıcısında. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="a451f-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="a451f-111">Örnek bir belge içerikle metinsel ("vermedi biliyor?" ...) ve iki kod örnekleri için hedef olarak kullanılan nesneler (uygulanýr ve bir köprü resim), katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="a451f-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a451f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a451f-112">Example</span></span>  
 <span data-ttu-id="a451f-113">Aşağıdaki kod örneğinde katıştırılmış nesneler koleksiyonunu içinden almak nasıl gösteren bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a451f-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="a451f-114">Giriş sağlanan örnek belge için iki nesne (bir görüntü öğesi ve bir metin öğesi) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a451f-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a451f-115">Bir görüntü öğesi içinde görüntüyü genellikle açıklayan ilişkili bazı iç metin olmalıdır, <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "bir mavi içinde.").</span><span class="sxs-lookup"><span data-stu-id="a451f-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="a451f-116">Ancak, resim nesnesi yayılan bir metin aralığını alındığında, görüntünün ne bu açıklama metni metin akışında döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a451f-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="a451f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a451f-117">Example</span></span>  
 <span data-ttu-id="a451f-118">Aşağıdaki kod örneğinde içinde katıştırılmış bir nesneden bir metin aralığını edinme gösteren bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a451f-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="a451f-119">Alınan metin boş bir aralığın başlangıç endpoint izleyen "... burada aralığı</span><span class="sxs-lookup"><span data-stu-id="a451f-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="a451f-120">Okyanusu. (boşluk) "ve kapanış bitiş endpoint önündeki". "katıştırılmış köprüyü temsil eden (giriş sağlanan görüntüsü gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="a451f-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="a451f-121">Bu boş bir aralığın olsa da, sıfır olmayan span içerdiğinden, bozuk bir aralığı dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="a451f-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a451f-122"><xref:System.Windows.Automation.TextPattern>bir metin tabanlı katıştırılmış nesne bir köprü gibi alabilirsiniz; Ancak, ikincil bir <xref:System.Windows.Automation.TextPattern> tam işlevselliğini kullanıma sunmak için katıştırılmış nesneden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a451f-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="a451f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a451f-123">See Also</span></span>  
 [<span data-ttu-id="a451f-124">UI Otomasyon textpattern öğesine genel bakış</span><span class="sxs-lookup"><span data-stu-id="a451f-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="a451f-125">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="a451f-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="a451f-126">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="a451f-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="a451f-127">UI Otomasyonu kullanarak metin kutusuna içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="a451f-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="a451f-128">UI Otomasyonu kullanarak metin bulma ve vurgulama</span><span class="sxs-lookup"><span data-stu-id="a451f-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
