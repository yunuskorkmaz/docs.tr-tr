---
title: ".NET Framework'te Kanal İşlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a>.NET Framework'te Kanal İşlemleri
Kanallar, işlemler arası iletişim için bir yol sağlar. Kanallar iki tür vardır:  
  
-   Anonim kanallar.  
  
     Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Anonim kanallar adlandırılmış kanallar'den daha az ek yük gerektirir ancak sınırlı hizmetleri sunar. Anonim kanallar tek yönlüdür ve bir ağ üzerinden kullanılamaz. Bunlar yalnızca tek bir sunucu örneği destekler. Anonim Kanallar, iş parçacıkları arasında ya da oluşturulduğunda, burada kanal tanıtıcıları kolayca alt işlem geçirilebilir üst ve alt işlemleri arasındaki iletişim için faydalıdır.  
  
     .NET Framework, anonim kanallar kullanarak uygulama <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları.  
  
     Bkz: [nasıl yapılır: yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Adlandırılmış Kanallar.  
  
     Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Adlandırılmış Kanallar tek yönlü veya çift yönlü olabilir. Bunlar ileti tabanlı iletişim destekler ve birden çok istemcilerin aynı kanal adını kullanarak sunucu işlemi aynı anda bağlanmasına olanak sağlamak. Adlandırılmış kanallar da uzak sunucularda kendi izinlerini kullanmak bağlantı işlemleri sağlayan kimliğe bürünme özelliğini destekler.  
  
     .NET Framework, adlandırılmış kanallar kullanarak uygulama <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları.  
  
     Bkz: [nasıl yapılır: ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya ve akış t-O](../../../docs/standard/io/index.md)  
 [Nasıl yapılır: yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [Nasıl yapılır: ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
