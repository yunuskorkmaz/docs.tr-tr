---
title: "Saniyede Akışı Yapılan İşlem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6769b3d875471ddb56b3888a49f72978f4ee786b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem
Sayaç adı: Saniye başına yapılan işlemler  
  
## <a name="description"></a>Açıklama  
 Bu ikinci bir işlem için işlem sayısı aktarılan. Bu sayaç, bir işlem kimliği işleme gönderilen bir ileti bulunur dilediğiniz zaman artırılır.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
