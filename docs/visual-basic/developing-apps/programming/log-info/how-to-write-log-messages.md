---
title: 'Nasıl yapılır: Günlük iletileri (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: c12d0cde7d8128400769cd2e93361bb10e08f59b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967028"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="729fb-102">Nasıl yapılır: Günlük iletileri (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="729fb-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="729fb-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="729fb-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="729fb-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` izleme bilgileri günlüğe kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="729fb-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="729fb-105">Özel durum bilgilerini günlük için kullanma `My.Application.Log.WriteException` yöntemi; bkz: [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="729fb-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="729fb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="729fb-106">Example</span></span>  
 <span data-ttu-id="729fb-107">Bu örnekte `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="729fb-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="729fb-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="729fb-108">.NET Framework Security</span></span>  
 <span data-ttu-id="729fb-109">Günlüğe yazma veri kullanıcı parolalar gibi hassas bilgiler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="729fb-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="729fb-110">Daha fazla bilgi için [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="729fb-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729fb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="729fb-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="729fb-112">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="729fb-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="729fb-113">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="729fb-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="729fb-114">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="729fb-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="729fb-115">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı yeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="729fb-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="729fb-116">İzlenecek yol: My.Application.Log çıktısını filtreleme</span><span class="sxs-lookup"><span data-stu-id="729fb-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
