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
ms.openlocfilehash: f8675582fe6bafefd94d6a740c3263e407dfd4e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523961"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="1be3a-102">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme</span><span class="sxs-lookup"><span data-stu-id="1be3a-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="1be3a-103">Daha gelişmiş çift arabelleğe alma senaryoları için kullandığınız [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kendi çift arabelleğe alma mantığını uygulamak için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="1be3a-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="1be3a-104">Ayırma ve tek tek grafik arabellekleri yönetme sorumlu sınıfı <xref:System.Drawing.BufferedGraphicsContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1be3a-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="1be3a-105">Her uygulamanın kendi varsayılan var. <xref:System.Drawing.BufferedGraphicsContext> , yöneten tüm bu uygulama için arabelleğe alma çift varsayılan.</span><span class="sxs-lookup"><span data-stu-id="1be3a-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="1be3a-106">Çağırarak bu örneğine başvuru alabilir <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="1be3a-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="1be3a-107">BufferedGraphicsContext varsayılan bir başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="1be3a-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="1be3a-108">Ayarlama <xref:System.Drawing.BufferedGraphicsManager.Current%2A> aşağıdaki kod örneğinde gösterildiği gibi özelliği.</span><span class="sxs-lookup"><span data-stu-id="1be3a-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1be3a-109">Çağrı gerekmez `Dispose` yöntemi <xref:System.Drawing.BufferedGraphicsContext> , alırsınız başvuru <xref:System.Drawing.BufferedGraphicsManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1be3a-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="1be3a-110"><xref:System.Drawing.BufferedGraphicsManager> Tüm bellek ayırma ve dağıtım için varsayılan işleme <xref:System.Drawing.BufferedGraphicsContext> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1be3a-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="1be3a-111">Animasyon gibi grafik açısından yoğun uygulamalar için bazen bir adanmış kullanarak performansı artırabilir <xref:System.Drawing.BufferedGraphicsContext> yerine <xref:System.Drawing.BufferedGraphicsContext> tarafından sağlanan <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="1be3a-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="1be3a-112">Bu, oluşturma ve uygulama tarafından kullanılan bellek büyük olmaz ancak, uygulama ile ilişkili tüm diğer arabelleğe alınan grafikleri yönetme performans yükünü yansıtılmasını olmadan grafik arabellekleri ayrı ayrı yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1be3a-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="1be3a-113">Ayrılmış BufferedGraphicsContext oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1be3a-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="1be3a-114">Bildirme ve yeni bir örneğini oluşturmak <xref:System.Drawing.BufferedGraphicsContext> aşağıdaki kod örneğinde gösterildiği gibi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1be3a-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="1be3a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1be3a-115">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [<span data-ttu-id="1be3a-116">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="1be3a-116">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="1be3a-117">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme</span><span class="sxs-lookup"><span data-stu-id="1be3a-117">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
