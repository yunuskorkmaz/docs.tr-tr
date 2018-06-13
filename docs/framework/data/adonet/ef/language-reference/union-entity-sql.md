---
title: Birleşim (varlık SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764885"
---
# <a name="union-entity-sql"></a>Birleşim (varlık SQL)
İki veya daha fazla sorguların sonuçlarını tek bir koleksiyona birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Tüm ifadeler koleksiyonuyla birleştirmek için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.  
  
 UNION  
 Birden çok koleksiyon birleştirilir ve tek bir koleksiyon olarak döndürülen olduğunu belirtir.  
  
 TÜM  
 Birden çok koleksiyon birleştirilir ve yinelenenleri de dahil olmak üzere tek bir koleksiyon döndürülen olduğunu belirtir. Belirtilmezse, yinelemeleri sonuç koleksiyonundan kaldırılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 UNION biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu UNION ALL işleci iki sorguların sonuçlarını tek bir koleksiyona birleştirmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
