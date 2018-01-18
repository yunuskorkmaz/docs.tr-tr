---
title: "- (Bölme) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f9f640d50ec24b30cedfe0d4d8d4982509efc35
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="-divide-entity-sql"></a>/ (Bölme (varlık SQL))
Bir sayıyı bir başkası tarafından böler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Bölmek için sayısal ifade. `dividend`sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
 `divisor`  
 Tarafından bölünen bölmek için sayısal ifade. `divisor`sayısal veri türleri herhangi birinin geçerli bir ifade değil.  
  
## <a name="result-types"></a>Sonuç türleri  
 İki bağımsız değişken örtük tür yükseltme sonuçları veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır / aritmetik bir numarası bir başkası tarafından bölmek için işleci. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
