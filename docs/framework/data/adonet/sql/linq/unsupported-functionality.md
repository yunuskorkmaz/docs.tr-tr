---
title: Desteklenmeyen işlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5022c9011c2aac5b3272e359f991c40236a5673f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686711"
---
# <a name="unsupported-functionality"></a>Desteklenmeyen işlev
LINQ to SQL'de aşağıdaki SQL işlevleri var olan ortak dil çalışma zamanının (CLR) çeviri sunulamaz ve .NET Framework oluşturur:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Ancak `LIKE` desteklenmeyen benzer işlevselliği doğrudan çeviri var. <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı. Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ to SQL desteği sınırlı `DATEDIFF`. Benzer bir işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.  
  
-   `ROUND`  
  
     LINQ to SQL desteği sınırlı `ROUND`. Daha fazla bilgi için [System.Math yöntemleri](system-math-methods.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
