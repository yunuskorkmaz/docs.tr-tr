---
title: 'Nasıl yapılır: Kümesi kalem genişliği ve hizalamasını'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: e82f406b4fdca93df7a811eea5506846d56fda28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703055"
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="d0666-102">Nasıl yapılır: Kümesi kalem genişliği ve hizalamasını</span><span class="sxs-lookup"><span data-stu-id="d0666-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="d0666-103">Oluştururken bir <xref:System.Drawing.Pen>, kalem genişliği oluşturucusuna bağımsız değişkenlerden biri olarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0666-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="d0666-104">Kalem genişliği ile de değiştirebileceğiniz <xref:System.Drawing.Pen.Width%2A> özelliği <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d0666-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="d0666-105">Teorik bir çizgi genişliği 0 ' var.</span><span class="sxs-lookup"><span data-stu-id="d0666-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="d0666-106">1 piksel genişliğinde bir çizgi çizdiğinizde, piksel teorik satırında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="d0666-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="d0666-107">Birden fazla piksel genişliğinde bir çizgi çizin, piksel teorik satırında ya da ortalanır veya teorik satırın bir tarafında görünür.</span><span class="sxs-lookup"><span data-stu-id="d0666-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="d0666-108">Kalem hizalamayı özelliğini ayarlayabilirsiniz bir <xref:System.Drawing.Pen> teorik satırlara, kalem ile çizilen piksel nasıl yerleştirileceğini belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="d0666-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="d0666-109">Değerleri <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, ve <xref:System.Drawing.Drawing2D.PenAlignment.Inset> aşağıda görünen kod örnekleri üyeleridir <xref:System.Drawing.Drawing2D.PenAlignment> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d0666-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="d0666-110">Aşağıdaki kod örneği iki kez bir çizgi çizer: siyah kalem genişliği 1 ile bir kez ve yeşil bir kalem genişliği 10 ile bir kez.</span><span class="sxs-lookup"><span data-stu-id="d0666-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="d0666-111">Kalem genişliği değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d0666-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="d0666-112">Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğini <xref:System.Drawing.Drawing2D.PenAlignment.Center> (yeşil kalem ile çizilen piksel teorik satırında ortalanacağını belirtmek için varsayılan).</span><span class="sxs-lookup"><span data-stu-id="d0666-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="d0666-113">Sonuçta elde edilen satırı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0666-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="d0666-114">![Kalemler](./media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="d0666-114">![Pens](./media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="d0666-115">Aşağıdaki kod örneği iki kez bir dikdörtgen çizer: siyah kalem genişliği 1 ile bir kez ve yeşil bir kalem genişliği 10 ile bir kez.</span><span class="sxs-lookup"><span data-stu-id="d0666-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="d0666-116">Kalem hizalamayı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d0666-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="d0666-117">Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğini <xref:System.Drawing.Drawing2D.PenAlignment.Center> yeşil kalem ile çizilen piksel dikdörtgenin sınırında ortalanacağını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d0666-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="d0666-118">Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0666-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="d0666-119">![Kalemler](./media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="d0666-119">![Pens](./media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="d0666-120">Bir iç kalem oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d0666-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="d0666-121">Yukarıdaki kod örneğinde üçüncü deyim şu şekilde değiştirerek yeşil kalem hizalamayı değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d0666-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="d0666-122">Artık geniş yeşil çizginin piksellerde dikdörtgenin iç, aşağıdaki çizimde gösterildiği gibi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0666-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="d0666-123">![Kalemler](./media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="d0666-123">![Pens](./media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0666-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0666-124">See also</span></span>
- [<span data-ttu-id="d0666-125">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="d0666-125">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="d0666-126">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="d0666-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
