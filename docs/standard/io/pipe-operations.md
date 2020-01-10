---
title: .NET 'teki kanal Işlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706562"
---
# <a name="pipe-operations-in-net"></a>.NET 'teki kanal Işlemleri
Kanallar, işlemler arası iletişim için bir yol sağlar. İki tür kanal vardır:  
  
- Anonim kanallar.  
  
     Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Anonim kanallar, adlandırılmış kanallara göre daha az ek yük gerektirir, ancak sınırlı hizmetler sunar. Anonim kanallar tek yönlü ve ağ üzerinden kullanılamaz. Yalnızca tek bir sunucu örneğini destekler. Anonim kanallar, iş parçacıkları arasındaki iletişim için veya kanal tutamaçlarının oluşturulduğu sırada alt işleme kolayca geçirilebileceği üst ve alt işlemler arasında yararlıdır.  
  
     .NET ' te, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları kullanarak anonim kanallar uygulayacağız.  
  
     Bkz. [nasıl yapılır: yerel Işlemler arası iletişim Için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Adlandırılmış kanallar.  
  
     Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Adlandırılmış kanallar tek yönlü veya çift yönlü olabilir. İleti tabanlı iletişimi destekler ve aynı kanal adını kullanarak birden fazla istemcinin sunucu işlemine aynı anda bağlanmasına izin verir. Adlandırılmış Kanallar, kimliğe bürünme özelliğini de destekler ve bu sayede, uzak sunucularda kendi izinlerini kullanmak üzere bağlantı kurma işlemi sağlanır.  
  
     .NET ' te, adlandırılmış kanalları <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları kullanarak uygularmış olursunuz.  
  
     Bkz. [nasıl yapılır: ağ Işlem iletişimi Için adlandırılmış kanalları kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
- [Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
