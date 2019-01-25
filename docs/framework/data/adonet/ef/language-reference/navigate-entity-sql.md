---
title: (Varlık SQL) gidin
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: e66a09276f40ab6d9ff7c11bb160385b4c1efb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542567"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="9ee06-102">(Varlık SQL) gidin</span><span class="sxs-lookup"><span data-stu-id="9ee06-102">NAVIGATE (Entity SQL)</span></span>
<span data-ttu-id="9ee06-103">Oluşturulan varlıklar arasında ilişki üzerinden gider.</span><span class="sxs-lookup"><span data-stu-id="9ee06-103">Navigates over the relationship established between entities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ee06-104">Syntax</span></span>  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ee06-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9ee06-105">Arguments</span></span>  
 `instance-expresssion`  
 <span data-ttu-id="9ee06-106">Bir varlık örneği.</span><span class="sxs-lookup"><span data-stu-id="9ee06-106">An instance of an entity.</span></span>  
  
 `relationship-type`  
 <span data-ttu-id="9ee06-107">Kavramsal şema tanım dili (CSDL) dosyasından bir ilişki türü adı.</span><span class="sxs-lookup"><span data-stu-id="9ee06-107">The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="9ee06-108">`relationship-type` Olarak nitelenmiş \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="9ee06-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>  
  
 `to`  
 <span data-ttu-id="9ee06-109">İlişki sonu.</span><span class="sxs-lookup"><span data-stu-id="9ee06-109">The end of the relationship.</span></span>  
  
 `from`  
 <span data-ttu-id="9ee06-110">İlişki başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="9ee06-110">The beginning of the relationship.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ee06-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ee06-111">Return Value</span></span>  
 <span data-ttu-id="9ee06-112">Varsa önem düzeyini sonlandırmak için 1, dönüş değeri olacak `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="9ee06-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="9ee06-113">Varsa önem düzeyini sonlandırmak için n olduğundan, dönüş değeri olacak `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="9ee06-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ee06-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ee06-114">Remarks</span></span>  
 <span data-ttu-id="9ee06-115">Birinci sınıf yapılardan ilişkisidir [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span><span class="sxs-lookup"><span data-stu-id="9ee06-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="9ee06-116">İki veya daha fazla varlık türleri ilişkiler oluşturulabilir ve kullanıcılar üzerinde bir bitiş (varlık) arasında ilişki gidebilir.</span><span class="sxs-lookup"><span data-stu-id="9ee06-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="9ee06-117">`from` ve `to` ilişki içinde ad çözümlemesi belirsizlik olmaz olduğunda koşullu olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ee06-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>  
  
 <span data-ttu-id="9ee06-118">NAVIGATE O ve C alanında geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9ee06-118">NAVIGATE is valid in O and C space.</span></span>  
  
 <span data-ttu-id="9ee06-119">Bir gezinti yapısı genel formu aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9ee06-119">The general form of a navigation construct is the following:</span></span>  
  
 <span data-ttu-id="9ee06-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span><span class="sxs-lookup"><span data-stu-id="9ee06-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>  
  
 <span data-ttu-id="9ee06-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9ee06-121">For example:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="9ee06-122">OrderCustomer olduğu `relationship`, müşteri ve sipariş `to-end` (müşteri) ve `from-end` (sıra) ilişki.</span><span class="sxs-lookup"><span data-stu-id="9ee06-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="9ee06-123">OrderCustomer oluştu n: 1 ilişki sonra Ref navıgate ifadesi sonuç türü olan\<Müşteri >.</span><span class="sxs-lookup"><span data-stu-id="9ee06-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>  
  
 <span data-ttu-id="9ee06-124">Bu ifadenin daha basit form aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9ee06-124">The simpler form of this expression is the following:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="9ee06-125">Benzer şekilde, aşağıdaki biçimde bir sorguda navıgate ifadesi bir koleksiyon oluşturur < Ref\<sipariş >>.</span><span class="sxs-lookup"><span data-stu-id="9ee06-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 <span data-ttu-id="9ee06-126">Örnek ifade bir varlık/başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ee06-126">The instance-expression must be an entity/ref type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ee06-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ee06-127">Example</span></span>  
 <span data-ttu-id="9ee06-128">Aşağıdaki varlık SQL sorgusu NAVIGATE işleci oluşturulan adresi ve SalesOrderHeader varlık türleri ilişkinin üzerine gitmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ee06-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="9ee06-129">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="9ee06-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9ee06-130">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9ee06-130">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9ee06-131">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9ee06-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9ee06-132">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="9ee06-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a><span data-ttu-id="9ee06-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ee06-133">See also</span></span>
- [<span data-ttu-id="9ee06-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9ee06-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="9ee06-135">Nasıl yapılır: Gezinme işleci ile ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="9ee06-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
