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
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912226"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="4237e-102">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="4237e-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="4237e-103">Dikdörtgen veya elips gibi kapalı bir şekil, bir ana hat ve iç öğesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4237e-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="4237e-104">Ana hat bir kalemle çizilir ve iç kısım fırçayla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4237e-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> <span data-ttu-id="4237e-105">GDI+ kapalı şekillerin,,, ve özelliklerini doldurmak için çeşitli fırça sınıfları sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush> <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="4237e-105">GDI+ provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="4237e-106">Bu sınıfların hepsi <xref:System.Drawing.Brush> sınıfından devralınır.</span><span class="sxs-lookup"><span data-stu-id="4237e-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="4237e-107">Aşağıdaki çizimde, düz fırçayla doldurulmuş bir dikdörtgen ve bir tarama fırçası ile doldurulmuş bir elips gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4237e-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="4237e-108">![Doldurulmuş şekiller](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="4237e-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="4237e-109">Düz fırçalar</span><span class="sxs-lookup"><span data-stu-id="4237e-109">Solid Brushes</span></span>  
 <span data-ttu-id="4237e-110">Kapalı bir şekli doldurmanız için, <xref:System.Drawing.Graphics> sınıfının ve bir <xref:System.Drawing.Brush>örneğinin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4237e-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="4237e-111"><xref:System.Drawing.Graphics> Sınıfının örneği, <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A> gibiyöntemlersağlarveörneğinColorvemodelgibi<xref:System.Drawing.Brush> dolgunun özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="4237e-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="4237e-112">, <xref:System.Drawing.Brush> Fill metoduna bağımsız değişkenlerden biri olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4237e-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="4237e-113">Aşağıdaki kod örneği, bir elipsin düz kırmızı renkle nasıl doldurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4237e-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> <span data-ttu-id="4237e-114">Yukarıdaki örnekte, fırça, ' den <xref:System.Drawing.SolidBrush> <xref:System.Drawing.Brush>devralan türüdür.</span><span class="sxs-lookup"><span data-stu-id="4237e-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="4237e-115">Tarama fırçaları</span><span class="sxs-lookup"><span data-stu-id="4237e-115">Hatch Brushes</span></span>  
 <span data-ttu-id="4237e-116">Bir şekli tarama fırçası ile doldururken bir ön plan rengi, arka plan rengi ve tarama stili belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4237e-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="4237e-117">Ön plan rengi, tarama renggidir.</span><span class="sxs-lookup"><span data-stu-id="4237e-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 <span data-ttu-id="4237e-118">GDI+ 50 'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stil, <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal> <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>' dir.</span><span class="sxs-lookup"><span data-stu-id="4237e-118">GDI+ provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="4237e-119">![Doldurulmuş şekiller](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="4237e-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="4237e-120">Doku fırçaları</span><span class="sxs-lookup"><span data-stu-id="4237e-120">Texture Brushes</span></span>  
 <span data-ttu-id="4237e-121">Bir doku fırçası ile bir şekli bit eşlemde depolanan bir desenli doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4237e-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="4237e-122">Örneğin, aşağıdaki resmin adlı `MyTexture.bmp`bir disk dosyasında depolandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4237e-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="4237e-123">![Doldurulmuş şekil](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="4237e-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="4237e-124">Aşağıdaki kod örneği, içinde `MyTexture.bmp`depolanan resmi tekrarlayarak nasıl bir elips doldurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4237e-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="4237e-125">Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4237e-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="4237e-126">![Doldurulmuş şekil](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="4237e-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="4237e-127">Gradyan fırçaları</span><span class="sxs-lookup"><span data-stu-id="4237e-127">Gradient Brushes</span></span>  
 <span data-ttu-id="4237e-128">GDI+ iki tür gradyan fırça sağlar: doğrusal ve yol.</span><span class="sxs-lookup"><span data-stu-id="4237e-128">GDI+ provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="4237e-129">Doğrusal bir gradyan fırçası kullanarak şekli yatay, dikey veya çapraz bir şekilde hareket ettirmek için kademeli olarak değişen renkle doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4237e-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="4237e-130">Aşağıdaki kod örneği, elips sol kenarından sağ kenara hareket ettirmek için mavi ile yeşil arasında değişen bir elipsi yatay bir gradyan fırçayla nasıl dolduracağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4237e-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="4237e-131">Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4237e-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="4237e-132">![Doldurulmuş şekil](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="4237e-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="4237e-133">Bir yol gradyan fırçası, bir şeklin merkezinden kenara doğru hareket eden rengi değiştirecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4237e-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="4237e-134">![Doldurulmuş şekil](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="4237e-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="4237e-135">Yol gradyan fırçaları oldukça esnektir.</span><span class="sxs-lookup"><span data-stu-id="4237e-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="4237e-136">Aşağıdaki çizimde yer değiştiren üçgeni doldurmaları için kullanılan gradyan fırçası, köşelerin her üç farklı rengin her biri için ortadaki kırmızı 'dan kırmızıya değişir.</span><span class="sxs-lookup"><span data-stu-id="4237e-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="4237e-137">![Doldurulmuş şekil](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="4237e-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4237e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4237e-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="4237e-139">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="4237e-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="4237e-140">Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme</span><span class="sxs-lookup"><span data-stu-id="4237e-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="4237e-141">Nasıl yapılır: Bir Windows formunda doldurulmuş Elips çizme</span><span class="sxs-lookup"><span data-stu-id="4237e-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
