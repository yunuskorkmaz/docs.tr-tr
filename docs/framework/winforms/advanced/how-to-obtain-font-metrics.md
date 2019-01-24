---
title: 'Nasıl yapılır: Yazı tipi ölçümleri alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 5e37725363640bd02fc3e0f62f66d21151b497fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657265"
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="f8fed-102">Nasıl yapılır: Yazı tipi ölçümleri alma</span><span class="sxs-lookup"><span data-stu-id="f8fed-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="f8fed-103"><xref:System.Drawing.FontFamily> Sınıfı belirli ailesi/stil birleşimi için çeşitli ölçümleri alma aşağıdaki yöntemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f8fed-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="f8fed-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="f8fed-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="f8fed-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="f8fed-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="f8fed-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="f8fed-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="f8fed-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="f8fed-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="f8fed-108">Bu yöntem tarafından döndürülen sayılara boyutu ve belirli bir ölçü bağımsız oldukları yazı tipi tasarım birimlerinde olduğundan <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="f8fed-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="f8fed-109">Aşağıdaki çizim, çeşitli ölçümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8fed-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="f8fed-110">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="f8fed-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8fed-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8fed-111">Example</span></span>  
 <span data-ttu-id="f8fed-112">Aşağıdaki örnek, Normal stili Arial yazı tipi ailesinin ölçümleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f8fed-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="f8fed-113">Kod ayrıca oluşturur bir <xref:System.Drawing.Font> (Arial ailesinde göre) nesne boyutu 16 piksel ve görüntüler (piksel cinsinden) için belirli ölçümleri <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="f8fed-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="f8fed-114">Örnek kodun çıktısı aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8fed-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="f8fed-115">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="f8fed-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="f8fed-116">Önceki çizimde çıkış ilk iki satırlık unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8fed-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="f8fed-117"><xref:System.Drawing.Font> Nesne döndürür, 16, boyutunu ve <xref:System.Drawing.FontFamily> 2.048 bir em yüksekliğini nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8fed-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="f8fed-118">Bu iki sayı (16 ve 2.048) yazı tipi tasarım birimleri ve (Bu durum piksel cinsinden) birimleri arasında dönüştürme için önemli olduğu <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="f8fed-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="f8fed-119">Örneğin, ascent tasarım birimlerinden piksel olarak şu şekilde dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8fed-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="f8fed-120">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="f8fed-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="f8fed-121">Aşağıdaki kod konumlandırır metni dikey olarak ayarlayarak <xref:System.Drawing.PointF.Y%2A> veri üyesi bir <xref:System.Drawing.PointF> nesne.</span><span class="sxs-lookup"><span data-stu-id="f8fed-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="f8fed-122">Y koordinatını artırılana `font.Height` her yeni satır metin için.</span><span class="sxs-lookup"><span data-stu-id="f8fed-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="f8fed-123"><xref:System.Drawing.Font.Height%2A> Özelliği bir <xref:System.Drawing.Font> nesnesini döndürür (piksel cinsinden) satır aralığı için o belirli <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="f8fed-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="f8fed-124">Bu örnekte, bir sayı tarafından döndürülen <xref:System.Drawing.Font.Height%2A> 19 olduğu.</span><span class="sxs-lookup"><span data-stu-id="f8fed-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="f8fed-125">Bu satır aralığı ölçüm piksel dönüştürerek elde edilen (bir tamsayıya yuvarlanır) numarasıyla aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8fed-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="f8fed-126">(Boyut veya em boyutu olarak da bilinir) em yüksekliği ascent ve iniş olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8fed-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="f8fed-127">Hücre Yüksekliği ascent ve iniş çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f8fed-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="f8fed-128">Hücre Yüksekliği iç önde gelen eksi em boyuna eşit.</span><span class="sxs-lookup"><span data-stu-id="f8fed-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="f8fed-129">Hücre Yüksekliği artı başlıca dış satır aralığını eşit.</span><span class="sxs-lookup"><span data-stu-id="f8fed-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8fed-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f8fed-130">Compiling the Code</span></span>  
 <span data-ttu-id="f8fed-131">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f8fed-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fed-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8fed-132">See also</span></span>
- [<span data-ttu-id="f8fed-133">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="f8fed-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="f8fed-134">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="f8fed-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
