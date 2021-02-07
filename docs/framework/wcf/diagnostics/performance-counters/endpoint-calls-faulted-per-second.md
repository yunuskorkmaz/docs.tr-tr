---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: saniye başına hatalı çağrı'
title: 'Uç Noktası: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 160680f215dbb3eea5ad15c756c7dc68a0629a90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759620"
---
# <a name="endpoint-calls-faulted-per-second"></a>Uç Noktası: Saniyede Hatalı Çağrı

Sayaç adı: saniye başına hatalı çağrı.  
  
## <a name="description"></a>Description  

 Bu uç noktaya saniye içinde hata döndüren çağrı sayısı.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar. SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur. SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../specifying-and-handling-faults-in-contracts-and-services.md)
