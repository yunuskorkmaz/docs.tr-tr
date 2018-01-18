---
title: "Birleşim (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 067c3fedb1e03741158209751de9a13a00c23c35
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
