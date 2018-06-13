---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473561"
---
# <a name="security-calls-not-authorized-per-second"></a>Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.  
  
## <a name="description"></a>Açıklama  
 Bu işlemde ikinci bir kimlik doğrulamada başarısız çağrı sayısı.  
  
 Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`. Gelen ileti geçerli bir kullanıcıdan ve düzgün şekilde korumalı, ancak kullanıcının belirli görevleri gerçekleştirmek için yetkili değil gösterir.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
