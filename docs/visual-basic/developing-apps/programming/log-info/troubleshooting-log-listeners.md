---
title: 'Sorun giderme: Günlük dinleyicileri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: f2dba14ed883b428e47b71533bcb51506167fd49
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979014"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="da01a-102">Sorun giderme: Günlük dinleyicileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da01a-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="da01a-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.</span><span class="sxs-lookup"><span data-stu-id="da01a-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="da01a-104">Hangi günlük dinleyicileri bu iletileri almak belirlemek için bkz: [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="da01a-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="da01a-105">`Log` Nesne günlük filtreleme kaydeder bilgi tutarını sınırlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da01a-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="da01a-106">Filtreler yanlış, günlükleri yanlış bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="da01a-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="da01a-107">Filtreleme hakkında daha fazla bilgi için bkz. [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="da01a-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="da01a-108">Ancak, bir günlük hatalı yapılandırıldıysa, geçerli yapılandırma hakkında daha fazla bilgi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="da01a-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="da01a-109">Ulaşmak için bu bilgileri günlüğe aracılığıyla Gelişmiş `TraceSource` özelliği.</span><span class="sxs-lookup"><span data-stu-id="da01a-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="da01a-110">Kod günlük nesneye için günlük dinleyicileri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="da01a-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="da01a-111">İçeri aktarma <xref:System.Diagnostics> kod dosyasının başında ad alanı.</span><span class="sxs-lookup"><span data-stu-id="da01a-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="da01a-112">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="da01a-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2.  <span data-ttu-id="da01a-113">Her bir günlüğün dinleyicileri için bilgi içeren bir dize döndüren bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="da01a-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3.  <span data-ttu-id="da01a-114">Günlüğün izleme dinleyicilerine koleksiyonunu geçirmek `GetListeners` işlev ve dönüş değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="da01a-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="da01a-115">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="da01a-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da01a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da01a-116">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="da01a-117">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="da01a-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="da01a-118">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="da01a-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
