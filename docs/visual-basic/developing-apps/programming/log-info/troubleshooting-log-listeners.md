---
title: "Sorun Giderme: Günlük Dinleyicileri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="2a50d-102">Sorun Giderme: Günlük Dinleyicileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a50d-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="2a50d-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2a50d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="2a50d-104">Hangi günlük dinleyicileri bu iletilerini belirlemek için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="2a50d-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="2a50d-105">`Log` Nesne günlük filtreleme, günlükleri bilgi tutarını sınırlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a50d-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="2a50d-106">Filtreler yanlış olmadığını günlükleri yanlış bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2a50d-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="2a50d-107">Filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="2a50d-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="2a50d-108">Ancak, bir günlük hatalı yapılandırıldıysa, geçerli yapılandırması hakkında daha fazla bilgi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2a50d-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="2a50d-109">İçin edinebilirsiniz bu bilgileri günlük aracılığıyla Gelişmiş `TraceSource` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a50d-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="2a50d-110">Kod günlük nesnesinde günlük dinleyicileri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="2a50d-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="2a50d-111">İçeri aktarma <xref:System.Diagnostics> kod dosyasının başında ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2a50d-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="2a50d-112">Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="2a50d-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="2a50d-113">Her günlüğün dinleyicileri için bilgileri içeren bir dize döndüren bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a50d-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="2a50d-114">Günlüğün izleme dinleyicileri koleksiyonu geçirmek `GetListeners` işlev ve dönüş değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a50d-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="2a50d-115">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a50d-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a50d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a50d-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="2a50d-117">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="2a50d-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="2a50d-118">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="2a50d-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
