---
title: "Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama"
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
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e5858da25174c8bc1de18d534023b57b58253e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="1f309-102">Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1f309-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="1f309-103">Oluştururken bir <xref:System.Drawing.Pen>, oluşturucu bağımsız değişkenlerinden biri olarak kalem genişliği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f309-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="1f309-104">Kalem genişliği ile de değiştirebilirsiniz <xref:System.Drawing.Pen.Width%2A> özelliği <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f309-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="1f309-105">Teorik bir çizgi genişliği 0 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1f309-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="1f309-106">1 piksel genişliğinde bir çizgi çizerken piksel teorik satırında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="1f309-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="1f309-107">Birden fazla piksel genişliğinde olan çizgi çizme, piksel teorik satırında ya da ortalanır veya teorik satır bir tarafında görünür.</span><span class="sxs-lookup"><span data-stu-id="1f309-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="1f309-108">Kalem hizalama özelliği ayarlayabileceğiniz bir <xref:System.Drawing.Pen> ile bu kalem çizilmiş piksel teorik satırları göre nasıl yerleştirileceğini belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="1f309-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="1f309-109">Değerleri <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, ve <xref:System.Drawing.Drawing2D.PenAlignment.Inset> aşağıda görünen kod örnekleri üyeleri olan <xref:System.Drawing.Drawing2D.PenAlignment> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="1f309-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="1f309-110">Aşağıdaki kod örneğinde bir çizgi iki kez çizer: kez siyah kalem genişliği 1 ile bir kez yeşil kalem genişliği 10.</span><span class="sxs-lookup"><span data-stu-id="1f309-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="1f309-111">Kalem genişliği değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1f309-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="1f309-112">Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğine <xref:System.Drawing.Drawing2D.PenAlignment.Center> (yeşil kalem ile çizilmiş piksel teorik satırda ortalanmış belirtmek için varsayılan).</span><span class="sxs-lookup"><span data-stu-id="1f309-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="1f309-113">Aşağıdaki çizimde, sonuçta elde edilen satır gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f309-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="1f309-114">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="1f309-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="1f309-115">Aşağıdaki kod örneğinde bir dikdörtgen iki kez çizer: kez siyah kalem genişliği 1 ile bir kez yeşil kalem genişliği 10.</span><span class="sxs-lookup"><span data-stu-id="1f309-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="1f309-116">Kalem hizalamasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1f309-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="1f309-117">Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğine <xref:System.Drawing.Drawing2D.PenAlignment.Center> ile yeşil kalem çizilmiş piksel dikdörtgen sınırında ortalanmış olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1f309-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="1f309-118">Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f309-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="1f309-119">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="1f309-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="1f309-120">Bir iç metin kalem oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1f309-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="1f309-121">Yeşil kalem hizalama önceki kod örneğinde üçüncü deyimi aşağıdaki gibi değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="1f309-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="1f309-122">Artık piksel geniş yeşil bir çizgi olarak aşağıdaki çizimde gösterildiği gibi dikdörtgenin iç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1f309-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="1f309-123">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="1f309-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f309-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f309-124">See Also</span></span>  
 [<span data-ttu-id="1f309-125">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f309-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="1f309-126">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="1f309-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
