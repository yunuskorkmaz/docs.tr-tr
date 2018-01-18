---
title: "&lt;(Küçüktür) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5bf1560c0bebafcfdbf79ca9a9906c9df23b7cae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="lt-less-than-entity-sql"></a>&lt;(Küçüktür) (Varlık SQL)
Sol ifade sağ ifade'den küçük bir değer olup olmadığını belirlemek için iki ifadeye karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade. Her iki ifadeleri örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.  
  
## <a name="result-types"></a>Sonuç türleri  
 `true`Sol ifade sağ ifade'den küçük bir değer varsa; Aksi takdirde `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu kullanır < karşılaştırma işlecinin sol ifade sağ ifade'den küçük bir değer olup olmadığını belirlemek için iki ifadeye karşılaştırın. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
