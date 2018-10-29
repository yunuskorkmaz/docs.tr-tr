---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 15890506aece94a07d4b97101519007accf3570a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196157"
---
# <a name="security-calls-not-authorized-per-second"></a>Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.  
  
## <a name="description"></a>Açıklama  
 Bu işlemde ikinci bir kimlik doğrulamada başarısız olan çağrı sayısı.  
  
 Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`. Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
