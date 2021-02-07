---
description: 'Daha fazla bilgi edinin: desteklenmeyen Işlevler'
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5c44dd4aad2d2ee4ec5e00ce42f4de9400cea478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680895"
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
