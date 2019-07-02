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
ms.openlocfilehash: 24079f24bdae5fefd785a20dda9b29a190fb4068
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505253"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="7ffe2-102">Koordinat Sistemi Türleri</span><span class="sxs-lookup"><span data-stu-id="7ffe2-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="7ffe2-103">GDI +'da üç koordinat kullanır: dünya, sayfa ve cihaz.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="7ffe2-104">Dünya koordinatlarını bir belirli grafik grubuna ilişkin model için kullanılan koordinatları ve .NET Framework yöntemleri için geçirdiğiniz koordinatları.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="7ffe2-105">Bir form veya denetim gibi çizim yüzeyi tarafından kullanılan koordinat sistemini sayfa koordinatlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="7ffe2-106">Cihaz, bir ekran veya kağıt gibi üzerine çizilmiş fiziksel cihaz tarafından kullanılan koordinat koordinatları.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="7ffe2-107">Çağrısı yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, geçirdiğiniz noktaları <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi —`(0, 0)` ve `(160, 80)`— dünyanın koordinat alanındadır.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="7ffe2-108">GDI +'da satırın ekranda çizebilirsiniz önce bir dizi dönüştürmeyi koordinatları geçirin.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="7ffe2-109">Gerçek koordinat dönüştürmesini adlı bir dönüştürme dünya koordinatlarını sayfa koordinatlarına dönüştüren ve sayfa dönüşümü adlı başka bir dönüştürme sayfa koordinatlarına cihaz koordinatlarına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="7ffe2-110">Dönüşümler ve koordinat sistemi</span><span class="sxs-lookup"><span data-stu-id="7ffe2-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="7ffe2-111">Sol üst köşesinin yerine istemci alanını gövdesine, kaynağı olan bir koordinat sistemi çalışmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="7ffe2-112">Örneğin, istemci alanın sol kenarından 100 piksel ve 50 piksel istemci alanının üst kaynağı istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="7ffe2-113">Aşağıdaki çizimde, böyle bir koordinat sistemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="7ffe2-114">![Koordinat sistemi](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="7ffe2-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="7ffe2-115">Çağrısı yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, aşağıdaki çizimde gösterilen satır alın.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="7ffe2-116">![Koordinat sistemi](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="7ffe2-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="7ffe2-117">Üç koordinat satırınızda bitiş noktası koordinatları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7ffe2-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ffe2-118">Dünya</span><span class="sxs-lookup"><span data-stu-id="7ffe2-118">World</span></span>|<span data-ttu-id="7ffe2-119">(0, 0) için (160, 80)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="7ffe2-120">Sayfa</span><span class="sxs-lookup"><span data-stu-id="7ffe2-120">Page</span></span>|<span data-ttu-id="7ffe2-121">(100, 50) için (260, 130)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="7ffe2-122">Cihaz</span><span class="sxs-lookup"><span data-stu-id="7ffe2-122">Device</span></span>|<span data-ttu-id="7ffe2-123">(100, 50) için (260, 130)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="7ffe2-124">Sayfa koordinat istemci alanını sol üst köşesinde kaynağına sahip olduğunu unutmayın; her zaman, bu durumda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="7ffe2-125">Ayrıca piksel ölçü olduğundan, cihaz koordinatlarını sayfa koordinatlarına aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="7ffe2-126">Piksel (örneğin, inç) dışında bir ölçü ayarlarsanız, cihaz koordinatlarını sayfa koordinatlarına farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="7ffe2-127">Dünya koordinatlarını sayfa koordinatlarına eşler, gerçek koordinat dönüştürmesini tutulur <xref:System.Drawing.Graphics.Transform%2A> özelliği <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="7ffe2-128">Önceki örnekte gerçek koordinat dönüştürmesini çeviri 100 birim x yönünde ve y yönünde 50 Birim var.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="7ffe2-129">Aşağıdaki örnek, gerçek koordinat dönüştürmesini ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından kullanan <xref:System.Drawing.Graphics> önceki şekilde gösterildiği çizgi çizmek için nesne:</span><span class="sxs-lookup"><span data-stu-id="7ffe2-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="7ffe2-130">Sayfa dönüşümü için cihaz koordinatlarını sayfa koordinatlarına eşler.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="7ffe2-131"><xref:System.Drawing.Graphics> Sağlar sınıfını <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> sayfa dönüşümü düzenlemek için özellikler.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="7ffe2-132"><xref:System.Drawing.Graphics> Sınıfı iki salt okunur özellikler sağlar <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>, yatay ve dikey inç başına nokta görünen cihazın İnceleme için.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="7ffe2-133">Kullanabileceğiniz <xref:System.Drawing.Graphics.PageUnit%2A> özelliği <xref:System.Drawing.Graphics> piksel dışındaki bir ölçü belirtmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ffe2-134">Ayarlayamazsınız <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini <xref:System.Drawing.GraphicsUnit.World>, fiziksel bir birim değil ve bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="7ffe2-135">Aşağıdaki örnek bir çizgi çizer (0, 0) için (2, 1), burada noktası (2, 1), 2 inç sağa ve aşağı 1 inç noktasından (0, 0):</span><span class="sxs-lookup"><span data-stu-id="7ffe2-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="7ffe2-136">Kalemi oluştururken bir kalem genişliği belirtmezseniz, önceki örnekte geniş bir inç bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="7ffe2-137">Kalem genişliği ikinci bağımsız değişkeni belirtebilirsiniz <xref:System.Drawing.Pen> Oluşturucusu:</span><span class="sxs-lookup"><span data-stu-id="7ffe2-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="7ffe2-138">Görüntü cihazı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz önceki örnekte çizginin bitiş noktaları üç koordinat alanlarındaki aşağıdaki koordinatlar vardır:</span><span class="sxs-lookup"><span data-stu-id="7ffe2-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ffe2-139">Dünya</span><span class="sxs-lookup"><span data-stu-id="7ffe2-139">World</span></span>|<span data-ttu-id="7ffe2-140">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="7ffe2-141">Sayfa</span><span class="sxs-lookup"><span data-stu-id="7ffe2-141">Page</span></span>|<span data-ttu-id="7ffe2-142">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="7ffe2-143">Cihaz</span><span class="sxs-lookup"><span data-stu-id="7ffe2-143">Device</span></span>|<span data-ttu-id="7ffe2-144">(0, 0, için (192, 96)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="7ffe2-145">Dünya koordinat kaynağı istemci alanını sol üst köşesinde olduğundan, sayfa koordinatlarına dünya koordinatları ile aynı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="7ffe2-146">Çeşitli efektler elde etmek için world ve sayfa dönüştürmeleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="7ffe2-147">Örneğin, ölçü birimi olarak inç kullanmak istediğiniz ve istemci alanını 1/2 inç istemci alanının üst ve sol kenarından 2 inç olacak şekilde, koordinat sistemi kaynağını istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="7ffe2-148">Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından bir çizgi çizer (0, 0) için (2, 1):</span><span class="sxs-lookup"><span data-stu-id="7ffe2-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="7ffe2-149">Çizgi ve koordinat sistemini aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="7ffe2-150">![Koordinat sistemi](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="7ffe2-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="7ffe2-151">Görüntü cihazı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz önceki örnekte çizginin bitiş noktaları üç koordinat alanlarındaki aşağıdaki koordinatlar vardır:</span><span class="sxs-lookup"><span data-stu-id="7ffe2-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ffe2-152">Dünya</span><span class="sxs-lookup"><span data-stu-id="7ffe2-152">World</span></span>|<span data-ttu-id="7ffe2-153">(0, 0) için (2, 1)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="7ffe2-154">Sayfa</span><span class="sxs-lookup"><span data-stu-id="7ffe2-154">Page</span></span>|<span data-ttu-id="7ffe2-155">(2, 0,5) için (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="7ffe2-156">Cihaz</span><span class="sxs-lookup"><span data-stu-id="7ffe2-156">Device</span></span>|<span data-ttu-id="7ffe2-157">(192, 48) için (384, 144)</span><span class="sxs-lookup"><span data-stu-id="7ffe2-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ffe2-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ffe2-158">See also</span></span>

- [<span data-ttu-id="7ffe2-159">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="7ffe2-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="7ffe2-160">Dönüşümlerin Matrisle Temsili</span><span class="sxs-lookup"><span data-stu-id="7ffe2-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
