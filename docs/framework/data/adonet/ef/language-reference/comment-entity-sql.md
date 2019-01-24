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
# <a name="---comment-entity-sql"></a><span data-ttu-id="60c10-102">--(Açıklama) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="60c10-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="60c10-103">Sorgu açıklamaları bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="60c10-103">queries can contain comments.</span></span> <span data-ttu-id="60c10-104">İki kısa çizgi (`--`) bir yorum satırını başlatın.</span><span class="sxs-lookup"><span data-stu-id="60c10-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c10-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60c10-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="60c10-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="60c10-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="60c10-107">Yorumun metni içeren karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="60c10-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60c10-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="60c10-108">Example</span></span>  
 <span data-ttu-id="60c10-109">Aşağıdaki varlık SQL sorgusu açıklamaları kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="60c10-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="60c10-110">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="60c10-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="60c10-111">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="60c10-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="60c10-112">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="60c10-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="60c10-113">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="60c10-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="60c10-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60c10-114">See also</span></span>
- [<span data-ttu-id="60c10-115">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60c10-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="60c10-116">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="60c10-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
