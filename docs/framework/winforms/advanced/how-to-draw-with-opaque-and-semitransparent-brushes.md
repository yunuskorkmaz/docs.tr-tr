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
ms.openlocfilehash: 91aa3e89e2ff6d20432dbc5e988f2877059b4cdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523614"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="d0aea-102">Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme</span><span class="sxs-lookup"><span data-stu-id="d0aea-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="d0aea-103">Bir şekli doldurduğunuzda geçmesi gereken bir <xref:System.Drawing.Brush> dolgu yöntemlerinden birini nesnesine <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d0aea-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d0aea-104">Bir parametresinin <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu olan bir <xref:System.Drawing.Color> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0aea-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="d0aea-105">Donuk bir şekli doldurmak için 255 rengin alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0aea-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="d0aea-106">Yarı saydam bir şekli doldurmak için 1 ile 254 arasında herhangi bir değere alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0aea-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="d0aea-107">Yarı saydam bir şekli doldurduğunuzda şeklinin rengi arka plan renkleri ile karıştırılan.</span><span class="sxs-lookup"><span data-stu-id="d0aea-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="d0aea-108">Alfa bileşeni şekli ve arka plan renklerini nasıl karma belirtir; alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleri yerleştirin ve alfa değerleri 255 yakın şekil rengine üzerinde daha fazla ağırlık yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d0aea-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0aea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0aea-109">Example</span></span>  
 <span data-ttu-id="d0aea-110">Aşağıdaki örnek, bir bit eşlem çizer ve bit eşlem üst üste üç elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="d0aea-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="d0aea-111">İlk elipsin donuk 255 alfa bir bileşeninin kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0aea-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="d0aea-112">Yarı saydam şekilde ikinci ve üçüncü elipsleri 128, alfasayısal bir bileşeninin kullanın; üç nokta üzerinden arka plan görüntüsü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0aea-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="d0aea-113">Ayarlar arama <xref:System.Drawing.Graphics.CompositingQuality%2A> özellik gama düzeltmesi ile birlikte yapılması üçüncü elipsin karıştırma eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d0aea-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="d0aea-114">Aşağıdaki çizimde, aşağıdaki kodu çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0aea-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="d0aea-115">![Donuk ve yarı saydam](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="d0aea-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0aea-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d0aea-116">Compiling the Code</span></span>  
 <span data-ttu-id="d0aea-117">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d0aea-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0aea-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0aea-118">See Also</span></span>  
 [<span data-ttu-id="d0aea-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="d0aea-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="d0aea-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="d0aea-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="d0aea-121">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="d0aea-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="d0aea-122">Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme</span><span class="sxs-lookup"><span data-stu-id="d0aea-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
