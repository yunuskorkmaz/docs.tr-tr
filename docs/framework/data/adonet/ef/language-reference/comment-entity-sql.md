---
title: --(Açıklama) (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 4b3c801999d520a775c1a7026c945c027145b59d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764170"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="78153-102">--(Açıklama) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="78153-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="78153-103"> sorguları açıklamaları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="78153-103"> queries can contain comments.</span></span> <span data-ttu-id="78153-104">İki kısa çizgi (`--`) bir açıklama satırı başlatın.</span><span class="sxs-lookup"><span data-stu-id="78153-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78153-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78153-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="78153-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="78153-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="78153-107">Açıklama metnini içeren karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="78153-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78153-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="78153-108">Example</span></span>  
 <span data-ttu-id="78153-109">Aşağıdaki varlık SQL sorgusunu açıklamaları kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78153-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="78153-110">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="78153-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="78153-111">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="78153-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="78153-112">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="78153-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="78153-113">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="78153-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="78153-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78153-114">See Also</span></span>  
 [<span data-ttu-id="78153-115">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="78153-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="78153-116">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="78153-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
