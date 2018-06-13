---
title: Yazı Tipleri ve Metin Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526269"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="db752-102">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="db752-102">Using Fonts and Text</span></span>
<span data-ttu-id="db752-103">Tarafından sunulan birkaç sınıfı vardır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin Windows Forms'ta çizme.</span><span class="sxs-lookup"><span data-stu-id="db752-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="db752-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> metin yazı tipi ve biçimi dikdörtgen sınırlayıcı konum gibi çeşitli özelliklerini belirtmenize olanak veren yöntemler.</span><span class="sxs-lookup"><span data-stu-id="db752-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="db752-105">Ayrıca, çizme ve ölçmek metinle [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] statik kullanarak <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="db752-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="db752-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Yöntemleri de olanak tanır konumu, yazı tipi ve biçimini belirtin.</span><span class="sxs-lookup"><span data-stu-id="db752-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="db752-107">Ya da seçebilirsiniz [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] veya [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] için metin işleme; ancak, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] teklifleri performansı ve daha doğru metin ölçme genellikle daha iyi.</span><span class="sxs-lookup"><span data-stu-id="db752-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="db752-108">Metin işlemeye katkıda bulunan diğer sınıfları içerir `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="db752-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db752-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="db752-109">In This Section</span></span>  
 [<span data-ttu-id="db752-110">Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db752-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="db752-111">Nasıl oluşturulacağını gösterir `Font` ve `FontFamily` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="db752-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="db752-112">Nasıl yapılır: Belirtilen bir Konuma Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="db752-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="db752-113">Bir konumu belirli kullanarak metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db752-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="db752-114">Nasıl yapılır: Dikdörtgende Sarmalanmış Metin</span><span class="sxs-lookup"><span data-stu-id="db752-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="db752-115">Dikdörtgen kullanarak metin çizme açıklanmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db752-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="db752-116">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="db752-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="db752-117">Nasıl kullanılacağı ortaya [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin çizme.</span><span class="sxs-lookup"><span data-stu-id="db752-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="db752-118">Nasıl yapılır: Çizilmiş Metni Hizalama</span><span class="sxs-lookup"><span data-stu-id="db752-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="db752-119">Nasıl biçimlendirileceğini gösterir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin.</span><span class="sxs-lookup"><span data-stu-id="db752-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="db752-120">Nasıl yapılır: Dikey Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db752-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="db752-121">Dikey olarak hizalanmış metinle çizmek açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db752-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="db752-122">Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama</span><span class="sxs-lookup"><span data-stu-id="db752-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="db752-123">Gösterir nasıl metin ile sekme durakları ile çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db752-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="db752-124">Nasıl yapılır: Yüklü Yazı Tiplerini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="db752-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="db752-125">Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db752-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="db752-126">Nasıl yapılır: Özel Yazı Tipi Koleksiyonu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db752-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="db752-127">Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="db752-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="db752-128">Nasıl yapılır: Yazı Tipi Ölçümleri Alma</span><span class="sxs-lookup"><span data-stu-id="db752-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="db752-129">Hücre Yokuş ve düşüşü gibi yazı tipi ölçümleri alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db752-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="db752-130">Nasıl yapılır: Metinle Düzgünleştirme Kullanma</span><span class="sxs-lookup"><span data-stu-id="db752-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="db752-131">Metin çizim sırasında düzgünleştirme kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db752-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db752-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="db752-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="db752-133">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="db752-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="db752-134">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="db752-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="db752-135">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="db752-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="db752-136">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="db752-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="db752-137">Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="db752-137">Describes this class and contains links to all of its members.</span></span>
