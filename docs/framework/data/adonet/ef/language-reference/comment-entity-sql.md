---
title: --(Açıklama) (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 477a5f9aefeec46766a93c1e6ae9f3ecb3c3677f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705704"
---
# <a name="---comment-entity-sql"></a>--(Açıklama) (varlık SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgu açıklamaları bulunabilir. İki kısa çizgi (`--`) bir yorum satırını başlatın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 `text_of_comment`  
 Yorumun metni içeren karakter dizesidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu açıklamaları kullanımı gösterilmiştir. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
