---
title: 'Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme'
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
ms.openlocfilehash: 922cf6f9fd506e6095d87c3e0ee9eff85f920eba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586975"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="985e5-102">Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme</span><span class="sxs-lookup"><span data-stu-id="985e5-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="985e5-103">Bir şekil doldururken geçmesi gereken bir <xref:System.Drawing.Brush> dolgu yöntemlerinden birini nesnesine <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="985e5-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="985e5-104">Bir parametre <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> nesne.</span><span class="sxs-lookup"><span data-stu-id="985e5-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="985e5-105">Donuk bir şekli doldurmak için renk alfa bileşeni 255'e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="985e5-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="985e5-106">Yarı saydam bir şekil doldurmak için 1 ila 254 herhangi bir değere alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="985e5-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="985e5-107">Yarı saydam bir şekil doldururken şeklin rengi ile arka plan renklerini harmanlanan.</span><span class="sxs-lookup"><span data-stu-id="985e5-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="985e5-108">Alfa bileşeni şekli ve arka plan renkleri nasıl karıştırılır belirtir. alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleriyle yerleştirin ve alfa değerleri 255 yakın şekil rengine üzerinde daha fazla ağırlık yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="985e5-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="985e5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="985e5-109">Example</span></span>  
 <span data-ttu-id="985e5-110">Aşağıdaki örnek, bir bit eşlem çizer ve sonra bit eşlem çakışma üç elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="985e5-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="985e5-111">Donuk bir alfa bileşeni, 255, ilk üç nokta kullanır.</span><span class="sxs-lookup"><span data-stu-id="985e5-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="985e5-112">Yarı saydam şekilde bir alfa bileşeni 128, ikinci ve üçüncü üç nokta simgesini kullanın. üç nokta üzerinden arka plan resmi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="985e5-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="985e5-113">Ayarlar arama <xref:System.Drawing.Graphics.CompositingQuality%2A> özelliği neden olur üçüncü bir elipsin gama düzeltmesi ile birlikte yapılması karıştırma.</span><span class="sxs-lookup"><span data-stu-id="985e5-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="985e5-114">Aşağıdaki kodun çıktısı aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="985e5-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="985e5-115">![Donuk ve yarı saydam fırçalarla](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="985e5-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="985e5-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="985e5-116">Compiling the Code</span></span>  
 <span data-ttu-id="985e5-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="985e5-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985e5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="985e5-118">See also</span></span>
- [<span data-ttu-id="985e5-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="985e5-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="985e5-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="985e5-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="985e5-121">Nasıl yapılır: Denetiminize saydam arka plan verme</span><span class="sxs-lookup"><span data-stu-id="985e5-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="985e5-122">Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="985e5-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
