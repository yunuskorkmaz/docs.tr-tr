---
title: Disk belleği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 4c9a08604c90422ac461bdd7db895b18b633e87e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402091"
---
# <a name="paging-entity-sql"></a>Disk belleği (varlık SQL)
Fiziksel disk belleği kullanarak gerçekleştirilebilir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. Belirleyici fiziksel disk belleği gerçekleştirmek için atla ve sınırı kullanmanız gerekir. Yalnızca satır determinsitic olmayan bir yolla sonuç sayısını kısıtlamak istiyorsanız, kullanması gereken [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP ve SKIP/LIMIT birbirini dışlar.  
  
## <a name="top-overview"></a>ÜST genel bakış  
 SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştirici izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi yalnızca ilk satır kümesini sorgu sonuç döndüren belirtir. Daha fazla bilgi için [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>ATLA ve sınırı genel bakış  
 ATLA ve sınırı ORDER BY yan tümcesi parçasıdır. ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçları sıralama belirtimine göre sıralanır ve sonraki satırdaki Atla ifadesinden hemen sonra başlayan satırları sonuç kümesini içerir. Örneğin, Atla 5 ilk beş satırları atlar ve Altıncı satırdan ileriye doğru döndürür. Bir sınırı ifade alt yan tümcesi bir ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve elde edilen satır sayısı sınırı ifade tarafından sınırlanır. Örneğin, sınırı 5 sonuç beş örnekler ya da satır kümesi kısıtlar. ATLA ve sınırı birlikte kullanılması gerekmez; yalnızca Atla kullanın ya da yalnızca ORDER BY yan tümcesi ile SINIRLAYIN. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Nasıl yapılır: sorgu aracılığıyla sayfa sonuçları](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
