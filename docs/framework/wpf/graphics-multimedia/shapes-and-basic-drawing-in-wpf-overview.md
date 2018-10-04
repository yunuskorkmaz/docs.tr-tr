---
title: WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler
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
ms.openlocfilehash: 47df352c3b001f088f34ea057b34698efc4f4b53
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778107"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="cc512-102">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="cc512-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="cc512-103">Bu konu ile nasıl genel bir fikir veren <xref:System.Windows.Shapes.Shape> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="cc512-104">A <xref:System.Windows.Shapes.Shape> bir tür <xref:System.Windows.UIElement> ekrana bir şekil çizme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc512-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="cc512-105">Kullanıcı Arabirimi öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri içinde kullanılabilir <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim.</span><span class="sxs-lookup"><span data-stu-id="cc512-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="cc512-106">birkaç grafik ve işleme hizmetlerine erişim katmanı sunar.</span><span class="sxs-lookup"><span data-stu-id="cc512-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="cc512-107">En üst katmanında <xref:System.Windows.Shapes.Shape> nesneleri düzen ve katılım gibi birçok yararlı özellik sağlar ve kullanmak kolay [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.</span><span class="sxs-lookup"><span data-stu-id="cc512-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="cc512-108">Şekil nesneleri</span><span class="sxs-lookup"><span data-stu-id="cc512-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="cc512-109">çok sayıda kullanıma hazır sunar <xref:System.Windows.Shapes.Shape> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="cc512-110">Tüm şekil nesneleri devralınacak <xref:System.Windows.Shapes.Shape> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cc512-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="cc512-111">Kullanılabilir şekil nesneleri dahil etme <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="cc512-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="cc512-112"><xref:System.Windows.Shapes.Shape> nesneleri, aşağıdaki genel özellikleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="cc512-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="cc512-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin ana hat nasıl boyanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cc512-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="cc512-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin ana hat kalınlığı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cc512-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="cc512-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin içinin nasıl boyanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cc512-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="cc512-116">Koordinatları ve köşeleri belirtmek için veri özellikleri, CİHAZDAN bağımsız piksel cinsinden ölçülür.</span><span class="sxs-lookup"><span data-stu-id="cc512-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="cc512-117">Oldukları türetilmesi çünkü <xref:System.Windows.UIElement>, şekil nesneleri, paneller ve çoğu denetimleri içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc512-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="cc512-118"><xref:System.Windows.Controls.Canvas> Masasıdır karmaşık çizimleri oluşturmak için mutlak alt nesnelerinin konumlandırma desteklediğinden özellikle iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="cc512-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="cc512-119"><xref:System.Windows.Shapes.Line> Sınıfı iki nokta arasında bir çizgi çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc512-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="cc512-120">Aşağıdaki örnek, satır koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc512-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="cc512-121">Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="cc512-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="cc512-122">![Çizim satırı](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="cc512-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="cc512-123">Ancak <xref:System.Windows.Shapes.Line> sağlamasına bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, bu ayarın hiçbir etkisi nedeniyle bir <xref:System.Windows.Shapes.Line> alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="cc512-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="cc512-124">Başka bir ortak şekli <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="cc512-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="cc512-125">Oluşturma bir <xref:System.Windows.Shapes.Ellipse> şeklin tanımlayarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="cc512-126">Bir daire çizmek için belirtin bir <xref:System.Windows.Shapes.Ellipse> olan <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerler eşit.</span><span class="sxs-lookup"><span data-stu-id="cc512-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="cc512-127">İşlenen bir örneği aşağıdaki resimde gösterilmektedir <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="cc512-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="cc512-128">![Elips çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="cc512-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="cc512-129">Yolları ve geometrileri kullanma</span><span class="sxs-lookup"><span data-stu-id="cc512-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="cc512-130"><xref:System.Windows.Shapes.Path> Sınıfı, eğriler ve karmaşık şekiller çizme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc512-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="cc512-131">Bu eğriler ve şekiller kullanarak açıklanan <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="cc512-132">Kullanılacak bir <xref:System.Windows.Shapes.Path>, oluşturduğunuz bir <xref:System.Windows.Media.Geometry> ve ayarlamak için kullanın <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc512-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="cc512-133">Var olan çeşitli <xref:System.Windows.Media.Geometry> aralarından seçim nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="cc512-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, Ve <xref:System.Windows.Media.EllipseGeometry> görece Basit şekiller sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="cc512-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="cc512-135">Daha karmaşık şekiller veya eğriler oluşturmak için kullanmak bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cc512-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="cc512-136">PathGeometry ve PathSegments</span><span class="sxs-lookup"><span data-stu-id="cc512-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="cc512-137"><xref:System.Windows.Media.PathGeometry> nesneleri oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc512-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="cc512-138">Her <xref:System.Windows.Media.PathFigure> kendisi bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şekil bağlı bir bölümünü temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="cc512-139">Kesim türleri aşağıdakileri kapsamaktadır: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="cc512-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="cc512-140">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisi çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="cc512-141">Aşağıdaki görüntüde, işlenen şekli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc512-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="cc512-142">![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="cc512-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="cc512-143">Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları için bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc512-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="cc512-144">XAML söz dizimi olarak kısaltılır</span><span class="sxs-lookup"><span data-stu-id="cc512-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="cc512-145">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], özel bir kısaltılmış sözdizimi tanımlamak için kullanabilirsiniz bir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="cc512-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="cc512-146">Aşağıdaki örnekte, kısaltılmış sözdizimi, karmaşık bir şekil çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="cc512-147">Aşağıdaki görüntüde bir işlenen gösterilmektedir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="cc512-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="cc512-148">![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="cc512-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="cc512-149"><xref:System.Windows.Shapes.Path.Data%2A> Öznitelik dize başlar yolu için bir başlangıç noktası koordinat sistemi oluşturan M tarafından gösterilen "moveto" komutu ile <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="cc512-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cc512-150"><xref:System.Windows.Shapes.Path> Parametreler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc512-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="cc512-151">M büyük harf, geçerli bir yeni nokta için bir mutlak konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc512-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="cc512-152">Bir küçük harf m göreli koordinatları belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc512-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="cc512-153">Bir üçüncü dereceden Bezier eğrisi başına (100,200) ilk parça olan ve (400,175) son iki çizilen kullanarak kontrol noktaları (100,25) ve (400,350).</span><span class="sxs-lookup"><span data-stu-id="cc512-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="cc512-154">Bu kesimin C komutta belirtilir <xref:System.Windows.Shapes.Path.Data%2A> dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cc512-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="cc512-155">Yeniden Büyük Harf C mutlak bir yol belirtir; küçük harf c göreli bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc512-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="cc512-156">Bir önceki alt yolun bitiş noktasından (400,175) yeni bir bitiş noktasına (280,175) çizgi belirten H mutlak yatay "lineto" komutu ile ikinci kesim başlar.</span><span class="sxs-lookup"><span data-stu-id="cc512-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="cc512-157">Yatay "lineto" komutu olduğundan, belirtilen değeri olan bir *x*-koordine edin.</span><span class="sxs-lookup"><span data-stu-id="cc512-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="cc512-158">Tam yol sözdizimi için bkz. <xref:System.Windows.Shapes.Path.Data%2A> başvuru ve [PathGeometry kullanarak şekil oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="cc512-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="cc512-159">Şekilleri Boyama</span><span class="sxs-lookup"><span data-stu-id="cc512-159">Painting Shapes</span></span>  
 <span data-ttu-id="cc512-160"><xref:System.Windows.Media.Brush> bir şeklin boyamak için kullanılan nesneleri <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc512-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="cc512-161">Aşağıdaki örnek, vuruş ve dolgu bir <xref:System.Windows.Shapes.Ellipse> belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cc512-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="cc512-162">Geçerli giriş Fırça özellikleri için bir anahtar sözcük ya da onaltılık renk değeri olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cc512-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="cc512-163">Özellikleri kullanılabilir rengi anahtar sözcükler hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.Colors> sınıfını <xref:System.Windows.Media> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cc512-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="cc512-164">Aşağıdaki görüntüde işlenen gösterilmektedir <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="cc512-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="cc512-165">![Bir elips](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="cc512-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="cc512-166">Alternatif olarak, açıkça oluşturmak için bir özellik öğesi sözdizimini kullanabilirsiniz bir <xref:System.Windows.Media.SolidColorBrush> şekli düz renk ile boyamak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="cc512-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="cc512-167">İşlenen şekli aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cc512-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="cc512-168">![SolidColorBrush çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="cc512-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="cc512-169">Bir şeklin vuruş veya gradyanlar, görüntüleri, desenleri ve daha fazlasıyla dolgu boyama de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc512-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="cc512-170">Daha fazla bilgi için [düz renkler ve gradyanlar genel bakış boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc512-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="cc512-171">Esneyebilen şekiller</span><span class="sxs-lookup"><span data-stu-id="cc512-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="cc512-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, Ve <xref:System.Windows.Shapes.Rectangle> tüm sınıflar bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc512-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="cc512-173">Bu özellik belirler nasıl bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini (çizilecek Şekil) esnetilmiş doldurmak için <xref:System.Windows.Shapes.Shape> nesnenin düzen alanı.</span><span class="sxs-lookup"><span data-stu-id="cc512-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="cc512-174">A <xref:System.Windows.Shapes.Shape> nesnenin Düzen yer alan miktarı <xref:System.Windows.Shapes.Shape> düzen sistemi tarafından sonlandırıldığından açık bir ayrılmış <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı nedeniyle veya kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarları.</span><span class="sxs-lookup"><span data-stu-id="cc512-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="cc512-175">Windows Presentation Foundation'da Düzen hakkında ek bilgi için bkz: [Düzen](../../../../docs/framework/wpf/advanced/layout.md) genel bakış.</span><span class="sxs-lookup"><span data-stu-id="cc512-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="cc512-176">Uzat özelliği şu değerlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="cc512-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="cc512-177"><xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini değil uzatılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="cc512-178"><xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini kendi düzen alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="cc512-179">En boy oranı korunur değil.</span><span class="sxs-lookup"><span data-stu-id="cc512-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="cc512-180"><xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini mümkün olduğunca, özgün en boy oranını korurken kendi düzen alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="cc512-181"><xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, tamamen kendi özgün en boy oranını korurken kendi düzen alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="cc512-182">Unutmayın, bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini uzatılır <xref:System.Windows.Shapes.Shape> nesnenin anahat uzatma sonra boyanır.</span><span class="sxs-lookup"><span data-stu-id="cc512-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="cc512-183">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Polygon> (1,1) (0,1) için çok küçük bir üçgen (0,0) öğesinden çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="cc512-184"><xref:System.Windows.Shapes.Polygon> Nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100 olarak ayarlanır ve kendi esnetme özelliğini doldurmak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cc512-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="cc512-185">Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içeriğini (üçgen) daha büyük alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="cc512-186">Şekilleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cc512-186">Transforming Shapes</span></span>  
 <span data-ttu-id="cc512-187"><xref:System.Windows.Media.Transform> Sınıfı iki boyutlu düzlemde şekilleri dönüştürme bulunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc512-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="cc512-188">Döndürme dönüşümü farklı türlerini içerir (<xref:System.Windows.Media.RotateTransform>), Ölçek (<xref:System.Windows.Media.ScaleTransform>), eğme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="cc512-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="cc512-189">Bir şekle uygulamak için ortak bir dönüştürme bir dönüş ' dir.</span><span class="sxs-lookup"><span data-stu-id="cc512-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="cc512-190">Bir şekli döndürmek için oluşturun bir <xref:System.Windows.Media.RotateTransform> ve belirtin, <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc512-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="cc512-191">Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 45 derece 90 açı saat yönünde; vb. Bu öğe 90 derece döndürür; yönünde öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc512-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="cc512-192">Ayarlama <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> öğe döndürüldüğü noktası denetlemek istiyorsanız özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cc512-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="cc512-193">Bu özellik değerleri, dönüştürülmekte olan öğenin koordinat ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="cc512-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="cc512-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> sıfır varsayılan değerlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc512-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="cc512-195">Son olarak, uygulama <xref:System.Windows.Media.RotateTransform> öğeye.</span><span class="sxs-lookup"><span data-stu-id="cc512-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="cc512-196">Şeklin düzenini etkileyen dönüşüm istemiyorsanız ayarlamak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc512-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="cc512-197">Aşağıdaki örnekte, bir <xref:System.Windows.Media.RotateTransform> şeklin sol üst köşedeki (0,0) bir şekil 45 derece döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc512-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="cc512-198">Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu kez noktası hakkında (25,50) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cc512-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="cc512-199">Aşağıdaki çizimde, iki dönüşümler uygulanırken sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc512-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="cc512-200">![farklı merkezi noktalarıyla 45 derece döndürme](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="cc512-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="cc512-201">Önceki örneklerde, her şekil nesnesi için tek bir dönüştürme uygulandı.</span><span class="sxs-lookup"><span data-stu-id="cc512-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="cc512-202">Bir şekil (veya başka bir kullanıcı Arabirimi öğesi) birden çok dönüşüm uygulamak için bir <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="cc512-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc512-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc512-203">See Also</span></span>  
 [<span data-ttu-id="cc512-204">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cc512-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="cc512-205">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc512-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="cc512-206">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc512-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="cc512-207">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="cc512-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="cc512-208">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="cc512-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
