---
title: Şekiller ve temel çizime genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731627"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="2e85c-102">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="2e85c-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="2e85c-103">Bu konu, <xref:System.Windows.Shapes.Shape> nesneleriyle nasıl çizileceğini gösteren bir genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="2e85c-104"><xref:System.Windows.Shapes.Shape>, ekrana şekil çizmenizi sağlayan bir <xref:System.Windows.UIElement> türüdür.</span><span class="sxs-lookup"><span data-stu-id="2e85c-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="2e85c-105">UI öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="2e85c-106">, grafik ve işleme hizmetlerine birkaç farklı erişim katmanı sunar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="2e85c-107">Üst katmanda <xref:System.Windows.Shapes.Shape> nesnelerinin kullanımı kolaydır ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemine düzen ve katılım gibi birçok yararlı özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="2e85c-108">Şekil nesneleri</span><span class="sxs-lookup"><span data-stu-id="2e85c-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="2e85c-109">, kullanıma yönelik birkaç <xref:System.Windows.Shapes.Shape> nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="2e85c-110">Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıfından devralınır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="2e85c-111">Kullanılabilir şekil nesneleri <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>ve <xref:System.Windows.Shapes.Rectangle>içerir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="2e85c-112"><xref:System.Windows.Shapes.Shape> nesneler aşağıdaki ortak özellikleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="2e85c-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahattının nasıl boyanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="2e85c-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin anahattının kalınlığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="2e85c-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: şeklin iç kısmının nasıl boyanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="2e85c-116">Cihazdan bağımsız piksellerde ölçülen koordinatları ve köşeleri belirtmek için veri özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2e85c-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="2e85c-117"><xref:System.Windows.UIElement>türettikleri için, şekil nesneleri panellerin ve çoğu denetimin içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="2e85c-118"><xref:System.Windows.Controls.Canvas> panel, alt nesnelerinin mutlak konumunu desteklediğinden karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="2e85c-119"><xref:System.Windows.Shapes.Line> sınıfı iki noktaya çizgi çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="2e85c-120">Aşağıdaki örnek, çizgi koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="2e85c-121">Aşağıdaki görüntüde işlenen <xref:System.Windows.Shapes.Line>gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="2e85c-122">![Çizgi çizimi](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="2e85c-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="2e85c-123"><xref:System.Windows.Shapes.Line> sınıfı bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği sağlamasına karşın, bir <xref:System.Windows.Shapes.Line> alanı olmadığından, bu ayarın hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="2e85c-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="2e85c-124">Diğer bir yaygın şekil <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="2e85c-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="2e85c-125">Şeklin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini tanımlayarak <xref:System.Windows.Shapes.Ellipse> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e85c-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="2e85c-126">Bir daire çizmek için <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri eşit olan bir <xref:System.Windows.Shapes.Ellipse> belirtin.</span><span class="sxs-lookup"><span data-stu-id="2e85c-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="2e85c-127">Aşağıdaki görüntüde bir işlenen <xref:System.Windows.Shapes.Ellipse>örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="2e85c-128">![Elips çizimi](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="2e85c-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="2e85c-129">Yolları ve geometrileri kullanma</span><span class="sxs-lookup"><span data-stu-id="2e85c-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="2e85c-130"><xref:System.Windows.Shapes.Path> sınıfı eğrileri ve karmaşık şekilleri çizmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="2e85c-131">Bu eğriler ve şekiller <xref:System.Windows.Media.Geometry> nesneleri kullanılarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="2e85c-132">Bir <xref:System.Windows.Shapes.Path>kullanmak için, bir <xref:System.Windows.Media.Geometry> oluşturup <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliğini ayarlamak için bunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2e85c-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="2e85c-133">Aralarından seçim yapabileceğiniz çeşitli <xref:System.Windows.Media.Geometry> nesneleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="2e85c-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>ve <xref:System.Windows.Media.EllipseGeometry> sınıfları görece basit şekilleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="2e85c-135">Daha karmaşık şekiller oluşturmak veya Eğriler oluşturmak için <xref:System.Windows.Media.PathGeometry>kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="2e85c-136">PathGeometry ve PathSegments</span><span class="sxs-lookup"><span data-stu-id="2e85c-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="2e85c-137"><xref:System.Windows.Media.PathGeometry> nesneler bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesnesinden oluşur; Her <xref:System.Windows.Media.PathFigure> farklı bir "şekil" veya şekli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e85c-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="2e85c-138">Her <xref:System.Windows.Media.PathFigure>, her biri şekil veya şeklin bağlı bir bölümünü temsil eden bir veya daha fazla <xref:System.Windows.Media.PathSegment> nesnesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="2e85c-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="2e85c-139">Segment türleri şunları içerir: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>ve <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="2e85c-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="2e85c-140">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisini çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="2e85c-141">Aşağıdaki görüntüde işlenmiş şekil gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="2e85c-142">![Yol çizimi](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="2e85c-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="2e85c-143"><xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları hakkında daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e85c-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="2e85c-144">XAML kısaltılmış sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e85c-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="2e85c-145">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir <xref:System.Windows.Shapes.Path>anlatmak için özel kısaltılmış bir sözdizimi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e85c-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="2e85c-146">Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="2e85c-147">Aşağıdaki görüntüde işlenen bir <xref:System.Windows.Shapes.Path>gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="2e85c-148">![Yol çizimi](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="2e85c-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="2e85c-149"><xref:System.Windows.Shapes.Path.Data%2A> öznitelik dizesi, <xref:System.Windows.Controls.Canvas>koordinat sistemindeki yol için bir başlangıç noktası kuran, M tarafından belirtilen "MoveTo" komutuyla başlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2e85c-150"><xref:System.Windows.Shapes.Path> veri parametreleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="2e85c-151">Büyük harf, yeni geçerli nokta için mutlak bir konum gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="2e85c-152">Küçük harf m, göreli koordinatları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="2e85c-153">İlk kesim, (100.200) ve bitiş saati (400.175) ile başlayan üçüncü dereceden Bezier eğrisdir ve iki denetim noktası (100, 25) ve (400.350) kullanılarak çizilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="2e85c-154">Bu segment <xref:System.Windows.Shapes.Path.Data%2A> öznitelik dizesinde C komutu tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="2e85c-155">Yine, büyük harf C mutlak bir yolu belirtir; küçük harfli c, göreli bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="2e85c-156">İkinci kesim, önceki alt yolun uç noktasından (400.175) yeni bir uç noktaya (280.175) çizilmiş bir çizgi belirten mutlak yatay "lineto" komutu H ile başlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="2e85c-157">Yatay bir "lineto" komutu olduğundan, belirtilen değer bir *x*koordinatı.</span><span class="sxs-lookup"><span data-stu-id="2e85c-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="2e85c-158">Tüm yol sözdizimi için bkz. <xref:System.Windows.Shapes.Path.Data%2A> başvurusu ve [PathGeometry kullanarak şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="2e85c-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="2e85c-159">Şekilleri boyama</span><span class="sxs-lookup"><span data-stu-id="2e85c-159">Painting Shapes</span></span>  
 <span data-ttu-id="2e85c-160"><xref:System.Windows.Media.Brush> nesneler, bir şeklin <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>boyamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="2e85c-161">Aşağıdaki örnekte, <xref:System.Windows.Shapes.Ellipse> vuruş ve dolgusu belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="2e85c-162">Fırça özelliklerinin geçerli girişinin bir anahtar sözcük veya onaltılık renk değeri olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="2e85c-163">Kullanılabilir renk anahtar sözcükleri hakkında daha fazla bilgi için, <xref:System.Windows.Media> ad alanındaki <xref:System.Windows.Media.Colors> sınıfının özelliklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```xaml
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 <span data-ttu-id="2e85c-164">Aşağıdaki görüntüde işlenen <xref:System.Windows.Shapes.Ellipse>gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="2e85c-165">![Elips](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="2e85c-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="2e85c-166">Alternatif olarak, şekli düz bir renkle boyamak için açıkça bir <xref:System.Windows.Media.SolidColorBrush> nesnesi oluşturmak üzere özellik öğesi sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e85c-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 <span data-ttu-id="2e85c-167">Aşağıdaki çizimde, işlenmiş şekil gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="2e85c-168">![SolidColorBrush çizimi](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="2e85c-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="2e85c-169">Ayrıca, bir şeklin konturunu veya degradelerini, resimleri, desenleri ve daha fazlasını boyayabilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="2e85c-170">Daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e85c-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="2e85c-171">Uzatılabilir şekiller</span><span class="sxs-lookup"><span data-stu-id="2e85c-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="2e85c-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>ve <xref:System.Windows.Shapes.Rectangle> sınıflarının hepsi bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="2e85c-173">Bu özellik, bir <xref:System.Windows.Shapes.Shape> nesnesinin içeriğinin (çizilecek şekil) <xref:System.Windows.Shapes.Shape> nesnenin düzen alanını doldurmak için nasıl uzatılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="2e85c-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="2e85c-174"><xref:System.Windows.Shapes.Shape> nesnenin düzen alanı, <xref:System.Windows.Shapes.Shape> bir <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı ya da <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarları nedeniyle, Düzen sistemi tarafından ayrılan alan miktarıdır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="2e85c-175">Windows Presentation Foundation düzen hakkında daha fazla bilgi için bkz. [düzene](../advanced/layout.md) genel bakış.</span><span class="sxs-lookup"><span data-stu-id="2e85c-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="2e85c-176">Esnetme özelliği aşağıdaki değerlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="2e85c-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="2e85c-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri genişletilmedi.</span><span class="sxs-lookup"><span data-stu-id="2e85c-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="2e85c-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri, düzen alanını doldurmak için uzatılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="2e85c-179">En boy oranı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="2e85c-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="2e85c-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> nesnenin içerikleri, özgün en boy oranını korurken düzen alanını doldurmak için mümkün olduğunca uzatılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="2e85c-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> nesnenin içeriği, özgün en boy oranını korurken düzen alanını tamamen doldurmak için uzatılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="2e85c-182"><xref:System.Windows.Shapes.Shape> nesnenin içerikleri uzatıldığında, <xref:System.Windows.Shapes.Shape> nesnesinin anahattının uzatma sonrasında boyanmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="2e85c-183">Aşağıdaki örnekte, (0, 0) ile (0, 1) arasında (1, 1) çok küçük bir üçgen çizmek için bir <xref:System.Windows.Shapes.Polygon> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="2e85c-184"><xref:System.Windows.Shapes.Polygon> nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve Esnetme özelliği Fill olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="2e85c-185">Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içerikleri (üçgeni) daha büyük alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a><span data-ttu-id="2e85c-186">Şekilleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2e85c-186">Transforming Shapes</span></span>  
 <span data-ttu-id="2e85c-187"><xref:System.Windows.Media.Transform> sınıfı, şekilleri iki boyutlu bir düzlemde dönüştürmek için yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e85c-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="2e85c-188">Farklı dönüştürme türleri arasında döndürme (<xref:System.Windows.Media.RotateTransform>), ölçek (<xref:System.Windows.Media.ScaleTransform>), eğriltme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>) bulunur.</span><span class="sxs-lookup"><span data-stu-id="2e85c-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="2e85c-189">Bir şekle uygulanacak ortak bir dönüşüm bir dönüşdir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="2e85c-190">Bir şekli döndürmek için bir <xref:System.Windows.Media.RotateTransform> oluşturun ve <xref:System.Windows.Media.RotateTransform.Angle%2A>belirtin.</span><span class="sxs-lookup"><span data-stu-id="2e85c-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="2e85c-191">45 <xref:System.Windows.Media.RotateTransform.Angle%2A>, öğe 45 derece saat yönünde döner; 90 açısı öğe 90 derece saat yönünde döner; vb.</span><span class="sxs-lookup"><span data-stu-id="2e85c-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="2e85c-192">Öğenin döndürüldüğü noktayı denetlemek istiyorsanız <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="2e85c-193">Bu özellik değerleri, dönüştürülmekte olan öğenin koordinat alanında ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="2e85c-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> varsayılan değerleri sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="2e85c-195">Son olarak, <xref:System.Windows.Media.RotateTransform> öğesine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="2e85c-196">Dönüşümün düzeni etkilemesini istemiyorsanız şeklin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="2e85c-197">Aşağıdaki örnekte, şeklin sol üst köşesinden (0, 0) bir şekil 45 derece döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e85c-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="2e85c-198">Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu zaman nokta (25, 50) ile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2e85c-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="2e85c-199">Aşağıdaki çizimde, iki dönüştürme uygulamanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e85c-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="2e85c-200">![farklı orta noktaları olan 45 derece döndürme](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="2e85c-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="2e85c-201">Önceki örneklerde, her şekil nesnesine tek bir dönüşüm uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2e85c-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="2e85c-202">Bir şekle (veya başka bir kullanıcı arabirimi öğesine) birden çok dönüşüm uygulamak için <xref:System.Windows.Media.TransformGroup>kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e85c-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e85c-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e85c-203">See also</span></span>

- [<span data-ttu-id="2e85c-204">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2e85c-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="2e85c-205">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2e85c-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="2e85c-206">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2e85c-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="2e85c-207">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="2e85c-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="2e85c-208">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="2e85c-208">Animation Overview</span></span>](animation-overview.md)
