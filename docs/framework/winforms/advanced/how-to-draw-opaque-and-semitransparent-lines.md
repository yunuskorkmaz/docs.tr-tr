---
title: 'Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 210916bbaf437d8f71b07e8107eb0cdc0989ea42
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465626"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="58143-102">Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="58143-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="58143-103">Bir çizgi çizdiğinizde geçmesi gereken bir <xref:System.Drawing.Pen> nesnesini <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="58143-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="58143-104">Parametrelerinden biri <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> nesne.</span><span class="sxs-lookup"><span data-stu-id="58143-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="58143-105">Donuk bir çizgi çizmek için renk alfa bileşeni 255'e ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58143-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="58143-106">Yarı saydam fırçalarla çizgi çizmek için 1 ila 254 herhangi bir değere alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58143-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="58143-107">Arka plan üzerinde yarı saydam bir çizgi çizdiğinizde, çizginin rengi ile arka plan renklerini harmanlanan.</span><span class="sxs-lookup"><span data-stu-id="58143-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="58143-108">Satır, arka plan renkleri nasıl karıştırılmıştır alfa bileşeni belirtir. alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleriyle yerleştirin ve alfa değerleri 255 yakın çizgi rengini üzerinde daha fazla ağırlık yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="58143-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58143-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="58143-109">Example</span></span>  
 <span data-ttu-id="58143-110">Aşağıdaki örnek, bir bit eşlem çizer ve sonra da bit eşlem arka plan olarak kullanan üç satır çizer.</span><span class="sxs-lookup"><span data-stu-id="58143-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="58143-111">Donuk bir alfa bileşeni, 255, ilk satırı kullanır.</span><span class="sxs-lookup"><span data-stu-id="58143-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="58143-112">Yarı saydam şekilde bir alfa bileşeni 128, ikinci ve üçüncü satır kullanın. arka plandaki resmin arkasını satırları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58143-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="58143-113">Ayarlar deyimi <xref:System.Drawing.Graphics.CompositingQuality%2A> özelliği neden gama düzeltmesi ile birlikte yapılması için üçüncü satırı karıştırma.</span><span class="sxs-lookup"><span data-stu-id="58143-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
 <span data-ttu-id="58143-114">Aşağıdaki kodu çıktı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="58143-114">The following illustration shows the output of the following code:</span></span>  
  
 ![Donuk ve yarı saydam fırçalarla çıkış gösteren şekil](./media/how-to-draw-opaque-and-semitransparent-lines/opaque-semitransparent-lines.png)  

## <a name="compiling-the-code"></a><span data-ttu-id="58143-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="58143-116">Compiling the Code</span></span>  
 <span data-ttu-id="58143-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="58143-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58143-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58143-118">See also</span></span>
- [<span data-ttu-id="58143-119">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="58143-119">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="58143-120">Nasıl yapılır: Denetiminize saydam arka plan verme</span><span class="sxs-lookup"><span data-stu-id="58143-120">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="58143-121">Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme</span><span class="sxs-lookup"><span data-stu-id="58143-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)
