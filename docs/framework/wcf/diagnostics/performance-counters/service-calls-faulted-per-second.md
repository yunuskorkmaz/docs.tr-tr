---
title: 'Hizmet: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 211240d5bef7fe31a36f636313b48a2b9e15b239
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556017"
---
# <a name="service-calls-faulted-per-second"></a>Hizmet: Saniyede Hatalı Çağrı
Sayaç adı: saniye başına hatalı çağrı.  
  
## <a name="description"></a>Description  
 Saniye içinde bu hizmete hata döndüren çağrı sayısı.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar. SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur. SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../specifying-and-handling-faults-in-contracts-and-services.md)
