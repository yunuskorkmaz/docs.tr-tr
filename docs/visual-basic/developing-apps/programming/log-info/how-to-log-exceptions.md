---
title: 'Nasıl Yapılır: Günlük Özel Durumları'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352081"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="130e2-102">Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="130e2-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="130e2-103">Uygulamanızda oluşan `My.Application.Log` `My.Log` özel durumlar hakkında bilgi günlüğe kaydetmek için nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="130e2-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="130e2-104">Bu örnekler, açıkça `My.Application.Log.WriteException` yakaladığınız özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="130e2-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="130e2-105">İzleme bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteEntry` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="130e2-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="130e2-106">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="130e2-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="130e2-107">İşlenen özel bir durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="130e2-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="130e2-108">Özel durum bilgilerini oluşturacak yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="130e2-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="130e2-109">Özel `Try...Catch` durumu yakalamak için bir blok kullanın.</span><span class="sxs-lookup"><span data-stu-id="130e2-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="130e2-110">`Try` Blokta özel durum oluşturabilecek kodu koyun.</span><span class="sxs-lookup"><span data-stu-id="130e2-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="130e2-111">Özel <xref:System.NullReferenceException> durum `Dim` `MsgBox` neden olmak için açıklama ve satırları uncomment.</span><span class="sxs-lookup"><span data-stu-id="130e2-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="130e2-112">Blokta, `Catch` özel `My.Application.Log.WriteException` durum bilgilerini yazmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="130e2-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="130e2-113">Aşağıdaki örnek, işlenmiş bir özel durum günlüğe kaydetme için tam kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="130e2-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="130e2-114">İşlenmemiş bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="130e2-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="130e2-115">**Çözüm Gezgini'nde**bir proje seçili var.</span><span class="sxs-lookup"><span data-stu-id="130e2-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="130e2-116">**Proje** menüsünde **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="130e2-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="130e2-117">**Uygulama** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="130e2-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="130e2-118">Kod Düzenleyicisi'ni açmak için **Uygulama Etkinliklerini Görüntüle** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="130e2-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="130e2-119">Bu, ApplicationEvents.vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="130e2-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="130e2-120">Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun.</span><span class="sxs-lookup"><span data-stu-id="130e2-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="130e2-121">**Genel** menüde **MyApplication Events'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="130e2-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="130e2-122">**Bildirimler** **menüsünde, UnhandledException'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="130e2-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="130e2-123">Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> uygulama çalışmadan önce olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="130e2-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="130e2-124">Yöntem `My.Application.Log.WriteException` olay işleyicisine `UnhandledException` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="130e2-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="130e2-125">Aşağıdaki örnek, işlenmemiş bir özel durum günlüğe kaydetmeiçin tam kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="130e2-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="130e2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="130e2-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="130e2-127">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="130e2-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="130e2-128">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="130e2-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="130e2-129">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="130e2-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="130e2-130">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="130e2-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
