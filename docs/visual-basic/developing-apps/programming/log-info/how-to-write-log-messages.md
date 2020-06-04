---
title: 'Nasıl yapılır: Günlük İletileri Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410055"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="4e800-102">Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e800-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="4e800-103">`My.Application.Log` `My.Log` Uygulamanız hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e800-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="4e800-104">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e800-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="4e800-105">Özel durum bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteException` yöntemini kullanın; bkz. [nasıl yapılır: günlük özel durumları](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="4e800-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e800-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e800-106">Example</span></span>

<span data-ttu-id="4e800-107">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e800-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="4e800-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4e800-108">.NET Framework Security</span></span>

<span data-ttu-id="4e800-109">Günlüğe yazdığınız verilerin kullanıcı parolaları gibi hassas bilgileri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4e800-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="4e800-110">Daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="4e800-110">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e800-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e800-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="4e800-112">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="4e800-112">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="4e800-113">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="4e800-113">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="4e800-114">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="4e800-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="4e800-115">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="4e800-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="4e800-116">İzlenecek yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="4e800-116">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)
