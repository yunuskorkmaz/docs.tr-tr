---
title: 'Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
ms.openlocfilehash: 17da19e88dfa837cc1e45d0b6af2ebdbfd00182c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157137"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı
Sayaç adı: güvenlik çağrıları değil yetkili / saniye  
  
## <a name="description"></a>Açıklama  
 Geçerli bir kullanıcıdan ve düzgün şekilde korumalı, bir saniye, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.  
  
 Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
