---
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: fb030a5f212be71d99b66f101e5e8411fbe4de33
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618136"
---
# <a name="unsupported-functionality"></a>Desteklenmeyen İşlev
LINQ to SQL'de aşağıdaki SQL işlevleri var olan ortak dil çalışma zamanının (CLR) çeviri sunulamaz ve .NET Framework oluşturur:  
  
- `STDDEV`  
  
- `LIKE`  
  
     Ancak `LIKE` desteklenmeyen benzer işlevselliği doğrudan çeviri var. <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı. Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     LINQ to SQL desteği sınırlı `DATEDIFF`. Benzer bir işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.  
  
- `ROUND`  
  
     LINQ to SQL desteği sınırlı `ROUND`. Daha fazla bilgi için [System.Math yöntemleri](system-math-methods.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
