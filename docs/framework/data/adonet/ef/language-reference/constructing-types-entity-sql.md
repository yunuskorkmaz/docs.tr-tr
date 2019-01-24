---
title: Oluşturma türleri (SQL varlık)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 917c59a6602ce0313b91ba78fd59d11596f86e9f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718591"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="44bc4-102">Oluşturma türleri (SQL varlık)</span><span class="sxs-lookup"><span data-stu-id="44bc4-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="44bc4-103">üç tür oluşturucular sağlar: Oluşturucular, adlandırılmış Tür oluşturucu ve koleksiyon oluşturucular satır.</span><span class="sxs-lookup"><span data-stu-id="44bc4-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="44bc4-104">Satır oluşturucular</span><span class="sxs-lookup"><span data-stu-id="44bc4-104">Row Constructors</span></span>  
 <span data-ttu-id="44bc4-105">Satır oluşturucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] anonim, yapısal olarak belirlenmiş bir veya daha fazla değer kayıtları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="44bc4-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="44bc4-106">Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerleri türlerine karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="44bc4-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="44bc4-107">Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="44bc4-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="44bc4-108">Row oluşturucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework bir çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="44bc4-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="44bc4-109">"Diğer ad kuralları" bölümünde daha fazla bilgi için bkz. [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44bc4-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="44bc4-110">Row oluşturucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="44bc4-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="44bc4-111">Row oluşturucusunda ifadeleri başka diğer adlar aynı oluşturucu içinde başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="44bc4-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="44bc4-112">Aynı row oluşturucusunda iki ifadeler aynı ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="44bc4-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="44bc4-113">Satır oluşturucular hakkında daha fazla bilgi için bkz. [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44bc4-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="44bc4-114">Koleksiyon oluşturucular</span><span class="sxs-lookup"><span data-stu-id="44bc4-114">Collection Constructors</span></span>  
 <span data-ttu-id="44bc4-115">Koleksiyon oluşturucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değerler listesinden bir çoklu küme örneği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="44bc4-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="44bc4-116">Oluşturucu tüm değerleri karşılıklı olarak uyumlu türünde olmalıdır `T`, oluşturucu türü bir koleksiyon oluşturur `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="44bc4-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="44bc4-117">Örneğin, aşağıdaki ifade, tamsayı bir koleksiyonunu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="44bc4-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="44bc4-118">Öğelerin türü belirlenemiyor çünkü boş multiset oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="44bc4-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="44bc4-119">Aşağıdakiler geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="44bc4-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="44bc4-120">Daha fazla bilgi için [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44bc4-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="44bc4-121">Adlandırılmış Tür oluşturucu (NamedType başlatıcılar)</span><span class="sxs-lookup"><span data-stu-id="44bc4-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="44bc4-122">tür oluşturucular (başlatıcılar adlandırılmış karmaşık türlerin örneklerini oluşturmak için) ve varlık türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44bc4-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="44bc4-123">Örneğin, aşağıdaki ifade bir örneği oluşturan bir `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="44bc4-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="44bc4-124">Aşağıdaki ifade, karmaşık bir türün örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44bc4-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="44bc4-125">Aşağıdaki ifade, iç içe geçmiş bir karmaşık türün örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44bc4-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="44bc4-126">Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlık örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44bc4-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="44bc4-127">Aşağıdaki örnek, bir karmaşık türü null bir özelliğini başlatmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44bc4-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="44bc4-128">Oluşturucusuna bağımsız değişken türü özniteliklerini bildirimi aynı sırada olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="44bc4-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="44bc4-129">Daha fazla bilgi için [adlandırılmış Tür oluşturucu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44bc4-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bc4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44bc4-130">See also</span></span>
- [<span data-ttu-id="44bc4-131">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="44bc4-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="44bc4-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="44bc4-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="44bc4-133">Tür Sistemi</span><span class="sxs-lookup"><span data-stu-id="44bc4-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
