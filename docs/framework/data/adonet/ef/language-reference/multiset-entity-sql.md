---
title: Çoklu küme (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319590"
---
# <a name="multiset-entity-sql"></a>Çoklu küme (Entity SQL)
Bir değer listesinden bir çoklu küme örneği oluşturur. Çoklu küme oluşturucudaki tüm değerler `T`uyumlu türde olmalıdır. Boş çok kümeli oluşturuculara izin verilmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Herhangi bir geçerli değer listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 \<T > türünde bir koleksiyon.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üç tür Oluşturucu sağlar: satır oluşturucular, nesne oluşturucular ve çoklu küme (veya koleksiyon) oluşturucuları. Daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.  
  
 Çoklu küme Oluşturucu bir değer listesinden bir çoklu küme örneği oluşturur. Oluşturucudaki tüm değerler uyumlu türde olmalıdır.  
  
 Örneğin, aşağıdaki ifade tamsayı olan bir çok küme oluşturur.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> İç içe yerleştirilmiş çoklu küme sabit değerleri yalnızca bir kaydırma çoklu kümeli tek bir çoklu küme öğesi olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`. Kaydırma çoklu kümeli birden çok çoklu küme öğesine (örneğin, `{{1, 2}, {3, 4}}`) sahip olduğunda, iç içe yerleştirilmiş çoklu küme sabit değerleri desteklenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir değer listesinden bir çoklu küme örneği oluşturmak için çoklu küme işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
