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
# <a name="interpreting-network-tracing"></a>Ağ İzlemeyi Yorumlama
Ağ izleme etkinleştirildiğinde, uygulamanızın çeşitli <xref:System.Net> sınıf üyelerine yaptığı aramaları yakalamak için izleme özelliğini kullanabilirsiniz. Bu aramalardan çıkan çıktı aşağıdaki örneklere benzer olabilir.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 Önceki örnekte,[588] geçerli iş parçacığının benzersiz tanımlayıcısIdır. (4357) ve (4387) uygulamanın başlamasından bu yana geçen milisaniye sayısını gösteren zaman damgalarıdır. Zaman damgasını izleyen **veriler, Socket.Send**yöntemine giren ve çıkan uygulamayı gösterir. **Gönder** yöntemini çalıştıran nesne, benzersiz tanımlayıcısı olarak 33574638'e sahiptir. Yöntem çıkış izi iade değerini içerir (önceki örnekte 61).  
  
 Ağ izlemeleri, Hypertext Transfer Protocol (HTTP) gibi uygulama düzeyi protokollerini kullanarak uygulamanızdan gönderilen veya uygulamanız tarafından alınan ağ trafiğini yakalayabilir. Bu veriler metin ve isteğe bağlı olarak hexadecimal veri olarak yakalanabilir. **Tracemode** özniteliğinin değeri olarak **includehex** belirttiğiniz zaman hexadecimal veriler kullanılabilir. (Bu öznitelik hakkında ayrıntılı bilgi için [bkz.](how-to-configure-network-tracing.md) Aşağıdaki örnek izleme **includehex**kullanılarak oluşturuldu.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Hexadecimal verileri atlamak **için, yalnızca** **izleme modu** özniteliği için değer olarak protokol belirtin. Aşağıdaki örnek, yalnızca **protokol** belirtildiğinde izlemeyi gösterir.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [Nasıl yapılır: Ağ İzlemeyi Yapılandırma](how-to-configure-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
