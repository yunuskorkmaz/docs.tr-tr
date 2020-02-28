---
title: Koordinat Sistemi Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159812"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="992cd-102">Koordinat Sistemi Türleri</span><span class="sxs-lookup"><span data-stu-id="992cd-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="992cd-103">GDI+ üç koordinat alanı kullanır: Dünya, sayfa ve cihaz.</span><span class="sxs-lookup"><span data-stu-id="992cd-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="992cd-104">Dünya koordinatları, belirli bir grafik dünyasını modellemek için kullanılan koordinatlardır ve .NET Framework yöntemlere geçirdiğiniz koordinatlardır.</span><span class="sxs-lookup"><span data-stu-id="992cd-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="992cd-105">Sayfa koordinatları, bir form veya denetim gibi bir çizim yüzeyi tarafından kullanılan koordinat sistemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="992cd-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="992cd-106">Cihaz koordinatları, bir ekran veya kağıt sayfası gibi, üzerine çizilmiş fiziksel cihaz tarafından kullanılan koordinatlardır.</span><span class="sxs-lookup"><span data-stu-id="992cd-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="992cd-107">`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`çağrısı yaptığınızda, <xref:System.Drawing.Graphics.DrawLine%2A> yöntemine geçirdiğiniz noktaları —`(0, 0)` ve `(160, 80)`— dünya koordinat alanında olur.</span><span class="sxs-lookup"><span data-stu-id="992cd-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="992cd-108">GDI+, ekranda çizgi çizmeden önce koordinatları bir dizi dönüşümden geçer.</span><span class="sxs-lookup"><span data-stu-id="992cd-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="992cd-109">Dünya dönüşümü olarak adlandırılan bir dönüşüm, dünya koordinatlarını sayfa koordinatlarına dönüştürür ve sayfa dönüşümü olarak adlandırılan başka bir dönüşüm, sayfa koordinatlarını cihaz koordinatlarına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="992cd-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="992cd-110">Sistemleri dönüştürür ve koordine et</span><span class="sxs-lookup"><span data-stu-id="992cd-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="992cd-111">Sol üst köşede değil, istemci alanının gövdesinde kaynağına sahip bir koordinat sistemiyle çalışmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="992cd-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="992cd-112">Örneğin, kaynağın, istemci alanının sol kenarından 100 piksel olmasını istediğinizi ve istemci alanının en üstünde 50 pikseli olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="992cd-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="992cd-113">Aşağıdaki çizimde bu tür bir koordinat sistemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="992cd-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="992cd-114">![Koordinat sistemi](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="992cd-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="992cd-115">`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`çağrısı yaptığınızda aşağıdaki çizimde gösterilen satırı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="992cd-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="992cd-116">![Koordinat sistemi](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="992cd-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="992cd-117">Üç koordinat alanındaki satırlarınızın uç noktaların koordinatları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="992cd-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="992cd-118">Dünya</span><span class="sxs-lookup"><span data-stu-id="992cd-118">World</span></span>|<span data-ttu-id="992cd-119">(0, 0)-(160, 80)</span><span class="sxs-lookup"><span data-stu-id="992cd-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="992cd-120">Sayfasında</span><span class="sxs-lookup"><span data-stu-id="992cd-120">Page</span></span>|<span data-ttu-id="992cd-121">(100, 50)-(260, 130)</span><span class="sxs-lookup"><span data-stu-id="992cd-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="992cd-122">Cihaz</span><span class="sxs-lookup"><span data-stu-id="992cd-122">Device</span></span>|<span data-ttu-id="992cd-123">(100, 50)-(260, 130)</span><span class="sxs-lookup"><span data-stu-id="992cd-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="992cd-124">Sayfa koordinat alanının, istemci alanının sol üst köşesinde bulunan kaynağı olduğunu unutmayın; Bu durum her zaman olur.</span><span class="sxs-lookup"><span data-stu-id="992cd-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="992cd-125">Ayrıca, ölçü birimi piksel olduğundan, cihaz koordinatları sayfa koordinatlarıyla aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="992cd-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="992cd-126">Ölçü birimini piksel dışında bir değere ayarlarsanız (örneğin, inç), cihaz koordinatları sayfa koordinatlarından farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="992cd-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="992cd-127">Dünya koordinatlarını sayfa koordinatlarına eşleyen dünya dönüştürmesi, <xref:System.Drawing.Graphics> sınıfının <xref:System.Drawing.Graphics.Transform%2A> özelliğinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="992cd-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="992cd-128">Yukarıdaki örnekte, World Transformation, y yönünde x Direction ve 50 birimlerindeki çeviri 100 birimleridir.</span><span class="sxs-lookup"><span data-stu-id="992cd-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="992cd-129">Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnesinin dünya dönüşümünü ayarlar ve ardından bu <xref:System.Drawing.Graphics> nesnesini kullanarak önceki şekilde gösterilen satırı çizer:</span><span class="sxs-lookup"><span data-stu-id="992cd-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="992cd-130">Sayfa dönüştürme sayfa koordinatlarını cihaz koordinatlarına eşler.</span><span class="sxs-lookup"><span data-stu-id="992cd-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="992cd-131"><xref:System.Drawing.Graphics> sınıfı, sayfa dönüşümünü işlemek için <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="992cd-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="992cd-132"><xref:System.Drawing.Graphics> sınıfı ayrıca, görüntüleme cihazının yatay ve dikey noktaların incelenmesiyle ilgili <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>iki salt okuma özelliği de sağlar.</span><span class="sxs-lookup"><span data-stu-id="992cd-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="992cd-133"><xref:System.Drawing.Graphics> sınıfının <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini kullanarak, pikselden farklı bir ölçü birimi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="992cd-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="992cd-134">Bu fiziksel bir birim olmadığından ve bir özel duruma neden olacağı için <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini <xref:System.Drawing.GraphicsUnit.World>ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="992cd-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="992cd-135">Aşağıdaki örnek (0, 0) ile (2, 1) arasında bir çizgi çizer, burada nokta (2, 1), nokta (0, 0) ile sağ ve 1 inç arasında 2 ' dir:</span><span class="sxs-lookup"><span data-stu-id="992cd-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> <span data-ttu-id="992cd-136">Kaleminizi oluştururken bir kalem genişliği belirtmezseniz, yukarıdaki örnek bir inç genişliğinde bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="992cd-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="992cd-137"><xref:System.Drawing.Pen> oluşturucusuna ikinci bağımsız değişkende kalem genişliğini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="992cd-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="992cd-138">Görüntü cihazının yatay yönde 96 nokta ve dikey yönde 96 nokta/inç olduğunu varsaydığımızda, önceki örnekteki satırın uç noktaları üç koordinat alanında aşağıdaki koordinatlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="992cd-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="992cd-139">Dünya</span><span class="sxs-lookup"><span data-stu-id="992cd-139">World</span></span>|<span data-ttu-id="992cd-140">(0, 0)-(2, 1)</span><span class="sxs-lookup"><span data-stu-id="992cd-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="992cd-141">Sayfasında</span><span class="sxs-lookup"><span data-stu-id="992cd-141">Page</span></span>|<span data-ttu-id="992cd-142">(0, 0)-(2, 1)</span><span class="sxs-lookup"><span data-stu-id="992cd-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="992cd-143">Cihaz</span><span class="sxs-lookup"><span data-stu-id="992cd-143">Device</span></span>|<span data-ttu-id="992cd-144">(0, 0)-(192, 96)</span><span class="sxs-lookup"><span data-stu-id="992cd-144">(0, 0) to (192, 96)</span></span>|  
  
 <span data-ttu-id="992cd-145">Dünya koordinat alanının kaynağı istemci alanının sol üst köşesinde olduğundan, sayfa koordinatları dünyanın koordinatlarıyla aynı olur.</span><span class="sxs-lookup"><span data-stu-id="992cd-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="992cd-146">Çeşitli etkilere ulaşmak için dünya ve sayfa dönüştürmelerini birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="992cd-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="992cd-147">Örneğin, ölçü birimi olarak inç kullanmak istediğinizi ve koordinat sisteminizin kaynağının, istemci alanının sol kenarından 2 cm ve istemci alanının en üstünden 1/2 inç olmasını istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="992cd-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="992cd-148">Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnesinin dünya ve sayfa dönüştürmelerini ayarlar ve (0, 0) öğesinden (2, 1) bir çizgi çizer:</span><span class="sxs-lookup"><span data-stu-id="992cd-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="992cd-149">Aşağıdaki çizimde çizgi ve koordinat sistemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="992cd-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="992cd-150">![Koordinat sistemi](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="992cd-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="992cd-151">Görüntü cihazının yatay yönde 96 nokta ve dikey yönde 96 nokta/inç olduğunu varsaydığımızda, önceki örnekteki satırın uç noktaları üç koordinat alanında aşağıdaki koordinatlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="992cd-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="992cd-152">Dünya</span><span class="sxs-lookup"><span data-stu-id="992cd-152">World</span></span>|<span data-ttu-id="992cd-153">(0, 0)-(2, 1)</span><span class="sxs-lookup"><span data-stu-id="992cd-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="992cd-154">Sayfasında</span><span class="sxs-lookup"><span data-stu-id="992cd-154">Page</span></span>|<span data-ttu-id="992cd-155">(2, 0,5)-(4, 1,5)</span><span class="sxs-lookup"><span data-stu-id="992cd-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="992cd-156">Cihaz</span><span class="sxs-lookup"><span data-stu-id="992cd-156">Device</span></span>|<span data-ttu-id="992cd-157">(192, 48)-(384, 144)</span><span class="sxs-lookup"><span data-stu-id="992cd-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="992cd-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="992cd-158">See also</span></span>

- [<span data-ttu-id="992cd-159">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="992cd-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="992cd-160">Dönüşümlerin Matrisle Temsili</span><span class="sxs-lookup"><span data-stu-id="992cd-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
