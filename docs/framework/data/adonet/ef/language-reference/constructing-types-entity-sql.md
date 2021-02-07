---
description: 'Daha fazla bilgi: tür oluşturma (Entity SQL)'
title: Türleri oluşturma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 5963c34ffd8e9273d400cc16ba93f72ded2ede46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724849"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="23d9a-103">Türleri oluşturma (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="23d9a-103">Constructing Types (Entity SQL)</span></span>

<!-- markdownlint-disable DOCSMD001 -->
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="23d9a-104">Üç tür Oluşturucu sağlar: satır oluşturucular, adlandırılmış tür oluşturucular ve koleksiyon oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="23d9a-104">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>

## <a name="row-constructors"></a><span data-ttu-id="23d9a-105">Satır oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="23d9a-105">Row Constructors</span></span>

<span data-ttu-id="23d9a-106">' De satır oluşturucuları kullanarak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="23d9a-106">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="23d9a-107">Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="23d9a-107">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="23d9a-108">Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)` :</span><span class="sxs-lookup"><span data-stu-id="23d9a-108">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>

`ROW(1 AS a, "abc" AS b, a + 34 AS c)`

<span data-ttu-id="23d9a-109">Bir satır oluşturucusunda ifade için bir diğer ad sağlamazsanız, Entity Framework bir tane oluşturmaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="23d9a-109">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="23d9a-110">Daha fazla bilgi için, [tanımlayıcılardaki](identifiers-entity-sql.md)"diğer ad kuralları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23d9a-110">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>

<span data-ttu-id="23d9a-111">Aşağıdaki kurallar, bir satır oluşturucusunda ifade diğer ad için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="23d9a-111">The following rules apply to expression aliasing in a row constructor:</span></span>

- <span data-ttu-id="23d9a-112">Bir satır oluşturucudaki ifadeler aynı oluşturucuda diğer diğer adlara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="23d9a-112">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>
- <span data-ttu-id="23d9a-113">Aynı satır oluşturucusunun iki ifadesi aynı diğer ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="23d9a-113">Two expressions in the same row constructor cannot have the same alias.</span></span>

<span data-ttu-id="23d9a-114">Satır oluşturucular hakkında daha fazla bilgi için bkz. [Row](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23d9a-114">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>

## <a name="collection-constructors"></a><span data-ttu-id="23d9a-115">Koleksiyon oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="23d9a-115">Collection Constructors</span></span>

<span data-ttu-id="23d9a-116">' De koleksiyon oluşturucuları kullanarak bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değer listesinden bir çoklu küme örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23d9a-116">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="23d9a-117">Oluşturucudaki tüm değerler karşılıklı olarak uyumlu türde olmalıdır `T` ve Oluşturucu türünde bir koleksiyon oluşturur `Multiset<T>` .</span><span class="sxs-lookup"><span data-stu-id="23d9a-117">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="23d9a-118">Örneğin, aşağıdaki ifade bir tamsayılar koleksiyonu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="23d9a-118">For example, the following expression creates a collection of integers:</span></span>

`Multiset(1, 2, 3)`

`{1, 2, 3}`

<span data-ttu-id="23d9a-119">Öğelerin türü belirlenemediğinden boş çok kümeli oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="23d9a-119">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="23d9a-120">Aşağıdakiler geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="23d9a-120">The following is not valid:</span></span>

`multiset() {}`

<span data-ttu-id="23d9a-121">Daha fazla bilgi için bkz. [Çoklu küme](multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23d9a-121">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>

## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="23d9a-122">Adlandırılmış tür oluşturucuları (NamedType başlatıcıları)</span><span class="sxs-lookup"><span data-stu-id="23d9a-122">Named Type Constructors (NamedType Initializers)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="23d9a-123">adlandırılmış karmaşık türlerin ve varlık türlerinin örneklerini oluşturmak için tür oluşturucuların (başlatıcılar) kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="23d9a-123">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="23d9a-124">Örneğin, aşağıdaki ifade bir türün örneğini oluşturur `Person` .</span><span class="sxs-lookup"><span data-stu-id="23d9a-124">For example, the following expression creates an instance of a `Person` type.</span></span>

`Person("abc", 12)`

<span data-ttu-id="23d9a-125">Aşağıdaki ifade, karmaşık bir türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23d9a-125">The following expression creates an instance of a complex type.</span></span>

`MyModel.ZipCode(‘98118’, ‘4567’)`

<span data-ttu-id="23d9a-126">Aşağıdaki ifade, iç içe geçmiş karmaşık bir türün örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23d9a-126">The following expression creates an instance of a nested complex type.</span></span>

`MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`

<span data-ttu-id="23d9a-127">Aşağıdaki ifade, iç içe geçmiş karmaşık türe sahip bir varlık örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23d9a-127">The following expression creates an instance of an entity with a nested complex type.</span></span>

`MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`

<span data-ttu-id="23d9a-128">Aşağıdaki örnek, bir karmaşık türün özelliğinin null olarak nasıl başlatılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23d9a-128">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`

<span data-ttu-id="23d9a-129">Oluşturucunun bağımsız değişkenlerinin, türün özniteliklerinin bildirimiyle aynı sırada olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="23d9a-129">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>

<span data-ttu-id="23d9a-130">Daha fazla bilgi için bkz. [adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23d9a-130">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23d9a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23d9a-131">See also</span></span>

- [<span data-ttu-id="23d9a-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="23d9a-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="23d9a-133">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="23d9a-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="23d9a-134">Tür sistemi</span><span class="sxs-lookup"><span data-stu-id="23d9a-134">Type System</span></span>](type-system-entity-sql.md)
