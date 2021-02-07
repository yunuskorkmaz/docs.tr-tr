---
description: Hakkında daha fazla bilgi edinin:--(Açıklama) (Entity SQL)
title: --(Açıklama) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 793649177d9e64bead7b8755f35bdb51f53f4dd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724979"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="47176-103">--(Açıklama) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="47176-103">-- (Comment) (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="47176-104">sorgular, açıklamalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47176-104">queries can contain comments.</span></span> <span data-ttu-id="47176-105">İki kısa çizgi ( `--` ) bir açıklama satırı başlatın.</span><span class="sxs-lookup"><span data-stu-id="47176-105">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47176-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="47176-106">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="47176-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="47176-107">Arguments</span></span>  

 `text_of_comment`  
 <span data-ttu-id="47176-108">Açıklamanın metnini içeren karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="47176-108">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47176-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="47176-109">Example</span></span>  

 <span data-ttu-id="47176-110">Aşağıdaki Entity SQL sorgusu, yorumların nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="47176-110">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="47176-111">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="47176-111">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="47176-112">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="47176-112">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="47176-113">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="47176-113">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="47176-114">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="47176-114">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="47176-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47176-115">See also</span></span>

- [<span data-ttu-id="47176-116">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47176-116">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="47176-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="47176-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
