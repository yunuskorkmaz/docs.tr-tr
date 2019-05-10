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
ms.openlocfilehash: 953a1944073a8cb5b19ef072e2a523baec3a5605
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650001"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="b80c6-102">Nasıl yapılır: Doğrusal Gradyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b80c6-102">How to: Create a Linear Gradient</span></span>
<span data-ttu-id="b80c6-103">GDI +'da yatay, dikey ve Çapraz doğrusal gradyanlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b80c6-103">GDI+ provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="b80c6-104">Varsayılan olarak, aynı şekilde doğrusal gradyan rengi değişir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="b80c6-105">Ancak, Tekdüzen olmayan biçimde rengini değiştirir, böylece doğrusal gradyan özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b80c6-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  

> [!NOTE]
> <span data-ttu-id="b80c6-106">Bu makaledeki örneklerde bir denetimin çağrılan yöntemlerdir <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="b80c6-106">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

<span data-ttu-id="b80c6-107">Aşağıdaki örnek, bir satır, bir elips ve dikdörtgen Yatay doğrusal gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="b80c6-107">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
<span data-ttu-id="b80c6-108"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu dört bağımsız değişken alır: iki nokta ve iki rengi.</span><span class="sxs-lookup"><span data-stu-id="b80c6-108">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="b80c6-109">İlk noktası (0, 10) ilk rengi (kırmızı) ile ilişkilendirilir ve ikinci bir nokta (200, 10) ikinci rengi (mavi) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-109">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="b80c6-110">Gelen çizgi beklediğiniz gibi (0, 10) için (200, 10) değişiklikleri aşamalı olarak mavi ve kırmızı.</span><span class="sxs-lookup"><span data-stu-id="b80c6-110">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="b80c6-111">10'luk bloklar noktaları (0, 10) ve (200, 10) önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-111">The 10s in the points (0, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="b80c6-112">Önemli olan, iki nokta aynı ikinci koordinat sahip olabilir; bunları bağlayan bir çizgi yataydır.</span><span class="sxs-lookup"><span data-stu-id="b80c6-112">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="b80c6-113">Elips ve dikdörtgen de aşamalı olarak kırmızı, mavi ve yatay koordinatı 0 ile 200'e gider gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b80c6-113">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="b80c6-114">Aşağıdaki çizimde, çizgi, elips ve dikdörtgen gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-114">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="b80c6-115">Yatay koordinat 200 arttıkça renk gradyanı kendisini tekrarlar olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b80c6-115">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="b80c6-116">![Doğrusal gradyan](./media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="b80c6-116">![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="b80c6-117">Yatay doğrusal gradyanlar kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b80c6-117">To use horizontal linear gradients</span></span>  
  
- <span data-ttu-id="b80c6-118">Donuk kırmızı ve donuk mavi renkle üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="b80c6-118">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="b80c6-119">Önceki örnekte, 200 yatay koordinat için 0 yatay bir Koordinattan geçerken renk bileşenlerine doğrusal olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b80c6-119">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="b80c6-120">Örneğin, bir nokta olan ilk koordinatı 0 ile 200 arasında olan sürenin yarısına ulaşıldığında, 0 ile 255 arasında ortasında ise mavi bir bileşen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b80c6-120">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 <span data-ttu-id="b80c6-121">GDI +'da, bir renk gradyan kenarından değişir şekilde ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b80c6-121">GDI+ allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="b80c6-122">Siyahtan kırmızı aşağıdaki tabloya göre değiştiren bir gradyan fırçası oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="b80c6-122">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="b80c6-123">Yatay koordinatı</span><span class="sxs-lookup"><span data-stu-id="b80c6-123">Horizontal coordinate</span></span>|<span data-ttu-id="b80c6-124">RGB bileşenleri</span><span class="sxs-lookup"><span data-stu-id="b80c6-124">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="b80c6-125">0</span><span class="sxs-lookup"><span data-stu-id="b80c6-125">0</span></span>|<span data-ttu-id="b80c6-126">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b80c6-126">(0, 0, 0)</span></span>|  
|<span data-ttu-id="b80c6-127">40</span><span class="sxs-lookup"><span data-stu-id="b80c6-127">40</span></span>|<span data-ttu-id="b80c6-128">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b80c6-128">(128, 0, 0)</span></span>|  
|<span data-ttu-id="b80c6-129">200</span><span class="sxs-lookup"><span data-stu-id="b80c6-129">200</span></span>|<span data-ttu-id="b80c6-130">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="b80c6-130">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="b80c6-131">Yatay koordinatı 0 ile 200 biçimini yüzde 20'sinden yalnızca olduğunda kırmızı bileşeni yarım yoğunlukta olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b80c6-131">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="b80c6-132">Aşağıdaki örnek kümeleri <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> üç göreli yoğunluklarını üç göreli konum ile ilişkilendirilecek özellik.</span><span class="sxs-lookup"><span data-stu-id="b80c6-132">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> property to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="b80c6-133">Yukarıdaki tabloda olduğu gibi bir göreli 0,5 yoğunluğunu 0.2 göreli bir konum ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-133">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="b80c6-134">Kod, bir elips ve dikdörtgen gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="b80c6-134">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="b80c6-135">Aşağıdaki çizimde, sonuçta elde edilen elips ve dikdörtgen gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-135">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="b80c6-136">![Doğrusal gradyan](./media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="b80c6-136">![Linear Gradient](./media/cslineargradient2.png "cslineargradient2")</span></span>  

### <a name="to-customize-linear-gradients"></a><span data-ttu-id="b80c6-137">Doğrusal gradyanlar özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b80c6-137">To customize linear gradients</span></span>  
  
- <span data-ttu-id="b80c6-138">Donuk siyah ve donuk kırmızı renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="b80c6-138">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="b80c6-139">Önceki örneklerde gradyanlar yatay; yatay bir çizgi boyunca taşımak gibi diğer bir deyişle, kademeli olarak rengi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-139">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="b80c6-140">Dikey Gradyan ve çapraz gradyanlar de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b80c6-140">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="b80c6-141">Aşağıdaki örnek noktaları (0, 0) ve (200, 100) geçirir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b80c6-141">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="b80c6-142">Mavi ilişkili olduğu (0, 0) ve yeşil ilişkili olduğu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b80c6-142">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="b80c6-143">Doğrusal gradyan fırçası ile bir satır (Kalem genişliği 10 ile) bir elips doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b80c6-143">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="b80c6-144">Aşağıdaki çizim, satır ve üç nokta gösterir.</span><span class="sxs-lookup"><span data-stu-id="b80c6-144">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="b80c6-145">Not geçerken elips değişiklikleri rengi kademeli olarak satırında aracılığıyla geçirme satırına paralel (0, 0) ve (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b80c6-145">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="b80c6-146">![Doğrusal gradyan](./media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="b80c6-146">![Linear Gradient](./media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="b80c6-147">Çapraz doğrusal gradyanlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="b80c6-147">To create diagonal linear gradients</span></span>  
  
- <span data-ttu-id="b80c6-148">Donuk mavi ve donuk yeşil renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.</span><span class="sxs-lookup"><span data-stu-id="b80c6-148">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="b80c6-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b80c6-149">See also</span></span>

- [<span data-ttu-id="b80c6-150">Şekilleri Doldurmak için Gradyan Fırçası Kullanma</span><span class="sxs-lookup"><span data-stu-id="b80c6-150">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="b80c6-151">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="b80c6-151">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
