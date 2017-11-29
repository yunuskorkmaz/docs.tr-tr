---
title: "Türler (varlık SQL) oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 48dab533e26d6353c29667d81ea547f4b15d280f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="b7b0d-102">Türler (varlık SQL) oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7b0d-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b7b0d-103">üç tür oluşturucular sağlar: satır Oluşturucular, adlandırılmış türü oluşturucuları ve koleksiyon oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-103"> provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="b7b0d-104">Satır oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b7b0d-104">Row Constructors</span></span>  
 <span data-ttu-id="b7b0d-105">Satır kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="b7b0d-106">Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerlerin türleri için karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="b7b0d-107">Örneğin, aşağıdaki deyim türünde bir değer oluşturur `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="b7b0d-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="b7b0d-108">Row kurucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework oluşturur dener.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="b7b0d-109">Daha fazla bilgi için bkz: "Diğer ad kuralları" bölümünde [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0d-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="b7b0d-110">Row kurucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b7b0d-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="b7b0d-111">Bir satır oluşturucusunda ifadelerinde başka diğer adlar aynı oluşturucuda başvuruda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="b7b0d-112">İki ifadeye aynı row kurucusunda aynı ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="b7b0d-113">Satır oluşturucular hakkında daha fazla bilgi için bkz: [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0d-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="b7b0d-114">Koleksiyon oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b7b0d-114">Collection Constructors</span></span>  
 <span data-ttu-id="b7b0d-115">Koleksiyon kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değerler listesinden bir çoklu küme örneği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="b7b0d-116">Oluşturucu tüm değerleri karşılıklı olarak uyumlu türünde olmalıdır `T`, ve Oluşturucusu türünden bir koleksiyona üretir `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="b7b0d-117">Örneğin, aşağıdaki ifade tamsayılar bir koleksiyonunu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b7b0d-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="b7b0d-118">Boş multiset oluşturucular öğelerin türü belirlenemediğinden izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="b7b0d-119">Şu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="b7b0d-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="b7b0d-120">Daha fazla bilgi için bkz: [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0d-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="b7b0d-121">Adlandırılmış türü oluşturucuları (NamedType başlatıcıları)</span><span class="sxs-lookup"><span data-stu-id="b7b0d-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b7b0d-122">türü oluşturucuları (adlandırılmış karmaşık türlerin örnekleri oluşturmak için başlatıcıları) ve varlık türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-122"> allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="b7b0d-123">Örneğin, aşağıdaki ifade bir örneğini oluşturur bir `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="b7b0d-124">Aşağıdaki ifade, karmaşık türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="b7b0d-125">Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="b7b0d-126">Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlığın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="b7b0d-127">Aşağıdaki örnek, bir özellik NULL karmaşık türün başlatmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="b7b0d-128">Oluşturucu bağımsız değişken türü özniteliklerini bildirimi aynı sırada olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="b7b0d-129">Daha fazla bilgi için bkz: [adlı Tür oluşturucu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0d-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b0d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-130">See Also</span></span>  
 [<span data-ttu-id="b7b0d-131">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7b0d-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b7b0d-132">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="b7b0d-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="b7b0d-133">Tür sistemi</span><span class="sxs-lookup"><span data-stu-id="b7b0d-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
