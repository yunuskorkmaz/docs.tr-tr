---
title: 'Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100942"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="54e7c-102">Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme</span><span class="sxs-lookup"><span data-stu-id="54e7c-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="54e7c-103">Bir şekil doldururken geçmesi gereken bir <xref:System.Drawing.Brush> dolgu yöntemlerinden birini nesnesine <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54e7c-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="54e7c-104">Bir parametre <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> nesne.</span><span class="sxs-lookup"><span data-stu-id="54e7c-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="54e7c-105">Donuk bir şekli doldurmak için renk alfa bileşeni 255'e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54e7c-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="54e7c-106">Yarı saydam bir şekil doldurmak için 1 ila 254 herhangi bir değere alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54e7c-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="54e7c-107">Yarı saydam bir şekil doldururken şeklin rengi ile arka plan renklerini harmanlanan.</span><span class="sxs-lookup"><span data-stu-id="54e7c-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="54e7c-108">Alfa bileşeni şekli ve arka plan renkleri nasıl karıştırılır belirtir. alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleriyle yerleştirin ve alfa değerleri 255 yakın şekil rengine üzerinde daha fazla ağırlık yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="54e7c-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e7c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="54e7c-109">Example</span></span>  
 <span data-ttu-id="54e7c-110">Aşağıdaki örnek, bir bit eşlem çizer ve sonra bit eşlem çakışma üç elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="54e7c-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="54e7c-111">Donuk bir alfa bileşeni, 255, ilk üç nokta kullanır.</span><span class="sxs-lookup"><span data-stu-id="54e7c-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="54e7c-112">Yarı saydam şekilde bir alfa bileşeni 128, ikinci ve üçüncü üç nokta simgesini kullanın. üç nokta üzerinden arka plan resmi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e7c-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="54e7c-113">Ayarlar arama <xref:System.Drawing.Graphics.CompositingQuality%2A> özelliği neden olur üçüncü bir elipsin gama düzeltmesi ile birlikte yapılması karıştırma.</span><span class="sxs-lookup"><span data-stu-id="54e7c-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="54e7c-114">Aşağıdaki kodu çıktı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="54e7c-114">The following illustration shows the output of the following code:</span></span> 
  
 ![Çizim donuk ve yarı saydam fırçalarla çıktısını gösterir.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54e7c-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="54e7c-116">Compiling the Code</span></span>  
 <span data-ttu-id="54e7c-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs>`e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="54e7c-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e7c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e7c-118">See also</span></span>

- [<span data-ttu-id="54e7c-119">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="54e7c-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="54e7c-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="54e7c-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="54e7c-121">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="54e7c-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="54e7c-122">Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme</span><span class="sxs-lookup"><span data-stu-id="54e7c-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
