---
title: "(Varlık SQL) gidin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a860fae543e4d74e2b0569ed3672f3dc113f84c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="0a299-102">(Varlık SQL) gidin</span><span class="sxs-lookup"><span data-stu-id="0a299-102">NAVIGATE (Entity SQL)</span></span>
<span data-ttu-id="0a299-103">Varlıklar arasında kurulan ilişki üzerinden gider.</span><span class="sxs-lookup"><span data-stu-id="0a299-103">Navigates over the relationship established between entities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a299-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a299-104">Syntax</span></span>  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a299-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0a299-105">Arguments</span></span>  
 `instance-expresssion`  
 <span data-ttu-id="0a299-106">Bir varlık örneği.</span><span class="sxs-lookup"><span data-stu-id="0a299-106">An instance of an entity.</span></span>  
  
 `relationship-type`  
 <span data-ttu-id="0a299-107">Kavramsal şema tanım dili (CSDL) dosyasından ilişki türü adı.</span><span class="sxs-lookup"><span data-stu-id="0a299-107">The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="0a299-108">`relationship-type` Olarak nitelenmiş \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="0a299-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>  
  
 `to`  
 <span data-ttu-id="0a299-109">İlişki sonu.</span><span class="sxs-lookup"><span data-stu-id="0a299-109">The end of the relationship.</span></span>  
  
 `from`  
 <span data-ttu-id="0a299-110">İlişki başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="0a299-110">The beginning of the relationship.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a299-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a299-111">Return Value</span></span>  
 <span data-ttu-id="0a299-112">Varsa önemi sona erdirmek için 1 ise, dönüş değeri olacaktır `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="0a299-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="0a299-113">Varsa önemi sonuna n ise, dönüş değeri olacaktır `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="0a299-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a299-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a299-114">Remarks</span></span>  
 <span data-ttu-id="0a299-115">İlişkileri olan birinci sınıf yapılardan [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span><span class="sxs-lookup"><span data-stu-id="0a299-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="0a299-116">İki veya daha fazla varlık türleri ilişkileri oluşturulabilir ve kullanıcılar bir uç (varlık) arasında ilişki üzerinden gezinebilir.</span><span class="sxs-lookup"><span data-stu-id="0a299-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="0a299-117">`from`ve `to` ilişki içinde ad çözümlemesi belirsizlik olmaz olduğunda koşullu isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0a299-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>  
  
 <span data-ttu-id="0a299-118">Bul O ve C alanı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0a299-118">NAVIGATE is valid in O and C space.</span></span>  
  
 <span data-ttu-id="0a299-119">Bir gezinti yapısı genel form aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0a299-119">The general form of a navigation construct is the following:</span></span>  
  
 <span data-ttu-id="0a299-120">gidin (`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ]])</span><span class="sxs-lookup"><span data-stu-id="0a299-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>  
  
 <span data-ttu-id="0a299-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0a299-121">For example:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="0a299-122">OrderCustomer olduğu `relationship`, müşteri ve sipariş `to-end` (müşteri) ve `from-end` (sırasıyla) ilişkisinin.</span><span class="sxs-lookup"><span data-stu-id="0a299-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="0a299-123">OrderCustomer edildi n: 1 ilişki sonra Ref Bul ifade sonuç türü olan\<Müşteri >.</span><span class="sxs-lookup"><span data-stu-id="0a299-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>  
  
 <span data-ttu-id="0a299-124">Bu ifade basit biçimidir aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0a299-124">The simpler form of this expression is the following:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="0a299-125">Benzer şekilde, aşağıdaki biçimde bir sorguya Bul ifade bir koleksiyon oluşturur < Ref\<sipariş >>.</span><span class="sxs-lookup"><span data-stu-id="0a299-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 <span data-ttu-id="0a299-126">Örnek ifadesi, bir varlık/ref türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a299-126">The instance-expression must be an entity/ref type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a299-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a299-127">Example</span></span>  
 <span data-ttu-id="0a299-128">Aşağıdaki varlık SQL sorgusunu Bul işleci oluşturulan adresi ve SalesOrderHeader varlık türleri ilişkinin üzerinden gitmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a299-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="0a299-129">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0a299-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0a299-130">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0a299-130">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0a299-131">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0a299-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0a299-132">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0a299-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a><span data-ttu-id="0a299-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a299-133">See Also</span></span>  
 [<span data-ttu-id="0a299-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a299-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="0a299-135">Nasıl yapılır: gidin ilişkileriyle gidin işleci</span><span class="sxs-lookup"><span data-stu-id="0a299-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
