---
title: . NET'te kanal işlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f02f7a8a327e117b92ef826b8dcd7fc742c9b4c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647808"
---
# <a name="pipe-operations-in-net"></a>. NET'te kanal işlemleri
Kanallar, işlemler arası iletişim için bir yol sağlar. Kanallar iki tür vardır:  
  
- Anonim kanallar.  
  
     Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Anonim kanallar adlandırılmış kanallardan daha az ek yük gerektirir, ancak sınırlı hizmetleri sunar. Anonim Kanallar, tek yönlü ve bir ağ üzerinden kullanılamaz. Bunlar, yalnızca tek bir sunucu örneği destekler. Üst ve alt işlemlerin oluşturulduğunda burada kanal tanıtıcıları kolayca alt işleme geçirilebilir veya iş parçacığı arasında iletişim için anonim kanalları yararlıdır.  
  
     . NET'te, anonim kanalları kullanarak uygulamanız <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları.  
  
     Bkz: [nasıl yapılır: Yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Adlandırılmış Kanallar.  
  
     Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Adlandırılmış Kanallar, tek yönlü veya çift yönlü olabilir. Bunlar, ileti tabanlı iletişim destekler ve birden çok istemci aynı anda aynı kanal adını kullanarak sunucu işlemine bağlanmasına izin. Adlandırılmış Kanallar, bağlantı işlemlerinin uzak sunucularda kendi izinlerini kullanmasını sağlayan kimliğe bürünme da destekler.  
  
     . NET'te, adlandırılmış kanallar kullanarak uygulamanız <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları.  
  
     Bkz: [nasıl yapılır: Ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
- [Nasıl yapılır: Yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Nasıl yapılır: Ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
