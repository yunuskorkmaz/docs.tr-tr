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
ms.openlocfilehash: ff53942cb90721d5411f99b261f90366d039e151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529759"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="b41a7-102">Koordinat Sistemi Türleri</span><span class="sxs-lookup"><span data-stu-id="b41a7-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b41a7-103"> üç koordinat alanları kullanır: world, sayfa ve aygıt.</span><span class="sxs-lookup"><span data-stu-id="b41a7-103"> uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="b41a7-104">Dünya koordinat belirli bir grafik world model oluşturmak için kullanılan koordinatları ve .NET Framework yöntemlere geçirmek koordinatları.</span><span class="sxs-lookup"><span data-stu-id="b41a7-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="b41a7-105">Sayfa koordinat bir form veya denetim gibi bir çizim yüzeyini tarafından kullanılan koordinat sistemi bakın.</span><span class="sxs-lookup"><span data-stu-id="b41a7-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="b41a7-106">Cihaz koordinat ekran veya kağıt gibi sonuna çizilen bir fiziksel aygıt tarafından kullanılan koordinatlar belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b41a7-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="b41a7-107">Arama yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, geçişi için noktaları <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi —`(0, 0)` ve `(160, 80)`— dünya koordinat alanındadır.</span><span class="sxs-lookup"><span data-stu-id="b41a7-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="b41a7-108">Önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgi ekranda çizebilirsiniz, bir dizi dönüştürmeyi koordinatları geçirin.</span><span class="sxs-lookup"><span data-stu-id="b41a7-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="b41a7-109">Dünya dönüşümü adlı bir dönüşüm world koordinatları sayfa koordinatlara dönüştürür ve sayfa dönüşümü adlı başka bir dönüşüm sayfa koordinatları aygıt koordinatlara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b41a7-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="b41a7-110">Dönüşümler ve koordinat sistemleri</span><span class="sxs-lookup"><span data-stu-id="b41a7-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="b41a7-111">Sol üst köşe yerine istemci alanını gövdesinde kaynağına sahip bir koordinat sistemi çalışmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="b41a7-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="b41a7-112">Örneğin, istemci alanını sol kenarından 100 piksel ve istemci alanını üstünden 50 piksel olması için kaynak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="b41a7-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="b41a7-113">Aşağıdaki çizimde, bu tür bir koordinat sistemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b41a7-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="b41a7-114">![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="b41a7-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="b41a7-115">Arama yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, aşağıdaki çizimde gösterilen satır alın.</span><span class="sxs-lookup"><span data-stu-id="b41a7-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b41a7-116">![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="b41a7-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="b41a7-117">Üç koordinat alanları, satır uç noktalarına koordinatlarını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b41a7-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b41a7-118">Dünya</span><span class="sxs-lookup"><span data-stu-id="b41a7-118">World</span></span>|<span data-ttu-id="b41a7-119">(0, 0) için (160, 80)</span><span class="sxs-lookup"><span data-stu-id="b41a7-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="b41a7-120">Sayfa</span><span class="sxs-lookup"><span data-stu-id="b41a7-120">Page</span></span>|<span data-ttu-id="b41a7-121">(100, 50) için (260, 130)</span><span class="sxs-lookup"><span data-stu-id="b41a7-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="b41a7-122">Cihaz</span><span class="sxs-lookup"><span data-stu-id="b41a7-122">Device</span></span>|<span data-ttu-id="b41a7-123">(100, 50) için (260, 130)</span><span class="sxs-lookup"><span data-stu-id="b41a7-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="b41a7-124">Sayfa koordinat istemci alanını sol üst köşesinde kaynağına sahip olduğunu unutmayın; Bu durumda her zaman olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b41a7-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="b41a7-125">Ayrıca ölçü piksel olduğundan, cihaz koordinatları sayfa koordinatları ile aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b41a7-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="b41a7-126">Piksel (örneğin, inç) dışında bir şey için ölçü ayarlarsanız, aygıt koordinatları sayfa koordinatları farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b41a7-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="b41a7-127">Dünya koordinat sayfa koordinatlara eşler, dünya dönüşümü tutulur <xref:System.Drawing.Graphics.Transform%2A> özelliği <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b41a7-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="b41a7-128">Önceki örnekte, dünya dönüşümü x yönünde çeviri 100 birimlerinde y yönünde 50 birime ise.</span><span class="sxs-lookup"><span data-stu-id="b41a7-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="b41a7-129">Aşağıdaki örnek, dünya dönüşümü ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından kullanan <xref:System.Drawing.Graphics> Yukarıdaki çizimde gösterilen çizgi çizmek için nesnesi:</span><span class="sxs-lookup"><span data-stu-id="b41a7-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="b41a7-130">Sayfa dönüşümü sayfa koordinatları aygıt koordinatlara eşler.</span><span class="sxs-lookup"><span data-stu-id="b41a7-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="b41a7-131"><xref:System.Drawing.Graphics> SAX <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> sayfa dönüşümü düzenleme özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b41a7-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="b41a7-132"><xref:System.Drawing.Graphics> Sınıfı iki salt okunur özellikler sağlar <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>, yatay ve dikey inç başına nokta görüntü aygıtının incelenmesinin.</span><span class="sxs-lookup"><span data-stu-id="b41a7-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="b41a7-133">Kullanabileceğiniz <xref:System.Drawing.Graphics.PageUnit%2A> özelliği <xref:System.Drawing.Graphics> piksel dışında bir ölçü belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b41a7-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b41a7-134">Ayarlayamazsınız <xref:System.Drawing.Graphics.PageUnit%2A> özelliğine <xref:System.Drawing.GraphicsUnit.World>, bu fiziksel bir birim değil ve bir özel durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="b41a7-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="b41a7-135">Aşağıdaki örnek bir satırından çizer (0, 0) için (2, 1), burada noktası (2, 1), 2 inç sağına ve aşağı 1 inç noktasından (0, 0):</span><span class="sxs-lookup"><span data-stu-id="b41a7-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="b41a7-136">Kalem yapısı oluştururken kalem genişliği belirtmezseniz, önceki örnekte bir inç geniş bir çizgi çizin.</span><span class="sxs-lookup"><span data-stu-id="b41a7-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="b41a7-137">İkinci bağımsız değişkeni kalem genişliği belirtebilirsiniz <xref:System.Drawing.Pen> Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="b41a7-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="b41a7-138">Görüntü aygıtı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz, önceki örnekte satırının bitiş noktaları aşağıdaki koordinatları üç koordinat alanlarında vardır:</span><span class="sxs-lookup"><span data-stu-id="b41a7-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b41a7-139">Dünya</span><span class="sxs-lookup"><span data-stu-id="b41a7-139">World</span></span>|<span data-ttu-id="b41a7-140">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="b41a7-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="b41a7-141">Sayfa</span><span class="sxs-lookup"><span data-stu-id="b41a7-141">Page</span></span>|<span data-ttu-id="b41a7-142">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="b41a7-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="b41a7-143">Cihaz</span><span class="sxs-lookup"><span data-stu-id="b41a7-143">Device</span></span>|<span data-ttu-id="b41a7-144">(0, 0, için (192, 96)</span><span class="sxs-lookup"><span data-stu-id="b41a7-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="b41a7-145">Dünya koordinat kökeni istemci alanını sol üst köşesinde olduğundan, sayfa koordinatları world koordinatları ile aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b41a7-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="b41a7-146">Çeşitli efektler elde etmek için world ve sayfa dönüştürmeleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b41a7-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="b41a7-147">Örneğin, inç ölçü birimi kullanmak istediğiniz ve istemci alanını 1/2 inç istemci alanının üst ve sol kenarından 2 inç olacak şekilde, koordinat sistemi kökeni istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="b41a7-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="b41a7-148">Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesne ve bir satırından çizer (0, 0) için (2, 1):</span><span class="sxs-lookup"><span data-stu-id="b41a7-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="b41a7-149">Aşağıdaki çizimde satır ve koordinat sistemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b41a7-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="b41a7-150">![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="b41a7-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="b41a7-151">Görüntü aygıtı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz, önceki örnekte satırının bitiş noktaları aşağıdaki koordinatları üç koordinat alanlarında vardır:</span><span class="sxs-lookup"><span data-stu-id="b41a7-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b41a7-152">Dünya</span><span class="sxs-lookup"><span data-stu-id="b41a7-152">World</span></span>|<span data-ttu-id="b41a7-153">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="b41a7-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="b41a7-154">Sayfa</span><span class="sxs-lookup"><span data-stu-id="b41a7-154">Page</span></span>|<span data-ttu-id="b41a7-155">(2, 0,5) için (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="b41a7-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="b41a7-156">Cihaz</span><span class="sxs-lookup"><span data-stu-id="b41a7-156">Device</span></span>|<span data-ttu-id="b41a7-157">(192, 48) için (384, 144)</span><span class="sxs-lookup"><span data-stu-id="b41a7-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b41a7-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b41a7-158">See Also</span></span>  
 [<span data-ttu-id="b41a7-159">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b41a7-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="b41a7-160">Dönüşümlerin Matrisle Temsili</span><span class="sxs-lookup"><span data-stu-id="b41a7-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
