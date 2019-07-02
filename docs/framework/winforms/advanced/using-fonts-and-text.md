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
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505114"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="3a021-102">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a021-102">Using Fonts and Text</span></span>
<span data-ttu-id="3a021-103">Windows Form üzerinde metin çizim GDI +'da ve GDI tarafından sunulan çeşitli sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="3a021-103">There are several classes offered by GDI+ and GDI for drawing text on Windows Forms.</span></span> <span data-ttu-id="3a021-104">GDI + <xref:System.Drawing.Graphics> sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> yöntemleri metnin konumu, dikdörtgen, yazı tipi ve biçim sınırlayıcı gibi çeşitli özelliklerini belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a021-104">The GDI+ <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="3a021-105">Ayrıca, çizme ve'using static GDI ile metin ölçmek <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3a021-105">In addition, you can draw and measure text with GDI using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="3a021-106">GDI yöntemleri konumu, yazı tipi ve biçim belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a021-106">The GDI methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="3a021-107">GDI veya GDI +'da metin işleme için seçebilirsiniz; Ancak, GDI genellikle daha iyi performans ve daha doğru metin ölçme sunar.</span><span class="sxs-lookup"><span data-stu-id="3a021-107">You can choose either GDI or GDI+ for text rendering; however, GDI generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="3a021-108">Metin işlemeyle katkıda bulunan diğer sınıfları `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="3a021-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a021-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3a021-109">In This Section</span></span>  
 [<span data-ttu-id="3a021-110">Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="3a021-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="3a021-111">Oluşturma işlemi gösterilmektedir `Font` ve `FontFamily` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3a021-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="3a021-112">Nasıl yapılır: Belirtilen bir konuma metin çizme</span><span class="sxs-lookup"><span data-stu-id="3a021-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="3a021-113">GDI +'da ve GDI kullanarak bir belirli konumda metin çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a021-113">Describes how to draw text in a certain location using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="3a021-114">Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme</span><span class="sxs-lookup"><span data-stu-id="3a021-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="3a021-115">GDI +'da ve GDI kullanarak dikdörtgene metin çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a021-115">Explains how to draw text in a rectangle using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="3a021-116">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="3a021-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="3a021-117">Metin çizim GDI nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3a021-117">Demonstrates how to use GDI for drawing text.</span></span>  
  
 [<span data-ttu-id="3a021-118">Nasıl yapılır: Çizilmiş metni hizalama</span><span class="sxs-lookup"><span data-stu-id="3a021-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="3a021-119">GDI +'da ve GDI metnin nasıl biçimlendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a021-119">Shows how to format GDI+ and GDI text.</span></span>  
  
 [<span data-ttu-id="3a021-120">Nasıl yapılır: Dikey metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a021-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="3a021-121">GDI +'da dikey hizalı metin çizme açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a021-121">Describes how to draw vertically aligned text with GDI+.</span></span>  
  
 [<span data-ttu-id="3a021-122">Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama</span><span class="sxs-lookup"><span data-stu-id="3a021-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="3a021-123">Programlarını nasıl GDI + ile sekme durakları ile metin çizin.</span><span class="sxs-lookup"><span data-stu-id="3a021-123">Shows how draw text with tab stops with GDI+.</span></span>  
  
 [<span data-ttu-id="3a021-124">Nasıl yapılır: Yüklü yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="3a021-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="3a021-125">Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a021-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="3a021-126">Nasıl yapılır: Özel yazı tipi koleksiyonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a021-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="3a021-127">Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesne.</span><span class="sxs-lookup"><span data-stu-id="3a021-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="3a021-128">Nasıl yapılır: Yazı tipi ölçümleri alma</span><span class="sxs-lookup"><span data-stu-id="3a021-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="3a021-129">Hücre ascent ve iniş gibi yazı tipi ölçümleri alma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a021-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="3a021-130">Nasıl yapılır: Metinle düzgünleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="3a021-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="3a021-131">Metin çizim sırasında düzgünleştirme kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a021-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a021-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3a021-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="3a021-133">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3a021-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="3a021-134">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3a021-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="3a021-135">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3a021-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="3a021-136">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3a021-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="3a021-137">Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3a021-137">Describes this class and contains links to all of its members.</span></span>
