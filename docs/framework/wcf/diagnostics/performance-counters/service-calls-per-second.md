---
title: "Hizmet: Saniye Başına Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 940249c4ec0317013efcb03aafc11d384ec0363f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-per-second"></a>Hizmet: Saniye Başına Çağrı
Sayaç adı: Saniye başına çağrı.  
  
## <a name="description"></a>Açıklama  
 Bu ikinci hizmetinde yapılan çağrı sayısı.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 -D 0) / F) burada (N) pay son örnekleme aralığı sırasında geçen çizgilerine sayısı payda (D) temsil son örnekleme aralığı sırasında gerçekleştirilen işlemler sayısını temsil eder ve F çizgilerine sıklığı.
