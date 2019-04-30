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
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769425"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="7e102-102">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="7e102-102">Using Fonts and Text</span></span>
<span data-ttu-id="7e102-103">Tarafından sunulan çeşitli sınıfı vardır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin Windows Forms'ta çizme.</span><span class="sxs-lookup"><span data-stu-id="7e102-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="7e102-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> yöntemleri metnin konumu, dikdörtgen, yazı tipi ve biçim sınırlayıcı gibi çeşitli özelliklerini belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e102-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="7e102-105">Ayrıca, çizme ve ölçmek metinle [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 'using static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7e102-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="7e102-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Yöntemleri de belirtmenize olanak tanır konumu, yazı tipi ve biçimi.</span><span class="sxs-lookup"><span data-stu-id="7e102-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="7e102-107">Ya da tercih edebilirsiniz [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] veya [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ; metin işleme için ancak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] performans ve daha doğru metin ölçme genellikle daha iyi sunar.</span><span class="sxs-lookup"><span data-stu-id="7e102-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="7e102-108">Metin işlemeyle katkıda bulunan diğer sınıfları `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="7e102-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e102-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7e102-109">In This Section</span></span>  
 [<span data-ttu-id="7e102-110">Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="7e102-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="7e102-111">Oluşturma işlemi gösterilmektedir `Font` ve `FontFamily` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7e102-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="7e102-112">Nasıl yapılır: Belirtilen bir konuma metin çizme</span><span class="sxs-lookup"><span data-stu-id="7e102-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="7e102-113">Bir konum belirli kullanarak metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e102-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="7e102-114">Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme</span><span class="sxs-lookup"><span data-stu-id="7e102-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="7e102-115">Metin kullanarak bir dikdörtgen çizmek kullanılan nasıl açıklanmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e102-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="7e102-116">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="7e102-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="7e102-117">Nasıl kullanılacağını gösteren [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin çizme.</span><span class="sxs-lookup"><span data-stu-id="7e102-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="7e102-118">Nasıl yapılır: Çizilmiş metni hizalama</span><span class="sxs-lookup"><span data-stu-id="7e102-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="7e102-119">Biçimlendirilecek nasıl gösterir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin.</span><span class="sxs-lookup"><span data-stu-id="7e102-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="7e102-120">Nasıl yapılır: Dikey metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e102-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="7e102-121">Dikey hizalı metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e102-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="7e102-122">Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama</span><span class="sxs-lookup"><span data-stu-id="7e102-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="7e102-123">Programlarını nasıl sekme durakları ile ile metin çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e102-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="7e102-124">Nasıl yapılır: Yüklü yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="7e102-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="7e102-125">Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e102-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="7e102-126">Nasıl yapılır: Özel yazı tipi koleksiyonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e102-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="7e102-127">Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesne.</span><span class="sxs-lookup"><span data-stu-id="7e102-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="7e102-128">Nasıl yapılır: Yazı tipi ölçümleri alma</span><span class="sxs-lookup"><span data-stu-id="7e102-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="7e102-129">Hücre ascent ve iniş gibi yazı tipi ölçümleri alma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e102-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="7e102-130">Nasıl yapılır: Metinle düzgünleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="7e102-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="7e102-131">Metin çizim sırasında düzgünleştirme kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e102-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7e102-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7e102-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="7e102-133">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7e102-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="7e102-134">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7e102-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="7e102-135">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7e102-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="7e102-136">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7e102-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="7e102-137">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="7e102-137">Describes this class and contains links to all of its members.</span></span>
