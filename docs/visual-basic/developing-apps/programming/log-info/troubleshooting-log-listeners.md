---
title: 'Sorun Giderme: Günlük Dinleyicileri'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346864"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="d0f93-102">Sorun Giderme: Günlük Dinleyicileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0f93-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="d0f93-103">Uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f93-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="d0f93-104">Bu iletileri hangi günlük dinleyicilerinin alacağını belirlemek için bkz. [Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="d0f93-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="d0f93-105">`Log` nesnesi, günlük filtrelemeyi günlüğe kaydettiği bilgi miktarını sınırlamak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f93-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="d0f93-106">Filtreler yanlış yapılandırılmış ise, günlüklerde yanlış bilgiler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f93-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="d0f93-107">Filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="d0f93-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="d0f93-108">Ancak, bir günlük yanlış yapılandırılmışsa, geçerli yapılandırması hakkında daha fazla bilgiye ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f93-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="d0f93-109">Bu bilgilere günlüğün gelişmiş `TraceSource` özelliği aracılığıyla ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f93-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="d0f93-110">Koddaki günlük nesnesinin günlük dinleyicilerini belirleme</span><span class="sxs-lookup"><span data-stu-id="d0f93-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="d0f93-111">Kod dosyasının başındaki <xref:System.Diagnostics> ad alanını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d0f93-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="d0f93-112">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="d0f93-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="d0f93-113">Günlük dinleyicilerinin her biri için bilgilerden oluşan bir dize döndüren bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d0f93-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="d0f93-114">Günlük izleme dinleyicilerinin koleksiyonunu `GetListeners` işlevine geçirin ve dönüş değerini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d0f93-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="d0f93-115">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0f93-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f93-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f93-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="d0f93-117">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="d0f93-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="d0f93-118">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="d0f93-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
