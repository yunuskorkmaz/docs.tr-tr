---
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: d4fe3d91b80197d962989cd2d3bc9bb2df6e3ffe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164161"
---
# <a name="unsupported-functionality"></a>Desteklenmeyen İşlev

LINQ to SQL, aşağıdaki SQL işlevselliği mevcut ortak dil çalışma zamanının (CLR) ve .NET Framework yapılarının çevirisi aracılığıyla sunulamaz:  
  
- `STDDEV`  
  
- `LIKE`  
  
     `LIKE`Doğrudan çeviri aracılığıyla desteklenmese de, sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> . Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     LINQ to SQL için sınırlı destek vardır `DATEDIFF` . Sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> .  
  
- `ROUND`  
  
     LINQ to SQL için sınırlı destek vardır `ROUND` . Daha fazla bilgi için bkz. [System. Math yöntemleri](system-math-methods.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
