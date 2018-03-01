---
title: "Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="52024-102">Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52024-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="52024-103">Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanız ile ilgili bilgileri günlüğe kaydetmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52024-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="52024-104">Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` izleme bilgileri günlüğe kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="52024-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="52024-105">Özel durum bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteException` yöntemi; bkz: [nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="52024-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52024-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="52024-106">Example</span></span>  
 <span data-ttu-id="52024-107">Bu örnekte `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="52024-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="52024-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="52024-108">.NET Framework Security</span></span>  
 <span data-ttu-id="52024-109">Kullanıcı parolaları gibi hassas bilgileri günlüğe yaz veri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="52024-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="52024-110">Daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="52024-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52024-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52024-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="52024-112">Uygulama günlükleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="52024-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="52024-113">Nasıl yapılır: günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="52024-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="52024-114">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="52024-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="52024-115">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="52024-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="52024-116">İzlenecek yol: My.Application.Log çıktısını filtreleme</span><span class="sxs-lookup"><span data-stu-id="52024-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
