---
title: GIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319549"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="f4cab-102">GIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f4cab-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="f4cab-103">Varlıklar arasında belirlenen ilişkinin üzerine gider.</span><span class="sxs-lookup"><span data-stu-id="f4cab-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4cab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4cab-104">Syntax</span></span>

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="f4cab-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f4cab-105">Arguments</span></span>

<span data-ttu-id="f4cab-106">bir varlığın örneğini `instance-expression`.</span><span class="sxs-lookup"><span data-stu-id="f4cab-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="f4cab-107">kavramsal şema tanım dili (CSDL) dosyasından ilişkinin tür adını `relationship-type`.</span><span class="sxs-lookup"><span data-stu-id="f4cab-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="f4cab-108">`relationship-type`, \<ad alanı > olarak nitelenir.\<ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="f4cab-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="f4cab-109">ilişkinin sonuna `to`.</span><span class="sxs-lookup"><span data-stu-id="f4cab-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="f4cab-110">ilişkinin başlangıcını `from`.</span><span class="sxs-lookup"><span data-stu-id="f4cab-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="f4cab-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4cab-111">Return Value</span></span>

<span data-ttu-id="f4cab-112">To end 'in kardinalitesi 1 ise, dönüş değeri `Ref<T>`olur.</span><span class="sxs-lookup"><span data-stu-id="f4cab-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="f4cab-113">To end 'in kardinalitei n ise, dönüş değeri `Collection<Ref<T>>`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4cab-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4cab-114">Remarks</span></span>

<span data-ttu-id="f4cab-115">İlişkiler Varlık Veri Modeli (EDM) ilk sınıf yapılardır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="f4cab-116">İki veya daha fazla varlık türü arasında ilişkiler kurulabilir ve kullanıcılar bir uçtan diğerine (varlık) ilişki üzerinde gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4cab-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="f4cab-117">ilişki içinde ad çözümlemesinde hiçbir belirsizlik olmadığında, `from` ve `to` koşullu olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="f4cab-118">GIT, O ve C alanında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f4cab-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="f4cab-119">Bir gezinti yapısının genel formu aşağıdaki şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f4cab-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="f4cab-120">gezinme (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])</span><span class="sxs-lookup"><span data-stu-id="f4cab-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="f4cab-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4cab-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="f4cab-122">Burada OrderCustomer `relationship`ve müşteri ve sipariş ilişkinin `to-end` (müşteri) ve `from-end` (sipariş).</span><span class="sxs-lookup"><span data-stu-id="f4cab-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="f4cab-123">OrderCustomer bir n:1 ilişkisi ise, gezinme ifadesinin sonuç türü, başvuru\<müşteri > olur.</span><span class="sxs-lookup"><span data-stu-id="f4cab-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="f4cab-124">Bu ifadenin daha basit biçimi aşağıdaki şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f4cab-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="f4cab-125">Benzer şekilde, aşağıdaki formun bir sorgusunda, gezinme ifadesi bir koleksiyon < ref\<sırası > > oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4cab-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="f4cab-126">Örnek ifadesi bir varlık/başvuru türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="f4cab-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4cab-127">Example</span></span>

<span data-ttu-id="f4cab-128">Aşağıdaki Entity SQL sorgusu, Address ve SalesOrderHeader varlık türleri arasında belirlenen ilişki üzerinde gezinmek için GEZINME işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="f4cab-129">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f4cab-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f4cab-130">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f4cab-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="f4cab-131">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="f4cab-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="f4cab-132">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="f4cab-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a><span data-ttu-id="f4cab-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4cab-133">See also</span></span>

- [<span data-ttu-id="f4cab-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4cab-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f4cab-135">Nasıl yapılır: gezinme Işleçle Ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="f4cab-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
