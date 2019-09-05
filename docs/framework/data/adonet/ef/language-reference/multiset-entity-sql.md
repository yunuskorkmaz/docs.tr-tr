---
title: Çoklu küme (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 8e02d2d3171c9f08333ecef7ee22e65100bdf822
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250090"
---
# <a name="multiset-entity-sql"></a>Çoklu küme (Entity SQL)
Bir değer listesinden bir çoklu küme örneği oluşturur. Çoklu küme oluşturucudaki tüm değerler uyumlu türde `T`olmalıdır. Boş çok kümeli oluşturuculara izin verilmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli değer listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 > Çok kümeli\<T türünde bir koleksiyon.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Üç tür Oluşturucu sağlar: satır oluşturucular, nesne oluşturucular ve çoklu küme (veya koleksiyon) oluşturucuları. Daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.  
  
 Çoklu küme Oluşturucu bir değer listesinden bir çoklu küme örneği oluşturur. Oluşturucudaki tüm değerler uyumlu türde olmalıdır.  
  
 Örneğin, aşağıdaki ifade tamsayı olan bir çok küme oluşturur.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> İç içe yerleştirilmiş çoklu küme sabit değerleri yalnızca bir kaydırma çoklu kümeli tek bir çoklu küme öğesi olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`. Kaydırma çoklu kümeli birden çok çoklu küme öğesine (örneğin, `{{1, 2}, {3, 4}}`) sahip olduğunda, iç içe yerleştirilmiş çoklu küme sabit değerleri desteklenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir değer listesinden bir çoklu küme örneği oluşturmak için çoklu küme işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
