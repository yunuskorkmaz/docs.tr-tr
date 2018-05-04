---
title: SINIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b844c5a132d36a4ca9d660607bbfe0f39ceab718
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="limit-entity-sql"></a>SINIR (varlık SQL)
Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir. ORDER BY from yan tümcesi sınırı ayrı olarak kullanılamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Seçilecek öğe sayısı.  
  
 İfade LIMIT alt yan ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve sonuçta elde edilen satır sayısı sınırı ifadeyle kısıtlanmış olabilir. Örneğin, sınır 5 sonuç 5 örnekleri veya satır kümesini kısıtlar. SINIR sınırı bulunması ORDER BY yan tümcesi gerektirir özel durumla dön işlevsel olarak eşdeğerdir. Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.  
  
> [!NOTE]
>  Varlık Sql sorgusu üst varsa geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesinin aynı sorgu ifadesinde yok. Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu ORDER BY işleci sınırı ile bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
