---
title: --(Açıklama) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040282"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="4dc49-102">--(Açıklama) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4dc49-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4dc49-103">sorguları, açıklamalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4dc49-103">queries can contain comments.</span></span> <span data-ttu-id="4dc49-104">İki tire (`--`) bir açıklama satırı başlatın.</span><span class="sxs-lookup"><span data-stu-id="4dc49-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc49-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dc49-105">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="4dc49-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4dc49-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="4dc49-107">Açıklamanın metnini içeren karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="4dc49-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dc49-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dc49-108">Example</span></span>  
 <span data-ttu-id="4dc49-109">Aşağıdaki Entity SQL sorgusu, yorumların nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4dc49-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="4dc49-110">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4dc49-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4dc49-111">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4dc49-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4dc49-112">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="4dc49-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4dc49-113">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="4dc49-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="4dc49-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dc49-114">See also</span></span>

- [<span data-ttu-id="4dc49-115">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4dc49-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="4dc49-116">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4dc49-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
