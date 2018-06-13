---
title: 'Nasıl yapılır: Yazı Tipi Ölçümleri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 3cc5ee303efe6c703a61eef6c7448979b487f6bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524215"
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="708be-102">Nasıl yapılır: Yazı Tipi Ölçümleri Alma</span><span class="sxs-lookup"><span data-stu-id="708be-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="708be-103"><xref:System.Drawing.FontFamily> Sınıfı, belirli ailesi/stil birleşimi için çeşitli ölçümleri alma aşağıdaki yöntemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="708be-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="708be-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="708be-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="708be-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="708be-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="708be-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="708be-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="708be-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="708be-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="708be-108">Boyut ve belirli bir ölçü bağımsız şekilde bu yöntemler tarafından döndürülen yazı tipi tasarım birimlerinde numaralarıdır <xref:System.Drawing.Font> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="708be-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="708be-109">Aşağıdaki çizimde, çeşitli ölçümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="708be-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="708be-110">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="708be-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="708be-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="708be-111">Example</span></span>  
 <span data-ttu-id="708be-112">Aşağıdaki örnek Arial yazı tipi ailesinin Normal stilini ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="708be-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="708be-113">Kod ayrıca oluşturur bir <xref:System.Drawing.Font> boyutu 16 piksel ve bu belirli (piksel cinsinden) ölçümlerini görüntüler'ün (Arial ailesini temel alan) nesnesiyle <xref:System.Drawing.Font> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="708be-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="708be-114">Aşağıdaki çizimde örnek kod çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="708be-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="708be-115">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="708be-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="708be-116">Önceki çizimde çıktısını ilk iki satır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="708be-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="708be-117"><xref:System.Drawing.Font> Nesnesi döndürür 16, boyutunu ve <xref:System.Drawing.FontFamily> nesne 2.048 em yüksekliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="708be-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="708be-118">Bu iki (16 ve 2.048) yazı tipi tasarım birimleri ve (Bu örnek piksel cinsinden) birimleri arasında dönüştürme anahtarını numaralarıdır <xref:System.Drawing.Font> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="708be-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="708be-119">Örneğin, Yokuş tasarım birimlerinden piksel olarak şu şekilde dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="708be-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="708be-120">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="708be-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="708be-121">Aşağıdaki kod konumlandırır metin dikey olarak ayarlayarak <xref:System.Drawing.PointF.Y%2A> veri üyesi bir <xref:System.Drawing.PointF> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="708be-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="708be-122">Y koordinatını artırılır `font.Height` yeni her metin satırının için.</span><span class="sxs-lookup"><span data-stu-id="708be-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="708be-123"><xref:System.Drawing.Font.Height%2A> Özelliği bir <xref:System.Drawing.Font> nesnesi döndürür (piksel cinsinden) satır aralığı için bu belirli <xref:System.Drawing.Font> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="708be-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="708be-124">Bu örnekte, sayısı tarafından döndürülen <xref:System.Drawing.Font.Height%2A> 19 değil.</span><span class="sxs-lookup"><span data-stu-id="708be-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="708be-125">Bunun için piksel satır aralığı ölçüm dönüştürerek elde (tamsayıya yuvarlanan) numarasıyla aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="708be-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="708be-126">(Boyutu veya em boyutu olarak da bilinir) em yükseklik Yokuş ve düşüşü toplamı olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="708be-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="708be-127">Hücre Yüksekliği Yokuş ve düşüşü toplamı denir.</span><span class="sxs-lookup"><span data-stu-id="708be-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="708be-128">Hücre Yüksekliği iç başında eksi em yüksekliğini eşittir.</span><span class="sxs-lookup"><span data-stu-id="708be-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="708be-129">Hücre Yüksekliği artı dış başında eşittir satır aralığı.</span><span class="sxs-lookup"><span data-stu-id="708be-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="708be-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="708be-130">Compiling the Code</span></span>  
 <span data-ttu-id="708be-131">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="708be-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708be-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="708be-132">See Also</span></span>  
 [<span data-ttu-id="708be-133">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="708be-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="708be-134">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="708be-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
