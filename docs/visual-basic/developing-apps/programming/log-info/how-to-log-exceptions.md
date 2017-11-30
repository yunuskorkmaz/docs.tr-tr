---
title: "Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 320bc5d06f4c8e673745b600fd369af287fe8105
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="457b6-102">Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="457b6-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="457b6-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` oluşan özel durumlar hakkında bilgi, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="457b6-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="457b6-104">Bu örnekler nasıl kullanılacağını `My.Application.Log.WriteException` açıkça catch özel durumları ve işlenmeyen özel durumları günlüğe kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="457b6-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="457b6-105">İzleme bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteEntry` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="457b6-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="457b6-106">Daha fazla bilgi için bkz:<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="457b6-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="457b6-107">İşlenmiş özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="457b6-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="457b6-108">Özel durum bilgilerini oluşturur yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="457b6-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  <span data-ttu-id="457b6-109">Kullanım bir `Try...Catch` Özel catch bloğu.</span><span class="sxs-lookup"><span data-stu-id="457b6-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  <span data-ttu-id="457b6-110">Bir özel durum üretebilir kod put `Try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="457b6-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="457b6-111">Açıklamadan çıkarın `Dim` ve `MsgBox` neden satırları bir <xref:System.NullReferenceException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="457b6-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  <span data-ttu-id="457b6-112">İçinde `Catch` engellemek, kullanın `My.Application.Log.WriteException` yöntemi özel durum bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="457b6-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     <span data-ttu-id="457b6-113">Aşağıdaki örnekte bir özel durumu günlüğe kaydetme için tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="457b6-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="457b6-114">İşlenmeyen bir özel durum günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="457b6-114">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="457b6-115">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="457b6-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="457b6-116">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="457b6-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="457b6-117">Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="457b6-117">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="457b6-118">Tıklatın **uygulama olaylarını görüntüle** düğmesi kod düzenleyicisini açın.</span><span class="sxs-lookup"><span data-stu-id="457b6-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="457b6-119">Bu ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="457b6-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="457b6-120">Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="457b6-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="457b6-121">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="457b6-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="457b6-122">Üzerinde **bildirimleri** menüsünde seçin **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="457b6-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="457b6-123">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalıştırılmadan önce olay.</span><span class="sxs-lookup"><span data-stu-id="457b6-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="457b6-124">Ekleme `My.Application.Log.WriteException` yönteme `UnhandledException` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="457b6-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     <span data-ttu-id="457b6-125">Aşağıdaki örnek, işlenmeyen bir özel durum günlüğe kaydetme için tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="457b6-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="457b6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="457b6-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="457b6-127">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="457b6-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="457b6-128">Nasıl yapılır: günlük iletileri yazma</span><span class="sxs-lookup"><span data-stu-id="457b6-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="457b6-129">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="457b6-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="457b6-130">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="457b6-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
