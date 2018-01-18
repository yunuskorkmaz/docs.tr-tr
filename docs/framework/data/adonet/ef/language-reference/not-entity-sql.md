---
title: "! (YOK) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f3786724280cc077574f37e4d373c85faf5340f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="-not-entity-sql"></a>! (YOK) (Varlık SQL)
Üzerindeki geçersiz kılar bir `Boolean` ifade.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Tüm geçerli ifade bir Boole değeri döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Ünlem işareti (!) NOT işleci aynı işlevselliğe sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu üzerindeki geçersiz kılar için değil işlecini kullanan bir `Boolean` ifade. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
