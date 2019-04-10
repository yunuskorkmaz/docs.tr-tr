---
title: "Nasıl yapılır: Visual Basic'te günlük özel durumları"
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 53bf93a326123ddb1e26ef5964fa057148505116
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307229"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="a98bc-102">Nasıl yapılır: Visual Basic'te günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="a98bc-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="a98bc-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` oluşan özel durumları hakkında bilgi uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a98bc-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="a98bc-104">Bu örneklerin nasıl kullanabileceğinizi gösteren `My.Application.Log.WriteException` açıkça catch özel durumları ve işlenmeyen özel durumları günlüğe kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a98bc-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="a98bc-105">İzleme bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteEntry` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a98bc-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="a98bc-106">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a98bc-106">For more information, see</span></span> <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="a98bc-107">İşlenen özel durum oturum için</span><span class="sxs-lookup"><span data-stu-id="a98bc-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="a98bc-108">Özel durum bilgileri oluşturan bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a98bc-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="a98bc-109">Kullanım bir `Try...Catch` istisna yakalamak için blok.</span><span class="sxs-lookup"><span data-stu-id="a98bc-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="a98bc-110">Bir özel durum oluşturabilir kodu put `Try` blok.</span><span class="sxs-lookup"><span data-stu-id="a98bc-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="a98bc-111">Açıklamadan çıkarın `Dim` ve `MsgBox` neden satırları bir <xref:System.NullReferenceException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="a98bc-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="a98bc-112">İçinde `Catch` engelleme, kullanın `My.Application.Log.WriteException` özel durum bilgilerini yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a98bc-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="a98bc-113">Aşağıdaki örnek, işlenen özel durum günlüğe kaydetme için tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a98bc-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="a98bc-114">İşlenmeyen bir özel durum oturum için</span><span class="sxs-lookup"><span data-stu-id="a98bc-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="a98bc-115">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="a98bc-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a98bc-116">Üzerinde **proje** menüsünde seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a98bc-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="a98bc-117">Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a98bc-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="a98bc-118">Tıklayın **uygulama olaylarını görüntüle** düğmesine Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="a98bc-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="a98bc-119">Bu ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="a98bc-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="a98bc-120">Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a98bc-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="a98bc-121">Üzerinde **genel** menüsünde seçin **MyApplication olayları**.</span><span class="sxs-lookup"><span data-stu-id="a98bc-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="a98bc-122">Üzerinde **bildirimleri** menüsünde seçin **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="a98bc-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="a98bc-123">Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalışmadan önce olay.</span><span class="sxs-lookup"><span data-stu-id="a98bc-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="a98bc-124">Ekleme `My.Application.Log.WriteException` yönteme `UnhandledException` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a98bc-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="a98bc-125">Aşağıdaki örnek, işlenmeyen bir özel durum günlüğe kaydetme için tam kod gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a98bc-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a98bc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a98bc-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="a98bc-127">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="a98bc-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="a98bc-128">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="a98bc-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="a98bc-129">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="a98bc-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a98bc-130">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a98bc-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
