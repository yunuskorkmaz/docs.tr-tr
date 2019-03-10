---
title: GDI+'da Kalemler, Çizgiler ve Dikdörtgenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 91f41fb4acf5ec174bd76498a70aed3dcda076f9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705751"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="088ce-102">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="088ce-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="088ce-103">İle çizgi çizmek için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oluşturmak gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="088ce-103">To draw lines with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="088ce-104"><xref:System.Drawing.Graphics> Nesne çizim yapan yöntemler sağlar ve <xref:System.Drawing.Pen> nesnesi gibi çizgi rengini, genişliğini ve stili özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="088ce-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="088ce-105">Bir çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="088ce-105">Drawing a Line</span></span>  
 <span data-ttu-id="088ce-106">Bir çizgi çizmek için çağrı <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="088ce-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="088ce-107"><xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen nesne <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="088ce-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="088ce-108">Aşağıdaki örnek, (4, 2) noktadan noktaya (12, 6) bir çizgi çizer:</span><span class="sxs-lookup"><span data-stu-id="088ce-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="088ce-109"><xref:System.Drawing.Graphics.DrawLine%2A> Aşırı yüklenmiş bir yöntemidir <xref:System.Drawing.Graphics> çeşitli yolları sağladığınız bu bağımsız değişkenlerle olduklarından sınıfı.</span><span class="sxs-lookup"><span data-stu-id="088ce-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="088ce-110">Örneğin, iki oluşturabilirsiniz <xref:System.Drawing.Point> nesneleri ve pass <xref:System.Drawing.Point> bağımsız değişkenleri olarak nesneleri <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="088ce-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="088ce-111">Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="088ce-111">Constructing a Pen</span></span>  
 <span data-ttu-id="088ce-112">Oluşturduğunuzda, belirli öznitelikleri belirtebileceğiniz bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="088ce-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="088ce-113">Örneğin, bir `Pen` oluşturucusu, renk ve genişlik belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="088ce-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="088ce-114">Aşağıdaki örnek 2 genişliğini mavi bir çizgi çizer (0, 0) için (60, 30):</span><span class="sxs-lookup"><span data-stu-id="088ce-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="088ce-115">Kesik çizgi ve satır Caps</span><span class="sxs-lookup"><span data-stu-id="088ce-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="088ce-116"><xref:System.Drawing.Pen> Nesne de sunan özellikler gibi <xref:System.Drawing.Pen.DashStyle%2A>, satırın özelliklerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="088ce-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="088ce-117">Aşağıdaki örnek kesikli bir çizgi çizer (100, 50) için (300, 80):</span><span class="sxs-lookup"><span data-stu-id="088ce-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="088ce-118">Özelliklerini kullanabilirsiniz <xref:System.Drawing.Pen> nesne çok daha fazla satır özniteliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="088ce-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="088ce-119"><xref:System.Drawing.Pen.StartCap%2A> Ve <xref:System.Drawing.Pen.EndCap%2A> özellikler çizginin uçlarını görünümünü belirtin; uçları olabilir düz, kare, yuvarlak, üçgen, ya da özel bir şekil.</span><span class="sxs-lookup"><span data-stu-id="088ce-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="088ce-120"><xref:System.Drawing.Pen.LineJoin%2A> Özelliği, bağlı çizgiler (keskin köşeleri ile birleştirilmiş) gönye Eğimli, yuvarlak veya kırpılarak olup olmadığını belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="088ce-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="088ce-121">Aşağıdaki çizimde, çeşitli büyük harf ve birleştirme stilleri sahip satırları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="088ce-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="088ce-122">![Satırları](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="088ce-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="088ce-123">Dikdörtgen çizme</span><span class="sxs-lookup"><span data-stu-id="088ce-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="088ce-124">İle dikdörtgenler çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] satırlar çizme için benzer.</span><span class="sxs-lookup"><span data-stu-id="088ce-124">Drawing rectangles with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is similar to drawing lines.</span></span> <span data-ttu-id="088ce-125">Bir dikdörtgen çizmek için gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="088ce-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="088ce-126"><xref:System.Drawing.Graphics> Nesnesi sağlayan bir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesneyi çizgi genişliği ve rengine gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="088ce-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="088ce-127"><xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen nesne <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="088ce-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="088ce-128">Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (100, 50) bir 80 genişlik ve yükseklik 40'a:</span><span class="sxs-lookup"><span data-stu-id="088ce-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="088ce-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> Aşırı yüklenmiş bir yöntemidir <xref:System.Drawing.Graphics> çeşitli yolları sağladığınız bu bağımsız değişkenlerle olduklarından sınıfı.</span><span class="sxs-lookup"><span data-stu-id="088ce-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="088ce-130">Örneğin, oluşturun bir <xref:System.Drawing.Rectangle> nesne ve geçirin <xref:System.Drawing.Rectangle> nesnesini <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="088ce-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="088ce-131">A <xref:System.Drawing.Rectangle> nesnesi yöntemlerini ve özelliklerini düzenleme ve dikdörtgen hakkında bilgileri toplamak için sahiptir.</span><span class="sxs-lookup"><span data-stu-id="088ce-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="088ce-132">Örneğin, <xref:System.Drawing.Rectangle.Inflate%2A> ve <xref:System.Drawing.Rectangle.Offset%2A> yöntemleri, boyutunu ve konumunu dikdörtgenin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="088ce-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="088ce-133"><xref:System.Drawing.Rectangle.IntersectsWith%2A> Yöntemi bildirir olup dikdörtgen başka kesişip dikdörtgen, verilen ve <xref:System.Drawing.Rectangle.Contains%2A> yöntemi söyler, belirli bir noktaya dikdörtgen içinde olup.</span><span class="sxs-lookup"><span data-stu-id="088ce-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088ce-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="088ce-134">See also</span></span>
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [<span data-ttu-id="088ce-135">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="088ce-135">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="088ce-136">Nasıl yapılır: Bir Windows formunda çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="088ce-136">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)
- [<span data-ttu-id="088ce-137">Nasıl yapılır: Anahatlı şekil çizme</span><span class="sxs-lookup"><span data-stu-id="088ce-137">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
