---
title: "Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="cdd99-102">Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="cdd99-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="cdd99-103">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> daireler veya Oval bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetim.</span><span class="sxs-lookup"><span data-stu-id="cdd99-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="cdd99-104">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kareler, dikdörtgenler veya bir form veya kapsayıcı yuvarlak köşeli dikdörtgen çizmek için denetim.</span><span class="sxs-lookup"><span data-stu-id="cdd99-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="cdd99-105">Bu denetim, hem tasarım zamanında hem de çalışma zamanında şekiller çizmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd99-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="cdd99-106">Genişlik, renk ve kenarlık stilini değiştirerek bir şekli görünümünü özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd99-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="cdd99-107">Şeklin arka plan, varsayılan olarak saydamdır; düz renk, bir deseni, bir Gradyan Dolgu (bir renkten diğerine geçiş) veya bir görüntü görüntülemek için arka plan özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd99-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="cdd99-108">Tasarım zamanında basit bir şekil çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="cdd99-109">Sürükle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> veya <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> gelen denetim **Visual Basic PowerPacks** sekmesini (yüklemek için bkz: [Visual Basic Power Packs denetimlerine](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) içinde **araç kutusu** bir form veya kapsayıcı denetimi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-110">Boyutlandırma sürükleyin ve boyutu ve şekli konumlandırmak için tanıtıcıları taşıyın.</span><span class="sxs-lookup"><span data-stu-id="cdd99-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="cdd99-111">Ayrıca boyutu ve şekli değiştirerek Yerleştir `Size` ve `Position` özelliklerinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="cdd99-112">Dikdörtgene yuvarlanmış köşeleri ile oluşturmak için seçin `CornerRadius` özelliğinde **özellikleri** penceresi ve 0'dan büyük bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cdd99-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="cdd99-113">İçinde **özellikleri** penceresinde, Şekil görünümünü değiştirmek için isteğe bağlı olarak ek özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cdd99-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="cdd99-114">Çalışma zamanında basit bir şekil çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="cdd99-115">Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cdd99-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="cdd99-116">İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cdd99-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="cdd99-117">İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:</span><span class="sxs-lookup"><span data-stu-id="cdd99-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="cdd99-118">Aşağıdaki kodu ekleyin bir `Event` yordam:</span><span class="sxs-lookup"><span data-stu-id="cdd99-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="cdd99-119">Şekilleri özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cdd99-119">Customizing Shapes</span></span>  
 <span data-ttu-id="cdd99-120">Varsayılan ayarları kullandığınızda <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri bir piksel genişliğinde ve saydam arka plan düz bir siyah kenarlığa görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cdd99-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="cdd99-121">Özellikleri ayarlayarak enini, tarzını ve kenarlık rengini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd99-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="cdd99-122">Ek özellikler arka planını bir şekli düz renk, bir deseni, bir gradyan dolgu veya bir görüntü değiştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cdd99-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="cdd99-123">Arka plan şeklin değiştirmeden önce birkaç özelliklerini nasıl etkileşim bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cdd99-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="cdd99-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Özellik ayarı hiçbir etkisi sürece <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="cdd99-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="cdd99-125">Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> geçersiz kılmaları <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd99-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="cdd99-126">Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış bir desen değeri gibi <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> veya <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, düzeni görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd99-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="cdd99-127">Arka plan görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, koşuluyla <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="cdd99-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="cdd99-128">Gradyan Dolgu görüntülemek için <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmalıdır <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> ve <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> özelliği ayarlanmalıdır değerine dışında <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="cdd99-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="cdd99-129">Ayar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> özelliği bir görüntü için diğer tüm arka plan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="cdd99-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="cdd99-130">Özel kenarlık sahip bir daire çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="cdd99-131">Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-132">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="cdd99-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="cdd99-133">Ayarlama `BorderColor` özelliğini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="cdd99-134">Ayarlama `BorderStyle` dışında herhangi bir değer özelliğine `Solid`.</span><span class="sxs-lookup"><span data-stu-id="cdd99-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="cdd99-135">Ayarlama `BorderWidth` piksel cinsinden istediğiniz boyutu.</span><span class="sxs-lookup"><span data-stu-id="cdd99-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="cdd99-136">Düz Dolgu sahip bir daire çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="cdd99-137">Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-138">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="cdd99-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="cdd99-139">Ayarlama `BackColor` özelliğini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="cdd99-140">Ayarlama `BackStyle` özelliğine `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="cdd99-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="cdd99-141">Desenli dolgusu olan bir daire çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="cdd99-142">Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-143">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="cdd99-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="cdd99-144">Ayarlama `BackColor` özelliğini istediğiniz için arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="cdd99-145">Ayarlama `BackStyle` özelliğine `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="cdd99-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="cdd99-146">Ayarlama `FillColor` desenini istediğiniz renk özelliğine.</span><span class="sxs-lookup"><span data-stu-id="cdd99-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="cdd99-147">Ayarlama `FillStyle` dışında herhangi bir değer özelliğine `Transparent` veya `Solid`.</span><span class="sxs-lookup"><span data-stu-id="cdd99-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="cdd99-148">Gradyan dolgusu olan bir daire çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="cdd99-149">Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-150">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="cdd99-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="cdd99-151">Ayarlama `FillColor` özelliğini başlangıç rengini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="cdd99-152">Ayarlama `FillGradientColor` özelliğini Bitiş rengini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd99-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="cdd99-153">Ayarlama `FillGradientStyle` dışında bir değere özelliğine `None`.</span><span class="sxs-lookup"><span data-stu-id="cdd99-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="cdd99-154">Bir görüntü ile doldurulan bir daire çizmek için</span><span class="sxs-lookup"><span data-stu-id="cdd99-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="cdd99-155">Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cdd99-156">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="cdd99-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="cdd99-157">Seçin `BackgroundImage` özelliği ve tıklatın **üç nokta** düğmesini (…).</span><span class="sxs-lookup"><span data-stu-id="cdd99-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="cdd99-158">İçinde **Select Resource** iletişim kutusunda, görüntülemek için görüntüyü bir seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd99-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="cdd99-159">Hiçbir görüntü kaynakları listelenmiyorsa, tıklatın **alma** bir görüntü dosyasının konumuna gidin.</span><span class="sxs-lookup"><span data-stu-id="cdd99-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="cdd99-160">Tıklatın **Tamam** resim eklemek için.</span><span class="sxs-lookup"><span data-stu-id="cdd99-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd99-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd99-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="cdd99-162">Çizgi ve Şekil denetimlerine giriş</span><span class="sxs-lookup"><span data-stu-id="cdd99-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="cdd99-163">Nasıl yapılır: LineShape denetimiyle</span><span class="sxs-lookup"><span data-stu-id="cdd99-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
