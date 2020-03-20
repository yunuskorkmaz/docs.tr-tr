---
title: Tablo Değerli Parametreler
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174478"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="d4e9b-102">Tablo Değerli Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4e9b-102">Table-Valued Parameters</span></span>
<span data-ttu-id="d4e9b-103">Tablo değeri olan parametreler, birden çok tur gezisi veya verileri işlemek için özel sunucu tarafı mantığı gerektirmeden istemci uygulamasından SQL Server'a birden çok veri satırını işlemenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="d4e9b-104">Bir istemci uygulamasında veri satırları kapsüllemek ve tek bir parametreli komutverileri sunucuya göndermek için tablo değerli parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="d4e9b-105">Gelen veri satırları, Transact-SQL kullanılarak çalıştırılabilen bir tablo değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="d4e9b-106">Tablo değeri olan parametrelerdeki sütun değerlerine standart Transact-SQL SELECT deyimleri kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="d4e9b-107">Tablo değeri olan parametreler güçlü bir şekilde yazılır ve yapıları otomatik olarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="d4e9b-108">Tablo değeri olan parametrelerin boyutu yalnızca sunucu belleğiyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4e9b-109">Tablo değerindeki parametrede veri döndüremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="d4e9b-110">Tablo değeri olan parametreler yalnızca giriştedir; OUTPUT anahtar sözcüğü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="d4e9b-111">Tablo değeri olan parametreler hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="d4e9b-112">Kaynak</span><span class="sxs-lookup"><span data-stu-id="d4e9b-112">Resource</span></span>|<span data-ttu-id="d4e9b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e9b-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d4e9b-114">Tablo Değeri Olan Parametreleri Kullanın (Veritabanı Motoru)</span><span class="sxs-lookup"><span data-stu-id="d4e9b-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="d4e9b-115">Tablo değeri olan parametrelerin nasıl oluşturulup kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="d4e9b-116">[Kullanıcı Tanımlı Tablo Türleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="d4e9b-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="d4e9b-117">Tablo değeri olan parametreleri bildirmek için kullanılan kullanıcı tanımlı tablo türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="d4e9b-118">SQL Server'ın Önceki Sürümlerinde Birden Çok Satır Geçme</span><span class="sxs-lookup"><span data-stu-id="d4e9b-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="d4e9b-119">SQL Server 2008'e tablo değeri olan parametreler kullanılmadan önce, birden çok veri satırını depolanmış bir yordam veya parametreli SQL komutuna geçirme seçenekleri sınırlıydı.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="d4e9b-120">Geliştirici, birden çok satırı sunucuya geçirmek için aşağıdaki seçenekler arasından seçim yapabilir:</span><span class="sxs-lookup"><span data-stu-id="d4e9b-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="d4e9b-121">Birden çok sütun ve veri satırındaki değerleri temsil etmek için bir dizi tek tek parametre kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="d4e9b-122">Bu yöntem kullanılarak geçirilebilen veri miktarı, izin verilen parametre sayısıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="d4e9b-123">SQL Server yordamları, en fazla 2100 parametreye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="d4e9b-124">Sunucu tarafı mantığı, bu tek tek değerleri bir tablo değişkeninde veya işleme için geçici bir tabloda birleştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="d4e9b-125">Birden çok veri değerini sınırlı dizeleri veya XML belgelerine paketleyin ve ardından bu metin değerlerini bir yordam veya deyime geçirin.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="d4e9b-126">Bu, yordam ın veya deyimin veri yapılarını doğrulamak ve değerleri boşaltmak için gerekli mantığı içermesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="d4e9b-127">Birden çok satırı etkileyen veri modifikasyonları için bir dizi ayrı SQL `Update` deyimi oluşturun, örneğin bir <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="d4e9b-128">Değişiklikler sunucuya tek tek gönderilebilir veya gruplara ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="d4e9b-129">Ancak, birden çok deyim içeren toplu gruplar halinde gönderildiğinde bile, her deyim sunucuda ayrı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="d4e9b-130">Bir `bcp` tabloya çok <xref:System.Data.SqlClient.SqlBulkCopy> sayıda veri satırı yüklemek için yardımcı program veya nesneyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="d4e9b-131">Bu teknik çok verimli olmasına rağmen, veriler geçici bir tabloya veya tablo değişkenine yüklenmediği sürece sunucu tarafı işlemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="d4e9b-132">Tablo Değeri Nekadar Parametre Türleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e9b-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="d4e9b-133">Tablo değeri olan parametreler, Transact-SQL CREATE TYPE deyimleri kullanılarak tanımlanan güçlü bir şekilde yazılan tablo yapılarını temel almaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="d4e9b-134">İstemci uygulamalarınızda tablo değeri olan parametreleri kullanabilmek için önce bir tablo türü oluşturmanız ve SQL Server'daki yapıyı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="d4e9b-135">Tablo türleri oluşturma hakkında daha fazla bilgi için [Bkz. Kullanıcı Tanımlı Tablo Türleri.](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="d4e9b-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="d4e9b-136">Aşağıdaki deyim, CategoryID ve CategoryName sütunlarından oluşan CategoryTableType adlı bir tablo türü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d4e9b-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="d4e9b-137">Bir tablo türü oluşturduktan sonra, tablo değerindeki parametreleri bu türe göre bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="d4e9b-138">Aşağıdaki Transact-SQL parçası, depolanmış yordam tanımında tablo değeri olan bir parametrenin nasıl bildirilen ihtir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="d4e9b-139">READONLY anahtar kelimesinin tablo değerinde bir parametre yi bildirmek için gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="d4e9b-140">Tablo Değeri Olan Parametrelerle Veri Değiştirme (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d4e9b-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="d4e9b-141">Tablo değeri olan parametreler, tek bir deyim çalıştırılarak birden çok satırı etkileyen ayar tabanlı veri modifikasyonlarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="d4e9b-142">Örneğin, tablo değerindeki parametredeki tüm satırları seçebilir ve bunları bir veritabanı tablosuna ekleyebilir veya güncelleştirmek istediğiniz tabloya tablo değeri olan bir parametreyi birleştirerek güncelleştirme deyimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="d4e9b-143">Aşağıdaki Transact-SQL UPDATE deyimi, tablo değeri olan bir parametrenin Kategoriler tablosuna katılarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="d4e9b-144">FROM yan tümcesinde JOIN içeren tablo değeri nereli bir parametre kullandığınızda, tablo değeri olan parametrenin "ec" olarak kullanıldığı burada da diğer adı verilmelidir:</span><span class="sxs-lookup"><span data-stu-id="d4e9b-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="d4e9b-145">Bu İşlemel-SQL örneği, tek bir küme tabanlı işlemde INSERT gerçekleştirmek için tablo değerindeki bir parametreden satırların nasıl seçilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="d4e9b-146">Tablo Değeri Nekadar Değerlenen Parametrelerin Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="d4e9b-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="d4e9b-147">Tablo değeri olan parametreleriçin çeşitli sınırlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="d4e9b-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="d4e9b-148">Tablo değeri olan parametreleri [CLR kullanıcı tanımlı işlevlere geçiremezsiniz.](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)</span><span class="sxs-lookup"><span data-stu-id="d4e9b-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="d4e9b-149">Tablo değeri olan parametreler yalnızca UNIQUE veya PRIMARY KEY kısıtlamalarını desteklemek için dizine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="d4e9b-150">SQL Server, tablo değeri olan parametrelerle ilgili istatistikleri korumaz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="d4e9b-151">Tablo değeri olan parametreler Transact-SQL kodunda salt okunur.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="d4e9b-152">Tablo değerindeki parametrenin satırlarında sütun değerlerini güncelleştiremezsiniz ve satır lar ekleyemez veya silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="d4e9b-153">Tablo değerindeki parametrede depolanan yordamveya parametreli ifadeye geçirilen verileri değiştirmek için, verileri geçici bir tabloya veya tablo değişkenine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="d4e9b-154">Tablo değeri olan parametrelerin tasarımını değiştirmek için ALTER TABLE deyimlerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="d4e9b-155">SqlParameter Örneğini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4e9b-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="d4e9b-156"><xref:System.Data.SqlClient>tablo değeri olan parametrelerin <xref:System.Data.DataTable>veya <xref:System.Data.Common.DbDataReader> <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> nesnelerin doldurulmalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="d4e9b-157">Tablo değeri taşıyan parametre için bir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. özelliğini kullanarak bir tür adı belirtmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="d4e9b-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d4e9b-158">Sunucuda `TypeName` daha önce oluşturulmuş uyumlu bir türün adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d4e9b-159">Aşağıdaki kod parçası, veri eklemek <xref:System.Data.SqlClient.SqlParameter> için nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="d4e9b-160">Aşağıdaki örnekte, `addedCategories` değişken . <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="d4e9b-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d4e9b-161">Değişkenin nasıl doldurulur olduğunu görmek için, tablo [değeri olan parametreyi Depolanmış Yordam'a geçirmek](#passing)için bir sonraki bölümdeki örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="d4e9b-162">Bu parçada gösterildiği gibi, veri satırlarını tablo değerindeki bir parametreye akışı <xref:System.Data.Common.DbDataReader> için türetilen herhangi bir nesneyi de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4e9b-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="d4e9b-163">Tablo Değeri Olan Parametreyi Depolanan Yordama Geçirme</span><span class="sxs-lookup"><span data-stu-id="d4e9b-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="d4e9b-164">Bu örnek, tablo değerindeki parametre verilerinin depolanan bir yordama nasıl geçirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="d4e9b-165">Kod ayıkları <xref:System.Data.DataTable> <xref:System.Data.DataTable.GetChanges%2A> yöntemi kullanarak yeni bir satır ekledi.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="d4e9b-166">Kod daha sonra <xref:System.Data.SqlClient.SqlCommand>bir , <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliği <xref:System.Data.CommandType.StoredProcedure>ayarlar tanımlar .</span><span class="sxs-lookup"><span data-stu-id="d4e9b-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="d4e9b-167">Yöntem <xref:System.Data.SqlClient.SqlParameter> kullanılarak <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> doldurulur ve <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> `Structured`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="d4e9b-168">Daha <xref:System.Data.SqlClient.SqlCommand> sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntem kullanılarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="d4e9b-169">Tablo Değeri Nekadar Parametreli Bir Parametreyi Parametreli SQL Deyimine Geçirme</span><span class="sxs-lookup"><span data-stu-id="d4e9b-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="d4e9b-170">Aşağıdaki örnek, dbo'ya nasıl veri ekilir gösteriş gösterir. Veri kaynağı olarak tablo değeri olan bir parametreye sahip SELECT alt sorgusu içeren bir INSERT deyimi ni kullanarak kategoriler tablosu.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="d4e9b-171">Tablo değeri olan bir parametreyi parametreli SQL deyimine aktarırken, bir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. ' nin yeni özelliğini kullanarak tablo değeri taşıyan parametre için bir tür adı belirtmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="d4e9b-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d4e9b-172">Bu, `TypeName` sunucuda daha önce oluşturulmuş uyumlu bir türün adı ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d4e9b-173">Bu örnekteki kod, `TypeName` dbo'da tanımlanan tür yapısına başvurmak için özelliği kullanır. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4e9b-174">Tablo değerindeki bir parametrede bir kimlik sütunu için değer sağlıyorsanız, oturum için SET IDENTITY_INSERT deyimini vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="d4e9b-175">DataReader ile Satır Ları Akış</span><span class="sxs-lookup"><span data-stu-id="d4e9b-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="d4e9b-176">Ayrıca, tablo değeri olan <xref:System.Data.Common.DbDataReader> bir parametreye veri satırları akışı için türetilen herhangi bir nesneyi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="d4e9b-177">Aşağıdaki kod parçası, bir Oracle veritabanından bir ve <xref:System.Data.OracleClient.OracleCommand> bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="d4e9b-178">Kod daha sonra <xref:System.Data.SqlClient.SqlCommand> a'yı, tek bir giriş parametresi ile depolanan yordamı çağırmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="d4e9b-179"><xref:System.Data.SqlClient.SqlParameter> `Structured`Özelliği <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="d4e9b-180">Tablo <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> değeri `OracleDataReader` olan parametre olarak depolanan yordama ayarlanan sonucu geçer.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4e9b-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e9b-181">See also</span></span>

- [<span data-ttu-id="d4e9b-182">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4e9b-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d4e9b-183">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4e9b-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="d4e9b-184">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="d4e9b-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="d4e9b-185">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d4e9b-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="d4e9b-186">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4e9b-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
