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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc0764c689db15a256ad8384c10010c33b6a99f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a>Uç noktası: Saniyede Akışı Yapılan İşlem
Sayaç adı: Saniyede akışı yapılan işlemler.  
  
## <a name="description"></a>Açıklama  
 İşlem sayısı Bu uç noktada işlemleri için bir saniyede akışı yapılan işlem. Bu sayaç, bir işlem kimliği uç noktasına gönderilen bir ileti bulunur dilediğiniz zaman artırılır.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
