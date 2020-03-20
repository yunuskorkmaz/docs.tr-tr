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
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182448"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="54f22-102">Bir Grafik Nesnesinin Durumunu Yönetme</span><span class="sxs-lookup"><span data-stu-id="54f22-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="54f22-103">Sınıf <xref:System.Drawing.Graphics> GDI+'nin kalbinde yer aldı.</span><span class="sxs-lookup"><span data-stu-id="54f22-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="54f22-104">Bir <xref:System.Drawing.Graphics> şey çizmek için, bir nesne elde, özelliklerini <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawImage%2A>ayarlamak <xref:System.Drawing.Graphics.DrawString%2A>ve yöntemleri , , , ve benzeri) diyoruz.</span><span class="sxs-lookup"><span data-stu-id="54f22-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="54f22-105">Aşağıdaki örnek, <xref:System.Drawing.Graphics.DrawRectangle%2A> bir <xref:System.Drawing.Graphics> nesnenin yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="54f22-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54f22-106"><xref:System.Drawing.Graphics.DrawRectangle%2A> Yönteme geçirilen ilk bağımsız <xref:System.Drawing.Pen> değişken bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="54f22-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="54f22-107">Grafik Durumu</span><span class="sxs-lookup"><span data-stu-id="54f22-107">Graphics State</span></span>  
 <span data-ttu-id="54f22-108">Bir <xref:System.Drawing.Graphics> nesne, çizim yöntemleri sağlamaktan <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>daha fazlasını yapar, gibi ve.</span><span class="sxs-lookup"><span data-stu-id="54f22-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="54f22-109">Bir <xref:System.Drawing.Graphics> nesne, aşağıdaki kategorilere bölünebilen grafik durumunu da korur:</span><span class="sxs-lookup"><span data-stu-id="54f22-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="54f22-110">Kalite ayarları</span><span class="sxs-lookup"><span data-stu-id="54f22-110">Quality settings</span></span>  
  
- <span data-ttu-id="54f22-111">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="54f22-111">Transformations</span></span>  
  
- <span data-ttu-id="54f22-112">Kırpma bölgesi</span><span class="sxs-lookup"><span data-stu-id="54f22-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="54f22-113">Kalite Ayarları</span><span class="sxs-lookup"><span data-stu-id="54f22-113">Quality Settings</span></span>  
 <span data-ttu-id="54f22-114">Nesne, <xref:System.Drawing.Graphics> çizilen öğelerin kalitesini etkileyen çeşitli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="54f22-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="54f22-115">Örneğin, <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan antiialiasing türünü (varsa) belirtecek şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54f22-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="54f22-116">Kaliteyi etkileyen diğer <xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.CompositingMode%2A>özellikler <xref:System.Drawing.Graphics.CompositingQuality%2A>, <xref:System.Drawing.Graphics.InterpolationMode%2A>, , ve .</span><span class="sxs-lookup"><span data-stu-id="54f22-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="54f22-117">Aşağıdaki örnek, biri yumuşatma modu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ayarlanmış, diğeri yumuşatma modu aşağıdakiler için ayarlanmış <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>iki elips çizer:</span><span class="sxs-lookup"><span data-stu-id="54f22-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="54f22-118">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="54f22-118">Transformations</span></span>  
 <span data-ttu-id="54f22-119">Nesne, <xref:System.Drawing.Graphics> o <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanan iki dönüşüm (dünya ve sayfa) tutar.</span><span class="sxs-lookup"><span data-stu-id="54f22-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54f22-120">Herhangi bir affine dönüşüm dünya dönüşümünde saklanabilir.</span><span class="sxs-lookup"><span data-stu-id="54f22-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="54f22-121">Affine dönüşümleri ölçekleme, döndürme, yansıtma, eğriltme ve çevirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="54f22-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="54f22-122">Sayfa dönüştürme ölçekleme ve birimleri değiştirmek için kullanılabilir (örneğin, pikselden inç'e).</span><span class="sxs-lookup"><span data-stu-id="54f22-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="54f22-123">Daha fazla bilgi için [Bkz. Koordinat Sistemleri ve Dönüşümler.](coordinate-systems-and-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="54f22-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="54f22-124">Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnenin dünya ve sayfa dönüşümlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="54f22-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54f22-125">Dünya dönüşümü 30 derecelik bir dönüşe ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="54f22-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="54f22-126">Sayfa dönüşümü, ikinciye <xref:System.Drawing.Graphics.DrawEllipse%2A> geçen koordinatların piksel yerine milimetre olarak kabul edilebis olması için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="54f22-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="54f22-127"><xref:System.Drawing.Graphics.DrawEllipse%2A> Kod, yönteme iki özdeş arama yapar.</span><span class="sxs-lookup"><span data-stu-id="54f22-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="54f22-128">Dünya dönüşümü ilk <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrıya uygulanır, ikinci <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrıya da dönüşümler (dünya ve sayfa) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="54f22-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="54f22-129">Aşağıdaki resimde iki elips gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54f22-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="54f22-130">30 derecelik döndürmenin koordinat sisteminin (istemci alanının sol üst köşesi) kökeni yle ilgili olduğunu unutmayın, elipslerin merkezleri yle ilgili değil.</span><span class="sxs-lookup"><span data-stu-id="54f22-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="54f22-131">Ayrıca, kalem genişliğinin ilk elips için 1 piksel ve ikinci elips için 1 milimetre anlamına geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="54f22-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![İki elips gösteren çizim: döndürme ve kalem genişliği.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="54f22-133">Kırpma Bölgesi</span><span class="sxs-lookup"><span data-stu-id="54f22-133">Clipping Region</span></span>  
 <span data-ttu-id="54f22-134">Nesne, <xref:System.Drawing.Graphics> o <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğeler için geçerli olan bir kırpma bölgesi tutar.</span><span class="sxs-lookup"><span data-stu-id="54f22-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54f22-135">Yöntemi arayarak kırpma bölgesini <xref:System.Drawing.Graphics.SetClip%2A> ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54f22-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="54f22-136">Aşağıdaki örnek, iki dikdörtgenin birleşimini oluşturarak artı şekilli bir bölge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54f22-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="54f22-137">Bu bölge, bir <xref:System.Drawing.Graphics> nesnenin kırpma bölgesi olarak belirlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="54f22-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54f22-138">Ardından kod, kırpma bölgesinin iç kısmıyla sınırlı iki satır çizer.</span><span class="sxs-lookup"><span data-stu-id="54f22-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="54f22-139">Aşağıdaki resimde kırpılalı çizgiler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="54f22-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Sınırlı klip bölgesini gösteren diyagram.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="54f22-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54f22-141">See also</span></span>

- [<span data-ttu-id="54f22-142">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="54f22-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="54f22-143">İç İçe Grafik Kapsayıcılarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="54f22-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
