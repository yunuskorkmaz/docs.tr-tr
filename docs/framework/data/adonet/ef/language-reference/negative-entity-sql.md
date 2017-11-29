---
title: "- (Negatif) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0cc2ca457fe8666bddd6f4ab40d2823d9d44c591
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="--negative-entity-sql"></a>-(Olumsuz) (varlık SQL)
Sayısal bir ifadenin değerini negatif döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Sayısal veri türleri herhangi birinin geçerli bir ifade.  
  
## <a name="result-types"></a>Sonuç türleri  
 Veri türü `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `expression` imzasız bir tür sonuç türü türüne en yakından ilişkili imzalı türü olacaktır `expression`. Örneğin, varsa `expression` bayt, Int16 döndürülecek türünde bir değer türüdür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır sayısal bir ifadenin değerini negatif döndürülecek aritmetik işleç. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
