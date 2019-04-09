---
title: UNION (varlık SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: ea74cb77df059556876364237887d6dfa21e5609
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165860"
---
# <a name="union-entity-sql"></a>UNION (varlık SQL)
İki veya daha fazla sorguların sonuçlarını tek bir koleksiyon birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tüm ifadeler koleksiyon ile birleştirmek için bir koleksiyon döndüren herhangi bir geçerli sorgu ifade aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.  
  
 UNION  
 Birden çok koleksiyon birleştirilir ve tek bir koleksiyon döndürülen olduğunu belirtir.  
  
 TÜM  
 Birden çok koleksiyon birleştirilir ve yinelenenler de dahil olmak üzere tek bir koleksiyon döndürülen olduğunu belirtir. Belirtilmezse, çoğaltmaları sonucu koleksiyondan kaldırılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir koleksiyonu aynı türde veya ortak bir temel veya türetilmiş tür `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 BİRLEŞİM biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir. Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu UNION ALL işleci iki sorgunun sonuçlarını tek bir koleksiyona birleştirmek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
