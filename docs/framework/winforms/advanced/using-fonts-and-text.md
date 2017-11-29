---
title: "Yazı Tipleri ve Metin Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="2697e-102">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="2697e-102">Using Fonts and Text</span></span>
<span data-ttu-id="2697e-103">Tarafından sunulan birkaç sınıfı vardır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin Windows Forms'ta çizme.</span><span class="sxs-lookup"><span data-stu-id="2697e-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="2697e-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> metin yazı tipi ve biçimi dikdörtgen sınırlayıcı konum gibi çeşitli özelliklerini belirtmenize olanak veren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="2697e-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="2697e-105">Ayrıca, çizme ve ölçmek metinle [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] statik kullanarak <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2697e-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="2697e-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Yöntemleri de olanak tanır konumu, yazı tipi ve biçimini belirtin.</span><span class="sxs-lookup"><span data-stu-id="2697e-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="2697e-107">Ya da seçebilirsiniz [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] veya [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] için metin işleme; ancak, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] teklifleri performansı ve daha doğru metin ölçme genellikle daha iyi.</span><span class="sxs-lookup"><span data-stu-id="2697e-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="2697e-108">Metin işlemeye katkıda bulunan diğer sınıfları içerir `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="2697e-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2697e-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2697e-109">In This Section</span></span>  
 [<span data-ttu-id="2697e-110">Nasıl yapılır: yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="2697e-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="2697e-111">Nasıl oluşturulacağını gösterir `Font` ve `FontFamily` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2697e-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="2697e-112">Nasıl yapılır: belirtilen konumda metin çizme</span><span class="sxs-lookup"><span data-stu-id="2697e-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="2697e-113">Bir konumu belirli kullanarak metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2697e-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="2697e-114">Nasıl yapılır: dikdörtgende sarmalanmış metin dikdörtgene</span><span class="sxs-lookup"><span data-stu-id="2697e-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="2697e-115">Dikdörtgen kullanarak metin çizme açıklanmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2697e-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="2697e-116">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="2697e-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="2697e-117">Nasıl kullanılacağı ortaya [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin çizme.</span><span class="sxs-lookup"><span data-stu-id="2697e-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="2697e-118">Nasıl yapılır: çizilmiş metni hizalama</span><span class="sxs-lookup"><span data-stu-id="2697e-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="2697e-119">Nasıl biçimlendirileceğini gösterir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin.</span><span class="sxs-lookup"><span data-stu-id="2697e-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="2697e-120">Nasıl yapılır: dikey metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="2697e-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="2697e-121">Dikey olarak hizalanmış metinle çizmek açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2697e-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="2697e-122">Nasıl yapılır: çizilmiş metinde sekme durakları ayarlama</span><span class="sxs-lookup"><span data-stu-id="2697e-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="2697e-123">Gösterir nasıl metin ile sekme durakları ile çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2697e-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="2697e-124">Nasıl yapılır: yüklü yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="2697e-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="2697e-125">Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2697e-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="2697e-126">Nasıl yapılır: özel yazı tipi koleksiyonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="2697e-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="2697e-127">Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2697e-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="2697e-128">Nasıl yapılır: yazı tipi ölçümleri alma</span><span class="sxs-lookup"><span data-stu-id="2697e-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="2697e-129">Hücre Yokuş ve düşüşü gibi yazı tipi ölçümleri alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2697e-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="2697e-130">Nasıl yapılır: metinle düzgünleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="2697e-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="2697e-131">Metin çizim sırasında düzgünleştirme kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2697e-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2697e-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="2697e-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="2697e-133">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2697e-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="2697e-134">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2697e-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="2697e-135">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2697e-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="2697e-136">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2697e-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="2697e-137">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2697e-137">Describes this class and contains links to all of its members.</span></span>
