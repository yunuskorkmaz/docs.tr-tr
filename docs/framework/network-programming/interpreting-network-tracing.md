---
title: Ağ izlemeyi yorumlama
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 94a64efcd7b4f354eaa22d1b646f36212f9c8fbb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152271"
---
# <a name="interpreting-network-tracing"></a>Ağ izlemeyi yorumlama
Ağ izleme etkin olduğunda izleme çağrıları, uygulamanızın çeşitli yapar yakalamak için kullanabileceğiniz <xref:System.Net> sınıf üyeleri. Bu çağrılarının çıktısı aşağıdaki örneklere benzer olabilir.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 [588] yukarıdaki örnekte geçerli iş parçacığının benzersiz tanımlayıcısıdır. (4357) ve (4387) olan zaman damgaları gösteren uygulama başlatıldığından beri geçen milisaniye sayısını. Zaman damgası aşağıdaki veri girme ve yönteminden çıkılıyor uygulama gösterir **Socket.Send**. Nesnesini yürütürken **Gönder** yöntemi kendi benzersiz tanımlayıcı olarak 33574638 sahiptir. Yöntemi çıkış izleme (önceki örnekte 61) dönüş değerini içerir.  
  
 Ağ izlerini gönderilen veya alınan Köprü Metni Aktarım Protokolü (HTTP) gibi uygulama düzeyi protokolleri kullanarak uygulamanız tarafından ağ trafiği yakalayabilirsiniz. Bu veriler metin olarak yakalanır ve isteğe bağlı olarak onaltılık veri. Onaltılık veriler, belirttiğiniz zaman kullanılabilir **includehex** değeri olarak **İzlemeModu** özniteliği. (Bu öznitelik hakkında ayrıntılı bilgi için bkz: [nasıl yapılır: Ağ izlemeyi yapılandırma](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Aşağıdaki örnek izleme kullanılarak oluşturulan **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Onaltılık veri atlamak için belirtin **protocolonly** değeri olarak **İzlemeModu** özniteliği. İzleme aşağıdaki örnekte, **protocolonly** belirtilir.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ İzlemeyi Etkinleştirme](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Nasıl Yapılır: Ağ izlemeyi yapılandırma](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [.NET Framework'te Ağ İzleme](../../../docs/framework/network-programming/network-tracing.md)
