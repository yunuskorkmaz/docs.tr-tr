---
title: Ağ İzlemeyi Yorumlama
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: fd617e152b1e86cc71dd8e3cc8a01f1d2f52c30a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047899"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="11ece-102">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="11ece-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="11ece-103">Ağ izleme etkinleştirildiğinde, uygulamanızın çeşitli <xref:System.Net> sınıf üyelerine yaptığı aramaları yakalamak için izleme özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ece-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="11ece-104">Bu aramalardan çıkan çıktı aşağıdaki örneklere benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="11ece-104">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="11ece-105">Önceki örnekte,[588] geçerli iş parçacığının benzersiz tanımlayıcısIdır.</span><span class="sxs-lookup"><span data-stu-id="11ece-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="11ece-106">(4357) ve (4387) uygulamanın başlamasından bu yana geçen milisaniye sayısını gösteren zaman damgalarıdır.</span><span class="sxs-lookup"><span data-stu-id="11ece-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="11ece-107">Zaman damgasını izleyen **veriler, Socket.Send**yöntemine giren ve çıkan uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ece-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="11ece-108">**Gönder** yöntemini çalıştıran nesne, benzersiz tanımlayıcısı olarak 33574638'e sahiptir.</span><span class="sxs-lookup"><span data-stu-id="11ece-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="11ece-109">Yöntem çıkış izi iade değerini içerir (önceki örnekte 61).</span><span class="sxs-lookup"><span data-stu-id="11ece-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="11ece-110">Ağ izlemeleri, Hypertext Transfer Protocol (HTTP) gibi uygulama düzeyi protokollerini kullanarak uygulamanızdan gönderilen veya uygulamanız tarafından alınan ağ trafiğini yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="11ece-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="11ece-111">Bu veriler metin ve isteğe bağlı olarak hexadecimal veri olarak yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="11ece-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="11ece-112">**Tracemode** özniteliğinin değeri olarak **includehex** belirttiğiniz zaman hexadecimal veriler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11ece-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="11ece-113">(Bu öznitelik hakkında ayrıntılı bilgi için [bkz.](how-to-configure-network-tracing.md) Aşağıdaki örnek izleme **includehex**kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="11ece-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="11ece-114">Hexadecimal verileri atlamak **için, yalnızca** **izleme modu** özniteliği için değer olarak protokol belirtin.</span><span class="sxs-lookup"><span data-stu-id="11ece-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="11ece-115">Aşağıdaki örnek, yalnızca **protokol** belirtildiğinde izlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ece-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="11ece-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ece-116">See also</span></span>

- [<span data-ttu-id="11ece-117">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="11ece-117">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="11ece-118">Nasıl yapılır: Ağ İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="11ece-118">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="11ece-119">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="11ece-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
