---
title: 'Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352093"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="0c771-102">Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c771-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="0c771-103">Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c771-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="0c771-104">Bu örnek, izleme `My.Application.Log.WriteEntry` bilgileri yazmak `Startup` `Shutdown` için yöntemin ve olayların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c771-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="0c771-105">Uygulamanın olay işleyici koduna erişmek için</span><span class="sxs-lookup"><span data-stu-id="0c771-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="0c771-106">**Çözüm Gezgini'nde**bir proje seçili var.</span><span class="sxs-lookup"><span data-stu-id="0c771-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0c771-107">**Proje** menüsünde **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="0c771-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="0c771-108">**Uygulama** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0c771-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="0c771-109">Kod Düzenleyicisi'ni açmak için **Uygulama Etkinliklerini Görüntüle** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0c771-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="0c771-110">Bu, ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="0c771-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="0c771-111">Uygulama başladığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0c771-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="0c771-112">Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0c771-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="0c771-113">**Genel** menüde **MyApplication Events'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="0c771-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="0c771-114">**Bildirimler** menüsünde **Başlangıç'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0c771-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="0c771-115">Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> uygulama çalışmadan önce olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="0c771-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="0c771-116">Yöntem `My.Application.Log.WriteEntry` olay işleyicisine `Startup` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c771-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="0c771-117">Uygulama kapandığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0c771-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="0c771-118">Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0c771-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="0c771-119">**Genel** menüde **MyApplication Events'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="0c771-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="0c771-120">**Bildirimler** menüsünde **Kapatma'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="0c771-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="0c771-121">Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> uygulama çalıştırdıktan sonra, ancak kapanmadan önce olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="0c771-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="0c771-122">Yöntem `My.Application.Log.WriteEntry` olay işleyicisine `Shutdown` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c771-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="0c771-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c771-123">Example</span></span>  

 <span data-ttu-id="0c771-124">Kod Düzenleyicisi'ndeki uygulama olaylarına erişmek için **Proje Tasarımcısı'nı** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c771-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="0c771-125">Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="0c771-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0c771-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c771-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="0c771-127">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c771-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="0c771-128">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="0c771-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
