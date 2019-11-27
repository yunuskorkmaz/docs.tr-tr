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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352093"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="3a517-102">Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a517-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="3a517-103">Uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a517-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="3a517-104">Bu örnek, izleme bilgilerini yazmak için `Startup` ve `Shutdown` olaylarıyla `My.Application.Log.WriteEntry` yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a517-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="3a517-105">Uygulamanın olay işleyicisi koduna erişmek için</span><span class="sxs-lookup"><span data-stu-id="3a517-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="3a517-106">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a517-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3a517-107">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="3a517-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="3a517-108">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3a517-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="3a517-109">Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3a517-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="3a517-110">Bu, ApplicationEvents. vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="3a517-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="3a517-111">Uygulama başladığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="3a517-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="3a517-112">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="3a517-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="3a517-113">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3a517-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="3a517-114">**Bildirimler** menüsünde, **Başlangıç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3a517-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="3a517-115">Uygulama, ana uygulama çalışmadan önce <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="3a517-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="3a517-116">`My.Application.Log.WriteEntry` yöntemini `Startup` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a517-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="3a517-117">Uygulama kapandığında iletileri günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="3a517-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="3a517-118">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="3a517-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="3a517-119">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3a517-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="3a517-120">**Bildirimler** menüsünde, **kapatır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3a517-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="3a517-121">Uygulama, ana uygulama çalıştırıldıktan sonra, ancak kapatılmadan önce <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="3a517-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="3a517-122">`My.Application.Log.WriteEntry` yöntemini `Shutdown` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a517-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="3a517-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a517-123">Example</span></span>  

 <span data-ttu-id="3a517-124">Kod düzenleyicisinde uygulama olaylarına erişmek için **Proje tasarımcısını** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a517-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="3a517-125">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3a517-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3a517-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a517-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="3a517-127">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a517-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="3a517-128">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="3a517-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
