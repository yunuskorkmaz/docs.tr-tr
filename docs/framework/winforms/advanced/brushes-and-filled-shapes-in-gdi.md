---
title: "GDI+'da Fırçalar ve Dolgulu Şekiller"
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
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89f0a7c86a83222030d9b50e20228f32e85ce730
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="08850-102">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="08850-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="08850-103">Dikdörtgene veya bir elips gibi kapalı bir şekil ana hattı ve bir iç oluşur.</span><span class="sxs-lookup"><span data-stu-id="08850-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="08850-104">Anahat kalem ile çizilir ve iç fırça ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="08850-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="08850-105">kapalı şekiller evin içindekiler doldurmak için birkaç fırça sınıflar sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="08850-105"> provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="08850-106">Tüm bu sınıfların devralınmalıdır <xref:System.Drawing.Brush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="08850-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="08850-107">Aşağıdaki çizimde bir dikdörtgen düz fırça ile doldurulur ve tarama fırça ile elips doldurulmuş gösterir.</span><span class="sxs-lookup"><span data-stu-id="08850-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="08850-108">![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="08850-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="08850-109">Düz Fırçalar</span><span class="sxs-lookup"><span data-stu-id="08850-109">Solid Brushes</span></span>  
 <span data-ttu-id="08850-110">Kapalı bir şekil doldurmak için bir örneğini gereksinim <xref:System.Drawing.Graphics> sınıfı ve bir <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="08850-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="08850-111">Örneğinin <xref:System.Drawing.Graphics> sınıfı yöntemleri gibi sağlar <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A>ve <xref:System.Drawing.Brush> dolgu rengini ve düzenini gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="08850-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="08850-112"><xref:System.Drawing.Brush> Fill yöntemi bağımsız değişkenlerden biri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="08850-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="08850-113">Aşağıdaki kod örneğinde elips düz bir kırmızı renkle doldurma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08850-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="08850-114">Önceki örnekte fırça türüdür <xref:System.Drawing.SolidBrush>, devralan <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="08850-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="08850-115">Tarama fırçalarını</span><span class="sxs-lookup"><span data-stu-id="08850-115">Hatch Brushes</span></span>  
 <span data-ttu-id="08850-116">Bir şekli tarama fırça ile doldurduğunuzda ön plan rengini, arka plan rengi ve bir tarama stilini belirtin.</span><span class="sxs-lookup"><span data-stu-id="08850-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="08850-117">Ön plan rengini tarama rengi ' dir.</span><span class="sxs-lookup"><span data-stu-id="08850-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="08850-118">50'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stillerdir <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="08850-118"> provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="08850-119">![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="08850-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="08850-120">Doku fırçaları</span><span class="sxs-lookup"><span data-stu-id="08850-120">Texture Brushes</span></span>  
 <span data-ttu-id="08850-121">Doku fırça ile bir şekli bir bitmap depolanan bir desen ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08850-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="08850-122">Örneğin, aşağıdaki resimde adlı bir disk dosyasında depolanan varsayalım `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="08850-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="08850-123">![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="08850-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="08850-124">Aşağıdaki kod örneğinde depolanan resim tekrarlayarak elips doldurmak nasıl gösterir `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="08850-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="08850-125">Aşağıdaki çizimde doldurulmuş elips gösterir.</span><span class="sxs-lookup"><span data-stu-id="08850-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="08850-126">![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="08850-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="08850-127">Gradyan Fırçalar</span><span class="sxs-lookup"><span data-stu-id="08850-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="08850-128">Gradyan Fırçalar iki tür sağlar: doğrusal ve yolu.</span><span class="sxs-lookup"><span data-stu-id="08850-128"> provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="08850-129">Bir şekli kademeli olarak şekli arasında taşıdığınızda gibi yatay, dikey veya çapraz değişiklikler renkle doldurmak için doğrusal gradyan fırçası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08850-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="08850-130">Aşağıdaki kod örneğinde elips elips sol kenarından sağ kenarı hareket ederken, yeşil mavi değişiklikler yatay bir gradyan fırçası doldurmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="08850-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="08850-131">Aşağıdaki çizimde doldurulmuş elips gösterir.</span><span class="sxs-lookup"><span data-stu-id="08850-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="08850-132">![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="08850-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="08850-133">Yolun gradyan fırçası kenar doğru şeklin Merkezi'nden taşırken rengini değiştirmek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="08850-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="08850-134">![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="08850-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="08850-135">Yolun gradyan Fırçalar oldukça esnektir.</span><span class="sxs-lookup"><span data-stu-id="08850-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="08850-136">Aşağıdaki çizimde değişikliklerden kademeli olarak kırmızı Center'da her üç farklı renk köşeleri adresindeki üçgen doldurmak için kullanılan gradyan fırçası.</span><span class="sxs-lookup"><span data-stu-id="08850-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="08850-137">![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="08850-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08850-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08850-138">See Also</span></span>  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [<span data-ttu-id="08850-139">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="08850-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="08850-140">Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme</span><span class="sxs-lookup"><span data-stu-id="08850-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [<span data-ttu-id="08850-141">Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme</span><span class="sxs-lookup"><span data-stu-id="08850-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
