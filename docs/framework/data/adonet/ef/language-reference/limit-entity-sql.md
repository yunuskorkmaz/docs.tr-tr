---
title: SINIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 4534148279ece3b00c45f61c6a35a74a64ca3b6f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406893"
---
# <a name="limit-entity-sql"></a>SINIR (varlık SQL)
Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir. From tümcesi ORDER BY sınırı ayrı olarak kullanılamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Seçilir öğe sayısı.  
  
 Bir sınırı ifade alt yan tümcesi bir ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve elde edilen satır sayısı sınırı ifade tarafından sınırlanır. Örneğin, sınırı 5 sonuç 5 örnekleri veya satır kümesi kısıtlar. SINIRI sınırı bulunması ORDER BY yan tümcesini gerektirir bir özel durumla BAŞA işlevsel olarak eşdeğerdir. Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.  
  
> [!NOTE]
>  Bir varlık Sql sorgusu üst durumunda Geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesi, aynı sorgu ifadesinde vardır. Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için sınır ile kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: Bu döndürür StructuralType sonuçları sorguyu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Nasıl yapılır: sorgu aracılığıyla sayfa sonuçları](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
