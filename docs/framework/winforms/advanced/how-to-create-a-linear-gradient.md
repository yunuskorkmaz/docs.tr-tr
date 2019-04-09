---
title: 'Nasıl yapılır: Doğrusal Gradyan Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 540b6d422be5d5c0898f019592a755258145d14d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125027"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="92a49-102">Nasıl yapılır: Doğrusal Gradyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="92a49-102">How to: Create a Linear Gradient</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="92a49-103">Yatay, dikey ve Çapraz doğrusal gradyanlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="92a49-103">provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="92a49-104">Varsayılan olarak, aynı şekilde doğrusal gradyan rengi değişir.</span><span class="sxs-lookup"><span data-stu-id="92a49-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="92a49-105">Ancak, Tekdüzen olmayan biçimde rengini değiştirir, böylece doğrusal gradyan özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92a49-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  
  
 <span data-ttu-id="92a49-106">Aşağıdaki örnek, bir satır, bir elips ve dikdörtgen Yatay doğrusal gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="92a49-106">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
 <span data-ttu-id="92a49-107"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu dört bağımsız değişken alır: iki nokta ve iki rengi.</span><span class="sxs-lookup"><span data-stu-id="92a49-107">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="92a49-108">İlk noktası (0, 10) ilk rengi (kırmızı) ile ilişkilendirilir ve ikinci bir nokta (200, 10) ikinci rengi (mavi) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="92a49-108">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="92a49-109">Gelen çizgi beklediğiniz gibi (0, 10) için (200, 10) değişiklikleri aşamalı olarak mavi ve kırmızı.</span><span class="sxs-lookup"><span data-stu-id="92a49-109">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="92a49-110">10'luk bloklar noktaları (50, 10) ve (200, 10) önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="92a49-110">The 10s in the points (50, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="92a49-111">Önemli olan, iki nokta aynı ikinci koordinat sahip olabilir; bunları bağlayan bir çizgi yataydır.</span><span class="sxs-lookup"><span data-stu-id="92a49-111">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="92a49-112">Elips ve dikdörtgen de aşamalı olarak kırmızı, mavi ve yatay koordinatı 0 ile 200'e gider gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92a49-112">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="92a49-113">Aşağıdaki çizimde, çizgi, elips ve dikdörtgen gösterilir.</span><span class="sxs-lookup"><span data-stu-id="92a49-113">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="92a49-114">Yatay koordinat 200 arttıkça renk gradyanı kendisini tekrarlar olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92a49-114">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="92a49-115">![Doğrusal gradyan](./media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="92a49-115">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="92a49-116">Yatay doğrusal gradyanlar kullanmak için</span><span class="sxs-lookup"><span data-stu-id="92a49-116">To use horizontal linear gradients</span></span>  
  
-   <span data-ttu-id="92a49-117">Donuk kırmızı ve donuk mavi renkle üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="92a49-117">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="92a49-118">Önceki örnekte, 200 yatay koordinat için 0 yatay bir Koordinattan geçerken renk bileşenlerine doğrusal olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="92a49-118">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="92a49-119">Örneğin, bir nokta olan ilk koordinatı 0 ile 200 arasında olan sürenin yarısına ulaşıldığında, 0 ile 255 arasında ortasında ise mavi bir bileşen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="92a49-119">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="92a49-120">bir renk gradyan kenarından değişir şekilde ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="92a49-120">allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="92a49-121">Siyahtan kırmızı aşağıdaki tabloya göre değiştiren bir gradyan fırçası oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="92a49-121">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="92a49-122">Yatay koordinatı</span><span class="sxs-lookup"><span data-stu-id="92a49-122">Horizontal coordinate</span></span>|<span data-ttu-id="92a49-123">RGB bileşenleri</span><span class="sxs-lookup"><span data-stu-id="92a49-123">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="92a49-124">0</span><span class="sxs-lookup"><span data-stu-id="92a49-124">0</span></span>|<span data-ttu-id="92a49-125">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="92a49-125">(0, 0, 0)</span></span>|  
|<span data-ttu-id="92a49-126">40</span><span class="sxs-lookup"><span data-stu-id="92a49-126">40</span></span>|<span data-ttu-id="92a49-127">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="92a49-127">(128, 0, 0)</span></span>|  
|<span data-ttu-id="92a49-128">200</span><span class="sxs-lookup"><span data-stu-id="92a49-128">200</span></span>|<span data-ttu-id="92a49-129">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="92a49-129">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="92a49-130">Yatay koordinatı 0 ile 200 biçimini yüzde 20'sinden yalnızca olduğunda kırmızı bileşeni yarım yoğunlukta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92a49-130">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="92a49-131">Aşağıdaki örnek kümeleri <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> özelliği bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> üç göreli yoğunluklarını üç göreli konum ile ilişkilendirilecek bir nesne.</span><span class="sxs-lookup"><span data-stu-id="92a49-131">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> property of a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="92a49-132">Yukarıdaki tabloda olduğu gibi bir göreli 0,5 yoğunluğunu 0.2 göreli bir konum ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="92a49-132">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="92a49-133">Kod, bir elips ve dikdörtgen gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="92a49-133">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="92a49-134">Aşağıdaki çizimde, sonuçta elde edilen elips ve dikdörtgen gösterilir.</span><span class="sxs-lookup"><span data-stu-id="92a49-134">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="92a49-135">![Doğrusal gradyan](./media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="92a49-135">![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")</span></span>  
  
### <a name="to-customize-linear-gradients"></a><span data-ttu-id="92a49-136">Doğrusal gradyanlar özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="92a49-136">To customize linear gradients</span></span>  
  
-   <span data-ttu-id="92a49-137">Donuk siyah ve donuk kırmızı renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="92a49-137">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="92a49-138">Önceki örneklerde gradyanlar yatay; yatay bir çizgi boyunca taşımak gibi diğer bir deyişle, kademeli olarak rengi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="92a49-138">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="92a49-139">Dikey Gradyan ve çapraz gradyanlar de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92a49-139">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="92a49-140">Aşağıdaki örnek noktaları (0, 0) ve (200, 100) geçirir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="92a49-140">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="92a49-141">Mavi ilişkili olduğu (0, 0) ve yeşil ilişkili olduğu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="92a49-141">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="92a49-142">Doğrusal gradyan fırçası ile bir satır (Kalem genişliği 10 ile) bir elips doldurulur.</span><span class="sxs-lookup"><span data-stu-id="92a49-142">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="92a49-143">Aşağıdaki çizim, satır ve üç nokta gösterir.</span><span class="sxs-lookup"><span data-stu-id="92a49-143">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="92a49-144">Not geçerken elips değişiklikleri rengi kademeli olarak satırında aracılığıyla geçirme satırına paralel (0, 0) ve (200, 100).</span><span class="sxs-lookup"><span data-stu-id="92a49-144">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="92a49-145">![Doğrusal gradyan](./media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="92a49-145">![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="92a49-146">Çapraz doğrusal gradyanlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="92a49-146">To create diagonal linear gradients</span></span>  
  
-   <span data-ttu-id="92a49-147">Donuk mavi ve donuk yeşil renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="92a49-147">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="92a49-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92a49-148">See also</span></span>

- [<span data-ttu-id="92a49-149">Şekilleri Doldurmak için Gradyan Fırçası Kullanma</span><span class="sxs-lookup"><span data-stu-id="92a49-149">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="92a49-150">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="92a49-150">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
