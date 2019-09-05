---
title: Komut Ağaçlarının Şekli
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248218"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="442a1-102">Komut Ağaçlarının Şekli</span><span class="sxs-lookup"><span data-stu-id="442a1-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="442a1-103">SQL oluşturma modülü, belirli bir giriş sorgusu komut ağacı ifadesine göre arka uca özel SQL sorgusu oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="442a1-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="442a1-104">Bu bölümde sorgu komut ağaçlarının özellikleri, özellikleri ve yapısı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="442a1-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="442a1-105">Sorgu komut ağaçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="442a1-105">Query Command Trees Overview</span></span>

<span data-ttu-id="442a1-106">Sorgu komut ağacı bir sorgunun nesne modeli gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="442a1-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="442a1-107">Sorgu komut ağaçları iki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="442a1-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="442a1-108">Öğesine göre [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]belirtilen bir giriş sorgusunu ifade etmek için.</span><span class="sxs-lookup"><span data-stu-id="442a1-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="442a1-109">Bir sağlayıcıya verilen bir çıkış sorgusunu ifade etmek ve arka uca yönelik bir sorgu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="442a1-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="442a1-110">Sorgu komut ağaçları, iç içe geçmiş Koleksiyonlar ve tür işlemleriyle çalışma desteği de dahil olmak üzere, bir varlığın belirli bir türde olup olmadığını kontrol etme ya da bir türe göre filtreleme kümeleri gibi SQL: 1999 uyumlu sorgulardan daha zengin semantiğini destekler.</span><span class="sxs-lookup"><span data-stu-id="442a1-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="442a1-111">DBQueryCommandTree. Query özelliği, sorgu mantığını tanımlayan ifade ağacının köküdür.</span><span class="sxs-lookup"><span data-stu-id="442a1-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="442a1-112">DBQueryCommandTree. Parameters özelliği, sorguda kullanılan parametrelerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="442a1-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="442a1-113">İfade ağacı DbExpression nesnelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="442a1-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="442a1-114">DbExpression nesnesi bazı hesaplamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="442a1-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="442a1-115">Birçok ifade türü, sabitleri, değişkenleri, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] işlevleri, oluşturucuları ve Filter ve JOIN gibi standart İlişkisel işleçleri içeren sorgu ifadeleri oluşturmak için tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="442a1-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="442a1-116">Her DbExpression nesnesinin, bu ifade tarafından üretilen sonucun türünü temsil eden bir ResultType özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="442a1-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="442a1-117">Bu tür bir TypeUsage olarak ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="442a1-118">Çıkış sorgusu komut ağacının şekilleri</span><span class="sxs-lookup"><span data-stu-id="442a1-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="442a1-119">Çıkış sorgusu komut ağaçları, ilişkisel (SQL) sorgularını yakından temsil eder ve sorgu komut ağaçları için uygulananlardan daha sıkı kurallara uyar.</span><span class="sxs-lookup"><span data-stu-id="442a1-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="442a1-120">Genellikle SQL 'e kolayca çevrilmiş yapılar içerir.</span><span class="sxs-lookup"><span data-stu-id="442a1-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="442a1-121">Giriş komut ağaçları, gezinti özelliklerini, varlıklar arasındaki ilişkilendirmeleri ve devralmayı destekleyen kavramsal modele göre ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="442a1-122">Çıkış komut ağaçları, depolama modeline göre ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="442a1-123">Giriş komut ağaçları, iç içe geçmiş koleksiyonları proje yapmanıza izin verir, ancak çıkış komut ağaçları değildir.</span><span class="sxs-lookup"><span data-stu-id="442a1-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="442a1-124">Çıkış sorgusu komut ağaçları, kullanılabilir DbExpression nesnelerinin bir alt kümesi kullanılarak oluşturulur ve hatta söz konusu alt kümedeki bazı ifadelerin kısıtlı kullanımı vardır.</span><span class="sxs-lookup"><span data-stu-id="442a1-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="442a1-125">Belirli bir ifadenin belirli bir türde olup olmadığını veya bir türe göre filtreleme kümelerini denetlemek gibi tür işlemleri çıkış komut ağaçlarında mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="442a1-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="442a1-126">Çıkış komut ağaçlarında, yalnızca bir filtre veya bir Case deyimi gibi bir koşul gerektiren deyimlerdeki koşullara göre yalnızca Boole değerleri döndüren ifadeler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="442a1-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="442a1-127">Çıkış sorgusu komut ağaçlarının kökü bir DbProjectExpression nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="442a1-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="442a1-128">Çıkış sorgusunda ifade türleri yok komut ağaçları</span><span class="sxs-lookup"><span data-stu-id="442a1-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="442a1-129">Aşağıdaki ifade türleri bir çıkış sorgusu komut ağacında geçerli değildir ve sağlayıcılar tarafından işlenmemelidir:</span><span class="sxs-lookup"><span data-stu-id="442a1-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="442a1-130">DbDerefExpression başvuru türünde</span><span class="sxs-lookup"><span data-stu-id="442a1-130">DbDerefExpression</span></span>

- <span data-ttu-id="442a1-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="442a1-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="442a1-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-133">DbIsOfExpression</span></span>

- <span data-ttu-id="442a1-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="442a1-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-135">DbRefExpression</span></span>

- <span data-ttu-id="442a1-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="442a1-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="442a1-138">İfade kısıtlamaları ve notları</span><span class="sxs-lookup"><span data-stu-id="442a1-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="442a1-139">Birçok ifade yalnızca çıkış sorgusu komut ağaçlarında kısıtlı bir şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="442a1-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="442a1-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-140">DbFunctionExpression</span></span>

<span data-ttu-id="442a1-141">Aşağıdaki işlev türleri geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="442a1-141">The following function types can be passed:</span></span>

- <span data-ttu-id="442a1-142">EDM ad alanı tarafından tanınan kurallı işlevler.</span><span class="sxs-lookup"><span data-stu-id="442a1-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="442a1-143">Buıltedattribute tarafından tanınan yerleşik (mağaza) işlevler.</span><span class="sxs-lookup"><span data-stu-id="442a1-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="442a1-144">Kullanıcı tanımlı işlevler.</span><span class="sxs-lookup"><span data-stu-id="442a1-144">User-defined functions.</span></span>

<span data-ttu-id="442a1-145">Kurallı işlevler (daha fazla bilgi için [kurallı işlevlere](./language-reference/canonical-functions.md) bakın), [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]öğesinin bir parçası olarak belirtilir ve sağlayıcılar bu belirtimlere göre kurallı işlevlere yönelik uygulamalar sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="442a1-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="442a1-146">Mağaza işlevleri, karşılık gelen sağlayıcı bildiriminde yer alan belirtimlere göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="442a1-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="442a1-147">Kullanıcı tanımlı işlevler SSDL içindeki belirtimlere dayanır.</span><span class="sxs-lookup"><span data-stu-id="442a1-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="442a1-148">Ayrıca, NiladicFunction özniteliğine sahip işlevlerin bağımsız değişkeni yoktur ve sonda parantez olmadan çevrilmelidir.</span><span class="sxs-lookup"><span data-stu-id="442a1-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="442a1-149">Diğer bir deyişle,  *\<* fonksiyonadı  *\<> ()* yerine fonksiyonadı >.</span><span class="sxs-lookup"><span data-stu-id="442a1-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="442a1-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="442a1-151">DbNewInstanceExpression oluşturamıyor yalnızca aşağıdaki iki durumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="442a1-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="442a1-152">DbProjectExpression 'ın Projection özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="442a1-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="442a1-153">Bu şekilde kullanıldığında, aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="442a1-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="442a1-154">Sonuç türü bir satır türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="442a1-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="442a1-155">Bağımsız değişkenlerinin her biri, temel bir türle bir sonuç üreten bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="442a1-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="442a1-156">Genellikle, her bağımsız değişken bir DbVariableReferenceExpression üzerinde bir PropertyExpression, bir işlev çağırma veya bir DbVariableReferenceExpression ya da işlev çağırma üzerinden DbPropertyExpression 'ın aritmetik bir hesaplaması gibi bir skaler ifadedir .</span><span class="sxs-lookup"><span data-stu-id="442a1-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="442a1-157">Ancak, bir DbNewInstanceExpression oluşturamıyor için bağımsız değişkenler listesinde skaler bir alt sorguyu temsil eden bir ifade da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="442a1-158">Skaler bir alt sorguyu temsil eden bir ifade, tam olarak bir satır ve bir basit türün bir sütununu DbElementExpression nesne köküyle döndüren bir alt sorguyu temsil eden bir ifade ağacıdır</span><span class="sxs-lookup"><span data-stu-id="442a1-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="442a1-159">Koleksiyon dönüş türü ile, bu durumda bağımsız değişkenler olarak sunulan ifadelerin yeni bir koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="442a1-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="442a1-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="442a1-161">Bir DbVariableReferenceExpression, DbPropertyExpression düğümünün bir alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="442a1-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="442a1-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-162">DbGroupByExpression</span></span>

<span data-ttu-id="442a1-163">Bir DbGroupByExpression 'ın toplamalar özelliği yalnızca DbFunctionAggregate türünde öğelere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="442a1-164">Başka bir toplama türü yok.</span><span class="sxs-lookup"><span data-stu-id="442a1-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="442a1-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-165">DbLimitExpression</span></span>

<span data-ttu-id="442a1-166">Özellik sınırı yalnızca bir DbConstantExpression veya DbParameterReferenceExpression olabilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="442a1-167">Ayrıca özellik özellikleri, .NET Framework sürüm 3,5 itibariyle her zaman false 'tur.</span><span class="sxs-lookup"><span data-stu-id="442a1-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="442a1-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="442a1-168">DbScanExpression</span></span>

<span data-ttu-id="442a1-169">Çıkış komut ağaçlarında kullanıldığında, DbScanExpression bir tablo, görünüm veya bir depolama sorgusu üzerinde EntitySetBase:: Target ile temsil edilen bir taramayı etkin bir şekilde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="442a1-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="442a1-170">Hedefin "sorgu tanımlama" meta veri özelliği null değilse, bir sorguyu temsil eder ve bu meta veri özelliğinde, depo şeması tanımında belirtilen dilde (veya diyalekt) belirtilen sorgu metni.</span><span class="sxs-lookup"><span data-stu-id="442a1-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="442a1-171">Aksi takdirde, hedef bir tabloyu veya görünümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="442a1-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="442a1-172">Şema ön eki, null değilse "Schema" meta veri özelliğinde bulunur, aksi takdirde varlık kapsayıcısı adıdır.</span><span class="sxs-lookup"><span data-stu-id="442a1-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="442a1-173">Tablo veya Görünüm adı, null değilse "Table" meta veri özelliğidir, aksi takdirde varlık kümesi tabanının Name özelliği olur.</span><span class="sxs-lookup"><span data-stu-id="442a1-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="442a1-174">Tüm bu özellikler, depo şeması tanım dosyasındaki (SSDL) karşılık gelen EntitySet 'in tanımından kaynaklanacak.</span><span class="sxs-lookup"><span data-stu-id="442a1-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="442a1-175">Temel türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="442a1-175">Using Primitive Types</span></span>

<span data-ttu-id="442a1-176">Çıkış komut ağaçlarında temel türlere başvurulduklarında, bunlara genellikle kavramsal modelin ilkel türlerinde başvurulur.</span><span class="sxs-lookup"><span data-stu-id="442a1-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="442a1-177">Ancak, bazı ifadelerde sağlayıcılara karşılık gelen depo temel türü gerekir.</span><span class="sxs-lookup"><span data-stu-id="442a1-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="442a1-178">Bu tür ifadelere örnek olarak, sağlayıcının null değeri karşılık gelen türe ataması gerekiyorsa DbCastExpression ve muhtemelen Dbsnullexpression sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="442a1-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="442a1-179">Bu durumlarda, sağlayıcılar temel tür türü ve onun modellerini temel alan sağlayıcı türüyle eşlemeyi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="442a1-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="442a1-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="442a1-180">See also</span></span>

- [<span data-ttu-id="442a1-181">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="442a1-181">SQL Generation</span></span>](sql-generation.md)
