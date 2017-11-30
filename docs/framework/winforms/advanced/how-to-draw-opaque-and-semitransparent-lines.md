---
title: "Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme"
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
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea65fd836a6e6fc00472f6139a0700ea859545cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="ebb10-102">Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme</span><span class="sxs-lookup"><span data-stu-id="ebb10-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="ebb10-103">Çizgi çizme zaman geçmesi gereken bir <xref:System.Drawing.Pen> nesnesini <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ebb10-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ebb10-104">Parametrelerden biri <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu olan bir <xref:System.Drawing.Color> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ebb10-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="ebb10-105">Opak bir çizgi çizmek için 255 rengin alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ebb10-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="ebb10-106">Yarı saydam bir çizgi çizmek için 1 ile 254 arasında herhangi bir değere alfa bileşenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ebb10-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="ebb10-107">Arka plan üzerinde yarı saydam çizgi çizme, çizginin rengini arka plan renkleri ile karıştırılan.</span><span class="sxs-lookup"><span data-stu-id="ebb10-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="ebb10-108">Alfa bileşeni, satır ve arka plan renklerini nasıl karma belirtir; alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleri yerleştirin ve alfa değerleri 255 yakın çizgi rengi üzerinde daha fazla ağırlık yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ebb10-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb10-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebb10-109">Example</span></span>  
 <span data-ttu-id="ebb10-110">Aşağıdaki örnek, bir bit eşlem çizer ve bit eşlem arka planı olarak kullanmak üç satır çizer.</span><span class="sxs-lookup"><span data-stu-id="ebb10-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="ebb10-111">İlk satırı donuk 255 alfa bir bileşeninin kullanır.</span><span class="sxs-lookup"><span data-stu-id="ebb10-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="ebb10-112">Yarı saydam şekilde ikinci ve üçüncü satırlarını 128, alfasayısal bir bileşeninin kullanın; arka plandaki resmin arkasını satırları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebb10-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="ebb10-113">Ayarlar deyimi <xref:System.Drawing.Graphics.CompositingQuality%2A> özellik gama düzeltmesi ile birlikte yapılması üçüncü satır karıştırma eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ebb10-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="ebb10-114">Aşağıdaki çizimde, aşağıdaki kodu çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebb10-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="ebb10-115">![Donuk ve yarı saydam](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span><span class="sxs-lookup"><span data-stu-id="ebb10-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebb10-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ebb10-116">Compiling the Code</span></span>  
 <span data-ttu-id="ebb10-117">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ebb10-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb10-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebb10-118">See Also</span></span>  
 [<span data-ttu-id="ebb10-119">Çizgi ve dolgularda alfa karıştırma</span><span class="sxs-lookup"><span data-stu-id="ebb10-119">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="ebb10-120">Nasıl yapılır: denetiminize saydam arka plan verin</span><span class="sxs-lookup"><span data-stu-id="ebb10-120">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="ebb10-121">Nasıl yapılır: donuk ve yarı saydam fırçalarla çizme</span><span class="sxs-lookup"><span data-stu-id="ebb10-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
