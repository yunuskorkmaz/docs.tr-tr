---
title: 'Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 965e3225f8cf1af6d61b81434089ebacac8ad13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138677"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="5de12-102">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme</span><span class="sxs-lookup"><span data-stu-id="5de12-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="5de12-103">Daha gelişmiş çift arabelleğe alma senaryolar için kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kendi iki kez arabelleğe alma mantığını uygulamak için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="5de12-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="5de12-104">Ayırma ve tek bir grafik arabellekleri yönetmekten sorumlu bir sınıfı <xref:System.Drawing.BufferedGraphicsContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5de12-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="5de12-105">Her uygulamanın kendi varsayılan sahip <xref:System.Drawing.BufferedGraphicsContext> , yöneten tüm çift bu uygulama için arabelleğe varsayılan.</span><span class="sxs-lookup"><span data-stu-id="5de12-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="5de12-106">Çağırarak bu örneğe bir başvuru alabilirsiniz <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="5de12-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="5de12-107">BufferedGraphicsContext varsayılan bir başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="5de12-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="5de12-108">Ayarlama <xref:System.Drawing.BufferedGraphicsManager.Current%2A> özelliği, aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5de12-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5de12-109">Çağrı gerekmez `Dispose` metodunda <xref:System.Drawing.BufferedGraphicsContext> , alırsınız başvuru <xref:System.Drawing.BufferedGraphicsManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5de12-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="5de12-110"><xref:System.Drawing.BufferedGraphicsManager> Tüm bellek ayırma ve dağıtım için varsayılan işleme <xref:System.Drawing.BufferedGraphicsContext> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5de12-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="5de12-111">Animasyon gibi grafik açısından yoğun uygulamalar için bazen bir adanmış kullanarak performansı artırabilir <xref:System.Drawing.BufferedGraphicsContext> yerine <xref:System.Drawing.BufferedGraphicsContext> tarafından sağlanan <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="5de12-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="5de12-112">Bu, oluşturmak ve uygulama tarafından kullanılan bellek daha büyük olacaktır ancak uygulamanız ile ilişkili tüm diğer arabelleğe alınan grafikleri yönetme performans yükü olmaksızın grafik arabellekleri tek tek yönetmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5de12-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="5de12-113">Adanmış BufferedGraphicsContext oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5de12-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="5de12-114">Bildirme ve yeni bir örneğini oluşturma <xref:System.Drawing.BufferedGraphicsContext> , aşağıdaki kod örneğinde gösterildiği gibi sınıf.</span><span class="sxs-lookup"><span data-stu-id="5de12-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="5de12-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5de12-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="5de12-116">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="5de12-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="5de12-117">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme</span><span class="sxs-lookup"><span data-stu-id="5de12-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
