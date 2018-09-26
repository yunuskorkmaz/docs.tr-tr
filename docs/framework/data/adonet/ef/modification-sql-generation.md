---
title: Değişiklik SQL oluşturma
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111964"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="11009-102">Değişiklik SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="11009-102">Modification SQL Generation</span></span>
<span data-ttu-id="11009-103">Bu bölümde bir değişiklik SQL oluşturma modülü için geliştirme anlatılmaktadır, (SQL:1999-uyumlu veritabanı) sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="11009-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="11009-104">Bu modül, uygun SQL INSERT, UPDATE veya DELETE deyimlerine bir değişikliği komut ağacı çevirmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="11009-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="11009-105">Select deyimleri için SQL oluşturma hakkında daha fazla bilgi için bkz. [SQL oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="11009-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="11009-106">Değişiklik komut ağaçlarını genel bakış</span><span class="sxs-lookup"><span data-stu-id="11009-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="11009-107">Değişiklik SQL oluşturma modülü, belirli bir giriş DbModificationCommandTree üzerinde temel veritabanı özgü değişiklik SQL deyimleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11009-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="11009-108">Bir DbModificationCommandTree nesne modeli, bir DML işlemi (bir ekleme, güncelleştirme veya silme işlemi) değişiklik temsilidir DbCommandTree devralıyor.</span><span class="sxs-lookup"><span data-stu-id="11009-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="11009-109">Üç uygulamaları DbModificationCommandTree vardır:</span><span class="sxs-lookup"><span data-stu-id="11009-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="11009-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="11009-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="11009-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="11009-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="11009-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="11009-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="11009-113">DbModificationCommandTree ve tarafından üretilen kendi uygulamalarını [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] her zaman tek bir satır işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11009-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="11009-114">Bu bölümde, .NET Framework sürüm 3.5, kısıtlama olmadan bu türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11009-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="11009-115">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="11009-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="11009-116">DbModificationCommandTree ayarlama değiştirme işlemi için hedef temsil eden bir hedef özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="11009-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="11009-117">Giriş kümesinde tanımlayan hedefin ifade her zaman DbScanExpression özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="11009-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="11009-118">Bir DbScanExpression ya da bir tablo veya Görünüm temsil edebilir veya bir veri kümesi meta verileri özelliği, hedef "sorgu tanımlama" ise null olmayan bir sorgu ile tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="11009-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="11009-119">Bir sorgu temsil eder bir DbScanExpression yalnızca bir sağlayıcı değiştirme hedefi belirlenen modelde tanımlayan bir sorgu kullanarak tanımlandı, ancak hiçbir işlev karşılık gelen bir değiştirme işlemi için sağlanan ulaşabilir.</span><span class="sxs-lookup"><span data-stu-id="11009-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="11009-120">Sağlayıcıları (SqlClient, örneğin, daha önceden) senaryosunu desteklemek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="11009-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="11009-121">DbInsertCommandTree komut ağaç olarak ifade edilen bir tek satır ekleme işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11009-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="11009-122">DbUpdateCommandTree komut ağaç olarak ifade edilen bir tek satır güncelleştirme işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11009-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="11009-123">DbDeleteCommandTree komut ağaç olarak ifade edilen bir tek satır silme işlemini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11009-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="11009-124">Değişiklik komut ağacı özellikleri kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="11009-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="11009-125">Aşağıdaki bilgileri ve kısıtlamaları değişikliği komut ağacı özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="11009-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="11009-126">DbInsertCommandTree ve DbUpdateCommandTree döndürme</span><span class="sxs-lookup"><span data-stu-id="11009-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="11009-127">Null olmadığında, döndürme komutu bir okuyucu döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="11009-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="11009-128">Aksi takdirde, komut, etkilenen satır sayısı (eklendiğinde veya güncelleştirildiğinde) belirten bir skaler değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="11009-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="11009-129">Döndürme değeri, eklenen veya güncelleştirilen satırı tabanlı döndürülmesi gereken sonuçlar bir projeksiyon belirtir.</span><span class="sxs-lookup"><span data-stu-id="11009-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="11009-130">Yalnızca Dbnewınstanceexpression her biriyle ilgili DbModificationCommandTree hedefi için bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olan bağımsız bir satırı temsil eden türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="11009-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="11009-131">Özellikleri döndürme her zaman depolama üretilen veya hesaplanan değerleri özelliğinde kullanılan DbPropertyExpressions tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="11009-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="11009-132">Satır eklenmekte tablonun en az bir özellik olarak oluşturulan ya da (StoreGeneratedPattern.Identity veya StoreGeneratedPattern.Computed olarak ssdl işaretli) hesaplanan deposu belirtildiğinde DbInsertCommandTree içinde döndürme null değil.</span><span class="sxs-lookup"><span data-stu-id="11009-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="11009-133">Döndürme DbUpdateCommandTrees içinde null değil, satır güncelleştiriliyor tablonun en az bir özellik deposu olarak belirtildiğinde (olarak işaretlenmişse StoreGeneratedPattern.Computed ssdl içinde) hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="11009-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="11009-134">SetClauses DbInsertCommandTree ve DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="11009-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="11009-135">INSERT listesini SetClauses belirtir veya güncelleştirme ekleme veya güncelleştirme işlemi tanımlayan bir yan tümceleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="11009-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="11009-136">Özellik güncelleştirilmesi gereken özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="11009-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="11009-137">Her zaman ilgili DbModificationCommandTree hedefinin bir başvuruyu temsil eder bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olur.</span><span class="sxs-lookup"><span data-stu-id="11009-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="11009-138">Değer özelliğini güncelleştirmek yeni değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="11009-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="11009-139">Tür ya da DbConstantExpression veya DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="11009-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="11009-140">Koşul DbUpdateCommandTree ve DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="11009-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="11009-141">Hedef koleksiyonun üyeleri güncelleştirildiğinde veya silindiğinde belirlemek için kullanılan karşılaştırma koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="11009-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="11009-142">Bu yerleşik DbExpressions aşağıdaki alt kümesini bir ifade ağacı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="11009-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="11009-143">DbComparisonExpression türde bir DbPropertyExression aşağıda kısıtlı olarak olan sağ alt ve sol alt bir DbConstantExpression ile eşittir.</span><span class="sxs-lookup"><span data-stu-id="11009-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="11009-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="11009-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="11009-145">Üzerinden bir DbPropertyExpresison kısıtlı olarak DbIsNullExpression</span><span class="sxs-lookup"><span data-stu-id="11009-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="11009-146">Karşılık gelen DbModificationCommandTree hedefi için bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinden DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="11009-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="11009-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="11009-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="11009-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="11009-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="11009-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="11009-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="11009-150">Örnek sağlayıcısında değişiklik SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="11009-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="11009-151">[Entity Framework örnek sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11009-151">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="11009-152">Bu, bir SQL Server 2005 veritabanını hedefler ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı üzerine bir sarmalayıcı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="11009-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="11009-153">Değişiklik SQL oluşturma Modülü (SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) örnek sağlayıcısı bir giriş DbModificationCommandTree alır ve tek bir değişiklik büyük olasılıkla döndürmek için bir select deyimi tarafından izlenen SQL deyimini oluşturan bir okuyucu tarafından DbModificationCommandTree belirtildi.</span><span class="sxs-lookup"><span data-stu-id="11009-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="11009-154">Hedef SQL Server veritabanı tarafından oluşturulan komutları şeklini etkileyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="11009-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="11009-155">Yardımcı sınıfları: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="11009-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="11009-156">ExpressionTranslator DbExpression türünde tüm değişiklik komut ağacı özellikleri için ortak bir basit translator işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="11009-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="11009-157">Bu değişikliği komut ağacı özelliklerini sınırlı olan ifade türleri çeviri destekler ve göz önünde belirli kısıtlamalar ile oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="11009-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="11009-158">Aşağıdaki bilgiler, belirli ifade türleri (Önemsiz çevirileri düğümleri atlanır) ziyaret açıklanır.</span><span class="sxs-lookup"><span data-stu-id="11009-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="11009-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="11009-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="11009-160">ExpressionTranslator preserveMemberValues ile oluşturulan zaman = true ve sağa sabiti (DbNullExpression) yerine bir DbConstantExpression, sol işleneni (DbPropertyExpressions) ile ilişkilendirir DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="11009-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="11009-161">Dönüş bir Select deyimi etkilenen satır tanımlamak üzere oluşturulan gerekiyorsa, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11009-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="11009-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="11009-162">DbConstantExpression</span></span>  
 <span data-ttu-id="11009-163">Ziyaret edilen her sabit bir parametre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="11009-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="11009-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="11009-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="11009-165">Oluşturma (tablo değişkeni kullanıldığında, yalnızca güncelleştirme senaryolarda gerçekleşir) bir diğer ad oluşturduğu sürece her zaman temsil eden girdi tablosu DbPropertyExpression örneğini düşünüldüğünde, takma ad için girişi belirtilmesi gerekiyor; Çeviri varsayılan olarak özellik adıdır.</span><span class="sxs-lookup"><span data-stu-id="11009-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="11009-166">Bir INSERT SQL komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="11009-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="11009-167">Oluşturulan INSERT komutu için belirli bir DbInsertCommandTree örnek sağlayıcısında aşağıdaki iki INSERT şablonlardan birini izler.</span><span class="sxs-lookup"><span data-stu-id="11009-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="11009-168">İlk şablon SetClauses listesinde değerlerine INSERT gerçekleştirmek için bir komut vardır ve döndürme özelliği null değildi, eklenen satır için döndürme özelliğinde belirtilen dönüş özellikleri için bir SELECT deyimi.</span><span class="sxs-lookup"><span data-stu-id="11009-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="11009-169">Koşul öğe "\@ @ROWCOUNT > 0" değeri bir satır eklenmişse true.</span><span class="sxs-lookup"><span data-stu-id="11009-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="11009-170">Koşul öğe "keyMemberI keyValueI = &#124; SCOPE_IDENTITY()" şeklini alır "keyMemberI SCOPE_IDENTITY() =" SCOPE_IDENTITY() bir kimlik (eklenen son kimlik değeri döndürdüğünden keyMemeberI depoda üretilmiş bir anahtar ise yalnızca depoda üretilmiş) sütunu.</span><span class="sxs-lookup"><span data-stu-id="11009-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="11009-171">INSERT burada birincil anahtarı depoda üretilmiş ancak bir tamsayı türü değil ve bu nedenle scope_identity()) ile kullanılamaz, bir satır eklemeyi belirtiyorsa, ikinci şablon gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11009-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="11009-172">Depoda üretilmiş bir bileşik anahtarı varsa de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11009-172">It is also used if there is a compound store-generated key.</span></span>  
  
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
  
 <span data-ttu-id="11009-173">Örnek sağlayıcısı ile birlikte modeli kullanan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11009-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="11009-174">Bu, bir DbInsertCommandTree INSERT komutu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11009-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="11009-175">Aşağıdaki kod, bir kategori ekler:</span><span class="sxs-lookup"><span data-stu-id="11009-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="11009-176">Bu kod, sağlayıcıya geçirilir aşağıdaki komut ağacı üretir:</span><span class="sxs-lookup"><span data-stu-id="11009-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="11009-177">Aşağıdaki SQL deyimini örnek sağlayıcısında üreten mağazası komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="11009-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="11009-178">Bir güncelleştirme SQL komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="11009-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="11009-179">Bir verilen DbUpdateCommandTree için oluşturulan güncelleştirme komutunu aşağıdaki şablonu temel alan:</span><span class="sxs-lookup"><span data-stu-id="11009-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="11009-180">Sahte set yan tümcesi set yan tümcesi olan ("@i = 0") hiçbir set yan tümceleri yalnızca belirtilen.</span><span class="sxs-lookup"><span data-stu-id="11009-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="11009-181">Tüm depolama sütunları yeniden hesaplanan emin olmak için budur.</span><span class="sxs-lookup"><span data-stu-id="11009-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="11009-182">Yalnızca döndürme özelliği null değilse, döndürme özelliğinde belirtilen özellikleri döndürmek için bir select deyimi oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="11009-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="11009-183">Aşağıdaki örnek, bir güncelleştirme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.</span><span class="sxs-lookup"><span data-stu-id="11009-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="11009-184">Aşağıdaki kullanıcı kodu bir kategori güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="11009-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="11009-185">Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir:</span><span class="sxs-lookup"><span data-stu-id="11009-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="11009-186">Örnek sağlayıcısında aşağıdaki depolama komutu üretir:</span><span class="sxs-lookup"><span data-stu-id="11009-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="11009-187">Silme SQL komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="11009-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="11009-188">Bir verilen DbDeleteCommandTree için oluşturulan DELETE komutu aşağıdaki şablonu temel alan:</span><span class="sxs-lookup"><span data-stu-id="11009-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="11009-189">Aşağıdaki örnek, bir silme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.</span><span class="sxs-lookup"><span data-stu-id="11009-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="11009-190">Aşağıdaki kullanıcı kodu bir kategoriyi siler:</span><span class="sxs-lookup"><span data-stu-id="11009-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="11009-191">Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir.</span><span class="sxs-lookup"><span data-stu-id="11009-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
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
  
 <span data-ttu-id="11009-192">Aşağıdaki depolama komutu örnek sağlayıcısı tarafından üretilir:</span><span class="sxs-lookup"><span data-stu-id="11009-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="11009-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11009-193">See Also</span></span>  
 [<span data-ttu-id="11009-194">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="11009-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
