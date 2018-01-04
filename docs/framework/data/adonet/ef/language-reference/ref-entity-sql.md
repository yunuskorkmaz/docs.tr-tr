---
title: "REF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1836b91876ac3c993f07902a644c130dda76f158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ref-entity-sql"></a><span data-ttu-id="a04d7-102">REF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a04d7-102">REF (Entity SQL)</span></span>
<span data-ttu-id="a04d7-103">Bir varlık örneği için bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="a04d7-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a04d7-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="a04d7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a04d7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a04d7-106">Bir varlık türünün bir örneği üretir herhangi geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="a04d7-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a04d7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a04d7-107">Return Value</span></span>  
 <span data-ttu-id="a04d7-108">Belirtilen varlık örneğine başvuru.</span><span class="sxs-lookup"><span data-stu-id="a04d7-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04d7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a04d7-109">Remarks</span></span>  
 <span data-ttu-id="a04d7-110">Bir varlık başvurusu Varlık anahtarı içerir ve bir varlık kümesinin adı.</span><span class="sxs-lookup"><span data-stu-id="a04d7-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="a04d7-111">Farklı varlık kümeleri aynı varlık türüne dayalı olabilir çünkü belirli Varlık anahtarı birden çok varlık kümesinde yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="a04d7-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="a04d7-112">Ancak, bir varlık başvurusunun her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="a04d7-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="a04d7-113">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a04d7-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="a04d7-114">Giriş ifadesi kalıcı bir varlık değilse, bir null başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a04d7-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="a04d7-115">Özellik ayıklama işleci (.), bir varlığın bir özelliğe erişmek için kullanılırsa, otomatik olarak dereferenced başvurudur.</span><span class="sxs-lookup"><span data-stu-id="a04d7-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a04d7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a04d7-116">Example</span></span>  
 <span data-ttu-id="a04d7-117">Aşağıdaki varlık SQL sorgusunu REF işleci giriş varlık bağımsız değişken için başvuru döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a04d7-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="a04d7-118">Ürün varlık bir özelliğe erişmek için bir özellik ayıklama işlemi (.) kullanıyoruz çünkü aynı sorgu başvuru dereferences.</span><span class="sxs-lookup"><span data-stu-id="a04d7-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="a04d7-119">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a04d7-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a04d7-120">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a04d7-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a04d7-121">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a04d7-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="a04d7-122">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a04d7-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="a04d7-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a04d7-123">See Also</span></span>  
 [<span data-ttu-id="a04d7-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="a04d7-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="a04d7-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="a04d7-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="a04d7-126">KEY</span><span class="sxs-lookup"><span data-stu-id="a04d7-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="a04d7-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a04d7-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a04d7-128">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="a04d7-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
