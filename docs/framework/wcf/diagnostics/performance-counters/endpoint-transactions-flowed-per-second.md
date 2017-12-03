---
title: "Uç noktası: Saniyede Akışı Yapılan İşlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58d1bec0110d669258e8f003cb1e882207133a5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a>Uç noktası: Saniyede Akışı Yapılan İşlem
Sayaç adı: Saniyede akışı yapılan işlemler.  
  
## <a name="description"></a>Açıklama  
 İşlem sayısı Bu uç noktada işlemleri için bir saniyede akışı yapılan işlem. Bu sayaç, bir işlem kimliği uç noktasına gönderilen bir ileti bulunur dilediğiniz zaman artırılır.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
