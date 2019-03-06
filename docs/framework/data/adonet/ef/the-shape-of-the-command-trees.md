---
title: Komut ağaçlarının şekli
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: aba5511b8baa395714bde315d9542932e854c98b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378554"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="b4c6f-102">Komut ağaçlarının şekli</span><span class="sxs-lookup"><span data-stu-id="b4c6f-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="b4c6f-103">SQL üretimi modülü, belirli bir giriş sorgu komut ağacı ifadeye göre bir arka uç belirli SQL sorgusu oluşturmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="b4c6f-104">Bu bölüm, özellikleri, özellikler ve sorgu komut ağaçlarının yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="b4c6f-105">Sorgu komut ağaçlarını genel bakış</span><span class="sxs-lookup"><span data-stu-id="b4c6f-105">Query Command Trees Overview</span></span>

<span data-ttu-id="b4c6f-106">Bir sorgu komut ağacı bir sorgu nesne modeli gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="b4c6f-107">Sorgu komut ağaçlarını iki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="b4c6f-108">Giriş sorgusu karşı belirtilen ifade [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4c6f-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="b4c6f-109">Bir sağlayıcıya verilen ve arka uç yönelik bir sorgu açıklayan bir çıkış sorgu ifade etmek için.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="b4c6f-110">Komut ağaçlarını destekleyen SQL:1999 uyumlu sorguları, iç içe geçmiş koleksiyonlar ve bir varlığın belirli bir tür olup olmadığını denetlemeye veya kümeleri bir türüne göre filtreleme gibi tür işlemleri ile çalışmak için destek dahil olmak üzere daha zengin bir semantik sorgu.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="b4c6f-111">Sorgu mantığı tanımlayan bir ifade ağacı kök DBQueryCommandTree.Query özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="b4c6f-112">DBQueryCommandTree.Parameters özelliği sorguda kullanılan parametrelerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="b4c6f-113">İfade ağacı Dbexpression'dan nesnelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="b4c6f-114">Dbexpression'dan nesne bazı hesaplama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="b4c6f-115">Çeşitli türlerde ifadeler tarafından sağlanan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sabitleri dahil olmak üzere, sorgu ifadeleri oluşturmak için değişkenler, İşlevler, Oluşturucular ve standart ilişkisel işleçler gibi filtre ve birleştirme.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="b4c6f-116">Her Dbexpression'dan nesnesi bu ifade tarafından üretilen sonuç türü temsil eden bir resulttype'ı özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="b4c6f-117">Bu tür bir typeusage değeri ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="b4c6f-118">Çıkış sorgu komut ağacı şekilleri</span><span class="sxs-lookup"><span data-stu-id="b4c6f-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="b4c6f-119">Çıkış sorgu komut ağaçlarını yakından ilişkisel (SQL) sorguları ve sorgu komutu ağaçlarına geçerli olandan çok daha sıkı kurallarına bağlı kalmanızı.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="b4c6f-120">Bunlar genellikle SQL'e kolayca çevrilir yapıları içerir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="b4c6f-121">Gezinti özellikleri, devralma ve varlıklar arasındaki ilişkileri destekler kavramsal modeline karşı giriş komut ağaçlarını cinsinden ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="b4c6f-122">Çıkış komut ağaçlarını depolama modelinde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="b4c6f-123">Giriş komut ağaçlarını iç içe geçmiş koleksiyonlar proje olanak sağlar, ancak çıkış komut ağaçlarını yapın.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="b4c6f-124">Çıkış sorgu komut ağaçlarını kullanılabilir Dbexpression'dan nesneler kümesini kullanarak oluşturulur ve bu alt bile bazı ifadeler sınırlı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="b4c6f-125">Verilen ifade belirli bir tür olup olmadığını denetlemeye veya kümeleri bir türüne göre filtreleme gibi işlemleri türü, çıkış komut ağaçlarında mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="b4c6f-126">Çıkış komut ağaçlarında Boolean değerleri döndüren ifadeler projeksiyonlar ve yalnızca gerektiren bir filtre veya case ifadesi gibi bir koşul ifadeleri koşullarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="b4c6f-127">Bir çıkış sorgu komut ağaçlarını DbProjectExpression nesne köküdür.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="b4c6f-128">İfade türleri çıkış sorgu komutu ağaçlarında yok</span><span class="sxs-lookup"><span data-stu-id="b4c6f-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="b4c6f-129">Aşağıdaki ifade türleri içinde bir çıkış sorgu komut ağacı geçerli değil ve sağlayıcıları tarafından ele alınması gerekmez:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="b4c6f-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-130">DbDerefExpression</span></span>

- <span data-ttu-id="b4c6f-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="b4c6f-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="b4c6f-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-133">DbIsOfExpression</span></span>

- <span data-ttu-id="b4c6f-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="b4c6f-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-135">DbRefExpression</span></span>

- <span data-ttu-id="b4c6f-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="b4c6f-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="b4c6f-138">İfade kısıtlamalar ve notlar</span><span class="sxs-lookup"><span data-stu-id="b4c6f-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="b4c6f-139">Birçok ifadeleri yalnızca çıktı sorgu komut ağaçlarını sınırlı bir şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="b4c6f-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-140">DbFunctionExpression</span></span>

<span data-ttu-id="b4c6f-141">Aşağıdaki işlev türleri geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-141">The following function types can be passed:</span></span>

- <span data-ttu-id="b4c6f-142">Edm ad alanı tarafından tanınan kurallı işlevler.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="b4c6f-143">Yerleşik (Depolama) işlevler BuiltInAttribute tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="b4c6f-144">Kullanıcı tanımlı işlevler.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-144">User-defined functions.</span></span>

<span data-ttu-id="b4c6f-145">Kurallı işlevler (bkz [kurallı işlevler](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) daha fazla bilgi için) parçası olarak belirtilen [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], ve sağlayıcıları bu belirtimlerle uyarlanan kurallı işlevler için uygulamaları sağlamanız.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="b4c6f-146">Store işlevleri ilgili sağlayıcı bildirimi özelliklere dayanır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="b4c6f-147">Kullanıcı tanımlı işlevleri SSDL teknik özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="b4c6f-148">Ayrıca, NiladicFunction özniteliğine sahip işlevleri bağımsız değişken yoktur ve sonunda parantez olmadan çevrilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="b4c6f-149">Diğer bir deyişle,  *\<functionName >* yerine  *\<functionName > ()*.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="b4c6f-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="b4c6f-151">Dbnewınstanceexpression, yalnızca aşağıdaki iki durumlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="b4c6f-152">Projeksiyon DbProjectExpression özelliği.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="b4c6f-153">Bu şekilde kullanıldığında aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b4c6f-153">When used as such the following restrictions apply:</span></span>

    - <span data-ttu-id="b4c6f-154">Sonuç türü satır türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-154">The result type must be a row type.</span></span>

    - <span data-ttu-id="b4c6f-155">Her bağımsız değişkenlerinden biri, bir basit türü ile bir sonuç üretir bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="b4c6f-156">Genellikle, her bağımsız değişken bir DbVariableReferenceExpression veya bir işlev çağrısını bir DbVariableReferenceExpression, bir işlev çağırma veya bir aritmetik hesaplaması DbPropertyExpression üzerinden bir PropertyExpression gibi skaler bir ifade. .</span><span class="sxs-lookup"><span data-stu-id="b4c6f-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="b4c6f-157">Ancak, skaler bir sorgu temsil eden bir ifade bir Dbnewınstanceexpression için bağımsız değişken listesinde de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="b4c6f-158">Skaler bir sorgu temsil eden bir ifade olan tam olarak bir satır ve tek sütunlu bir DbElementExpression nesne kök ile temel bir tür döndüren sorgu temsil eden bir ifade ağacı</span><span class="sxs-lookup"><span data-stu-id="b4c6f-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="b4c6f-159">Bir koleksiyon dönüş türüyle bu durumda, yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="b4c6f-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="b4c6f-161">Bir DbVariableReferenceExpression DbPropertyExpression düğümün alt öğesi bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="b4c6f-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-162">DbGroupByExpression</span></span>

<span data-ttu-id="b4c6f-163">Bir DbGroupByExpression'ın toplamalar özelliği yalnızca DbFunctionAggregate türünde öğelere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="b4c6f-164">Başka bir toplama türü vardır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="b4c6f-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-165">DbLimitExpression</span></span>

<span data-ttu-id="b4c6f-166">Sınır özelliği yalnızca bir DbConstantExpression veya bir DbParameterReferenceExpression olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="b4c6f-167">Ayrıca WithTies her zaman false .NET Framework 3.5 sürümü itibarıyla özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="b4c6f-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="b4c6f-168">DbScanExpression</span></span>

<span data-ttu-id="b4c6f-169">Çıkış komut ağaçlarında kullanıldığında DbScanExpression etkili bir şekilde bir tarama bir tablo, görünüm veya EntitySetBase::Target tarafından temsil edilen bir depo sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="b4c6f-170">Bir sorgu temsil eder hedefinin "sorgu tanımlama" meta veri özelliği null olmayan, ise, hangi sorgu metni meta veri deposu şeması tanımında belirtilen sağlayıcının belirli bir dil (veya diyalekti) özelliğinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="b4c6f-171">Aksi takdirde, hedef, bir tablo veya Görünüm temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="b4c6f-172">Ya da "Şema" meta veri özelliği, şema ön ekidir değilse varlık kapsayıcı adı null; Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="b4c6f-173">Tablo veya Görünüm adı ya da "Tablo" meta veri özelliği değilse varlık adı özniteliğinin temel ayarlayın, aksi halde null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="b4c6f-174">Tüm bu özellikler, depo şeması tanım dosyasında (SSDL) karşılık gelen Entityset'i tanımını kaynaklanan.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="b4c6f-175">İlkel türler kullanma</span><span class="sxs-lookup"><span data-stu-id="b4c6f-175">Using Primitive Types</span></span>

<span data-ttu-id="b4c6f-176">İlkel türler çıkış komut ağaçlarında başvurulduğunda, bunlar genellikle kavramsal modelin ilkel türlerinde başvurulur.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="b4c6f-177">Ancak, belirli ifadeler için karşılık gelen depolama ilkel tür sağlayıcıları gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="b4c6f-178">Sağlayıcı null karşılık gelen türe dönüştürme gerekiyorsa DbCastExpression ve büyük olasılıkla DbNullExpression, bu tür ifadeleri örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="b4c6f-179">Bu gibi durumlarda sağlayıcıları, ilkel tür türü ve kendi modelleri göre sağlayıcı türü için eşleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4c6f-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4c6f-180">See also</span></span>

- [<span data-ttu-id="b4c6f-181">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="b4c6f-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
