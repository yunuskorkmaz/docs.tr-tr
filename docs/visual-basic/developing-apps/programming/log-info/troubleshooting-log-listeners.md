---
title: 'Sorun Giderme: Günlük dinleyicileri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 12282df50bc42d2a153a9aa8db01f2654acd91ce
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299533"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="ae130-102">Sorun Giderme: Günlük dinleyicileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae130-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="ae130-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ae130-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="ae130-104">Hangi günlük dinleyicileri bu iletileri almak belirlemek için bkz: [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="ae130-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="ae130-105">`Log` Nesne günlük filtreleme kaydeder bilgi tutarını sınırlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae130-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="ae130-106">Filtreler yanlış, günlükleri yanlış bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ae130-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="ae130-107">Filtreleme hakkında daha fazla bilgi için bkz. [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="ae130-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="ae130-108">Ancak, bir günlük hatalı yapılandırıldıysa, geçerli yapılandırma hakkında daha fazla bilgi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ae130-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="ae130-109">Ulaşmak için bu bilgileri günlüğe aracılığıyla Gelişmiş `TraceSource` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae130-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="ae130-110">Kod günlük nesneye için günlük dinleyicileri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="ae130-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="ae130-111">İçeri aktarma <xref:System.Diagnostics> kod dosyasının başında ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ae130-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="ae130-112">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="ae130-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="ae130-113">Her bir günlüğün dinleyicileri için bilgi içeren bir dize döndüren bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ae130-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="ae130-114">Günlüğün izleme dinleyicilerine koleksiyonunu geçirmek `GetListeners` işlev ve dönüş değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ae130-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="ae130-115">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae130-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae130-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae130-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="ae130-117">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="ae130-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="ae130-118">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="ae130-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
