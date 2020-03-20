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
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142413"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="00703-102">Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme</span><span class="sxs-lookup"><span data-stu-id="00703-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="00703-103">Bir şekli doldurduğınızda, bir <xref:System.Drawing.Brush> nesneyi <xref:System.Drawing.Graphics> sınıfın doldurma yöntemlerinden birine geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00703-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="00703-104"><xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucunun tek parametresi <xref:System.Drawing.Color> bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="00703-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="00703-105">Opak bir şekli doldurmak için rengin alfa bileşenini 255 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00703-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="00703-106">Yarı saydam bir şekli doldurmak için alfa bileşenini 1'den 254'e kadar herhangi bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00703-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="00703-107">Yarı saydam bir şekli doldurduğunda, şeklin rengi arka plan daki renklerle karıştırılır.</span><span class="sxs-lookup"><span data-stu-id="00703-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="00703-108">Alfa bileşeni şekil ve arka plan renklerinin nasıl karıştırıldığını belirtir; 0'a yakın alfa değerleri arka plan renklerine daha fazla ağırlık, 255'e yakın alfa değerleri ise şekil rengine daha fazla ağırlık yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="00703-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00703-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="00703-109">Example</span></span>  
 <span data-ttu-id="00703-110">Aşağıdaki örnek bir bit eşlemi çizer ve sonra bit eşlemiyle çakışan üç elipsi doldurur.</span><span class="sxs-lookup"><span data-stu-id="00703-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="00703-111">İlk elips 255 alfa bileşeni kullanır, bu yüzden opaktır.</span><span class="sxs-lookup"><span data-stu-id="00703-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="00703-112">İkinci ve üçüncü elipsler 128'lik bir alfa bileşeni kullanırlar, bu yüzden yarı saydamdırlar; elipslerden arka plan görüntüsünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00703-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="00703-113"><xref:System.Drawing.Graphics.CompositingQuality%2A> Özelliği ayarlayan çağrı, üçüncü elipsin karıştırmasının gama düzeltmesi ile birlikte yapılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="00703-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="00703-114">Aşağıdaki resimde aşağıdaki kodun çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00703-114">The following illustration shows the output of the following code:</span></span>
  
 ![Opak ve yarı saydam çıktı gösteren çizim.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00703-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="00703-116">Compiling the Code</span></span>  
 <span data-ttu-id="00703-117">Önceki örnek Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve gerektirir , <xref:System.Windows.Forms.PaintEventHandler>hangi bir parametre .</span><span class="sxs-lookup"><span data-stu-id="00703-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00703-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00703-118">See also</span></span>

- [<span data-ttu-id="00703-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="00703-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="00703-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="00703-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="00703-121">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="00703-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="00703-122">Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme</span><span class="sxs-lookup"><span data-stu-id="00703-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
