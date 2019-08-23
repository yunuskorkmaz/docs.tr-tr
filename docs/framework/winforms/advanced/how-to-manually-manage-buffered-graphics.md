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
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968599"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="ad0e6-102">Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme</span><span class="sxs-lookup"><span data-stu-id="ad0e6-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="ad0e6-103">Daha gelişmiş çift arabelleğe alma senaryolarında, kendi çift arabelleğe alma mantığınızı uygulamak için .NET Framework sınıflarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-103">For more advanced double buffering scenarios, you can use the .NET Framework classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="ad0e6-104">Tek grafik arabelleklerinin <xref:System.Drawing.BufferedGraphicsContext> dağıtılmasından ve yönetiminden sorumlu sınıf, sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="ad0e6-105">Her uygulamanın, bu uygulama için <xref:System.Drawing.BufferedGraphicsContext> varsayılan iki arabelleğe alma işleminin tümünü yöneten kendi varsayılanı vardır.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="ad0e6-106">Çağırarak, <xref:System.Drawing.BufferedGraphicsManager.Current%2A>bu örneğe bir başvuru alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="ad0e6-107">Varsayılan BufferedGraphicsContext öğesine bir başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="ad0e6-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="ad0e6-108">Aşağıdaki kod örneğinde gösterildiği gibi özelliğiayarlayın.<xref:System.Drawing.BufferedGraphicsManager.Current%2A></span><span class="sxs-lookup"><span data-stu-id="ad0e6-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > <span data-ttu-id="ad0e6-109">Sınıfından aldığınız <xref:System.Drawing.BufferedGraphicsContext> `Dispose` başvuruüzerindeyönteminiçağırmanızgerekmez<xref:System.Drawing.BufferedGraphicsManager> .</span><span class="sxs-lookup"><span data-stu-id="ad0e6-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="ad0e6-110">, <xref:System.Drawing.BufferedGraphicsManager> Varsayılan<xref:System.Drawing.BufferedGraphicsContext> örnekler için tüm bellek ayırmayı ve dağıtımını işler.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="ad0e6-111">Animasyon gibi grafiksel olarak yoğun uygulamalarda, bazen tarafından <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsManager>sağlanması yerine adanmış bir kullanarak performansı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="ad0e6-112">Bu, uygulama tarafından tüketilen bellek daha büyük olsa da, uygulama ile ilişkili diğer tüm arabelleğe alınmış grafiklerin yönetilmesi için performans yükünü tek tek oluşturup yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="ad0e6-113">Adanmış bir BufferedGraphicsContext oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ad0e6-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="ad0e6-114">Aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Drawing.BufferedGraphicsContext> sınıfının yeni bir örneğini bildirin ve oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="ad0e6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0e6-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="ad0e6-116">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="ad0e6-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="ad0e6-117">Nasıl yapılır: Arabelleğe alınan grafikleri elle Işleme</span><span class="sxs-lookup"><span data-stu-id="ad0e6-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
