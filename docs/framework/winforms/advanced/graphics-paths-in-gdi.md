---
title: GDI+'da Grafik Yolları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523895"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="1d466-102">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="1d466-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="1d466-103">Yollar çizgiler, dikdörtgenler ve basit Eğriler birleştirerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d466-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="1d466-104">Gelen geri çağırma [vektör grafiklerine genel bakış](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) resim çizim için en kullanışlı olması için aşağıdaki temel yapı taşlarının kanıtlanmış:</span><span class="sxs-lookup"><span data-stu-id="1d466-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="1d466-105">satırları</span><span class="sxs-lookup"><span data-stu-id="1d466-105">Lines</span></span>  
  
-   <span data-ttu-id="1d466-106">Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="1d466-106">Rectangles</span></span>  
  
-   <span data-ttu-id="1d466-107">Üç nokta</span><span class="sxs-lookup"><span data-stu-id="1d466-107">Ellipses</span></span>  
  
-   <span data-ttu-id="1d466-108">Yaylar</span><span class="sxs-lookup"><span data-stu-id="1d466-108">Arcs</span></span>  
  
-   <span data-ttu-id="1d466-109">Çokgenler</span><span class="sxs-lookup"><span data-stu-id="1d466-109">Polygons</span></span>  
  
-   <span data-ttu-id="1d466-110">Ana Eğriler</span><span class="sxs-lookup"><span data-stu-id="1d466-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="1d466-111">Bézier eğrileri</span><span class="sxs-lookup"><span data-stu-id="1d466-111">Bézier splines</span></span>  
  
 <span data-ttu-id="1d466-112">GDI +'daki <xref:System.Drawing.Drawing2D.GraphicsPath> nesne dizisi bu yapı taşları tek bir birimde toplamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d466-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="1d466-113">Çizgiler, dikdörtgenler, çokgenler ve eğriler tüm dizisini sonra yapılan bir çağrı ile çizilebilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1d466-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="1d466-114">Aşağıdaki çizimde bir satır, bir yay, Bézier eğrisi ve Kardinal eğri birleştirilerek oluşturulan bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d466-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="1d466-115">![Yol](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="1d466-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="1d466-116">Bir yol kullanarak</span><span class="sxs-lookup"><span data-stu-id="1d466-116">Using a Path</span></span>  
 <span data-ttu-id="1d466-117"><xref:System.Drawing.Drawing2D.GraphicsPath> Sınıfı çizilmesi öğelerinin bir dizisini oluşturmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d466-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="1d466-118">Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listesi destekler.</span><span class="sxs-lookup"><span data-stu-id="1d466-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="1d466-119">Örneğin, bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi alır dört tamsayılar ve başka bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi iki alan <xref:System.Drawing.Point> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1d466-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="1d466-120">Tek bir çağrı yolunda birkaç öğe ekleme çoğul yardımcı yöntemi çizgiler, dikdörtgenler ve Bézier eğrileri yolunu eklemek için yöntemi vardır: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d466-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="1d466-121">Ayrıca, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> yöntemlerine sahip yardımcı yöntemler <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, eklemek kapalı eğri veya pasta yolu.</span><span class="sxs-lookup"><span data-stu-id="1d466-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="1d466-122">Bir yol çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Pen> nesnesini ve bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1d466-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="1d466-123"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi genişlik ve yolun işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="1d466-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="1d466-124"><xref:System.Drawing.Drawing2D.GraphicsPath> Nesnesi çizgiler ve yolunu oluşturur eğriler dizisi saklar.</span><span class="sxs-lookup"><span data-stu-id="1d466-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="1d466-125"><xref:System.Drawing.Pen> Nesne ve <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d466-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="1d466-126">Aşağıdaki örnekte bir satır, elips ve Bézier eğrisi oluşan bir yol çizilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1d466-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="1d466-127">Aşağıdaki çizimde yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d466-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="1d466-128">![Yol](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="1d466-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="1d466-129">Çizgiler, dikdörtgenler ve Eğriler için bir yol ekleme ek olarak, bir yol yolları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d466-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="1d466-130">Bu, büyük ve karmaşık yollar oluşturmak için var olan yollar birleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d466-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="1d466-131">Bir yol ekleyebilirsiniz iki başka öğeler vardır: dizeler ve Pastalar.</span><span class="sxs-lookup"><span data-stu-id="1d466-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="1d466-132">Bir pasta elips iç bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="1d466-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="1d466-133">Aşağıdaki örnek, Yayı Kardinal eğri, bir dize ve bir pasta bir yol oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1d466-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="1d466-134">Aşağıdaki çizimde yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d466-134">The following illustration shows the path.</span></span> <span data-ttu-id="1d466-135">Unutmayın; bir yolu, bağlı olması gerekmez. Yayı Kardinal eğri, dize ve pasta ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1d466-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="1d466-136">![Yollar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="1d466-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d466-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d466-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="1d466-138">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="1d466-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="1d466-139">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d466-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="1d466-140">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="1d466-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
