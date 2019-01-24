---
title: GDI+'da Fırçalar ve Dolgulu Şekiller
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 197678cfdced1e17ad87f521a30c7103c49df4e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624221"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="6c7ef-102">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="6c7ef-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="6c7ef-103">Kapalı şekil, bir elips ya da dikdörtgen gibi bir anahat ve bir iç oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="6c7ef-104">Ana hat kalem ile çizilir ve iç fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6c7ef-105">kapalı şekiller evin içindekiler doldurmak için birkaç fırça sınıfları sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-105">provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="6c7ef-106">Bu sınıfların tümü devralınacak <xref:System.Drawing.Brush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="6c7ef-107">Aşağıdaki çizimde, bir dikdörtgen ile düz fırça doldurulmuş ve elips tarama fırça ile doldurulmuş gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="6c7ef-108">![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="6c7ef-109">Düz fırça</span><span class="sxs-lookup"><span data-stu-id="6c7ef-109">Solid Brushes</span></span>  
 <span data-ttu-id="6c7ef-110">Örneği ihtiyacınız kapalı şekil doldurmak için <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="6c7ef-111">Örneğini <xref:System.Drawing.Graphics> yöntemleri gibi sağlar sınıfını <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A>ve <xref:System.Drawing.Brush> renk ve desen gibi dolgu özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="6c7ef-112"><xref:System.Drawing.Brush> Dolgu yöntemine geçirilen bağımsız değişkenlerden biri.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="6c7ef-113">Aşağıdaki kod örneği, bir elips kırmızı düz renk ile doldurun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="6c7ef-114">Önceki örnekte, fırça türünde <xref:System.Drawing.SolidBrush>, işlevinden devralan <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="6c7ef-115">Tarama fırçalarını</span><span class="sxs-lookup"><span data-stu-id="6c7ef-115">Hatch Brushes</span></span>  
 <span data-ttu-id="6c7ef-116">Bir şekli tarama fırça doldururken bir ön plan rengi, bir arka plan rengi ve bir tarama stilini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="6c7ef-117">Ön plan rengini tarama renktir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6c7ef-118">50'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stillerdir <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-118">provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="6c7ef-119">![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="6c7ef-120">Doku fırçaları</span><span class="sxs-lookup"><span data-stu-id="6c7ef-120">Texture Brushes</span></span>  
 <span data-ttu-id="6c7ef-121">Bir doku fırçası ile bir şekli bir bit eşlem içinde depolanan bir desen ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="6c7ef-122">Örneğin, aşağıdaki resimde adlı bir disk dosyasında depolanan varsayalım `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="6c7ef-123">![Şekil doldurulmuş](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="6c7ef-124">Aşağıdaki kod örneği, bir elips depolanan resim tekrarlayarak doldurmak gösterilmektedir `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="6c7ef-125">Dolu Elips aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="6c7ef-126">![Şekil doldurulmuş](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="6c7ef-127">Gradyan Fırçalar</span><span class="sxs-lookup"><span data-stu-id="6c7ef-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6c7ef-128">Gradyan Fırçalar iki çeşit sağlar: doğrusal ve yolu.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-128">provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="6c7ef-129">Bir şekli şekli arasında hareket ettikçe yatay, dikey kademeli olarak veya çapraz değişiklikleri rengi ile doldurmak için doğrusal gradyan fırçası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="6c7ef-130">Aşağıdaki kod örneği, bir elips sağ kenarına elipsin sol kenardan geçerken yeşil maviye değiştiren yatay bir gradyan fırçası doldurmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="6c7ef-131">Dolu Elips aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="6c7ef-132">![Şekil doldurulmuş](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="6c7ef-133">Yolun gradyan fırçası edge doğru bir şeklin Merkezi'nden geçerken rengini değiştirmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="6c7ef-134">![Şekil doldurulmuş](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="6c7ef-135">Yolun gradyan Fırçalar oldukça esnektir.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="6c7ef-136">Aşağıdaki çizimde değişiklikleri aşamalı olarak kırmızı merkezinde her köşe, üç farklı renkler üçgeni doldurmak için kullanılan gradyan fırçası.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="6c7ef-137">![Şekil doldurulmuş](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="6c7ef-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c7ef-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c7ef-138">See also</span></span>
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="6c7ef-139">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="6c7ef-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="6c7ef-140">Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme</span><span class="sxs-lookup"><span data-stu-id="6c7ef-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="6c7ef-141">Nasıl yapılır: Bir Windows formunda doldurulmuş elips çizme</span><span class="sxs-lookup"><span data-stu-id="6c7ef-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
