---
title: "Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fd742e7fa2b7870b8988e889a0df2b18a240bd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="34fec-102">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme</span><span class="sxs-lookup"><span data-stu-id="34fec-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="34fec-103">Kendi arabelleğe alınan grafikleri yönetiyorsanız, oluşturma ve grafik arabellekleri işlemek olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34fec-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="34fec-104">Örneklerini oluşturabilirsiniz <xref:System.Drawing.BufferedGraphics> yüzeyleri ekranınızda çizim çağırarak ilişkili sınıfı <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34fec-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="34fec-105">Bu yöntem oluşturur bir <xref:System.Drawing.BufferedGraphics> bir form veya denetim gibi belirli işleme yüzeyine ile ilişkili olan örneği.</span><span class="sxs-lookup"><span data-stu-id="34fec-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="34fec-106">Oluşturduktan sonra bir <xref:System.Drawing.BufferedGraphics> örneği çizim grafik temsil eden aracılığıyla arabelleğine <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34fec-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="34fec-107">Tüm grafik işlemleri gerçekleştirdikten sonra arabellek içeriğini ekrana çağırarak kopyalayabilirsiniz <xref:System.Drawing.BufferedGraphics.Render%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34fec-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34fec-108">Kendi işleme gerçekleştirirseniz artış yalnızca küçük olabilir ancak bellek tüketimi artacaktır.</span><span class="sxs-lookup"><span data-stu-id="34fec-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="34fec-109">El ile görüntülenecek grafik arabelleğe alındı.</span><span class="sxs-lookup"><span data-stu-id="34fec-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="34fec-110">Örneği için bir başvuru elde <xref:System.Drawing.BufferedGraphicsContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34fec-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="34fec-111">Daha fazla bilgi için bkz: [nasıl yapılır: el ile arabelleğe alınan grafikleri yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="34fec-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="34fec-112">Bir örneğini oluşturmak <xref:System.Drawing.BufferedGraphics> çağırarak sınıfı <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> aşağıdaki kod örneğinde gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34fec-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="34fec-113">Grafik ayarlayarak grafik arabelleğe çizin <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34fec-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="34fec-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="34fec-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="34fec-115">Tüm grafik arabelleğine çizim, işlemlerini tamamladıktan sonra arama <xref:System.Drawing.BufferedGraphics.Render%2A> arabellek ya da bu arabelleği ile ya da belirtilen bir çizim yüzeyini için aşağıdaki kod örneğinde gösterildiği gibi ilişkili çizim yüzeyini işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="34fec-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="34fec-116">Tamamlanan işleme grafik olduktan sonra arama `Dispose` yöntemi <xref:System.Drawing.BufferedGraphics> sistem kaynakları serbest örneği.</span><span class="sxs-lookup"><span data-stu-id="34fec-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="34fec-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34fec-117">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [<span data-ttu-id="34fec-118">Çift arabelleğe alınan grafikleri</span><span class="sxs-lookup"><span data-stu-id="34fec-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="34fec-119">Nasıl yapılır: arabelleğe alınan grafikleri elle yönetme</span><span class="sxs-lookup"><span data-stu-id="34fec-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
