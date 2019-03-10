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
ms.openlocfilehash: b6f0ebd500aa3503c0c0d473ebe21a61f4438862
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720429"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="cf14f-102">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="cf14f-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="cf14f-103">Yolları çizgiler, dikdörtgenler ve basit eğrileri birleştirerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cf14f-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="cf14f-104">Geri çekilemedi [vektör grafiklerine genel bakış](vector-graphics-overview.md) resimler çizmek için en kullanışlı olması için aşağıdaki temel yapı taşlarını kanıtladıktan:</span><span class="sxs-lookup"><span data-stu-id="cf14f-104">Recall from the [Vector Graphics Overview](vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="cf14f-105">satırları</span><span class="sxs-lookup"><span data-stu-id="cf14f-105">Lines</span></span>  
  
-   <span data-ttu-id="cf14f-106">Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="cf14f-106">Rectangles</span></span>  
  
-   <span data-ttu-id="cf14f-107">Ellipses</span><span class="sxs-lookup"><span data-stu-id="cf14f-107">Ellipses</span></span>  
  
-   <span data-ttu-id="cf14f-108">Yay</span><span class="sxs-lookup"><span data-stu-id="cf14f-108">Arcs</span></span>  
  
-   <span data-ttu-id="cf14f-109">Çokgenler</span><span class="sxs-lookup"><span data-stu-id="cf14f-109">Polygons</span></span>  
  
-   <span data-ttu-id="cf14f-110">Ana Eğriler</span><span class="sxs-lookup"><span data-stu-id="cf14f-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="cf14f-111">Bézier eğrileri</span><span class="sxs-lookup"><span data-stu-id="cf14f-111">Bézier splines</span></span>  
  
 <span data-ttu-id="cf14f-112">GDI +'ta, <xref:System.Drawing.Drawing2D.GraphicsPath> nesne, bu yapı taşlarını bir dizi tek bir birimde toplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf14f-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="cf14f-113">Tüm satırları, dikdörtgenler, çokgenler ve eğriler dizisini ardından bir çağrı ile kurulabilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf14f-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="cf14f-114">Aşağıdaki çizimde, bir satır, bir yay Bézier eğri ve Kardinal eğri birleştirilerek oluşturulan bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf14f-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="cf14f-115">![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="cf14f-115">![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="cf14f-116">Bir yol kullanma</span><span class="sxs-lookup"><span data-stu-id="cf14f-116">Using a Path</span></span>  
 <span data-ttu-id="cf14f-117"><xref:System.Drawing.Drawing2D.GraphicsPath> Sınıfı çizilecek öğelerinin bir dizisini oluşturmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf14f-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="cf14f-118">Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="cf14f-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="cf14f-119">Örneğin, bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi alır dört tamsayının ve başka bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi iki alan <xref:System.Drawing.Point> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cf14f-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="cf14f-120">Çizgiler ve dikdörtgenler Bézier eğrileri yolu eklemek için yöntemi birkaç öğeleri tek bir arama yoluna ekle çoğul yardımcı yöntemleri vardır: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf14f-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="cf14f-121">Ayrıca, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> yöntemlerine sahip yardımcı yöntemler <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, ekleyen bir kapalı eğri ya da pasta yolu.</span><span class="sxs-lookup"><span data-stu-id="cf14f-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="cf14f-122">Bir yol çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Pen> nesnesi ve bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne.</span><span class="sxs-lookup"><span data-stu-id="cf14f-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="cf14f-123"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi ve <xref:System.Drawing.Pen> nesneyi genişlik ve yolun işlemek için kullanılan çizginin rengi gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="cf14f-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="cf14f-124"><xref:System.Drawing.Drawing2D.GraphicsPath> Çizgiler ve eğrilerle yolu kolaylaştıran bir dizi nesnesini depolar.</span><span class="sxs-lookup"><span data-stu-id="cf14f-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="cf14f-125"><xref:System.Drawing.Pen> Nesne ve <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bağımsız değişkenleri olarak geçirilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf14f-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="cf14f-126">Aşağıdaki örnek, bir satır, bir elips ve Bézier eğri oluşan bir yol çizer:</span><span class="sxs-lookup"><span data-stu-id="cf14f-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="cf14f-127">Aşağıdaki çizimde yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf14f-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="cf14f-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="cf14f-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="cf14f-129">Çizgiler, dikdörtgenler ve eğriler yolunu eklemenin yanı sıra, bir yol yollar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf14f-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="cf14f-130">Bu, büyük ve karmaşık yolları oluşturmak için mevcut yolları birleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf14f-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="cf14f-131">Yolu ekleyebileceğiniz iki öğe: dizeleri ve pasta.</span><span class="sxs-lookup"><span data-stu-id="cf14f-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="cf14f-132">Bir pasta, bir elipsin iç bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="cf14f-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="cf14f-133">Aşağıdaki örnek, Yayı Kardinal eğri, bir dize ve bir pasta bir yol oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cf14f-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="cf14f-134">Aşağıdaki çizimde yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf14f-134">The following illustration shows the path.</span></span> <span data-ttu-id="cf14f-135">Unutmayın; bir yolu, bağlı olması gerekmez. Yayı Kardinal eğri, dize ve pasta ayrılır.</span><span class="sxs-lookup"><span data-stu-id="cf14f-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="cf14f-136">![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="cf14f-136">![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf14f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf14f-137">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="cf14f-138">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="cf14f-138">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="cf14f-139">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf14f-139">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="cf14f-140">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="cf14f-140">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
