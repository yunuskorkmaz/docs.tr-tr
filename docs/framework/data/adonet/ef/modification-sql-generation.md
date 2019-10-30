---
title: Değişiklik SQL Oluşturma
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039893"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="8ed73-102">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ed73-102">Modification SQL Generation</span></span>

<span data-ttu-id="8ed73-103">Bu bölümde, (SQL: 1999 uyumlu veritabanı) sağlayıcınız için bir değiştirme SQL oluşturma modülünün nasıl geliştirilmesi anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="8ed73-104">Bu modül, bir değiştirme komut ağacını uygun SQL INSERT, UPDATE veya DELETE ifadelerine çevirmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="8ed73-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="8ed73-105">Select deyimleri için SQL üretimi hakkında daha fazla bilgi için bkz. [SQL üretimi](sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="8ed73-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="8ed73-106">Değiştirme komut ağaçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="8ed73-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="8ed73-107">Değişiklik SQL oluşturma modülü, belirli bir giriş DbModificationCommandTree temelinde veritabanına özel değişiklik SQL deyimleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ed73-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="8ed73-108">DbModificationCommandTree bir değiştirme DML işleminin (bir INSERT, Update veya delete işlemi), DbCommandTree 'den devralan bir nesne modeli gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="8ed73-109">DbModificationCommandTree ' nin üç uygulaması vardır:</span><span class="sxs-lookup"><span data-stu-id="8ed73-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="8ed73-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="8ed73-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="8ed73-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="8ed73-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="8ed73-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="8ed73-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="8ed73-113">DbModificationCommandTree ve Entity Framework tarafından üretilen uygulamaları her zaman tek bir satır işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ed73-113">DbModificationCommandTree and its implementations that are produced by the Entity Framework always represent a single row operation.</span></span> <span data-ttu-id="8ed73-114">Bu bölümde, .NET Framework sürüm 3,5 ' de kısıtlamaları olan bu türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="8ed73-115">![Çizimindeki](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="8ed73-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="8ed73-116">DbModificationCommandTree, değişiklik işlemi için hedef kümesini temsil eden bir Target özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="8ed73-117">Giriş kümesini tanımlayan hedefin Expression özelliği her zaman DbScanExpression ' dır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="8ed73-118">Bir DbScanExpression bir tabloyu veya görünümü temsil edebilir ya da hedefin "sorgu tanımlaması" meta veri özelliği null değilse bir sorgu ile tanımlanmış bir veri kümesini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="8ed73-119">Bir sorguyu temsil eden bir DbScanExpression, küme, modelde bir tanımlama sorgusu kullanılarak tanımlanmışsa ancak ilgili değişiklik işlemi için hiçbir işlev sağlanmadıysa yalnızca bir değişikliğin hedefi olarak bir sağlayıcıya ulaşabilir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="8ed73-120">Sağlayıcılar böyle bir senaryoyu destekleyemeyebilir (örneğin, SqlClient).</span><span class="sxs-lookup"><span data-stu-id="8ed73-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="8ed73-121">DbInsertCommandTree, komut ağacı olarak ifade edilen tek satırlık ekleme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ed73-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="8ed73-122">DbUpdateCommandTree, komut ağacı olarak ifade edilen tek satırlık bir güncelleştirme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ed73-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="8ed73-123">DbDeleteCommandTree, komut ağacı olarak ifade edilen tek satırlık silme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ed73-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="8ed73-124">Değiştirme komut ağacı özelliklerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="8ed73-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="8ed73-125">Aşağıdaki bilgiler ve kısıtlamalar değiştirme komut ağacı özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="8ed73-126">DbInsertCommandTree ve DbUpdateCommandTree içine dönme</span><span class="sxs-lookup"><span data-stu-id="8ed73-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="8ed73-127">Null olmayan, döndürme komutun bir okuyucu döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="8ed73-128">Aksi takdirde, komut etkilenen satır sayısını belirten bir skaler değer döndürmelidir (ekli veya güncelleştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="8ed73-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="8ed73-129">Döndürülen değer, girilen veya güncellenen satıra göre döndürülecek sonuçların projeksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="8ed73-130">Yalnızca bir satırı temsil eden DbNewInstanceExpression oluşturamıyor türünde olabilir ve bağımsız değişkenlerinin her biri, karşılık gelen DbModificationCommandTree hedefine bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinde bir DbPropertyExpression olur.</span><span class="sxs-lookup"><span data-stu-id="8ed73-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="8ed73-131">Döndürülen özellikte kullanılan Dbpropertydeyimleriyle temsil edilen özellikler, her zaman üretilen veya hesaplanan değerleri depolar.</span><span class="sxs-lookup"><span data-stu-id="8ed73-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="8ed73-132">DbInsertCommandTree içinde, satır eklenmekte olan tablonun en az bir özelliği depo oluşturuldu veya hesaplandı (StoreGeneratedPattern. Identity veya StoreGeneratedPattern. ssdl içinde hesaplanan) olarak belirtildiğinde, döndüren döndürme null değildir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="8ed73-133">DbUpdateCommandTrees içinde, satırın güncelleştirilmekte olduğu tablonun en az bir özelliği (StoreGeneratedPattern. ssdl içinde hesaplanan) olarak belirtildiğinde, döndüren döndürme null değildir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="8ed73-134">DbInsertCommandTree ve DbUpdateCommandTree içindeki Settümceleri</span><span class="sxs-lookup"><span data-stu-id="8ed73-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="8ed73-135">Settümceleri ekleme veya güncelleştirme işlemini tanımlayan INSERT veya Update set yan tümceleri listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

<span data-ttu-id="8ed73-136">Liste öğeleri, ekleme veya güncelleştirme değiştirme işleminde tek bir yan tümce belirten DbModificationClause türü olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-136">The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation.</span></span> <span data-ttu-id="8ed73-137">DbSetClause, DbModificationClause öğesinden devralır ve bir özelliğin değerini ayarlayan bir değiştirme işleminde yan tümceyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-137">DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property.</span></span> <span data-ttu-id="8ed73-138">.NET Framework sürüm 3,5 ' den başlayarak, SetClause 'daki tüm öğeler SetClause türündedir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-138">Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.</span></span>

<span data-ttu-id="8ed73-139">Özelliği, güncellenmesi gereken özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-139">Property specifies the property that should be updated.</span></span> <span data-ttu-id="8ed73-140">Bir DbVariableReferenceExpression üzerinde her zaman bir DbPropertyExpression, buna karşılık gelen DbModificationCommandTree hedefine yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ed73-140">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="8ed73-141">Değer, özelliği güncelleştirilecek yeni değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-141">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="8ed73-142">Bu, DbConstantExpression veya Dbsnullexpression türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-142">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="8ed73-143">DbUpdateCommandTree ve DbDeleteCommandTree içindeki koşul</span><span class="sxs-lookup"><span data-stu-id="8ed73-143">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="8ed73-144">Koşul, hedef koleksiyonun hangi üyelerinin güncelleştirileceğini veya silineceğini belirlemekte kullanılan koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-144">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="8ed73-145">Bu, Dbdeyimlerden oluşan aşağıdaki alt kümesini oluşturulmuş bir ifade ağacıdır:</span><span class="sxs-lookup"><span data-stu-id="8ed73-145">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="8ed73-146">Sağ alt öğesi, aşağıda kısıtlanmış bir DbPropertyExpression ve bir DbConstantExpression sol alt öğesi olacak şekilde, türü eşittir DbComparisonExpression.</span><span class="sxs-lookup"><span data-stu-id="8ed73-146">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="8ed73-147">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-147">DbConstantExpression</span></span>

- <span data-ttu-id="8ed73-148">Aşağıda kısıtlanmış bir DbPropertyExpression üzerinde Dbissnullexpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-148">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="8ed73-149">Karşılık gelen DbModificationCommandTree hedefine yönelik bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinde DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="8ed73-149">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="8ed73-150">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-150">DbAndExpression</span></span>

- <span data-ttu-id="8ed73-151">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-151">DbNotExpression</span></span>

- <span data-ttu-id="8ed73-152">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-152">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="8ed73-153">Örnek sağlayıcıda değişiklik SQL üretimi</span><span class="sxs-lookup"><span data-stu-id="8ed73-153">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="8ed73-154">[Entity Framework örnek sağlayıcı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , Entity Framework destekleyen ADO.NET veri sağlayıcılarının bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-154">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the Entity Framework.</span></span> <span data-ttu-id="8ed73-155">SQL Server 2005 veritabanını hedefler ve System. Data. SqlClient ADO.NET 2,0 Veri Sağlayıcısı üzerine bir sarmalayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-155">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="8ed73-156">Örnek sağlayıcının (SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) değişiklik SQL oluşturma modülü, bir giriş DbModificationCommandTree alır ve tek bir değişiklik SQL deyiminden sonra bir SELECT deyiminden sonra gelen bir DbModificationCommandTree tarafından belirtilmişse okuyucu.</span><span class="sxs-lookup"><span data-stu-id="8ed73-156">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="8ed73-157">Oluşturulan komutların şeklinin hedef SQL Server veritabanından etkileneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ed73-157">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="8ed73-158">Yardımcı sınıflar: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="8ed73-158">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="8ed73-159">ExpressionTranslator, DbExpression türünde tüm değiştirme komut ağacı özellikleri için ortak bir basit çevirici işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="8ed73-159">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="8ed73-160">Yalnızca değiştirme komutu ağacının özelliklerinin kısıtlandığı ve belirli kısıtlamalarla birlikte oluşturulduğu ifade türlerinin çevirisini destekler.</span><span class="sxs-lookup"><span data-stu-id="8ed73-160">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="8ed73-161">Aşağıdaki bilgiler belirli ifade türlerini ziyaret etmenizi açıklar (önemsiz çevirileri olan düğümler atlanır).</span><span class="sxs-lookup"><span data-stu-id="8ed73-161">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="8ed73-162">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-162">DbComparisonExpression</span></span>

<span data-ttu-id="8ed73-163">ExpressionTranslator, preserveMemberValues = true ile oluşturulduğunda ve sağdaki sabit değeri bir DbConstantExpression (Dbsnullexpression yerine) olduğunda, sol işleneni (DbPropertyExpression) bununla ilişkilendirir DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="8ed73-163">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="8ed73-164">Bu, etkilenen satırı tanımlamak için bir return SELECT ifadesinin oluşturulması gerekiyorsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-164">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="8ed73-165">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-165">DbConstantExpression</span></span>

<span data-ttu-id="8ed73-166">Her ziyaret edilen sabit için bir parametre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ed73-166">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="8ed73-167">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="8ed73-167">DbPropertyExpression</span></span>

<span data-ttu-id="8ed73-168">Oluşturma işlemi her zaman giriş tablosunu temsil ettiğinden, kuşak bir diğer ad oluşturmadıysa (yalnızca bir tablo değişkeni kullanıldığında güncelleştirme senaryolarında olur), giriş için diğer ad belirtilmesi gerekmez; Çeviri varsayılan olarak özellik adını alır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-168">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="8ed73-169">INSERT SQL komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ed73-169">Generating an Insert SQL Command</span></span>

<span data-ttu-id="8ed73-170">Örnek sağlayıcıda verilen bir DbInsertCommandTree için, oluşturulan INSERT komutu aşağıdaki iki ekleme şablonundan birini izler.</span><span class="sxs-lookup"><span data-stu-id="8ed73-170">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="8ed73-171">İlk şablonda, Setyan tümceleri listesindeki değerleri verilen ekleme işlemini gerçekleştirmeye yönelik bir komut ve döndürülen özellik null değilse, ekli satır için döndürülen özellikte belirtilen özellikleri döndürecek bir SELECT deyimidir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-171">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="8ed73-172">Bir satır eklenirse, "\@@ROWCOUNT > 0" koşul öğesi doğru.</span><span class="sxs-lookup"><span data-stu-id="8ed73-172">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="8ed73-173">"KeyMemberI = keyValueI &#124; scope_identity ()" koşul öğesi, "keyMemberI = scope_identity ()" şeklini, ancak keyMemberI 'nin bir kimliğe ekli en son kimlik değerini döndürdüğü "keymemberi = ()" şeklini alır ( Depo oluşturuldu) sütunu.</span><span class="sxs-lookup"><span data-stu-id="8ed73-173">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="8ed73-174">INSERT, birincil anahtarın depoda oluşturulduğu, ancak bir tamsayı türü olmadığı ancak bu nedenle scope_identity () ile birlikte kullanılamayan bir satır eklemeyi belirtiyorsa ikinci şablon gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-174">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="8ed73-175">Bu, Birleşik bir depoda oluşturulan anahtar varsa da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-175">It is also used if there is a compound store-generated key.</span></span>

```sql
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

<span data-ttu-id="8ed73-176">Örnek sağlayıcıda bulunan modeli kullanan bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-176">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="8ed73-177">DbInsertCommandTree öğesinden bir INSERT komutu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ed73-177">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="8ed73-178">Aşağıdaki kod bir kategori ekler:</span><span class="sxs-lookup"><span data-stu-id="8ed73-178">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="8ed73-179">Bu kod, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-179">This code produces the following command tree, which is passed to the provider:</span></span>

```output
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

<span data-ttu-id="8ed73-180">Örnek sağlayıcının ürettiği mağaza komutu aşağıdaki SQL deyimidir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-180">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="8ed73-181">Bir Update SQL komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="8ed73-181">Generating an Update SQL Command</span></span>

<span data-ttu-id="8ed73-182">Belirli bir DbUpdateCommandTree için, oluşturulan güncelleştirme komutu aşağıdaki şablona dayalıdır:</span><span class="sxs-lookup"><span data-stu-id="8ed73-182">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="8ed73-183">Set yan tümcesi, yalnızca set yan tümceleri belirtilmemişse, sahte set yan tümcesine ("@i = 0") sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-183">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="8ed73-184">Bu, tüm mağaza hesaplanmış sütunlarının yeniden hesaplanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-184">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="8ed73-185">Yalnızca döndüren özelliği null değilse, return özelliğinde belirtilen özellikleri döndürmek için bir SELECT ifadesinin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-185">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="8ed73-186">Aşağıdaki örnek, bir Update komutu oluşturmak için örnek sağlayıcıda bulunan modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-186">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="8ed73-187">Aşağıdaki Kullanıcı kodu bir kategoriyi güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-187">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="8ed73-188">Bu Kullanıcı kodu, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-188">This user code produces the following command tree, which is passed to the provider:</span></span>

```output
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

<span data-ttu-id="8ed73-189">Örnek sağlayıcı aşağıdaki Store komutunu üretir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-189">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="8ed73-190">Bir DELETE SQL komutu oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="8ed73-190">Generating a Delete SQL Command</span></span>

<span data-ttu-id="8ed73-191">Belirli bir DbDeleteCommandTree için, oluşturulan DELETE komutu aşağıdaki şablona dayalıdır:</span><span class="sxs-lookup"><span data-stu-id="8ed73-191">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="8ed73-192">Aşağıdaki örnek, bir Delete komutu oluşturmak için örnek sağlayıcıda bulunan modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ed73-192">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="8ed73-193">Aşağıdaki Kullanıcı kodu bir kategoriyi siler:</span><span class="sxs-lookup"><span data-stu-id="8ed73-193">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="8ed73-194">Bu Kullanıcı kodu, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir.</span><span class="sxs-lookup"><span data-stu-id="8ed73-194">This user code produces the following command tree, which is passed to the provider.</span></span>

```output
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

<span data-ttu-id="8ed73-195">Aşağıdaki mağaza komutu örnek sağlayıcı tarafından üretilir:</span><span class="sxs-lookup"><span data-stu-id="8ed73-195">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="8ed73-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ed73-196">See also</span></span>

- [<span data-ttu-id="8ed73-197">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="8ed73-197">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
