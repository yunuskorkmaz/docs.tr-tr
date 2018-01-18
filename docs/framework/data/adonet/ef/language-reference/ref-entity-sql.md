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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 226a14daa706f6cf0481b752fa03dc95db3eff81
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="ref-entity-sql"></a><span data-ttu-id="99c4d-102">REF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="99c4d-102">REF (Entity SQL)</span></span>
<span data-ttu-id="99c4d-103">Bir varlık örneği için bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="99c4d-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99c4d-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="99c4d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="99c4d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="99c4d-106">Bir varlık türünün bir örneği üretir herhangi geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="99c4d-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99c4d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99c4d-107">Return Value</span></span>  
 <span data-ttu-id="99c4d-108">Belirtilen varlık örneğine başvuru.</span><span class="sxs-lookup"><span data-stu-id="99c4d-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99c4d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99c4d-109">Remarks</span></span>  
 <span data-ttu-id="99c4d-110">Bir varlık başvurusu Varlık anahtarı içerir ve bir varlık kümesinin adı.</span><span class="sxs-lookup"><span data-stu-id="99c4d-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="99c4d-111">Farklı varlık kümeleri aynı varlık türüne dayalı olabilir çünkü belirli Varlık anahtarı birden çok varlık kümesinde yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="99c4d-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="99c4d-112">Ancak, bir varlık başvurusunun her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="99c4d-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="99c4d-113">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="99c4d-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="99c4d-114">Giriş ifadesi kalıcı bir varlık değilse, bir null başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="99c4d-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="99c4d-115">Özellik ayıklama işleci (.), bir varlığın bir özelliğe erişmek için kullanılırsa, otomatik olarak dereferenced başvurudur.</span><span class="sxs-lookup"><span data-stu-id="99c4d-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c4d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="99c4d-116">Example</span></span>  
 <span data-ttu-id="99c4d-117">Aşağıdaki varlık SQL sorgusunu REF işleci giriş varlık bağımsız değişken için başvuru döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="99c4d-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="99c4d-118">Ürün varlık bir özelliğe erişmek için bir özellik ayıklama işlemi (.) kullanıyoruz çünkü aynı sorgu başvuru dereferences.</span><span class="sxs-lookup"><span data-stu-id="99c4d-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="99c4d-119">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="99c4d-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="99c4d-120">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="99c4d-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="99c4d-121">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="99c4d-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="99c4d-122">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="99c4d-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="99c4d-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99c4d-123">See Also</span></span>  
 [<span data-ttu-id="99c4d-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="99c4d-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="99c4d-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="99c4d-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="99c4d-126">KEY</span><span class="sxs-lookup"><span data-stu-id="99c4d-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="99c4d-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="99c4d-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="99c4d-128">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="99c4d-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
