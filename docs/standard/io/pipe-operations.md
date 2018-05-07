---
title: .NET Framework'te Kanal İşlemleri
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
ms.openlocfilehash: 1e0d2747abbacf766ddeda6f41404d8701cbc273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)  
 [Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
