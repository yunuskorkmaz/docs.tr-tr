---
title: 'Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 8b0d50e70572d849f20f01914d2380a64e4495a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587765"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="09ed8-102">Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09ed8-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="09ed8-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanız ile ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="09ed8-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="09ed8-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` izleme bilgileri günlüğe kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="09ed8-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="09ed8-105">Özel durum bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteException` yöntemi; bkz: [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="09ed8-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09ed8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="09ed8-106">Example</span></span>  
 <span data-ttu-id="09ed8-107">Bu örnekte `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="09ed8-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="09ed8-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="09ed8-108">.NET Framework Security</span></span>  
 <span data-ttu-id="09ed8-109">Kullanıcı parolaları gibi hassas bilgileri günlüğe yaz veri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="09ed8-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="09ed8-110">Daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="09ed8-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ed8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09ed8-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="09ed8-112">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="09ed8-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="09ed8-113">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="09ed8-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="09ed8-114">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="09ed8-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="09ed8-115">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="09ed8-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="09ed8-116">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="09ed8-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
