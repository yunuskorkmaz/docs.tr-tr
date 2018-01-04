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
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Veri Türleri ve İşlevleri](data-types-and-functions.md)
