---
title: Disk belleği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: dcde0b74bb3ec845dba4ddfe0a5e389e46bd1c8a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641760"
---
# <a name="paging-entity-sql"></a>Disk belleği (varlık SQL)
Fiziksel disk belleği kullanarak gerçekleştirilebilir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. Belirleyici fiziksel disk belleği gerçekleştirmek için atla ve sınırı kullanmanız gerekir. Yalnızca sonuç satır sayısı bir belirleyici olmayan şekilde kısıtlamak istiyorsanız, kullanması gereken [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP ve SKIP/LIMIT birbirini dışlar.  
  
## <a name="top-overview"></a>ÜST genel bakış  
 SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştirici izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi yalnızca ilk satır kümesini sorgu sonuç döndüren belirtir. Daha fazla bilgi için [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>ATLA ve sınırı genel bakış  
 ATLA ve sınırı ORDER BY yan tümcesi parçasıdır. ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçları sıralama belirtimine göre sıralanır ve sonraki satırdaki Atla ifadesinden hemen sonra başlayan satırları sonuç kümesini içerir. Örneğin, Atla 5 ilk beş satırları atlar ve Altıncı satırdan ileriye doğru döndürür. Bir sınırı ifade alt yan tümcesi bir ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve elde edilen satır sayısı sınırı ifade tarafından sınırlanır. Örneğin, sınırı 5 sonuç beş örnekler ya da satır kümesi kısıtlar. ATLA ve sınırı birlikte kullanılması gerekmez; yalnızca Atla kullanın ya da yalnızca ORDER BY yan tümcesi ile SINIRLAYIN. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Nasıl yapılır: Sorgu sonuçları sayfasından](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
