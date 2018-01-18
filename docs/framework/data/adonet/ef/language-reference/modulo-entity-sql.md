---
title: "(Modül) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a>(Modül) (Varlık SQL)
Bir başkası tarafından ayrılmış bir ifade kalanı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Bölmek için sayısal ifade. `dividend`sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
 `divisor`  
 Tarafından bölünen bölmek için sayısal ifade. `divisor`sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
## <a name="result-types"></a>Sonuç türleri  
 Edm.Int32  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu % aritmetik işleç başkası tarafından ayrılmış bir ifade kalanı döndürmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
