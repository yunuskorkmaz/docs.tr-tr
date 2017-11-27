---
title: "Nasıl yapılır: Doğrusal Gradyan Oluşturma"
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
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="eceb5-102">Nasıl yapılır: Doğrusal Gradyan Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eceb5-102">How to: Create a Linear Gradient</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="eceb5-103">Yatay, dikey ve Çapraz doğrusal gradyanlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="eceb5-103"> provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="eceb5-104">Varsayılan olarak, doğrusal gradyan rengi aynı şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="eceb5-105">Bununla birlikte, böylece Tekdüzen olmayan biçimde rengi değişir doğrusal gradyan özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eceb5-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  
  
 <span data-ttu-id="eceb5-106">Aşağıdaki örnek, bir satırı, elips ve dikdörtgen Yatay doğrusal gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="eceb5-106">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
 <span data-ttu-id="eceb5-107"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu dört bağımsız değişkenleri alır: iki nokta ve iki rengi.</span><span class="sxs-lookup"><span data-stu-id="eceb5-107">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="eceb5-108">İlk (0, 10) ilk rengi (kırmızı) ile ilişkili noktasıdır ve ikinci bir nokta (200, 10) ikinci rengi (mavi) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-108">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="eceb5-109">Gelen çizgi beklediğiniz gibi (0, 10) için (200, 10) değişiklikleri kademeli olarak mavi ve kırmızı.</span><span class="sxs-lookup"><span data-stu-id="eceb5-109">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="eceb5-110">10'luk bloklar noktaları (50, 10) ve (200, 10) önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-110">The 10s in the points (50, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="eceb5-111">Önemli olan iki nokta aynı ikinci koordinat olmasıdır — bunları bağlayan bir çizgi yataydır.</span><span class="sxs-lookup"><span data-stu-id="eceb5-111">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="eceb5-112">Elips ve dikdörtgen ayrıca kademeli olarak yatay koordinat 200'e 0'dan geçtikçe mavi ve kırmızı gelen değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-112">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="eceb5-113">Aşağıdaki çizimde, satır, elips ve dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-113">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="eceb5-114">Yatay koordinat 200 arttıkça renk gradyan kendisini tekrarlar olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eceb5-114">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="eceb5-115">![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="eceb5-115">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="eceb5-116">Yatay doğrusal gradyanlar kullanmak için</span><span class="sxs-lookup"><span data-stu-id="eceb5-116">To use horizontal linear gradients</span></span>  
  
-   <span data-ttu-id="eceb5-117">Donuk kırmızı ve donuk mavi renkte sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-117">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="eceb5-118">Yatay koordinatını 200 için yatay koordinatını 0 taşımak gibi önceki örnekte, renk bileşenleri doğrusal olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-118">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="eceb5-119">Örneğin, ilk koordinat 0 ve 200 arasında ortasında yer alan bir noktası 0 ile 255 arasında ortasında yer alan mavi bir bileşen sahip olur.</span><span class="sxs-lookup"><span data-stu-id="eceb5-119">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="eceb5-120">bir renk bir gradyan kenarından değişir şekilde ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eceb5-120"> allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="eceb5-121">Kırmızı aşağıdaki tabloya göre siyah değişikliklerini bir gradyan fırçası oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="eceb5-121">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="eceb5-122">Yatay koordinat</span><span class="sxs-lookup"><span data-stu-id="eceb5-122">Horizontal coordinate</span></span>|<span data-ttu-id="eceb5-123">RGB bileşenleri</span><span class="sxs-lookup"><span data-stu-id="eceb5-123">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="eceb5-124">0</span><span class="sxs-lookup"><span data-stu-id="eceb5-124">0</span></span>|<span data-ttu-id="eceb5-125">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="eceb5-125">(0, 0, 0)</span></span>|  
|<span data-ttu-id="eceb5-126">40</span><span class="sxs-lookup"><span data-stu-id="eceb5-126">40</span></span>|<span data-ttu-id="eceb5-127">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="eceb5-127">(128, 0, 0)</span></span>|  
|<span data-ttu-id="eceb5-128">200</span><span class="sxs-lookup"><span data-stu-id="eceb5-128">200</span></span>|<span data-ttu-id="eceb5-129">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="eceb5-129">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="eceb5-130">Yatay koordinat 200 0'dan şekilde yüzde 20'yalnızca olduğunda kırmızı bileşenini yarım yoğunlukta olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-130">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="eceb5-131">Aşağıdaki örnek kümeleri <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> özelliği bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> üç göreli yoğunluklarda üç göreli konumları ile ilişkilendirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="eceb5-131">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> property of a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="eceb5-132">Önceki tabloda olduğu gibi göreli bir 0,5 yoğunluğunu göreli konumunu 0.2 ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-132">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="eceb5-133">Kod elips ve dikdörtgen gradyan fırçası ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="eceb5-133">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="eceb5-134">Aşağıdaki çizimde sonuçta elde edilen elips ve dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-134">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="eceb5-135">![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="eceb5-135">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span></span>  
  
### <a name="to-customize-linear-gradients"></a><span data-ttu-id="eceb5-136">Doğrusal gradyanlar özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="eceb5-136">To customize linear gradients</span></span>  
  
-   <span data-ttu-id="eceb5-137">Donuk siyah ve donuk kırmızıyla sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-137">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="eceb5-138">Önceki örneklerde gradyan yatay; diğer bir deyişle, renk yatay bir çizgi boyunca taşırken kademeli olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-138">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="eceb5-139">Ayrıca, dikey gradyanlar ve Çapraz Gradyan tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eceb5-139">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="eceb5-140">Aşağıdaki örnek noktaları (0, 0) ve (200, 100) geçirir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="eceb5-140">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="eceb5-141">Mavi ilişkili olduğu (0, 0) ve yeşil ilişkili olduğu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="eceb5-141">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="eceb5-142">Bir çizgiyle (Kalem genişliği 10) ve elips doğrusal gradyan fırçası ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="eceb5-142">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="eceb5-143">Aşağıdaki çizimde satır ve üç nokta gösterir.</span><span class="sxs-lookup"><span data-stu-id="eceb5-143">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="eceb5-144">Not taşırken elips değişiklikleri rengi kademeli olarak satırında aracılığıyla geçirme satırına paralel (0, 0) ve (200, 100).</span><span class="sxs-lookup"><span data-stu-id="eceb5-144">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="eceb5-145">![Doğrusal gradyan](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="eceb5-145">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="eceb5-146">Çapraz doğrusal gradyanlar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eceb5-146">To create diagonal linear gradients</span></span>  
  
-   <span data-ttu-id="eceb5-147">Donuk mavi ve donuk yeşil sırasıyla üçüncü ve dördüncü bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="eceb5-147">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="eceb5-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eceb5-148">See Also</span></span>  
 [<span data-ttu-id="eceb5-149">Şekilleri doldurmak için gradyan fırçası kullanma</span><span class="sxs-lookup"><span data-stu-id="eceb5-149">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [<span data-ttu-id="eceb5-150">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="eceb5-150">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
