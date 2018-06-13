---
title: INTERSECT (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 98515ccf111bf78f49347f744a1226ca1957fbb6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761538"
---
# <a name="intersect-entity-sql"></a>INTERSECT (varlık SQL)
Her iki sorgu ifadeleri sol tarafından döndürülen tüm farklı değerler koleksiyonu ve INTERSECT işleneni sağ tarafında döndürür. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonu ile karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 INTERSECT biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu INTERSECT işlecini hem sorgu ifadeleri sol tarafından döndürülen tüm farklı değerler koleksiyonu ve INTERSECT işleneni sağ tarafında döndürmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
