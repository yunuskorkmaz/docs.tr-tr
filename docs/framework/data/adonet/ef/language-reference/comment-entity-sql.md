---
title: --(Açıklama) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 9ad6e38726d0802c3bc2090a4e6f11f008828ee5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197904"
---
# <a name="---comment-entity-sql"></a>--(Açıklama) (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular, açıklamalar içerebilir. İki kısa çizgi ( `--` ) bir açıklama satırı başlatın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `text_of_comment`  
 Açıklamanın metnini içeren karakter dizesidir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, yorumların nasıl kullanılacağını göstermektedir. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
