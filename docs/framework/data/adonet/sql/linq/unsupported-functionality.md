---
title: "Desteklenmeyen işlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="unsupported-functionality"></a>Desteklenmeyen işlevi
LINQ-SQL, aşağıdaki SQL işlevselliği varolan ortak dil çalışma zamanı (CLR) çeviri görüntülenemeyen ve .NET Framework oluşturur:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Ancak `LIKE` desteklenmiyor benzer işlevselliği bulunmaktadır doğrudan çeviri <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı. Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ-SQL desteği sınırlı `DATEDIFF`. Benzer işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.  
  
-   `ROUND`  
  
     LINQ-SQL desteği sınırlı `ROUND`. Daha fazla bilgi için bkz: [System.Math yöntemleri](system-math-methods.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri ve işlevleri](data-types-and-functions.md)
