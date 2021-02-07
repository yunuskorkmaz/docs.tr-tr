---
description: Hakkında daha fazla bilgi için bkz. saniyedeki hatalı çağrı
title: Saniyede Hatalı Çağrı
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: cbff7b24d2aa457bdbe3c600109f24c9672c7ab2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759685"
---
# <a name="calls-faulted-per-second"></a>Saniyede Hatalı Çağrı

Sayaç adı: Hatalı çağrı/saniye  
  
## <a name="description"></a>Description  

 Saniye içinde bu işleme hata döndüren çağrı sayısı.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar. SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur. SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../specifying-and-handling-faults-in-contracts-and-services.md)
