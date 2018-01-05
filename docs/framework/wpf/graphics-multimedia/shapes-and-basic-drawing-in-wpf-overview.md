---
title: "WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2912215cb8fb0090cef58e0201cc355da1f0bf19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="a1a8b-102">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="a1a8b-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="a1a8b-103">Bu konu ile çizmek nasıl genel bir fikir veren <xref:System.Windows.Shapes.Shape> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="a1a8b-104">A <xref:System.Windows.Shapes.Shape> bir tür <xref:System.Windows.UIElement> ekrana bir şekil çizme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="a1a8b-105">Kullanıcı Arabirimi öğeleri olduklarından <xref:System.Windows.Shapes.Shape> nesneleri içinde kullanılabilir <xref:System.Windows.Controls.Panel> öğeleri ve çoğu denetim.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="a1a8b-106">birkaç grafik ve işleme hizmetlerine erişim katmanı sunar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="a1a8b-107">En üst katmanında <xref:System.Windows.Shapes.Shape> nesneleridir kullanın ve düzeni ve katılım gibi çok sayıda kullanışlı özellikle sağlamak kolay [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olay sistemi.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="a1a8b-108">Şekil nesneleri</span><span class="sxs-lookup"><span data-stu-id="a1a8b-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="a1a8b-109">kullanıma hazır bir dizi sağlar <xref:System.Windows.Shapes.Shape> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="a1a8b-110">Tüm şekil nesneleri devralınmalıdır <xref:System.Windows.Shapes.Shape> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="a1a8b-111">Kullanılabilir şekil nesneleri dahil <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, ve <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a1a8b-112"><xref:System.Windows.Shapes.Shape>nesneleri aşağıdaki ortak özellikleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="a1a8b-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Şeklin anahat nasıl boyanır açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="a1a8b-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Şeklin Anahat kalınlığı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="a1a8b-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Şeklin iç nasıl boyanır açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="a1a8b-116">Koordinatları ve köşeleri belirtmek için veri özellikleri aygıttan bağımsız piksel cinsinden ölçülür.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="a1a8b-117">Öğesinden türetilen çünkü <xref:System.Windows.UIElement>, şekil nesneleri paneller ve çoğu denetim içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="a1a8b-118"><xref:System.Windows.Controls.Canvas> Panosudur mutlak alt nesnelerinin konumlandırma desteklediğinden karmaşık çizimler oluşturmak için özellikle iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="a1a8b-119"><xref:System.Windows.Shapes.Line> Sınıfı, iki nokta arasında bir çizgi çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="a1a8b-120">Aşağıdaki örnek çizgi koordinatları ve vuruş özelliklerini belirtmek için çeşitli yollar gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="a1a8b-121">Aşağıdaki resimde işlenen gösterilmiştir <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="a1a8b-122">![Satır çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="a1a8b-123">Ancak <xref:System.Windows.Shapes.Line> sağlamasına bir <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, onu ayarlamanın etkisi yoktur çünkü bir <xref:System.Windows.Shapes.Line> hiçbir alana sahip.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="a1a8b-124">Başka bir ortak şekli <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="a1a8b-125">Oluşturma bir <xref:System.Windows.Shapes.Ellipse> şeklin tanımlayarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="a1a8b-126">Bir daire çizmek için belirtmek bir <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> değerleri eşit.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="a1a8b-127">Aşağıdaki resimde işlenen bir örnek gösterilmiştir <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="a1a8b-128">![Elips çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="a1a8b-129">Yolları ve geometri kullanma</span><span class="sxs-lookup"><span data-stu-id="a1a8b-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="a1a8b-130"><xref:System.Windows.Shapes.Path> Sınıfı, eğriler ve karmaşık şekiller çizmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="a1a8b-131">Bu eğriler ve şekiller kullanarak açıklanan <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="a1a8b-132">Kullanılacak bir <xref:System.Windows.Shapes.Path>, oluşturduğunuz bir <xref:System.Windows.Media.Geometry> ve ayarlamak için kullanın <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Path.Data%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="a1a8b-133">Çeşitli vardır <xref:System.Windows.Media.Geometry> nesneleri seçin.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="a1a8b-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, Ve <xref:System.Windows.Media.EllipseGeometry> sınıfları ilgili basit şekilleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="a1a8b-135">Daha karmaşık şekiller veya eğriler oluşturmak için kullanın bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="a1a8b-136">PathGeometry ve PathSegments</span><span class="sxs-lookup"><span data-stu-id="a1a8b-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="a1a8b-137"><xref:System.Windows.Media.PathGeometry>nesneleri oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="a1a8b-138">Her <xref:System.Windows.Media.PathFigure> kendisini bir veya daha fazla oluşmaktadır <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şeklin bağlı bir bölümünü temsil eden nesneler.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="a1a8b-139">Kesim türleri şunlardır: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="a1a8b-140">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Path> ikinci dereceden Bezier eğrisi çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="a1a8b-141">Aşağıdaki resim işlenen şekli göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="a1a8b-142">![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="a1a8b-143">Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve diğer <xref:System.Windows.Media.Geometry> sınıfları için bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a1a8b-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="a1a8b-144">XAML kısaltılmış sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1a8b-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="a1a8b-145">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tanımlamak için özel bir kısaltılmış sözdizimi kullanabilirsiniz bir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="a1a8b-146">Aşağıdaki örnekte, karmaşık bir şekil çizmek için kısaltılmış sözdizimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="a1a8b-147">Aşağıdaki resimde bir işlenmiş gösterilmiştir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="a1a8b-148">![Yol çizim](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="a1a8b-149"><xref:System.Windows.Shapes.Path.Data%2A> Öznitelik dizesini başlar, M tarafından yol için bir başlangıç noktası koordinat sistemi oluşturan belirtilen "moveto" komutuyla <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a1a8b-150"><xref:System.Windows.Shapes.Path>Veri parametreleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="a1a8b-151">Büyük Harf M geçerli bir yeni nokta için mutlak bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="a1a8b-152">Küçük harf m koordinatlara göre gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="a1a8b-153">İlk kesim (100,200) küp bir Bezier eğrisi başında olduğundan ve (400,175) son çizilmiş iki kullanarak denetim noktası (100,25) ve (400,350).</span><span class="sxs-lookup"><span data-stu-id="a1a8b-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="a1a8b-154">Bu kesimin C komutu ile belirtilir <xref:System.Windows.Shapes.Path.Data%2A> öznitelik dize.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="a1a8b-155">Yeniden, büyük harf C mutlak bir yol gösterir; küçük harf c göreli bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="a1a8b-156">İkinci kesim mutlak yatay "lineto" komutu önceki alt yolun bitiş noktasından (400,175) yeni bir bitiş noktasına (280,175) içinden bir çizgi belirtir H ile başlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="a1a8b-157">Yatay "lineto" komutu olduğu için belirtilen değer bir *x*-koordinatı.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="a1a8b-158">Tam yol sözdizimi için bkz: <xref:System.Windows.Shapes.Path.Data%2A> başvurusu ve [PathGeometry kullanarak bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="a1a8b-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="a1a8b-159">Şekilleri Boyama</span><span class="sxs-lookup"><span data-stu-id="a1a8b-159">Painting Shapes</span></span>  
 <span data-ttu-id="a1a8b-160"><xref:System.Windows.Media.Brush>Şeklin boyamak için kullanılan nesneleri <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="a1a8b-161">Aşağıdaki örnek, vuruş ve dolgusunu bir <xref:System.Windows.Shapes.Ellipse> belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="a1a8b-162">Geçerli giriş Fırça özellikleri için bir anahtar sözcük veya onaltılık renk değeri olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="a1a8b-163">Özelliklerini kullanılabilir renk anahtar sözcükler hakkında daha fazla bilgi için bkz: <xref:System.Windows.Media.Colors> sınıfını <xref:System.Windows.Media> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```  
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
  
 <span data-ttu-id="a1a8b-164">Aşağıdaki resimde işlenen gösterilmiştir <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="a1a8b-165">![Elips](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="a1a8b-166">Alternatif olarak, açıkça oluşturmak için bir özellik öğesi sözdizimini kullanabilirsiniz bir <xref:System.Windows.Media.SolidColorBrush> şekli düz renk ile boyamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```  
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
  
 <span data-ttu-id="a1a8b-167">Aşağıdaki çizimde işlenen şekli göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="a1a8b-168">![SolidColorBrush çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="a1a8b-169">Şeklin vuruş veya dolgu gradyan, görüntüler, desenleri ve daha fazla ile de boyama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="a1a8b-170">Daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a1a8b-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="a1a8b-171">Uzatılabilir şekiller</span><span class="sxs-lookup"><span data-stu-id="a1a8b-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="a1a8b-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, Ve <xref:System.Windows.Shapes.Rectangle> tüm sınıflar bir <xref:System.Windows.Shapes.Shape.Stretch%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="a1a8b-173">Bu özellik belirler nasıl bir <xref:System.Windows.Shapes.Shape> doldurmak için nesnenin içeriğini (çizilecek Şekil) uzatılmış <xref:System.Windows.Shapes.Shape> nesnesinin düzen alanı.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="a1a8b-174">A <xref:System.Windows.Shapes.Shape> nesnenin düzeni yer alan miktarını <xref:System.Windows.Shapes.Shape> düzen sistemi tarafından sonlandırıldığından açık bir ayrılmış <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> ayarı veya nedeniyle kendi <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="a1a8b-175">Windows Presentation Foundation'da Düzen hakkında ek bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md) genel bakış.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="a1a8b-176">Stretch özelliği aşağıdaki değerlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="a1a8b-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="a1a8b-177"><xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini değil uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="a1a8b-178"><xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini düzeni alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="a1a8b-179">En boy oranını korunmaz.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="a1a8b-180"><xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, özgün en boy oranını koruyarak kendi düzen alanını doldurmak mümkün olduğunca uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="a1a8b-181"><xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape> Nesnenin içeriğini, tamamen kendi özgün en boy oranını koruyarak kendi düzen alanını doldurmak için uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="a1a8b-182">Unutmayın, bir <xref:System.Windows.Shapes.Shape> nesnenin içeriğini uzatılır <xref:System.Windows.Shapes.Shape> nesnesinin anahattı uzatma sonra boyanır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="a1a8b-183">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Polygon> (1,1) (0,1) için çok küçük bir üçgen (0,0) gelen çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="a1a8b-184"><xref:System.Windows.Shapes.Polygon> Nesnenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> 100'e ayarlanır ve doldurmak için esnetme özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="a1a8b-185">Sonuç olarak, <xref:System.Windows.Shapes.Polygon> nesnenin içeriğini (üçgen) daha büyük alanı dolduracak şekilde uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
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
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a><span data-ttu-id="a1a8b-186">Şekilleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1a8b-186">Transforming Shapes</span></span>  
 <span data-ttu-id="a1a8b-187"><xref:System.Windows.Media.Transform> Sınıfı, sistemi, iki boyutlu bir düzlem şekillerde dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="a1a8b-188">Farklı dönüştürme türleri döndürme içerir (<xref:System.Windows.Media.RotateTransform>), Ölçek (<xref:System.Windows.Media.ScaleTransform>), eğme (<xref:System.Windows.Media.SkewTransform>) ve çeviri (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="a1a8b-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="a1a8b-189">Bir şekle uygulamak için ortak bir dönüşüm bir döndürme ' dir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="a1a8b-190">Bir şekli döndürmek için oluşturma bir <xref:System.Windows.Media.RotateTransform> ve belirtin, <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="a1a8b-191">Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 90 bir açıda saat yönünde; vb. Bu öğe 90 derece döndürür saat yönünde 45 derece; öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="a1a8b-192">Ayarlama <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> öğesi döndürüldüğü noktası denetlemek istiyorsanız özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="a1a8b-193">Bu özellik değerlerini dönüştürülmekte olan öğenin koordinat ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="a1a8b-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A>ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> sıfır varsayılan değerlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="a1a8b-195">Son olarak, uygulama <xref:System.Windows.Media.RotateTransform> öğesi.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="a1a8b-196">Düzen etkilemek için dönüştürme istemiyorsanız şeklin ayarlayın <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="a1a8b-197">Aşağıdaki örnekte, bir <xref:System.Windows.Media.RotateTransform> şeklin sol üst köşede (0,0) bir şekli 45 derece döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="a1a8b-198">Sonraki örnekte, başka bir şekil 45 derece döndürülür, ancak bu kez (25,50) noktasına hakkında döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="a1a8b-199">Aşağıdaki çizimde iki dönüşümler uygulanırken sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="a1a8b-200">![farklı merkez nokta 45 derece döndürmeler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="a1a8b-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="a1a8b-201">Önceki örneklerde, tek bir dönüştürme her şekil nesnesine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="a1a8b-202">Bir şekle (veya başka bir UI öğesine) çoklu dönüşüm uygulamak için kullanmak bir <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a8b-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1a8b-203">See Also</span></span>  
 [<span data-ttu-id="a1a8b-204">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a1a8b-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="a1a8b-205">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1a8b-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="a1a8b-206">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1a8b-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="a1a8b-207">İzlenecek Yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="a1a8b-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="a1a8b-208">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a1a8b-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
