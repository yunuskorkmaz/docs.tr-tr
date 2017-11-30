---
title: "Bir Grafik Nesnesinin Durumunu Yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 438243d16d8031d99e27993cadb44fd58bbec0b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="77328-102">Bir Grafik Nesnesinin Durumunu Yönetme</span><span class="sxs-lookup"><span data-stu-id="77328-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="77328-103"><xref:System.Drawing.Graphics> Sınıftır merkezinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77328-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="77328-104">Herhangi bir şey çizmek için elde bir <xref:System.Drawing.Graphics> nesne özelliklerini ayarlamak ve yöntemlerini çağırın <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>vb.).</span><span class="sxs-lookup"><span data-stu-id="77328-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="77328-105">Aşağıdaki örnek çağrıları <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77328-106">Geçirilen ilk bağımsız değişken <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Pen> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a><span data-ttu-id="77328-107">Grafik Durumu</span><span class="sxs-lookup"><span data-stu-id="77328-107">Graphics State</span></span>  
 <span data-ttu-id="77328-108">A <xref:System.Drawing.Graphics> nesnesi birden fazla sağlayın çizim yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A> ve <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="77328-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="77328-109">A <xref:System.Drawing.Graphics> nesne ayrıca aşağıdaki kategorilere ayrılabilir grafik durumu korur:</span><span class="sxs-lookup"><span data-stu-id="77328-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="77328-110">Kalite ayarları</span><span class="sxs-lookup"><span data-stu-id="77328-110">Quality settings</span></span>  
  
-   <span data-ttu-id="77328-111">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="77328-111">Transformations</span></span>  
  
-   <span data-ttu-id="77328-112">Kırpma bölgesinin</span><span class="sxs-lookup"><span data-stu-id="77328-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="77328-113">Kalite ayarları</span><span class="sxs-lookup"><span data-stu-id="77328-113">Quality Settings</span></span>  
 <span data-ttu-id="77328-114">A <xref:System.Drawing.Graphics> nesnenin çizilir öğeleri kalitesini etkileyen çeşitli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="77328-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="77328-115">Örneğin, ayarlayabileceğiniz <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan düzgünleştirme (varsa) türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="77328-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="77328-116">Kalite etkileyen diğer özellikleri <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, ve <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="77328-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="77328-117">Aşağıdaki örnek kümesine yumuşatma mod ile iki elips çizer <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ve kümesine yumuşatma modu ile <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="77328-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a><span data-ttu-id="77328-118">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="77328-118">Transformations</span></span>  
 <span data-ttu-id="77328-119">A <xref:System.Drawing.Graphics> nesnesi tarafından çizilmiş tüm öğelerine uygulanan iki Dönüşümleri (world ve sayfa) tutar <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77328-120">Herhangi bir afin dönüştürme world dönüşümünde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="77328-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="77328-121">Afin dönüşümler ölçeklendirme, döndürme, yansıtma, eğriltme ve çevirme içerir.</span><span class="sxs-lookup"><span data-stu-id="77328-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="77328-122">Sayfa dönüşümü ölçekleme ve birimler (örneğin, piksel inç olarak) değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77328-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="77328-123">Daha fazla bilgi için bkz: [koordinat sistemleri ve dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="77328-123">For more information, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="77328-124">Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77328-125">Dünya dönüşümü için 30 derecelik döndürme ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="77328-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="77328-126">İkinci koordinatları geçirilen şekilde sayfa dönüşümü ayarlayın <xref:System.Drawing.Graphics.DrawEllipse%2A> piksel yerine milimetre olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="77328-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="77328-127">Kod iki özdeş çağrılar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77328-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="77328-128">Dünya dönüşümü ilk uygulanan <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrısı ve her iki dönüştürmeler (world ve sayfa) ikinci uygulanır <xref:System.Drawing.Graphics.DrawEllipse%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="77328-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 <span data-ttu-id="77328-129">Aşağıdaki çizimde iki elips gösterir.</span><span class="sxs-lookup"><span data-stu-id="77328-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="77328-130">30 derecelik döndürme (istemci alanının sol üst köşesinde) koordinat sistemi kökeni hakkında elipsleri merkezleri konusunda olmamasından unutmayın.</span><span class="sxs-lookup"><span data-stu-id="77328-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="77328-131">Ayrıca, 1 kalem genişliği için ikinci elips 1 piksel ilk üç nokta ve 1 milimetre anlamına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="77328-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 <span data-ttu-id="77328-132">![Oval](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span><span class="sxs-lookup"><span data-stu-id="77328-132">![Ovals](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span></span>  
  
### <a name="clipping-region"></a><span data-ttu-id="77328-133">Kırpma bölgesinin</span><span class="sxs-lookup"><span data-stu-id="77328-133">Clipping Region</span></span>  
 <span data-ttu-id="77328-134">A <xref:System.Drawing.Graphics> nesnesi tarafından çizilmiş tüm öğelere uygulanır kırpma bölgesinin tutar <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77328-135">Kırpma bölgesinin çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77328-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="77328-136">Aşağıdaki örnekte, iki dikdörtgen birleşimi oluşturan tarafından artı şeklinde bir bölge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77328-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="77328-137">Bu bölge kırpma bölgesinin atanmış bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77328-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="77328-138">Ardından kod kırpma bölgesinin iç için kısıtlı iki satır çizer.</span><span class="sxs-lookup"><span data-stu-id="77328-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 <span data-ttu-id="77328-139">Aşağıdaki çizimde kırpılmış satırları gösterir.</span><span class="sxs-lookup"><span data-stu-id="77328-139">The following illustration shows the clipped lines.</span></span>  
  
 <span data-ttu-id="77328-140">![Sınırlı Kırpma bölgesinin](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span><span class="sxs-lookup"><span data-stu-id="77328-140">![Limited Clip Region](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77328-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77328-141">See Also</span></span>  
 [<span data-ttu-id="77328-142">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="77328-142">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="77328-143">İç içe grafik kapsayıcılarını kullanma</span><span class="sxs-lookup"><span data-stu-id="77328-143">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
