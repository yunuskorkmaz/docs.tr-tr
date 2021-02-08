---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: uygulama başladığında veya kapandığında Iletileri günlüğe kaydetme (Visual Basic)'
title: 'Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 545a57c3666aa12e3763961d05067face9fe324a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775194"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="b766c-103">Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b766c-103">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="b766c-104">`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b766c-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="b766c-105">Bu örnek `My.Application.Log.WriteEntry` , `Startup` `Shutdown` izleme bilgilerini yazmak için yönteminin ve olaylarıyla birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b766c-105">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="b766c-106">Uygulamanın olay işleyicisi koduna erişmek için</span><span class="sxs-lookup"><span data-stu-id="b766c-106">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="b766c-107">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b766c-107">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b766c-108">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b766c-108">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b766c-109">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b766c-109">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="b766c-110">Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b766c-110">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="b766c-111">Bu, ApplicationEvents. vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="b766c-111">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="b766c-112">Uygulama başladığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="b766c-112">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="b766c-113">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="b766c-113">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="b766c-114">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b766c-114">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="b766c-115">**Bildirimler** menüsünde, **Başlangıç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b766c-115">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="b766c-116">Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalışmadan önce olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="b766c-116">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="b766c-117">`My.Application.Log.WriteEntry`Yöntemini `Startup` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b766c-117">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="b766c-118">Uygulama kapandığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="b766c-118">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="b766c-119">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="b766c-119">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="b766c-120">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b766c-120">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="b766c-121">**Bildirimler** menüsünde, **kapatır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b766c-121">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="b766c-122">Uygulama, uygulamayı kapatmadan <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> önce ana uygulama çalıştırıldıktan sonra başlatır.</span><span class="sxs-lookup"><span data-stu-id="b766c-122">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="b766c-123">`My.Application.Log.WriteEntry`Yöntemini `Shutdown` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b766c-123">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b766c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b766c-124">Example</span></span>  

 <span data-ttu-id="b766c-125">Kod düzenleyicisinde uygulama olaylarına erişmek için **Proje tasarımcısını** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b766c-125">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="b766c-126">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b766c-126">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b766c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b766c-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="b766c-128">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b766c-128">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="b766c-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="b766c-129">Working with Application Logs</span></span>](working-with-application-logs.md)
