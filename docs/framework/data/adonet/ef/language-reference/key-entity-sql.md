---
title: "ANAHTAR (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa18efd32998f881d49d7ebd71bad0cdf8122457
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="key-entity-sql"></a><span data-ttu-id="a0887-102">ANAHTAR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a0887-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="a0887-103">Bir başvuru veya varlık ifade anahtarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="a0887-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0887-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0887-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="a0887-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0887-105">Remarks</span></span>  
 <span data-ttu-id="a0887-106">Bir varlık anahtarı doğru sırada belirtilen varlık veya varlık başvurusu anahtar değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a0887-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="a0887-107">Birden çok varlık kümesine aynı türüne dayalı olabilir çünkü, aynı anahtar her varlık kümesinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a0887-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="a0887-108">Benzersiz bir başvuru almak için `REF`.</span><span class="sxs-lookup"><span data-stu-id="a0887-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="a0887-109">ANAHTAR işleci dönüş türü varlığın her anahtar için bir alan aynı sırada içeren bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="a0887-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="a0887-110">Aşağıdaki örnekte, anahtar işleci BadOrder varlığa bir başvuru geçirilir ve bu başvuruyu anahtar bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0887-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="a0887-111">Bu durumda, bir kayıt türü tam olarak bir alan karşılık gelen ile `Id` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0887-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="a0887-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0887-112">Example</span></span>  
 <span data-ttu-id="a0887-113">Aşağıdaki varlık SQL sorgusunu anahtar işlecini kullanan bir ifade türü başvuru içeren anahtar bölümünü ayıklamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0887-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="a0887-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a0887-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a0887-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a0887-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a0887-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a0887-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a0887-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a0887-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="a0887-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0887-118">See Also</span></span>  
 [<span data-ttu-id="a0887-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a0887-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a0887-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="a0887-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="a0887-121">REF</span><span class="sxs-lookup"><span data-stu-id="a0887-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="a0887-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="a0887-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
