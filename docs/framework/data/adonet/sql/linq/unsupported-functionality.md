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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b54bac0c9ce0b473ef8d86b039ef638b79af784f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
