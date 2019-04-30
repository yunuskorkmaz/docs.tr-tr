---
title: 'Hizmet: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 523e5182ca661e170e5cba01d5221b5c38251959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773420"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Hizmet: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye  
  
## <a name="description"></a>Açıklama  
 Geçerli bir kullanıcıdan ve düzgün şekilde korumalı, bir saniye, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.  
  
 Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
