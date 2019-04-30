---
title: MULTISET (varlık SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 44e411b8ae2f43bf3a729ac091ffd1eb4c462c63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760499"
---
# <a name="multiset-entity-sql"></a>MULTISET (varlık SQL)
Değerler listesinden bir çoklu küme örneği oluşturur. MULTISET Oluşturucu tüm değerleri uyumlu bir tür olmalıdır `T`. Boş çoklu küme oluşturuculara izin verilmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tüm geçerli değerlerin listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 MULTISET türündeki bir koleksiyon\<T >.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üç tür oluşturucular sağlar: satır Oluşturucular, nesne oluşturucuları ve oluşturucular multiset (veya koleksiyonu). Daha fazla bilgi için [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Multıset Oluşturucu değerler listesinden bir çoklu küme örneği oluşturur. Oluşturucu içinde tüm değerleri uyumlu bir tür olmalıdır.  
  
 Örneğin, aşağıdaki ifade, bir çoklu küme tamsayı oluşturur.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  İç içe geçmiş multiset değişmez değerleri, yalnızca bir kaydırma çoklu küme, tek bir çok kümeli öğe olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`. Kaydırma çoklu küme, birden fazla çok kümeli öğe olduğunda (örneğin, `{{1, 2}, {3, 4}}`), iç içe geçmiş multiset değişmez değerleri desteklenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu MULTISET işleci değerler listesinden bir çoklu küme örneği oluşturmak için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
