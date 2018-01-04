---
title: "Değişiklik SQL oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ed5c6fd4e8bdbf148a57401163936631236b46b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modification-sql-generation"></a><span data-ttu-id="6dc0a-102">Değişiklik SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc0a-102">Modification SQL Generation</span></span>
<span data-ttu-id="6dc0a-103">Bu bölüm için değiştirme SQL oluşturma modülü geliştirmek nasıl anlatır, (SQL:1999-uyumlu bir veritabanına) sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="6dc0a-104">Bu modül, uygun SQL INSERT, UPDATE veya DELETE deyimleri değişikliği komut ağacı çevirmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="6dc0a-105">Select deyimi için SQL oluşturma hakkında daha fazla bilgi için bkz: [SQL üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="6dc0a-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="6dc0a-106">Değişiklik komut ağaçlarını genel bakış</span><span class="sxs-lookup"><span data-stu-id="6dc0a-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="6dc0a-107">Değişiklik SQL oluşturma modülü üzerinde belirli bir giriş DbModificationCommandTree temel veritabanı özgü değişikliği SQL deyimlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="6dc0a-108">Bir değişiklik DML işlemi (bir ekleme, güncelleştirme veya silme işlemi) nesne modeli gösterimini bir DbModificationCommandTree olan DbCommandTree devralan.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="6dc0a-109">DbModificationCommandTree üç uygulamaları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="6dc0a-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="6dc0a-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="6dc0a-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="6dc0a-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="6dc0a-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="6dc0a-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="6dc0a-113">DbModificationCommandTree ve tarafından üretilen bunun uygulamalarını [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] her zaman tek bir satır işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="6dc0a-114">Bu bölümde, bu tür, .NET Framework sürüm 3.5 kısıtlamalar ile açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="6dc0a-115">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="6dc0a-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="6dc0a-116">DbModificationCommandTree değiştirme işlemi için ayarlanmış hedef temsil eden bir hedef özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="6dc0a-117">Giriş kümesi tanımlar hedefin ifade özelliği her zaman DbScanExpression olur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="6dc0a-118">Bir DbScanExpression ya da bir tablo veya Görünüm gösterebilir veya meta veri özelliği, hedef "sorgu tanımlama" ise, bir veri kümesi null olmayan bir sorgu ile tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="6dc0a-119">Bir sorgu temsil eden bir DbScanExpression yalnızca bir sağlayıcı değiştirme hedefi olarak belirlenen modelde tanımlayan bir sorgu kullanarak tanımlandı, ancak hiçbir işlev karşılık gelen değiştirme işlemi için sağlanan ulaşabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="6dc0a-120">Sağlayıcıları (SqlClient, örneğin, desteklemez) senaryosunu destekleyecek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="6dc0a-121">DbInsertCommandTree bir komut ağacındaki ifade edilen bir tek satır ekleme işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="6dc0a-122">DbUpdateCommandTree bir komut ağacındaki ifade edilen bir tek satır güncelleştirme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="6dc0a-123">DbDeleteCommandTree bir komut ağacındaki ifade edilen tek satır silme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="6dc0a-124">Değişiklik komut ağacı özellikleri kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="6dc0a-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="6dc0a-125">Aşağıdaki bilgiler ve kısıtlamaları değişiklik komut ağacı özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="6dc0a-126">DbInsertCommandTree ve DbUpdateCommandTree döndürme</span><span class="sxs-lookup"><span data-stu-id="6dc0a-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="6dc0a-127">Null olmayan döndürme komutu bir okuyucu döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="6dc0a-128">Aksi takdirde komut etkilenen satırların sayısını (eklenir veya güncelleştirilir) gösteren bir skaler değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="6dc0a-129">Bir yansıtma eklenen veya güncelleştirilen satır tabanlı döndürülecek sonuç döndürme değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="6dc0a-130">Tür bağımsız değişkenleri karşılık gelen DbModificationCommandTree hedef başvuru temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olan her bir satır temsil eden Dbnewınstanceexpression yalnızca olabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="6dc0a-131">Döndürme her zaman oluşturulan veya değerleri hesaplanmış sütun deposu özelliğinde kullanılan DbPropertyExpressions tarafından temsil edilen özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="6dc0a-132">En az bir satır eklenmekte tablonun oluşturulan veya (StoreGeneratedPattern.Identity veya StoreGeneratedPattern.Computed olarak ssdl işaretli) hesaplanmış deposu olarak belirtildiğinde DbInsertCommandTree içinde döndürme null değil.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="6dc0a-133">DbUpdateCommandTrees içinde döndürme null olmayan, satır güncelleştiriliyor tablosunun en az bir özellik deposu olarak belirtildiğinde hesaplanan (olarak işaretlenmişse StoreGeneratedPattern.Computed ssdl içinde).</span><span class="sxs-lookup"><span data-stu-id="6dc0a-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="6dc0a-134">DbInsertCommandTree ve DbUpdateCommandTree SetClauses</span><span class="sxs-lookup"><span data-stu-id="6dc0a-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="6dc0a-135">INSERT listesini SetClauses belirtir veya güncelleştirme ekleme veya güncelleştirme işlemi tanımlamak yan tümceleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="6dc0a-136">Özellik güncelleştirilmelidir özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="6dc0a-137">Her zaman bir başvuru karşılık gelen DbModificationCommandTree hedefi temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="6dc0a-138">Değer yeni değer özelliği güncelleştirileceği ile belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="6dc0a-139">Türü ya da DbConstantExpression veya DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="6dc0a-140">DbUpdateCommandTree ve DbDeleteCommandTree karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="6dc0a-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="6dc0a-141">Koşulu, hangi hedef koleksiyonun üyeleri güncelleştirilemez veya belirlemek için kullanılan koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="6dc0a-142">DbExpressions aşağıdaki alt kümesini yerleşik bir ifade ağacına şöyledir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="6dc0a-143">DbComparisonExpression tür aşağıda kısıtlı olarak DbPropertyExression olan sağ alt ve sol alt bir DbConstantExpression ile eşittir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="6dc0a-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="6dc0a-145">Bir DbPropertyExpresison kısıtlı olarak üzerinden DbIsNullExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="6dc0a-146">Karşılık gelen DbModificationCommandTree hedef başvuru temsil eden bir DbVariableReferenceExpression üzerinden DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="6dc0a-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="6dc0a-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="6dc0a-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="6dc0a-150">Örnek sağlayıcısında değişiklik SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc0a-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="6dc0a-151">[Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları bileşenlerinin gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dc0a-151">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="6dc0a-152">SQL Server 2005 veritabanlarını hedefler ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı en üstünde bir sarmalayıcı olarak uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="6dc0a-153">(SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) örnek sağlayıcısı'nın değişikliği SQL oluşturma modülü giriş DbModificationCommandTree alır ve tek bir değişiklik büyük olasılıkla döndürmek için bir select deyimi tarafından izlenen SQL deyimini üreten bir DbModificationCommandTree tarafından belirtilen okuyucu.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="6dc0a-154">Hedef SQL Server veritabanı tarafından oluşturulan komutları şeklini etkileyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="6dc0a-155">Yardımcı sınıfları: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="6dc0a-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="6dc0a-156">Tüm değişiklik komut ağacı özelliklerinin DbExpression türünde bir ortak basit Çeviricisi ExpressionTranslator görür.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="6dc0a-157">Yalnızca değişikliği komut ağacı özelliklerini kısıtlı ifade türleri çevrilmesi destekler ve aklınızda belirli kısıtlamalar ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="6dc0a-158">Aşağıdaki bilgiler, belirli ifade türleri (Önemsiz çevirileri düğümleriyle göz ardı edilir) ziyaret açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="6dc0a-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="6dc0a-160">Ne zaman ExpressionTranslator yapılandırılmıştır ile preserveMemberValues = true ve sağa sabiti (yerine DbNullExpression) bir DbConstantExpression olduğunda, bunu sol işleneni (DbPropertyExpressions) ile ilişkilendirir DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="6dc0a-161">Dönüş bir Select deyimi etkilenen satır tanımlamak üzere oluşturulan gerekiyorsa, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="6dc0a-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-162">DbConstantExpression</span></span>  
 <span data-ttu-id="6dc0a-163">Her ziyaret edilen sabit bir parametre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="6dc0a-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="6dc0a-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="6dc0a-165">O oluşturma (tablo değişkeni kullanıldığında, yalnızca güncelleştirme senaryolarda gerçekleşir) bir diğer ad oluşturduğu sürece her zaman temsil eden giriş tablosu DbPropertyExpression örneği, diğer ad için giriş belirtilmesi gerekiyor; Çeviri varsayılan özellik adı olarak.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="6dc0a-166">Bir INSERT SQL komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="6dc0a-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="6dc0a-167">Örnek Sağlayıcısı'nda belirtilen DbInsertCommandTree için oluşturulan INSERT komutu aşağıdaki iki Ekle şablonlarından birini izler.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="6dc0a-168">İlk şablon SetClauses listesinde değerlerine göre Ekle gerçekleştirmek için bir komut var ve döndürme özelliği null olmayan, eklenen satır için döndürme özelliğinde belirtilen özellikleri döndürmek için bir SELECT deyimi.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="6dc0a-169">Koşul öğesi "@@ROWCOUNT > 0" bir satır eklediyseniz doğrudur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-169">The predicate element "@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="6dc0a-170">Koşul öğesi "keyMemberI = keyValueI &#124; SCOPE_IDENTITY() "şeklini alır" keyMemberI SCOPE_IDENTITY() = "yalnızca keyMemeberI depoda üretilmiş bir anahtarı ise çünkü SCOPE_IDENTITY() (depoda üretilmiş) bir kimlik sütununa eklenen son kimlik değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="6dc0a-171">İkinci Şablon Ekle burada birincil anahtarı depoda üretilmiş ancak bir tamsayı türünde değil ve bu nedenle scope_identity()) ile kullanılamaz satır ekleme belirtiyorsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="6dc0a-172">Depoda üretilmiş bir bileşik anahtarı ise de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-172">It is also used if there is a compound store-generated key.</span></span>  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 <span data-ttu-id="6dc0a-173">Örnek sağlayıcısıyla içerdiği modelini kullanan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="6dc0a-174">Bu bir INSERT komutu DbInsertCommandTree oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="6dc0a-175">Aşağıdaki kod bir kategori ekler:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="6dc0a-176">Bu kod sağlayıcısına geçirilen aşağıdaki komut ağacı üretir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 <span data-ttu-id="6dc0a-177">Örnek sağlayıcısı üreten depolama komutu aşağıdaki SQL ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="6dc0a-178">Bir güncelleştirme SQL komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="6dc0a-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="6dc0a-179">Belirli bir DbUpdateCommandTree için oluşturulan güncelleştirme komutu aşağıdaki şablona göre:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="6dc0a-180">Set yan tümcesinin sahte set yan tümcesine sahip ("@i = 0") hiçbir set yan tümceleri yalnızca belirtilen.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="6dc0a-181">Bu herhangi deposu-sütunları yeniden hesaplanan olduğundan emin olmaktır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="6dc0a-182">Yalnızca döndürme özelliği null değilse, bir select deyimi döndürme özelliğinde belirtilen özellikleri döndürmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="6dc0a-183">Aşağıdaki örnek, bir güncelleştirme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="6dc0a-184">Aşağıdaki kullanıcı kodu bir kategori güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="6dc0a-185">Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 <span data-ttu-id="6dc0a-186">Örnek sağlayıcısı aşağıdaki depolama komutu üretir:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="6dc0a-187">Silme SQL komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="6dc0a-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="6dc0a-188">Belirli bir DbDeleteCommandTree için oluşturulan DELETE komutu aşağıdaki şablona göre:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="6dc0a-189">Aşağıdaki örnek, silme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="6dc0a-190">Aşağıdaki kullanıcı kodu bir kategori siler:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="6dc0a-191">Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 <span data-ttu-id="6dc0a-192">Aşağıdaki depolama komutu örnek sağlayıcısı tarafından oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="6dc0a-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6dc0a-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc0a-193">See Also</span></span>  
 [<span data-ttu-id="6dc0a-194">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="6dc0a-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
