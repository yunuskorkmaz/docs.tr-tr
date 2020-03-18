---
title: .NET'te Boru İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706562"
---
# <a name="pipe-operations-in-net"></a>.NET'te Boru İşlemleri
Borular süreçler arası iletişim için bir araç sağlar. İki tür boru vardır:  
  
- İsimsiz borular.  
  
     Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Anonim borular, adlandırılmış borulardan daha az ek yükü gerektirir, ancak sınırlı hizmetler sunar. Anonim borular tek yönlüve ağ üzerinden kullanılamaz. Yalnızca tek bir sunucu örneğini desteklerler. Anonim borular, iş parçacıkları arasındaki iletişim için veya boru tutamaçlarıoluşturulduğunda alt işleme kolayca geçirilebilen üst ve alt işlemler arasında yararlıdır.  
  
     .NET'te, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları kullanarak anonim borular uygularsınız.  
  
     [Bkz. Nasıl Yapılacağını Görün: Yerel İşlemler Arası İletişim için Anonim Borular Kullanın.](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
  
- Adı borular.  
  
     Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Adlandırılmış borular tek yönlü veya çift yönlü olabilir. İleti tabanlı iletişimi destekler ve aynı boş ad la sunucu işlemine aynı anda bağlanmak için birden çok istemciye izin verir. Adlandırılmış kanallar, bağlantı işlemlerinin uzak sunucularda kendi izinlerini kullanmasını sağlayan kimliğe bürünme işlemlerini de destekler.  
  
     .NET'te, adlandırılmış boruları <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> ve sınıfları kullanarak uygularsınız.  
  
     [Bkz. Nasıl Kullanılır: Ağ İşlemler Arası İletişim için Adlandırılmış Boruları Kullanın.](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
- [Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
