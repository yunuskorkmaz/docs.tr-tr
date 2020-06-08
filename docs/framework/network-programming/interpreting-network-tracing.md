---
title: Ağ İzlemeyi Yorumlama
description: Uygulamanızın .NET Framework çeşitli System.Net sınıf üyelerine yaptığı çağrıları yakalamak için izlemeyi nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 7a17e4ba14d8c5fe136667c4eb5bc5b2fd7a8242
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502372"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="6150e-103">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="6150e-103">Interpreting Network Tracing</span></span>
<span data-ttu-id="6150e-104">Ağ izleme etkinleştirildiğinde, uygulamanızın çeşitli sınıf üyelerine yaptığı çağrıları yakalamak için izlemeyi kullanabilirsiniz <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="6150e-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="6150e-105">Bu çağrılardan alınan çıkış aşağıdaki örneklere benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="6150e-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="6150e-106">Yukarıdaki örnekte, [588] geçerli iş parçacığının benzersiz tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="6150e-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="6150e-107">(4357) ve (4387), uygulamanın başlatılmasından bu yana geçen milisaniye sayısını belirten tarih damgalardır.</span><span class="sxs-lookup"><span data-stu-id="6150e-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="6150e-108">Zaman damgasından sonraki veriler, uygulamanın **yuva. Send**yöntemine giriş ve çıkış yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6150e-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="6150e-109">**Send** metodunu yürüten nesne benzersiz tanımlayıcı olarak 33574638 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6150e-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="6150e-110">Çıkış izleme yöntemi, dönüş değerini (önceki örnekte 61) içerir.</span><span class="sxs-lookup"><span data-stu-id="6150e-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="6150e-111">Ağ izlemeleri, uygulamanız tarafından gönderilen veya alınan ve Köprü Metni Aktarım Protokolü (HTTP) gibi uygulama düzeyi protokoller kullanılarak gönderilen ağ trafiğini yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="6150e-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="6150e-112">Bu veriler metin ve isteğe bağlı olarak onaltılık veri olarak yakalanabilir.</span><span class="sxs-lookup"><span data-stu-id="6150e-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="6150e-113">**TraceMode** özniteliğinin değeri olarak **ıncludehex** belirttiğinizde onaltılık veriler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6150e-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="6150e-114">(Bu öznitelikle ilgili ayrıntılı bilgi için bkz. [nasıl yapılır: ağ Izlemeyi yapılandırma](how-to-configure-network-tracing.md).) Aşağıdaki örnek izleme **ıncludehex**kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6150e-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="6150e-115">Onaltılık verileri atlamak için, yalnızca bir **TraceMode** özniteliği değeri olarak **protocolbelirtin** .</span><span class="sxs-lookup"><span data-stu-id="6150e-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="6150e-116">Aşağıdaki örnek, **yalnızca protocolbelirtildiğinde** izlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6150e-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="6150e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6150e-117">See also</span></span>

- [<span data-ttu-id="6150e-118">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6150e-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="6150e-119">Nasıl yapılır: Ağ İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6150e-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="6150e-120">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="6150e-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
