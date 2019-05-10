---
title: Bir Grafik Nesnesinin Durumunu Yönetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: be5042e62da6a9a8afd51af08b85dbe16d8eaac0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623631"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="f0efd-102">Bir Grafik Nesnesinin Durumunu Yönetme</span><span class="sxs-lookup"><span data-stu-id="f0efd-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="f0efd-103"><xref:System.Drawing.Graphics> Sınıftır yaklaşımının temelindeki [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0efd-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="f0efd-104">Herhangi bir şey çizmek için elde bir <xref:System.Drawing.Graphics> nesne özelliklerini ayarlayın ve yöntemlerinin çağrılması <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>vb.).</span><span class="sxs-lookup"><span data-stu-id="f0efd-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="f0efd-105">Aşağıdaki örnek çağrıları <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0efd-106">Geçirilen ilk bağımsız değişken <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="f0efd-107">Grafik Durumu</span><span class="sxs-lookup"><span data-stu-id="f0efd-107">Graphics State</span></span>  
 <span data-ttu-id="f0efd-108">A <xref:System.Drawing.Graphics> nesnesi birden fazla sağlayın çizim yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A> ve <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0efd-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="f0efd-109">A <xref:System.Drawing.Graphics> nesne Ayrıca, aşağıdaki kategorilere ayrılabilir grafik durumu, tutar:</span><span class="sxs-lookup"><span data-stu-id="f0efd-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="f0efd-110">Kalite ayarları</span><span class="sxs-lookup"><span data-stu-id="f0efd-110">Quality settings</span></span>  
  
- <span data-ttu-id="f0efd-111">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="f0efd-111">Transformations</span></span>  
  
- <span data-ttu-id="f0efd-112">Kırpma bölgesini</span><span class="sxs-lookup"><span data-stu-id="f0efd-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="f0efd-113">Kalite ayarları</span><span class="sxs-lookup"><span data-stu-id="f0efd-113">Quality Settings</span></span>  
 <span data-ttu-id="f0efd-114">A <xref:System.Drawing.Graphics> nesne çizilir öğeleri kalitesini etkileyen çeşitli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="f0efd-115">Örneğin, ayarlayabilirsiniz <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan (varsa) düzgünleştirme türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f0efd-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="f0efd-116">Kalite etkileyen diğer özellikleri <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, ve <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0efd-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="f0efd-117">Aşağıdaki örnek kümesine yumuşatma modu ile iki elipsler çizer <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> kümesine yumuşatma modu ile diğerini <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="f0efd-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="f0efd-118">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="f0efd-118">Transformations</span></span>  
 <span data-ttu-id="f0efd-119">A <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanır iki Dönüşümleri (dünya ve sayfa) tutar <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0efd-120">Afin herhangi bir dönüştürme gerçek koordinat dönüştürmesini içinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="f0efd-121">Afin dönüşümler ölçeklendirme, döndürme, yansıtma, eğme ve çevirme içerir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="f0efd-122">Sayfa dönüşümü, ölçekleme ve birimler (örneğin, piksel inç olarak) değiştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="f0efd-123">Daha fazla bilgi için [koordinat sistemleri ve dönüştürmeler](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="f0efd-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="f0efd-124">Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0efd-125">Gerçek koordinat dönüştürmesini bir 30 derece döndürme için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f0efd-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="f0efd-126">Böylece ikinci koordinatları geçirilen sayfa dönüşümü ayarlanır <xref:System.Drawing.Graphics.DrawEllipse%2A> milimetre yerine piksel olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="f0efd-127">Kod iki özdeş çağrılar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0efd-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="f0efd-128">Gerçek koordinat dönüştürmesini ilk uygulanan <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrısı ve her iki Dönüşümleri (dünya ve sayfa) ikinci uygulanır <xref:System.Drawing.Graphics.DrawEllipse%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="f0efd-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="f0efd-129">Aşağıdaki çizimde, iki üç nokta simgesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="f0efd-130">30 derece döndürme koordinat sisteminde (istemci alanını sol üst köşesinde) kaynağı hakkında üç nokta simgesini merkezleri hakkında değil unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0efd-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="f0efd-131">Ayrıca kalem genişliği 1 için ikinci üç noktanın 1 piksel artımlı ilk üç nokta işaretine ve 1 milimetre anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f0efd-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![İki üç nokta simgesini gösteren çizimde: döndürme ve Kalem genişliği.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="f0efd-133">Kırpma bölgesini</span><span class="sxs-lookup"><span data-stu-id="f0efd-133">Clipping Region</span></span>  
 <span data-ttu-id="f0efd-134">A <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanır bir kırpma bölgesini tutar <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0efd-135">Kırpma bölgesini çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0efd-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="f0efd-136">Aşağıdaki örnek, iki dikdörtgenler birleşimi oluşturan tarafından artı şeklindeki bir bölgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0efd-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="f0efd-137">Bu bölge kırpma bölgesini belirlenmiş bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0efd-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="f0efd-138">Ardından kod, kırpma bölgesini iç için kısıtlı olan iki satır çizer.</span><span class="sxs-lookup"><span data-stu-id="f0efd-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="f0efd-139">Kırpılmış satır aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f0efd-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Sınırlı kırpma bölgesini gösteren diyagram.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="f0efd-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0efd-141">See also</span></span>

- [<span data-ttu-id="f0efd-142">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="f0efd-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="f0efd-143">İç İçe Grafik Kapsayıcılarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0efd-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
