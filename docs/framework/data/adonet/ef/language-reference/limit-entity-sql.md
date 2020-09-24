---
title: SıNıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 81d135785e567d46a105adcafbf083f48cb4868e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161769"
---
# <a name="limit-entity-sql"></a>SıNıR (Entity SQL)

Fiziksel sayfalama, ORDER BY yan tümcesinde LIMIT alt yan tümcesi kullanılarak gerçekleştirilebilir. SıNıR, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `n`  
 Seçilecek öğe sayısı.  
  
 Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır. Örneğin, sınır 5, sonuç kümesini 5 örnek veya satır olarak kısıtlar. SıNıR, ORDER BY yan tümcesinin mevcut olmasını gerektiren sınır ile en üst ile eşdeğerdir. SKIP ve LIMIT, ORDER BY yan tümcesiyle birlikte bağımsız olarak kullanılabilir.  
  
> [!NOTE]
> En üstteki değiştirici ve SKIP alt yan tümcesi aynı sorgu ifadesinde varsa, bir varlık SQL sorgusu geçersiz olarak kabul edilir. ÜST ifade, sınır ifadesine göre değiştirilerek sorgunun yeniden yazılması gerekir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, SELECT ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için LIMIT ile ORDER BY işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](order-by-entity-sql.md)
- [Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Sayfalama](paging-entity-sql.md)
- [Sayfanın Üstü](top-entity-sql.md)
