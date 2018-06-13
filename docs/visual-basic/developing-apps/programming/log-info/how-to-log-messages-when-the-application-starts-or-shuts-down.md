---
title: 'Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588901"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="41b85-102">Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41b85-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="41b85-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="41b85-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="41b85-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemiyle `Startup` ve `Shutdown` olayları izleme bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="41b85-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="41b85-105">Uygulamanın olay işleyici kodu erişmek için</span><span class="sxs-lookup"><span data-stu-id="41b85-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="41b85-106">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="41b85-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="41b85-107">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="41b85-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="41b85-108">Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="41b85-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="41b85-109">Tıklatın **uygulama olaylarını görüntüle** düğmesi kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="41b85-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="41b85-110">Bu ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="41b85-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="41b85-111">Uygulama başladığında iletilerini günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="41b85-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="41b85-112">Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="41b85-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="41b85-113">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="41b85-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="41b85-114">Üzerinde **bildirimleri** menüsünde seçin **başlangıç**.</span><span class="sxs-lookup"><span data-stu-id="41b85-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="41b85-115">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalıştırılmadan önce olay.</span><span class="sxs-lookup"><span data-stu-id="41b85-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="41b85-116">Ekleme `My.Application.Log.WriteEntry` yönteme `Startup` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="41b85-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="41b85-117">Uygulama kapatıldığında iletilerini günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="41b85-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="41b85-118">Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="41b85-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="41b85-119">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="41b85-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="41b85-120">Üzerinde **bildirimleri** menüsünde seçin **kapatma**.</span><span class="sxs-lookup"><span data-stu-id="41b85-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="41b85-121">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay ana uygulama çalıştırıldıktan sonra ancak bunu kapatılmadan önce.</span><span class="sxs-lookup"><span data-stu-id="41b85-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="41b85-122">Ekleme `My.Application.Log.WriteEntry` yönteme `Shutdown` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="41b85-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="41b85-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="41b85-123">Example</span></span>  
 <span data-ttu-id="41b85-124">Kullanabileceğiniz **Proje Tasarımcısı** Kod Düzenleyicisi'nde uygulama olayları erişmek için.</span><span class="sxs-lookup"><span data-stu-id="41b85-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="41b85-125">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="41b85-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="41b85-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41b85-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="41b85-127">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41b85-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="41b85-128">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="41b85-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
