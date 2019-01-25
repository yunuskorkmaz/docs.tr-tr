---
title: 'Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle (Visual Studio) ile şekil çizme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701228"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="faa60-102">Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle (Visual Studio) ile şekil çizme</span><span class="sxs-lookup"><span data-stu-id="faa60-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="faa60-103">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> daireler veya Oval bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="faa60-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="faa60-104">Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kareler, dikdörtgenler veya bir form veya kapsayıcı yuvarlak köşeli dikdörtgen çizmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="faa60-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="faa60-105">Bu denetimi, hem tasarım zamanında hem de çalışma zamanında şekiller çizmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="faa60-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="faa60-106">Genişlik, renk ve kenarlık stilini değiştirerek bir şekil görünümünü özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="faa60-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="faa60-107">Varsayılan olarak arka planda bir şeklin şeffaftır; düz renk, bir desen, bir Gradyan Dolgu (bir renk diğerine geçiş) veya bir görüntü görüntülenecek arka plan özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="faa60-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="faa60-108">Basit bir şekil tasarım zamanında çizmek için</span><span class="sxs-lookup"><span data-stu-id="faa60-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="faa60-109">Sürükleme <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> veya <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimi **Visual Basic PowerPacks** sekme (yüklemek için bkz [Visual Basic Power Packs denetimlerine](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) içinde **araç kutusu** bir form veya kapsayıcı denetimi.</span><span class="sxs-lookup"><span data-stu-id="faa60-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-110">Boyutlandırma sürükleyin ve boyutu ve şekli yerleştirmek için tutamaçlarını taşıyın.</span><span class="sxs-lookup"><span data-stu-id="faa60-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="faa60-111">Ayrıca boyutu ve şekli değiştirerek yerleştirmek `Size` ve `Position` özelliklerinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="faa60-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="faa60-112">Yuvarlatılmış köşelere sahip bir dikdörtgen oluşturmak için seçin `CornerRadius` özelliğinde **özellikleri** penceresi ve 0'dan büyük bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="faa60-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="faa60-113">İçinde **özellikleri** penceresinde şekli görünümünü değiştirmek için isteğe bağlı olarak ek özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="faa60-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="faa60-114">Basit bir şekil çalışma zamanında çizmek için</span><span class="sxs-lookup"><span data-stu-id="faa60-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="faa60-115">Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="faa60-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="faa60-116">İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="faa60-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="faa60-117">İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:</span><span class="sxs-lookup"><span data-stu-id="faa60-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="faa60-118">Aşağıdaki kodu ekleyin bir `Event` yordam:</span><span class="sxs-lookup"><span data-stu-id="faa60-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="faa60-119">Şekiller özelleştirme</span><span class="sxs-lookup"><span data-stu-id="faa60-119">Customizing Shapes</span></span>  
 <span data-ttu-id="faa60-120">Varsayılan ayarları kullandığınızda <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri bir piksel genişliğinde ve saydam bir arka plan olan düz bir siyah kenarlığa görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="faa60-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="faa60-121">Özelliklerini ayarlayarak, genişlik, stili ve kenarlık rengini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="faa60-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="faa60-122">Ek özellikler arka planını bir şekli düz renk, bir desen, bir gradyan dolgu veya görüntü değiştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="faa60-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="faa60-123">Bir şeklin arka değiştirmeden önce birkaç özelliklerini nasıl etkileşimde bulunduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="faa60-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="faa60-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Özellik ayarı hiçbir etkisi sürece <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="faa60-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="faa60-125">Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> geçersiz kılmalar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="faa60-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="faa60-126">Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış bir desen değerine gibi <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> veya <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, deseni görüntülenmesi <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="faa60-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="faa60-127">Arka plan görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, koşuluyla <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="faa60-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="faa60-128">Bir Gradyan Dolgu görüntülemek için <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmalıdır <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> ve <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> özelliği ayarlanmalıdır değerine dışında <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="faa60-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="faa60-129">Ayar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> görüntü özelliğini, diğer tüm arka plan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="faa60-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="faa60-130">Özel bir kenarlığa sahip bir daire çizin</span><span class="sxs-lookup"><span data-stu-id="faa60-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="faa60-131">Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-132">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="faa60-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="faa60-133">Ayarlama `BorderColor` özelliğini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="faa60-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="faa60-134">Ayarlama `BorderStyle` dışında herhangi bir değer özelliğini `Solid`.</span><span class="sxs-lookup"><span data-stu-id="faa60-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="faa60-135">Ayarlama `BorderWidth` piksel cinsinden istediğiniz boyuta.</span><span class="sxs-lookup"><span data-stu-id="faa60-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="faa60-136">Bir tek renk dolgu olan bir daire çizme</span><span class="sxs-lookup"><span data-stu-id="faa60-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="faa60-137">Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-138">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="faa60-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="faa60-139">Ayarlama `BackColor` özelliğini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="faa60-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="faa60-140">Ayarlama `BackStyle` özelliğini `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="faa60-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="faa60-141">Desenli dolgu olan bir daire çizme</span><span class="sxs-lookup"><span data-stu-id="faa60-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="faa60-142">Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-143">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="faa60-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="faa60-144">Ayarlama `BackColor` özelliğini istediğiniz için arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="faa60-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="faa60-145">Ayarlama `BackStyle` özelliğini `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="faa60-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="faa60-146">Ayarlama `FillColor` özelliğini desenini istediğiniz rengi.</span><span class="sxs-lookup"><span data-stu-id="faa60-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="faa60-147">Ayarlama `FillStyle` dışında herhangi bir değer özelliğini `Transparent` veya `Solid`.</span><span class="sxs-lookup"><span data-stu-id="faa60-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="faa60-148">Gradyan Dolgu olan bir daire çizme</span><span class="sxs-lookup"><span data-stu-id="faa60-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="faa60-149">Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-150">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="faa60-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="faa60-151">Ayarlama `FillColor` başlangıç rengini istediğiniz renkle özelliği.</span><span class="sxs-lookup"><span data-stu-id="faa60-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="faa60-152">Ayarlama `FillGradientColor` Bitiş rengini istediğiniz renkle özelliği.</span><span class="sxs-lookup"><span data-stu-id="faa60-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="faa60-153">Ayarlama `FillGradientStyle` dışında bir değere `None`.</span><span class="sxs-lookup"><span data-stu-id="faa60-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="faa60-154">Bir görüntü ile dolu bir daire çizin</span><span class="sxs-lookup"><span data-stu-id="faa60-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="faa60-155">Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="faa60-156">İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="faa60-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="faa60-157">Seçin `BackgroundImage` özelliği ve tıklatın **üç nokta** düğmesini (…).</span><span class="sxs-lookup"><span data-stu-id="faa60-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="faa60-158">İçinde **seçin kaynak** iletişim kutusunda görüntülenecek resmin seçin.</span><span class="sxs-lookup"><span data-stu-id="faa60-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="faa60-159">Hiçbir resim kaynakları listelenirse, tıklayın **alma** bir görüntü dosyasının konumuna gidin.</span><span class="sxs-lookup"><span data-stu-id="faa60-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="faa60-160">Tıklayın **Tamam** resim eklemek için.</span><span class="sxs-lookup"><span data-stu-id="faa60-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa60-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa60-161">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [<span data-ttu-id="faa60-162">Çizgi ve Şekil Denetimlerine Giriş</span><span class="sxs-lookup"><span data-stu-id="faa60-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="faa60-163">Nasıl yapılır: LineShape denetimiyle çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="faa60-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
