---
title: 'Nasıl Yapılır: Günlük Özel Durumları'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352081"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="e98d4-102">Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="e98d4-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="e98d4-103">Uygulamanızda oluşan özel durumlarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e98d4-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="e98d4-104">Bu örnekler, açıkça yakalayadığınız özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için `My.Application.Log.WriteException` yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e98d4-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="e98d4-105">İzleme bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteEntry` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="e98d4-106">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="e98d4-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="e98d4-107">İşlenmiş bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="e98d4-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="e98d4-108">Özel durum bilgilerini oluşturacak yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e98d4-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="e98d4-109">Özel durumu yakalamak için `Try...Catch` bloğu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="e98d4-110">`Try` bloğunda özel durum üretebilen kodu koyun.</span><span class="sxs-lookup"><span data-stu-id="e98d4-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="e98d4-111">`Dim` ve `MsgBox` satırların açıklamasını <xref:System.NullReferenceException> özel durumuna neden olacak şekilde kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="e98d4-112">`Catch` bloğunda, özel durum bilgilerini yazmak için `My.Application.Log.WriteException` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="e98d4-113">Aşağıdaki örnek, işlenmiş bir özel durumu günlüğe kaydetmek için tüm kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e98d4-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="e98d4-114">İşlenmeyen bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="e98d4-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="e98d4-115">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e98d4-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e98d4-116">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e98d4-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="e98d4-117">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="e98d4-118">Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="e98d4-119">Bu, ApplicationEvents. vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="e98d4-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="e98d4-120">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="e98d4-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="e98d4-121">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e98d4-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="e98d4-122">**Bildirimler** menüsünde **UnhandledException**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e98d4-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="e98d4-123">Uygulama, ana uygulama çalışmadan önce <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="e98d4-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="e98d4-124">`My.Application.Log.WriteException` yöntemini `UnhandledException` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e98d4-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="e98d4-125">Aşağıdaki örnekte işlenmeyen bir özel durum günlüğe kaydetme için kodun tamamı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e98d4-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e98d4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e98d4-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="e98d4-127">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="e98d4-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="e98d4-128">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="e98d4-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="e98d4-129">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e98d4-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="e98d4-130">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e98d4-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
