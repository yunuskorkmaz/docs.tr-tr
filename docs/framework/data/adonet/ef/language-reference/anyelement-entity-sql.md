---
title: "ANYELEMENT (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: de08e590bcc7b2380f2edda0ebc918d7ce328f4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (varlık SQL)
Bir öğenin birden çok değerli bir koleksiyondan ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir öğeyi ayıklamak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tek bir öğeye koleksiyon ya da birden fazla koleksiyon varsa, bir öğeye; koleksiyon boş ise, döndürür `null`. Varsa `collection` türü koleksiyonudur `Collection<T>`, ardından `ANYELEMENT(collection)` türünün bir örneği üretir geçerli bir ifade `T`.  
  
## <a name="remarks"></a>Açıklamalar  
 ANYELEMENT birden çok değerli bir koleksiyondan bir öğeye ayıklar. Örneğin, aşağıdaki örnekte bir singleton öğesi kümesinden ayıklamaya çalışır `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu birden çok değerli bir koleksiyondaki bir öğe ayıklamak için ANYELEMENT işleci kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
