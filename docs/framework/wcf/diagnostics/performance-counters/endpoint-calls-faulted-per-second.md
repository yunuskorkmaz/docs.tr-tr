---
title: 'Uç Noktası: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 927f5370237b2502899d61f0b8d4bd79c8e00ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-faulted-per-second"></a>Uç Noktası: Saniyede Hatalı Çağrı
Sayaç adı: Saniyede hatalı çağrı.  
  
## <a name="description"></a>Açıklama  
 Hataları Bu uç noktaya bir saniyede döndürmüş çağrı sayısı.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)  
  
 Windows Communication Foundation (WCF) uygulamalarında hizmet yöntemleri işleme hata bilgileri SOAP hata iletileri kullanarak iletişim kurar. SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemcilerin kendi yürütme daha sağlam veya etkileşimli yapmak için kullanabileceği bir hataya sözleşmesi oluşturma ileti türlerini hatalarıdır. XML formundaki istemcilere SOAP hataları ifade olduğundan, yüksek oranda birlikte çalışabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
