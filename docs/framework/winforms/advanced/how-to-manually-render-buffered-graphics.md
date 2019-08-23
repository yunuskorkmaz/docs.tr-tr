---
title: 'Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931844"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="4aa37-102">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme</span><span class="sxs-lookup"><span data-stu-id="4aa37-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="4aa37-103">Kendi arabellekli grafiklerinizi yönetiyorsanız, grafik arabellekleri oluşturup işleyebilmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="4aa37-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="4aa37-104">Yöntemini çağırarak, <xref:System.Drawing.BufferedGraphics> <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> ekranınızda çizim yüzeyleriyle ilişkili sınıf örnekleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa37-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="4aa37-105">Bu yöntem, bir <xref:System.Drawing.BufferedGraphics> form veya denetim gibi belirli bir işleme yüzeyi ile ilişkili bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aa37-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="4aa37-106">Bir <xref:System.Drawing.BufferedGraphics> örnek oluşturduktan sonra, <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği aracılığıyla temsil ettiği arabelleğe grafik çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa37-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="4aa37-107">Tüm grafik işlemlerini gerçekleştirdikten sonra, <xref:System.Drawing.BufferedGraphics.Render%2A> yöntemini çağırarak arabelleğin içeriğini ekrana kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aa37-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4aa37-108">Kendi işleme gerçekleştirirseniz, bellek tüketimi artar, ancak artış yalnızca hafif olabilir.</span><span class="sxs-lookup"><span data-stu-id="4aa37-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="4aa37-109">Arabelleğe alınmış grafikleri el ile görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4aa37-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="4aa37-110"><xref:System.Drawing.BufferedGraphicsContext> Sınıfının bir örneğine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="4aa37-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="4aa37-111">Daha fazla bilgi için [nasıl yapılır: Arabellekli grafikleri](how-to-manually-manage-buffered-graphics.md)el ile yönetin.</span><span class="sxs-lookup"><span data-stu-id="4aa37-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="4aa37-112">Aşağıdaki kod örneğinde gösterildiği gibi <xref:System.Drawing.BufferedGraphics> <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemini çağırarak sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4aa37-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="4aa37-113"><xref:System.Drawing.BufferedGraphics.Graphics%2A> Özelliği ayarlayarak grafik arabelleğine grafik çizin.</span><span class="sxs-lookup"><span data-stu-id="4aa37-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="4aa37-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4aa37-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="4aa37-115">Grafik arabelleğine çizim işlemlerinizi tamamladıktan sonra, aşağıdaki kod örneğinde gösterildiği gibi, arabelleği işlemek için <xref:System.Drawing.BufferedGraphics.Render%2A> bu arabellek ile ilişkili çizim yüzeyine veya belirtilen çizim yüzeyine yönelik yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="4aa37-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="4aa37-116">Grafik oluşturmayı tamamladıktan sonra, sistem kaynaklarını serbest bırakmak `Dispose` için <xref:System.Drawing.BufferedGraphics> örneğinde yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="4aa37-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="4aa37-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aa37-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="4aa37-118">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="4aa37-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="4aa37-119">Nasıl yapılır: Arabellekli grafikleri el ile yönetme</span><span class="sxs-lookup"><span data-stu-id="4aa37-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
