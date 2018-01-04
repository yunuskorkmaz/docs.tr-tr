---
title: "--(Açıklama) (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 483e1c69aea94375983acd840f84512de54bc746
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="---comment-entity-sql"></a>--(Açıklama) (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]sorguları açıklamaları içerebilir. İki kısa çizgi (`--`) bir açıklama satırı başlatın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 `text_of_comment`  
 Açıklama metnini içeren karakter dizesidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu açıklamaları kullanımı gösterilmiştir. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
