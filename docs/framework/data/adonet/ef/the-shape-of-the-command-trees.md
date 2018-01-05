---
title: "Komut ağaçlarını şekli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 13e2e154a96b46d630b6df11fe3ae024d799c8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="91a86-102">Komut ağaçlarını şekli</span><span class="sxs-lookup"><span data-stu-id="91a86-102">The Shape of the Command Trees</span></span>
<span data-ttu-id="91a86-103">SQL oluşturma modülü, belirtilen giriş sorgu komut ağacı ifadesi temelinde bir arka uç belirli SQL sorgusu oluşturmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="91a86-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="91a86-104">Bu bölüm, özellikleri, özellikleri ve sorgu komut ağaçlarını yapısını anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91a86-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>  
  
## <a name="query-command-trees-overview"></a><span data-ttu-id="91a86-105">Sorgu komut ağaçlarını genel bakış</span><span class="sxs-lookup"><span data-stu-id="91a86-105">Query Command Trees Overview</span></span>  
 <span data-ttu-id="91a86-106">Bir sorgu komut ağacındaki bir sorguda nesne modeli gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="91a86-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="91a86-107">Sorgu komut ağaçlarını iki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="91a86-107">Query command trees serve two purposes:</span></span>  
  
-   <span data-ttu-id="91a86-108">Karşı belirtilen bir giriş sorgu ifade etmek için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91a86-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="91a86-109">Bir sağlayıcıya verilen ve arka uç yönelik bir sorgu açıklayan bir çıktı sorgu ifade etmek için.</span><span class="sxs-lookup"><span data-stu-id="91a86-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>  
  
 <span data-ttu-id="91a86-110">Query ağaçları SQL:1999 uyumlu sorgular, iç içe geçmiş koleksiyonlar ve türü işlemleri, bir varlığın belirli bir tür olup olmadığını denetleme veya kümeleri türüne göre filtreleme gibi ile çalışmak için destek dahil olmak üzere daha zengin semantiğini desteklemek komutu.</span><span class="sxs-lookup"><span data-stu-id="91a86-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>  
  
 <span data-ttu-id="91a86-111">Sorgu mantığını tanımlayan ifade ağacına kökündeki DBQueryCommandTree.Query özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="91a86-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="91a86-112">DBQueryCommandTree.Parameters özelliği sorguda kullanılan parametrelerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="91a86-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="91a86-113">İfade ağacına DbExpression nesnelerin oluşur.</span><span class="sxs-lookup"><span data-stu-id="91a86-113">The expression tree is composed of DbExpression objects.</span></span>  
  
 <span data-ttu-id="91a86-114">DbExpression nesnesi bazı hesaplama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91a86-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="91a86-115">Çeşitli türlerde ifadeleri tarafından sağlanan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sabitleri dahil olmak üzere sorgu ifadeleri oluşturmak için değişkenler, İşlevler, Oluşturucular ve standart ilişkisel işleçler gibi filtre ve birleştirme.</span><span class="sxs-lookup"><span data-stu-id="91a86-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="91a86-116">Her DbExpression nesnesi bu deyim tarafından üretilen sonuç türü gösteren bir ResultType özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="91a86-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="91a86-117">Bu tür bir TypeUsage ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="91a86-117">This type is expressed as a TypeUsage.</span></span>  
  
## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="91a86-118">Çıktı sorgu komut ağacı şekilleri</span><span class="sxs-lookup"><span data-stu-id="91a86-118">Shapes of the Output Query Command Tree</span></span>  
 <span data-ttu-id="91a86-119">Çıktı sorgu komut ağaçlarını yakından ilişkili (SQL) sorguları temsil eder ve sorgu komut ağaçlarını geçerli olandan çok daha sıkı kurallar uygun.</span><span class="sxs-lookup"><span data-stu-id="91a86-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="91a86-120">Bunlar genellikle SQL kolayca çevrilir yapılar içerir.</span><span class="sxs-lookup"><span data-stu-id="91a86-120">They typically contain constructs that are easily translated to SQL.</span></span>  
  
 <span data-ttu-id="91a86-121">Giriş komut ağaçlarını Gezinti özellikleri, varlıkların ve devralma arasındaki ilişkileri destekler kavramsal model karşı ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="91a86-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="91a86-122">Çıkış komut ağaçlarını depolama modeline göre belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="91a86-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="91a86-123">Giriş komut ağaçlarını proje iç içe geçmiş koleksiyonları olanak sağlar, ancak çıktı komut ağaçlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="91a86-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>  
  
 <span data-ttu-id="91a86-124">Çıktı sorgu komut ağaçlarını kullanılabilir DbExpression nesneler kümesini kullanılarak oluşturulur ve bu alt bile bazı ifadelerinde sınırlı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="91a86-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>  
  
 <span data-ttu-id="91a86-125">Verilen ifade belirli bir tür olup olmadığını denetleme veya kümeleri türüne göre filtreleme gibi türü işlemler, çıktı komut ağaçlarında yok.</span><span class="sxs-lookup"><span data-stu-id="91a86-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>  
  
 <span data-ttu-id="91a86-126">Çıkış komutu ağaçlarında Boole değerleri döndüren ifadeler tahminleri ve yalnızca bir filtre veya case deyimi gibi bir koşul gerektiren ifadeleri koşullarında için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91a86-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>  
  
 <span data-ttu-id="91a86-127">Bir çıkış sorgu komut ağaçlarını kökündeki DbProjectExpression nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="91a86-127">The root of an output query command trees is a DbProjectExpression object.</span></span>  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="91a86-128">İfade türleri çıkış sorgu komutu ağaçlarında yok</span><span class="sxs-lookup"><span data-stu-id="91a86-128">Expression Types Not Present in Output Query Command Trees</span></span>  
 <span data-ttu-id="91a86-129">Aşağıdaki ifade türleri bir çıktı sorgu komutu ağacında geçerli değildir ve sağlayıcıları tarafından yapılması gerekmez:</span><span class="sxs-lookup"><span data-stu-id="91a86-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>  
  
 <span data-ttu-id="91a86-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-130">DbDerefExpression</span></span>  
  
 <span data-ttu-id="91a86-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-131">DbEntityRefExpression</span></span>  
  
 <span data-ttu-id="91a86-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-132">DbRefKeyExpression</span></span>  
  
 <span data-ttu-id="91a86-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-133">DbIsOfExpression</span></span>  
  
 <span data-ttu-id="91a86-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-134">DbOfTypeExpression</span></span>  
  
 <span data-ttu-id="91a86-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-135">DbRefExpression</span></span>  
  
 <span data-ttu-id="91a86-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-136">DbRelationshipNavigationExpression</span></span>  
  
 <span data-ttu-id="91a86-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-137">DbTreatExpression</span></span>  
  
### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="91a86-138">İfade kısıtlamaları ve notlar</span><span class="sxs-lookup"><span data-stu-id="91a86-138">Expression Restrictions and Notes</span></span>  
 <span data-ttu-id="91a86-139">Birçok ifadeleri yalnızca çıktı sorgu komut ağaçlarını sınırlı bir şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="91a86-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>  
  
#### <a name="dbfunctionexpression"></a><span data-ttu-id="91a86-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-140">DbFunctionExpression</span></span>  
 <span data-ttu-id="91a86-141">Aşağıdaki işlev türleri geçirilebilir:</span><span class="sxs-lookup"><span data-stu-id="91a86-141">The following function types can be passed:</span></span>  
  
-   <span data-ttu-id="91a86-142">Edm ad alanı tarafından tanınan kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="91a86-142">Canonical functions that are recognized by the Edm namespace.</span></span>  
  
-   <span data-ttu-id="91a86-143">BuiltInAttribute tarafından tanınan yerleşik (Depolama) çalışır.</span><span class="sxs-lookup"><span data-stu-id="91a86-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>  
  
-   <span data-ttu-id="91a86-144">Kullanıcı tanımlı işlevler.</span><span class="sxs-lookup"><span data-stu-id="91a86-144">User-defined functions.</span></span>  
  
 <span data-ttu-id="91a86-145">Kurallı işlevleri (bkz [kurallı işlevleri](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) daha fazla bilgi için) parçası olarak belirtilen [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], ve sağlayıcıları bu belirtimlerle uyarlanan kurallı işlevleri için uygulamaları sağlamanız.</span><span class="sxs-lookup"><span data-stu-id="91a86-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="91a86-146">Depo işlevleri karşılık gelen sağlayıcı bildiriminde belirtimlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="91a86-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="91a86-147">Kullanıcı tanımlı işlevler SSDL belirtimlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="91a86-147">User defined functions are based on specifications in the SSDL.</span></span>  
  
 <span data-ttu-id="91a86-148">Ayrıca, işlevleri NiladicFunction özniteliğine sahip bağımsız değişken yoktur ve sonunda parantez olmadan çevrilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a86-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="91a86-149">Diğer bir deyişle,  *\<functionName >* yerine  *\<functionName > ()*.</span><span class="sxs-lookup"><span data-stu-id="91a86-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>  
  
#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="91a86-150">Dbnewınstanceexpression</span><span class="sxs-lookup"><span data-stu-id="91a86-150">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="91a86-151">Dbnewınstanceexpression, yalnızca aşağıdaki iki durumlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="91a86-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>  
  
-   <span data-ttu-id="91a86-152">DbProjectExpression projeksiyon özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="91a86-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="91a86-153">Bu nedenle kullanıldığında aşağıdaki kısıtlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="91a86-153">When used as such the following restrictions apply:</span></span>  
  
    -   <span data-ttu-id="91a86-154">Sonuç türü bir satır türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91a86-154">The result type must be a row type.</span></span>  
  
    -   <span data-ttu-id="91a86-155">Bağımsız değişkenlerinin her birini bir ilkel tür bir sonuçla üreten bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="91a86-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="91a86-156">Genellikle, her bir bağımsız değişkeni bir DbVariableReferenceExpression veya bir işlev çağrısını bir DbVariableReferenceExpression, bir işlev çağrısını ya da bir aritmetik hesaplaması DbPropertyExpression üzerinden PropertyExpression gibi skaler bir ifade. .</span><span class="sxs-lookup"><span data-stu-id="91a86-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="91a86-157">Ancak, skaler bir alt sorgu temsil eden bir ifade da bir Dbnewınstanceexpression için bağımsız değişkenlerin listesini ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="91a86-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="91a86-158">Tam olarak bir satır ve DbElementExperession nesne kök ile temel bir türünde bir sütun döndüren bir alt sorgu temsil eden bir ifade ağacına skaler bir alt sorgu temsil eden bir ifade değil</span><span class="sxs-lookup"><span data-stu-id="91a86-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExperession object root</span></span>  
  
-   <span data-ttu-id="91a86-159">Bir koleksiyon dönüş türüyle bu durumda, yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91a86-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>  
  
#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="91a86-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-160">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="91a86-161">Bir DbVariableReferenceExpression DbPropertyExpression düğümün alt öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a86-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>  
  
#### <a name="dbgroupbyexpression"></a><span data-ttu-id="91a86-162">Bir DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-162">DbGroupByExpression</span></span>  
 <span data-ttu-id="91a86-163">Bir dbgroupbyexpression toplamalar özelliği yalnızca DbFunctionAggregate türündeki öğeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="91a86-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="91a86-164">Başka bir toplama türü vardır.</span><span class="sxs-lookup"><span data-stu-id="91a86-164">There are no other aggregate types.</span></span>  
  
#### <a name="dblimitexpression"></a><span data-ttu-id="91a86-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-165">DbLimitExpression</span></span>  
 <span data-ttu-id="91a86-166">Sınır özelliği yalnızca bir DbConstantExpression veya DbParameterReferenceExpression olabilir.</span><span class="sxs-lookup"><span data-stu-id="91a86-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="91a86-167">Ayrıca WithTies her zaman, .NET Framework 3.5 sürümünü itibariyle false özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="91a86-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>  
  
#### <a name="dbscanexpression"></a><span data-ttu-id="91a86-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="91a86-168">DbScanExpression</span></span>  
 <span data-ttu-id="91a86-169">Çıkış komutu ağaçlarında kullanıldığında, DbScanExpression etkili bir şekilde bir tarama bir tablo, bir görünüm veya EnitySetBase::Target tarafından temsil edilen bir deposu sorgusu üzerinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91a86-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EnitySetBase::Target.</span></span>  
  
 <span data-ttu-id="91a86-170">Bir sorgu temsil eden hedef "sorgu tanımlama" meta veri özelliği boş ise, hangi sorgu metnini depo şeması tanım belirtildiği gibi sağlayıcının belirli bir dil (veya dialect) bu meta veri özelliği sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91a86-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>  
  
 <span data-ttu-id="91a86-171">Aksi takdirde, hedef bir tablo veya Görünüm temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91a86-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="91a86-172">Kendi şema önekini ya da "Şema" meta veri özelliği, olmasa bile kapsayıcı adı boş, aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="91a86-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="91a86-173">Tablo veya Görünüm adı ya da "Tablo" meta veri özelliği değilse varlığı adını temel ayarlayın, aksi halde null ' dir.</span><span class="sxs-lookup"><span data-stu-id="91a86-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>  
  
 <span data-ttu-id="91a86-174">Bu özellikleri depo şeması tanım dosyasındaki (SSDL) karşılık gelen EntitySet tanımını kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="91a86-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>  
  
### <a name="using-primitive-types"></a><span data-ttu-id="91a86-175">İlkel türler kullanma</span><span class="sxs-lookup"><span data-stu-id="91a86-175">Using Primitive Types</span></span>  
 <span data-ttu-id="91a86-176">İlkel türler çıkış komut ağaçlarında başvurulduğunda genellikle kavramsal modelin ilkel türlerinde başvurulur.</span><span class="sxs-lookup"><span data-stu-id="91a86-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="91a86-177">Ancak, belirli ifadeleri için karşılık gelen deposu ilkel tür sağlayıcıları gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a86-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="91a86-178">Sağlayıcı null değerine karşılık gelen tür cast gerekiyorsa, bu tür örnekleri DbCastExpression ve büyük olasılıkla DbNullExpression, içerir.</span><span class="sxs-lookup"><span data-stu-id="91a86-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="91a86-179">Bu durumlarda, sağlayıcıları, ilkel türü türü ve onun modelleri göre sağlayıcı türü için eşleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91a86-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a86-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91a86-180">See Also</span></span>  
 [<span data-ttu-id="91a86-181">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="91a86-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
