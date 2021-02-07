---
description: GEZINME hakkında daha fazla bilgi edinin (Entity SQL)
title: GIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 7fa39a988429fe0a658b01078d2369ad4767f4a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696509"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="e238c-103">GIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e238c-103">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="e238c-104">Varlıklar arasında belirlenen ilişkinin üzerine gider.</span><span class="sxs-lookup"><span data-stu-id="e238c-104">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="e238c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e238c-105">Syntax</span></span>

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="e238c-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e238c-106">Arguments</span></span>

<span data-ttu-id="e238c-107">`instance-expression` Bir varlık örneği.</span><span class="sxs-lookup"><span data-stu-id="e238c-107">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="e238c-108">`relationship-type` Kavramsal şema tanım dili (CSDL) dosyasından ilişkinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="e238c-108">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="e238c-109">, `relationship-type` Olarak nitelenir \<namespace> . \<relationship type name> ..</span><span class="sxs-lookup"><span data-stu-id="e238c-109">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="e238c-110">`to` İlişkinin sonu.</span><span class="sxs-lookup"><span data-stu-id="e238c-110">`to` The end of the relationship.</span></span>

<span data-ttu-id="e238c-111">`from` İlişkinin başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="e238c-111">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="e238c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e238c-112">Return Value</span></span>

<span data-ttu-id="e238c-113">To end 'in kardinalitesi 1 ise, dönüş değeri olacaktır `Ref<T>` .</span><span class="sxs-lookup"><span data-stu-id="e238c-113">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="e238c-114">To end 'in kardinalitei n ise, dönüş değeri olacaktır `Collection<Ref<T>>` .</span><span class="sxs-lookup"><span data-stu-id="e238c-114">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e238c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e238c-115">Remarks</span></span>

<span data-ttu-id="e238c-116">İlişkiler Varlık Veri Modeli (EDM) ilk sınıf yapılardır.</span><span class="sxs-lookup"><span data-stu-id="e238c-116">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="e238c-117">İki veya daha fazla varlık türü arasında ilişkiler kurulabilir ve kullanıcılar bir uçtan diğerine (varlık) ilişki üzerinde gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e238c-117">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="e238c-118">`from` ve `to` ilişki içinde ad çözümlemesinde hiçbir belirsizlik olmadığında koşullu olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e238c-118">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="e238c-119">GIT, O ve C alanında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e238c-119">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="e238c-120">Bir gezinti yapısının genel formu aşağıdaki şekildedir:</span><span class="sxs-lookup"><span data-stu-id="e238c-120">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="e238c-121">Git ( `instance-expression` , `relationship-type` , [ `to-end` [, `from-end` ]])</span><span class="sxs-lookup"><span data-stu-id="e238c-121">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="e238c-122">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e238c-122">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="e238c-123">Burada OrderCustomer, `relationship` ve müşteri ve sipariş `to-end` ilişkinin (müşteri) ve `from-end` (sipariş) olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="e238c-123">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="e238c-124">OrderCustomer bir n:1 ilişkisiyse, gezinme ifadesinin sonuç türü ref ' dir \<Customer> .</span><span class="sxs-lookup"><span data-stu-id="e238c-124">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="e238c-125">Bu ifadenin daha basit biçimi aşağıdaki şekildedir:</span><span class="sxs-lookup"><span data-stu-id="e238c-125">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="e238c-126">Benzer şekilde, aşağıdaki formun bir sorgusunda, gezinme ifadesi bir koleksiyon<başvuru \<Order>> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e238c-126">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="e238c-127">Örnek ifadesi bir varlık/başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e238c-127">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="e238c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e238c-128">Example</span></span>

<span data-ttu-id="e238c-129">Aşağıdaki Entity SQL sorgusu, Address ve SalesOrderHeader varlık türleri arasında belirlenen ilişki üzerinde gezinmek için GEZINME işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e238c-129">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="e238c-130">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e238c-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e238c-131">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e238c-131">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="e238c-132">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="e238c-132">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="e238c-133">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e238c-133">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a><span data-ttu-id="e238c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e238c-134">See also</span></span>

- [<span data-ttu-id="e238c-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e238c-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e238c-136">Nasıl yapılır: gezinme Işleçle Ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="e238c-136">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
