---
title: 'Nasıl yapılır: Günlük iletileri (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 4b4210983aa5bd57f1b0a89f2f06f089e98670f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594957"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="61ee7-102">Nasıl yapılır: Günlük iletileri (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="61ee7-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="61ee7-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızla ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="61ee7-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="61ee7-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` izleme bilgileri günlüğe kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61ee7-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="61ee7-105">Özel durum bilgilerini günlük için kullanma `My.Application.Log.WriteException` yöntemi; bkz: [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="61ee7-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61ee7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="61ee7-106">Example</span></span>  
 <span data-ttu-id="61ee7-107">Bu örnekte `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61ee7-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="61ee7-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="61ee7-108">.NET Framework Security</span></span>  
 <span data-ttu-id="61ee7-109">Günlüğe yazma veri kullanıcı parolalar gibi hassas bilgiler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="61ee7-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="61ee7-110">Daha fazla bilgi için [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="61ee7-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ee7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ee7-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="61ee7-112">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="61ee7-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="61ee7-113">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="61ee7-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="61ee7-114">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="61ee7-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="61ee7-115">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı yeri değiştirme</span><span class="sxs-lookup"><span data-stu-id="61ee7-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="61ee7-116">İzlenecek yol: My.Application.Log çıktısını filtreleme</span><span class="sxs-lookup"><span data-stu-id="61ee7-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
