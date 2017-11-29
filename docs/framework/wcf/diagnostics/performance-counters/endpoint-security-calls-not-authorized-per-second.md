---
title: "Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 50bb92a31af3775f17868c7057a160f64a82f0b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı
Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.  
  
## <a name="description"></a>Açıklama  
 Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı belirli görevleri gerçekleştirmek için yetkili değil.  
  
 Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
