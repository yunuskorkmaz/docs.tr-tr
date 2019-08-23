---
title: SıNıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: e637218bb3db69d4b09fd734b939fd30f50ed806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961881"
---
# <a name="limit-entity-sql"></a>SıNıR (Entity SQL)
Fiziksel sayfalama, ORDER BY yan tümcesinde LIMIT alt yan tümcesi kullanılarak gerçekleştirilebilir. SıNıR, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Seçilecek öğe sayısı.  
  
 Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır. Örneğin, sınır 5, sonuç kümesini 5 örnek veya satır olarak kısıtlar. SıNıR, ORDER BY yan tümcesinin mevcut olmasını gerektiren sınır ile en üst ile eşdeğerdir. SKIP ve LIMIT, ORDER BY yan tümcesiyle birlikte bağımsız olarak kullanılabilir.  
  
> [!NOTE]
> En üstteki değiştirici ve SKIP alt yan tümcesi aynı sorgu ifadesinde varsa, bir varlık SQL sorgusu geçersiz olarak kabul edilir. ÜST ifade, sınır ifadesine göre değiştirilerek sorgunun yeniden yazılması gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, SELECT ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için LIMIT ile ORDER BY işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
