---
title: Sayfalama (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 25d52734c30e087629be9923a43e720f94c96d04
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249570"
---
# <a name="paging-entity-sql"></a>Sayfalama (Entity SQL)
Fiziksel sayfalama, [order by](order-by-entity-sql.md) yan tümcesindeki [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt yan tümceleri kullanılarak gerçekleştirilebilir. Fiziksel disk belleği kullanımını kesin bir şekilde gerçekleştirmek için atla ve SıNıRLA ' yı kullanmanız gerekir. Sonuç olarak sonuçdaki satır sayısını belirleyici olmayan bir şekilde kısıtlamak istiyorsanız, [en üst](top-entity-sql.md)' i kullanmanız gerekir. TOP ve SKIP/LIMIT birbirini dışlıyor.  
  
## <a name="top-overview"></a>EN üst genel bakış  
 SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir. TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir. Daha fazla bilgi için bkz. [top](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Atla ve SıNıRLA genel bakış  
 Atla ve SıNıRLA ORDER BY yan tümcesinin bir parçasıdır. ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen bir sonraki satırdan başlayan satırları içerir. Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir. Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır. Örneğin, sınır 5, sonuç kümesini beş örnek veya satır olarak kısıtlar. ATLAMA ve SıNıRıN birlikte kullanılması gerekmez; yalnızca SKIP veya ORDER BY yan tümcesiyle SıNıRLA ' yı kullanabilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [SKIP](skip-entity-sql.md)  
  
- [LIMIT](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
