---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic özel durumları günlüğe kaydetme'
title: 'Nasıl yapılır: Özel Durumları Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: a4155de4e73c632edf071256976161cfdbffba77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775220"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="6a3bb-103">Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="6a3bb-103">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="6a3bb-104">`My.Application.Log` `My.Log` Uygulamanızda oluşan özel durumlarla ilgili bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-104">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="6a3bb-105">Bu örnekler, `My.Application.Log.WriteException` açıkça yakalayacak özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-105">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="6a3bb-106">İzleme bilgilerini günlüğe kaydetmek için yöntemini kullanın `My.Application.Log.WriteEntry` .</span><span class="sxs-lookup"><span data-stu-id="6a3bb-106">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="6a3bb-107">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-107">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="6a3bb-108">İşlenmiş bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="6a3bb-108">To log a handled exception</span></span>  
  
1. <span data-ttu-id="6a3bb-109">Özel durum bilgilerini oluşturacak yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-109">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="6a3bb-110">`Try...Catch`Özel durumu yakalamak için bir blok kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="6a3bb-111">Bloğa özel durum üretebilen kodu koyun `Try` .</span><span class="sxs-lookup"><span data-stu-id="6a3bb-111">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="6a3bb-112">`Dim` `MsgBox` Özel duruma neden olacak şekilde ve satırlarının açıklamasını kaldırın <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="6a3bb-112">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="6a3bb-113">`Catch`Bloğunda, `My.Application.Log.WriteException` özel durum bilgilerini yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-113">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="6a3bb-114">Aşağıdaki örnek, işlenmiş bir özel durumu günlüğe kaydetmek için tüm kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-114">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="6a3bb-115">İşlenmeyen bir özel durumu günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="6a3bb-115">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="6a3bb-116">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6a3bb-117">**Proje** menüsünde **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-117">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="6a3bb-118">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="6a3bb-119">Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-119">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="6a3bb-120">Bu, ApplicationEvents. vb dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-120">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="6a3bb-121">ApplicationEvents. vb dosyasını kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-121">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="6a3bb-122">**Genel** menüsünde **MyApplication olayları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-122">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="6a3bb-123">**Bildirimler** menüsünde **UnhandledException** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-123">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="6a3bb-124">Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalışmadan önce olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-124">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="6a3bb-125">`My.Application.Log.WriteException`Yöntemini `UnhandledException` olay işleyicisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-125">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="6a3bb-126">Aşağıdaki örnekte işlenmeyen bir özel durum günlüğe kaydetme için kodun tamamı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-126">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6a3bb-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a3bb-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="6a3bb-128">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="6a3bb-128">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="6a3bb-129">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="6a3bb-129">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="6a3bb-130">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="6a3bb-130">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="6a3bb-131">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6a3bb-131">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
