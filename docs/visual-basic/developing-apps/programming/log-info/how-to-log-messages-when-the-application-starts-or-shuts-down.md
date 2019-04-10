---
title: 'Nasıl yapılır: Uygulama başladığında günlük iletileri ya da kapatıldığında çalıştırılmalıdır (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 8fc7b441c6e19d70ceefa3422cf9823007280b64
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330577"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="6a026-102">Nasıl yapılır: Uygulama başladığında günlük iletileri ya da kapatıldığında çalıştırılmalıdır (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a026-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="6a026-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6a026-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="6a026-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemiyle `Startup` ve `Shutdown` olayları izleme bilgileri yazın.</span><span class="sxs-lookup"><span data-stu-id="6a026-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="6a026-105">Uygulama olay işleyici kodunun erişmek için</span><span class="sxs-lookup"><span data-stu-id="6a026-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="6a026-106">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="6a026-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6a026-107">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6a026-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="6a026-108">Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6a026-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="6a026-109">Tıklayın **uygulama olaylarını görüntüle** düğmesine Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="6a026-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="6a026-110">Bu ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="6a026-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="6a026-111">Uygulama başladığında iletilerini günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="6a026-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="6a026-112">Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6a026-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="6a026-113">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="6a026-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="6a026-114">Üzerinde **bildirimleri** menüsünde seçin **başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="6a026-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="6a026-115">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalışmadan önce olay.</span><span class="sxs-lookup"><span data-stu-id="6a026-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="6a026-116">Ekleme `My.Application.Log.WriteEntry` yönteme `Startup` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6a026-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="6a026-117">Uygulama kapatıldığında iletilerini günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="6a026-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="6a026-118">Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6a026-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="6a026-119">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="6a026-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="6a026-120">Üzerinde **bildirimleri** menüsünde seçin **kapatma**.</span><span class="sxs-lookup"><span data-stu-id="6a026-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="6a026-121">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay ana uygulama çalıştırıldıktan sonra ancak önce nasıl kapanıyorsa öyle kapanır.</span><span class="sxs-lookup"><span data-stu-id="6a026-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="6a026-122">Ekleme `My.Application.Log.WriteEntry` yönteme `Shutdown` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6a026-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="6a026-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a026-123">Example</span></span>  
 <span data-ttu-id="6a026-124">Kullanabileceğiniz **Proje Tasarımcısı** Kod Düzenleyicisi'nde uygulama olaylarını erişmek için.</span><span class="sxs-lookup"><span data-stu-id="6a026-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="6a026-125">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6a026-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6a026-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a026-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="6a026-127">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a026-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="6a026-128">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="6a026-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
