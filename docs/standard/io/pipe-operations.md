---
title: .NET 'teki kanal Işlemleri
description: ".NET 'teki kanal işlemleri hakkında bilgi edinin. Kanallar, işlemler arası iletişim için bir yol sağlar. İki tür kanal vardır: anonim kanallar ve adlandırılmış kanallar."
ms.date: 03/30/2017
helpviewer_keywords:
- pipes [.NET]
- pipe operations [.NET]
- interprocess communication [.NET], pipes
- I/O [.NET], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: bb8804c32b9f2b54b05298779bddae117c10dcf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734809"
---
# <a name="pipe-operations-in-net"></a>.NET 'teki kanal Işlemleri

Kanallar, işlemler arası iletişim için bir yol sağlar. İki tür kanal vardır:  
  
- Anonim kanallar.  
  
     Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Anonim kanallar, adlandırılmış kanallara göre daha az ek yük gerektirir, ancak sınırlı hizmetler sunar. Anonim kanallar tek yönlü ve ağ üzerinden kullanılamaz. Yalnızca tek bir sunucu örneğini destekler. Anonim kanallar, iş parçacıkları arasındaki iletişim için veya kanal tutamaçlarının oluşturulduğu sırada alt işleme kolayca geçirilebileceği üst ve alt işlemler arasında yararlıdır.  
  
     .NET ' te, ve sınıflarını kullanarak anonim kanallar uygulayacağız <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> .  
  
     Bkz. [nasıl yapılır: yerel Işlemler arası iletişim Için anonim kanallar kullanma](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Adlandırılmış kanallar.  
  
     Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Adlandırılmış kanallar tek yönlü veya çift yönlü olabilir. İleti tabanlı iletişimi destekler ve aynı kanal adını kullanarak birden fazla istemcinin sunucu işlemine aynı anda bağlanmasına izin verir. Adlandırılmış Kanallar, kimliğe bürünme özelliğini de destekler ve bu sayede, uzak sunucularda kendi izinlerini kullanmak üzere bağlantı kurma işlemi sağlanır.  
  
     .NET ' te, ve sınıflarını kullanarak adlandırılmış kanallar uygularmış olursunuz <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> .  
  
     Bkz. [nasıl yapılır: ağ Işlem iletişimi Için adlandırılmış kanalları kullanma](how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve akış g/ç](index.md)
- [Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma](how-to-use-named-pipes-for-network-interprocess-communication.md)
