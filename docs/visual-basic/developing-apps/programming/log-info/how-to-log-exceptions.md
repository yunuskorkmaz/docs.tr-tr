---
title: 'Nasıl yapılır: Özel Durumları Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 59ed7b836126a38f32b7c6f479570a566d236e6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410120"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="bc206-102">Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="bc206-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="bc206-103">`My.Application.Log` `My.Log` Uygulamanızda oluşan özel durumlarla ilgili bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc206-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="bc206-104">Bu örnekler, `My.Application.Log.WriteException` açıkça yakalayacak özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc206-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="bc206-105">İzleme bilgilerini günlüğe kaydetmek için yöntemini kullanın `My.Application.Log.WriteEntry` .</span><span class="sxs-lookup"><span data-stu-id="bc206-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="bc206-106">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc206-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="bc206-107">İşlenmiş bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="bc206-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="bc206-108">Özel durum bilgilerini oluşturacak yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bc206-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="bc206-109">`Try...Catch`Özel durumu yakalamak için bir blok kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc206-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="bc206-110">Bloğa özel durum üretebilen kodu koyun `Try` .</span><span class="sxs-lookup"><span data-stu-id="bc206-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="bc206-111">`Dim` `MsgBox` Özel duruma neden olacak şekilde ve satırlarının açıklamasını kaldırın <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="bc206-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="bc206-112">`Catch`Bloğunda, `My.Application.Log.WriteException` özel durum bilgilerini yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc206-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="bc206-113">Aşağıdaki örnek, işlenmiş bir özel durumu günlüğe kaydetmek için tüm kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc206-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="bc206-114">İşlenmeyen bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="bc206-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="bc206-115">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc206-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bc206-116">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="bc206-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="bc206-117">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bc206-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="bc206-118">Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bc206-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="bc206-119">Bu, ApplicationEvents. vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="bc206-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="bc206-120">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="bc206-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="bc206-121">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="bc206-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="bc206-122">**Bildirimler** menüsünde **UnhandledException**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="bc206-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="bc206-123">Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalışmadan önce olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="bc206-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="bc206-124">`My.Application.Log.WriteException`Yöntemini `UnhandledException` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bc206-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="bc206-125">Aşağıdaki örnekte işlenmeyen bir özel durum günlüğe kaydetme için kodun tamamı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc206-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="bc206-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc206-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="bc206-127">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="bc206-127">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="bc206-128">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="bc206-128">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="bc206-129">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="bc206-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="bc206-130">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="bc206-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
