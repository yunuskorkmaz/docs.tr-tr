---
title: Tablo Değerli Parametreler
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 316ccb19ca9e384be97a83e992af46934702aa0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780682"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="847ba-102">Tablo Değerli Parametreler</span><span class="sxs-lookup"><span data-stu-id="847ba-102">Table-Valued Parameters</span></span>
<span data-ttu-id="847ba-103">Tablo değerli parametreler, bir istemci uygulamasından birden çok veri satırını, verilerin işlenmesine yönelik birden çok gidiş dönüş veya özel sunucu tarafı mantığı gerekmeden SQL Server için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="847ba-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="847ba-104">Bir istemci uygulamasındaki veri satırlarını kapsüllemek ve verileri sunucuya tek parametreli bir komutta göndermek için tablo değerli parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="847ba-105">Gelen veri satırları, daha sonra Transact-SQL kullanılarak üzerinde çalışabilecek bir tablo değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="847ba-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="847ba-106">Tablo değerli parametrelerdeki sütun değerlerine, standart Transact-SQL SELECT deyimleri kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="847ba-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="847ba-107">Tablo değerli parametreler kesin şekilde türdedir ve yapısı otomatik olarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="847ba-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="847ba-108">Tablo değerli parametrelerin boyutu yalnızca sunucu belleği ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="847ba-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="847ba-109">Tablo değerli bir parametreye veri döndüremez.</span><span class="sxs-lookup"><span data-stu-id="847ba-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="847ba-110">Tablo değerli parametreler yalnızca giriş amaçlıdır; OUTPUT anahtar sözcüğü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="847ba-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="847ba-111">Tablo değerli parametreler hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="847ba-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="847ba-112">Kaynak</span><span class="sxs-lookup"><span data-stu-id="847ba-112">Resource</span></span>|<span data-ttu-id="847ba-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="847ba-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="847ba-114">SQL Server Books Online 'da [tablo değerli parametreler (veritabanı altyapısı)](https://go.microsoft.com/fwlink/?LinkId=98363)</span><span class="sxs-lookup"><span data-stu-id="847ba-114">[Table-Valued Parameters (Database Engine)](https://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server Books Online</span></span>|<span data-ttu-id="847ba-115">Tablo değerli parametrelerin nasıl oluşturulduğunu ve kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="847ba-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="847ba-116">SQL Server Books Online 'da [Kullanıcı tanımlı tablo türleri](https://go.microsoft.com/fwlink/?LinkId=98364)</span><span class="sxs-lookup"><span data-stu-id="847ba-116">[User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server Books Online</span></span>|<span data-ttu-id="847ba-117">Tablo değerli parametreleri bildirmek için kullanılan Kullanıcı tanımlı tablo türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="847ba-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="847ba-118">SQL Server önceki sürümlerinde birden çok satır geçirme</span><span class="sxs-lookup"><span data-stu-id="847ba-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="847ba-119">Tablo değerli parametreler SQL Server 2008 ' e sunulmadan önce, bir saklı yordama veya parametreli bir SQL komutuna birden fazla veri satırı geçirme seçenekleri sınırlandı.</span><span class="sxs-lookup"><span data-stu-id="847ba-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="847ba-120">Bir geliştirici, sunucuya birden çok satır geçirmek için aşağıdaki seçeneklerden birini seçebilir:</span><span class="sxs-lookup"><span data-stu-id="847ba-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="847ba-121">Birden çok sütundaki ve veri satırlarındaki değerleri temsil etmek için tek bir parametre serisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="847ba-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="847ba-122">Bu yöntem kullanılarak geçirilebilecek veri miktarı izin verilen parametrelerin sayısıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="847ba-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="847ba-123">SQL Server yordamlar, en çok 2100 parametreye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="847ba-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="847ba-124">Bu tek değerleri bir tablo değişkeninde veya işlemek üzere geçici bir tabloda birleştirmek için sunucu tarafı mantığı gerekir.</span><span class="sxs-lookup"><span data-stu-id="847ba-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="847ba-125">Birden çok veri değerini ayrılmış dizelere veya XML belgelerine paketleyin ve sonra bu metin değerlerini bir yordama veya ifadeye geçirin.</span><span class="sxs-lookup"><span data-stu-id="847ba-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="847ba-126">Bu yordam veya deyimin veri yapılarını doğrulamak ve değerleri yeniden paketlemek için gereken mantığı içermesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="847ba-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="847ba-127">`Update` '<xref:System.Data.SqlClient.SqlDataAdapter>In yöntemini çağırarak oluşturulanlar gibi birden çok satırı etkileyen veri değişiklikleri için bir dizi tekil SQL deyimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="847ba-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="847ba-128">Değişiklikler sunucuya ayrı ayrı veya toplu olarak gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="847ba-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="847ba-129">Ancak, birden çok deyim içeren toplu işlemlere gönderilse bile, her bir deyim sunucu üzerinde ayrı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="847ba-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="847ba-130">Bir tabloya birçok veri satırı yüklemek <xref:System.Data.SqlClient.SqlBulkCopy> için yardımcıprogramprogramınıveyanesnesinikullanın.`bcp`</span><span class="sxs-lookup"><span data-stu-id="847ba-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="847ba-131">Bu teknik çok verimli olsa da, veriler geçici bir tabloya veya tablo değişkenine yüklenmedikleri takdirde sunucu tarafı işlemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="847ba-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="847ba-132">Tablo değerli parametre türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="847ba-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="847ba-133">Tablo değerli parametreler, Transact-SQL CREATE TYPE deyimleri kullanılarak tanımlanan, kesin türü belirtilmiş tablo yapılarını temel alır.</span><span class="sxs-lookup"><span data-stu-id="847ba-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="847ba-134">İstemci uygulamalarınızda tablo değerli parametreleri kullanabilmeniz için bir tablo türü oluşturmanız ve yapıyı SQL Server tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="847ba-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="847ba-135">Tablo türleri oluşturma hakkında daha fazla bilgi için, SQL Server Books Online 'daki [Kullanıcı tanımlı tablo türleri](https://go.microsoft.com/fwlink/?LinkID=98364) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="847ba-135">For more information about creating table types, see [User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="847ba-136">Aşağıdaki ifade CategoryID ve CategoryName sütunlarından oluşan CategoryTableType adlı bir tablo türü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="847ba-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="847ba-137">Tablo türü oluşturduktan sonra, bu türe göre tablo değerli parametreler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="847ba-138">Aşağıdaki Transact-SQL parçası, saklı yordam tanımında tablo değerli bir parametre bildirme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="847ba-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="847ba-139">Tablo değerli bir parametre bildirmek için READONLY anahtar sözcüğünün gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="847ba-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="847ba-140">Tablo değerli parametrelerle verileri değiştirme (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="847ba-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="847ba-141">Tablo değerli parametreler, tek bir ifadeyi yürüterek birden çok satırı etkileyen küme tabanlı veri değişiklikleri içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="847ba-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="847ba-142">Örneğin, tablo değerli bir parametrede tüm satırları seçebilir ve bunları bir veritabanı tablosuna ekleyebilir veya tablo değerli bir parametreye güncelleştirmek istediğiniz tabloya katılarak bir Update bildirisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="847ba-143">Aşağıdaki Transact-SQL UPDATE bildiriminde, tablo değerli bir parametresinin Kategoriler tablosuna katılarak nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="847ba-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="847ba-144">FROM yan tümcesinde JOIN ile tablo değerli bir parametre kullandığınızda, burada gösterildiği gibi, aynı zamanda tablo değerli parametrenin "EC" olarak diğer adı da yer almalıdır:</span><span class="sxs-lookup"><span data-stu-id="847ba-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="847ba-145">Bu Transact-SQL örneği, tek bir küme tabanlı işlemde bir INSERT işlemini gerçekleştirmek için tablo değerli bir parametreden satırları nasıl seçeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="847ba-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="847ba-146">Tablo değerli parametrelerin sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="847ba-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="847ba-147">Tablo değerli parametrelere yönelik çeşitli sınırlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="847ba-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="847ba-148">Tablo değerli parametreleri [clr kullanıcı tanımlı işlevlere](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)geçiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="847ba-149">Tablo değerli parametrelerin yalnızca BENZERSIZ veya BIRINCIL anahtar kısıtlamalarını destekleyecek şekilde dizini oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="847ba-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="847ba-150">SQL Server tablo değerli parametrelerde istatistik bulundurmaz.</span><span class="sxs-lookup"><span data-stu-id="847ba-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="847ba-151">Tablo değerli parametreler Transact-SQL kodunda salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="847ba-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="847ba-152">Tablo değerli bir parametrenin satırlarındaki sütun değerlerini güncelleştiremezsiniz ve satır ekleyemez veya silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="847ba-153">Bir saklı yordama veya tablo değerli parametrede parametreli deyime geçirilen verileri değiştirmek için, verileri geçici bir tabloya veya tablo değişkenine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="847ba-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="847ba-154">Tablo değerli parametrelerin tasarımını değiştirmek için ALTER TABLE deyimlerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="847ba-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="847ba-155">SqlParameter örneğini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="847ba-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="847ba-156"><xref:System.Data.SqlClient><xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> veya nesnelerindentablo \  değerli parametrelerin doldurulmasına destek. <xref:System.Collections.Generic.IEnumerable%601> <xref:Microsoft.SqlServer.Server.SqlDataRecord></span><span class="sxs-lookup"><span data-stu-id="847ba-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="847ba-157">Öğesinin özelliğini<xref:System.Data.SqlClient.SqlParameter.TypeName%2A> kullanarak tablo değerli parametre için bir tür adı belirtmeniz gerekir. <xref:System.Data.SqlClient.SqlParameter></span><span class="sxs-lookup"><span data-stu-id="847ba-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="847ba-158">, `TypeName` Sunucuda daha önce oluşturulmuş olan uyumlu bir türün adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="847ba-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="847ba-159">Aşağıdaki kod parçası, verileri eklemek için nasıl <xref:System.Data.SqlClient.SqlParameter> yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="847ba-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
 
<span data-ttu-id="847ba-160">Aşağıdaki örnekte, `addedCategories` değişkeni bir <xref:System.Data.DataTable>içerir.</span><span class="sxs-lookup"><span data-stu-id="847ba-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="847ba-161">Değişkenin nasıl doldurulduğuna bakmak için, bir sonraki bölümdeki örneklere bakın ve bir [saklı yordama tablo değerli parametre geçirirsiniz](#passing).</span><span class="sxs-lookup"><span data-stu-id="847ba-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="847ba-162">Ayrıca, bu parçada gösterildiği gibi, veri <xref:System.Data.Common.DbDataReader> satırlarını tablo değerli bir parametreye akışı için öğesinden türetilmiş herhangi bir nesneyi de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="847ba-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing"></a><span data-ttu-id="847ba-163">Bir saklı yordama tablo değerli parametre geçirme</span><span class="sxs-lookup"><span data-stu-id="847ba-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="847ba-164">Bu örnek, bir saklı yordama tablo değerli parametre verilerinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="847ba-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="847ba-165">Kod, <xref:System.Data.DataTable> <xref:System.Data.DataTable.GetChanges%2A> yöntemi kullanılarak eklenen satırları yeni içine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="847ba-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="847ba-166">Kodu daha sonra bir <xref:System.Data.SqlClient.SqlCommand>tanımlar, <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliği olarak <xref:System.Data.CommandType.StoredProcedure>ayarlar.</span><span class="sxs-lookup"><span data-stu-id="847ba-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="847ba-167">, <xref:System.Data.SqlClient.SqlParameter> Yöntemi<xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> kullanılarak doldurulur ve, <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> olarak `Structured`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="847ba-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="847ba-168">Daha sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi kullanılarak yürütülür. <xref:System.Data.SqlClient.SqlCommand></span><span class="sxs-lookup"><span data-stu-id="847ba-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="847ba-169">Parametreli bir SQL bildirimine tablo değerli parametre geçirme</span><span class="sxs-lookup"><span data-stu-id="847ba-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="847ba-170">Aşağıdaki örnek, dbo 'ya nasıl veri ekleneceğini gösterir. Veri kaynağı olarak tablo değerli parametreye sahip bir SELECT deyimini içeren bir INSERT deyimini kullanarak Kategoriler tablosu.</span><span class="sxs-lookup"><span data-stu-id="847ba-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="847ba-171">Tablo değerli bir parametreyi parametreli bir SQL ifadesine geçirirken, <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>öğesinin yeni özelliğini kullanarak tablo değerli parametre için bir tür adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="847ba-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="847ba-172">Bu `TypeName` , sunucuda daha önce oluşturulmuş olan uyumlu bir türün adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="847ba-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="847ba-173">Bu örnekteki kod, dbo içinde tanımlanan `TypeName` tür yapısına başvurmak için özelliğini kullanır. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="847ba-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="847ba-174">Tablo değerli bir parametrede kimlik sütunu için bir değer sağlarsanız, oturum için SET IDENTITY_INSERT ifadesini vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="847ba-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="847ba-175">DataReader ile akış satırları</span><span class="sxs-lookup"><span data-stu-id="847ba-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="847ba-176">Ayrıca, veri satırlarını tablo değerli bir parametreye <xref:System.Data.Common.DbDataReader> akışı için öğesinden türetilmiş herhangi bir nesneyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="847ba-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="847ba-177">Aşağıdaki kod parçası, <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader>ve kullanarak bir Oracle veritabanından veri almayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="847ba-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="847ba-178">Daha sonra kod, bir <xref:System.Data.SqlClient.SqlCommand> saklı yordamı tek bir giriş parametresiyle çağırmak üzere bir yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="847ba-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="847ba-179"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Öğesinin özelliği olarak ayarlanır`Structured`. <xref:System.Data.SqlClient.SqlParameter></span><span class="sxs-lookup"><span data-stu-id="847ba-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="847ba-180">, <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` Sonuç kümesini saklı yordama tablo değerli bir parametre olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="847ba-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="847ba-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="847ba-181">See also</span></span>

- [<span data-ttu-id="847ba-182">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="847ba-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="847ba-183">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="847ba-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="847ba-184">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="847ba-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="847ba-185">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="847ba-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="847ba-186">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="847ba-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
