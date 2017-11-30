---
title: "GDI+'da Kalemler, Çizgiler ve Dikdörtgenler"
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b72bbaef26e1c61f86e354adc7df7404469ee0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="cf827-102">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="cf827-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="cf827-103">Satırıyla çizmek için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oluşturmak gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="cf827-103">To draw lines with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="cf827-104"><xref:System.Drawing.Graphics> Nesne gerçekten çizimi yapmak yöntemler sağlar ve <xref:System.Drawing.Pen> nesnesi çizgi rengini, genişliğini ve stil gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="cf827-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="cf827-105">Bir çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="cf827-105">Drawing a Line</span></span>  
 <span data-ttu-id="cf827-106">Bir çizgi çizmek için çağrı <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cf827-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cf827-107"><xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf827-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="cf827-108">Aşağıdaki örnekte bir satırı (4, 2) noktasından (12, 6) noktasına çizilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf827-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="cf827-109"><xref:System.Drawing.Graphics.DrawLine%2A>Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf827-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="cf827-110">Örneğin, iki oluşturabileceğiniz <xref:System.Drawing.Point> nesneleri ve geçişi <xref:System.Drawing.Point> nesneleri bağımsız değişken olarak <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cf827-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="cf827-111">Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf827-111">Constructing a Pen</span></span>  
 <span data-ttu-id="cf827-112">Oluşturduğunuz zaman, belirli öznitelikleri belirtebilirsiniz bir <xref:System.Drawing.Pen> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cf827-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="cf827-113">Örneğin, bir `Pen` oluşturucusu, renk ve genişlik belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf827-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="cf827-114">Aşağıdaki örnek mavi bir çizgi genişliği 2 çizer (0, 0) için (60, 30):</span><span class="sxs-lookup"><span data-stu-id="cf827-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="cf827-115">Kesikli satırları ve satır Caps</span><span class="sxs-lookup"><span data-stu-id="cf827-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="cf827-116"><xref:System.Drawing.Pen> Nesneyi de kullanıma sunan özellikleri gibi <xref:System.Drawing.Pen.DashStyle%2A>, satırın özelliklerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf827-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="cf827-117">Aşağıdaki örnek bir kesikli çizgi çizer (100, 50) için (300, 80):</span><span class="sxs-lookup"><span data-stu-id="cf827-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="cf827-118">Özelliklerini kullanabilirsiniz <xref:System.Drawing.Pen> nesne pek çok daha fazla çizgi özniteliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf827-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="cf827-119"><xref:System.Drawing.Pen.StartCap%2A> Ve <xref:System.Drawing.Pen.EndCap%2A> özellikleri satır uçlarından görünümünü belirtin; düz, kare, yuvarlatılmış, üçgen, uçları olabilir veya özel bir şekli.</span><span class="sxs-lookup"><span data-stu-id="cf827-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="cf827-120"><xref:System.Drawing.Pen.LineJoin%2A> Özelliği bağlı çizgilere (keskin köşeleri ile birleştirilen) gönye, Eğimli, yuvarlatılmış veya kırpılmış olup olmadığını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf827-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="cf827-121">Aşağıdaki çizimde çeşitli cap ve birleştirme stilleri çizgilerle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="cf827-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="cf827-122">![Satırları](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="cf827-122">![Lines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="cf827-123">Dikdörtgene çizme</span><span class="sxs-lookup"><span data-stu-id="cf827-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="cf827-124">İle dikdörtgenler çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] satırlar çizme için benzer.</span><span class="sxs-lookup"><span data-stu-id="cf827-124">Drawing rectangles with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is similar to drawing lines.</span></span> <span data-ttu-id="cf827-125">Dikdörtgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="cf827-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="cf827-126"><xref:System.Drawing.Graphics> Nesnesi sağlar bir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi çizgi genişliğini ve renk gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="cf827-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="cf827-127"><xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf827-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="cf827-128">Aşağıdaki örnek, sol üst köşede bir dikdörtgen çizer (100, 50), bir 80 genişliği ve yüksekliği 40 bir:</span><span class="sxs-lookup"><span data-stu-id="cf827-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="cf827-129"><xref:System.Drawing.Graphics.DrawRectangle%2A>Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf827-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="cf827-130">Örneğin, oluşturabileceğiniz bir <xref:System.Drawing.Rectangle> nesne ve geçirin <xref:System.Drawing.Rectangle> nesnesinin <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="cf827-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="cf827-131">A <xref:System.Drawing.Rectangle> nesnesi yöntemlerini ve özelliklerini düzenleme ve dikdörtgen hakkında bilgi toplanıyor sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cf827-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="cf827-132">Örneğin, <xref:System.Drawing.Rectangle.Inflate%2A> ve <xref:System.Drawing.Rectangle.Offset%2A> yöntemleri boyutunu ve konumunu dikdörtgenin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cf827-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="cf827-133"><xref:System.Drawing.Rectangle.IntersectsWith%2A> Yöntemi bildirir olup dikdörtgen başka kesiştiğinden dikdörtgen, verilen ve <xref:System.Drawing.Rectangle.Contains%2A> yöntemi söyler, verilen bir noktaya dikdörtgende olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="cf827-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf827-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf827-134">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [<span data-ttu-id="cf827-135">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf827-135">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="cf827-136">Nasıl yapılır: bir Windows formunda çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="cf827-136">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [<span data-ttu-id="cf827-137">Nasıl yapılır: Anahatlı şekil çizme</span><span class="sxs-lookup"><span data-stu-id="cf827-137">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
