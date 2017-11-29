---
title: "Hizmet: Saniyede Hatalı Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5cf587102814c5bbd2a9c22d88db90f48fbf4da1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-faulted-per-second"></a>Hizmet: Saniyede Hatalı Çağrı
Sayaç adı: Saniyede hatalı çağrı.  
  
## <a name="description"></a>Açıklama  
 Bir saniyede döndürmüş hataları bu hizmete çağrı sayısı.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)  
  
 İçinde [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] uygulamalar, hizmet yöntemleri iletişim SOAP hata iletileri kullanarak hata bilgilerini işleme. SOAP, bir hizmet işlemi için meta verileri içinde yer alan ve bu nedenle istemcilerin kendi yürütme daha sağlam veya etkileşimli yapmak için kullanabileceği bir hataya sözleşmesi oluşturma ileti türlerini hatalarıdır. XML formundaki istemcilere SOAP hataları ifade olduğundan, yüksek oranda birlikte çalışabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
