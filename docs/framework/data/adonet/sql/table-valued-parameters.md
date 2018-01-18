---
title: "Tablo değerli parametreleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e881213979d32cb9335f01d2804c35c19856b5e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="table-valued-parameters"></a><span data-ttu-id="5aee6-102">Tablo değerli parametreleri</span><span class="sxs-lookup"><span data-stu-id="5aee6-102">Table-Valued Parameters</span></span>
<span data-ttu-id="5aee6-103">Tablo değerli parametreleri birden çok istemci uygulamasından veri satırı sıralama için kolay bir yol sağlamak [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] verileri işlemek için birden çok gidiş dönüş veya özel bir sunucu tarafı mantık gerektiren olmadan.</span><span class="sxs-lookup"><span data-stu-id="5aee6-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="5aee6-104">Bir istemci uygulamasında veri satırı kapsüllemek ve tek bir parametreli komut sunucusuna veri gönderme için tablo değerli parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="5aee6-105">Gelen veri satırları sonra üzerinde kullanarak çalıştırılan tablo değişkeni depolanmış [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aee6-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5aee6-106">Sütun değerleri tablo değerli parametrelerinde standart kullanarak erişilebilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT deyimi.</span><span class="sxs-lookup"><span data-stu-id="5aee6-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="5aee6-107">Tablo değerli parametreleri kesin türü belirtilmiş ve bunların yapısı otomatik olarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5aee6-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="5aee6-108">Tablo değerli parametre boyutu yalnızca sunucu belleği ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5aee6-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aee6-109">Bir tablo değerli parametre veri döndüremez.</span><span class="sxs-lookup"><span data-stu-id="5aee6-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="5aee6-110">Tablo değerli parametre yalnızca değildir; Çıktı anahtar sözcüğü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5aee6-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="5aee6-111">Tablo değerli parametreleri hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="5aee6-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="5aee6-112">Kaynak</span><span class="sxs-lookup"><span data-stu-id="5aee6-112">Resource</span></span>|<span data-ttu-id="5aee6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aee6-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5aee6-114">[Tablo değerli parametreleri (veritabanı altyapısı)](http://go.microsoft.com/fwlink/?LinkId=98363) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları</span><span class="sxs-lookup"><span data-stu-id="5aee6-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="5aee6-115">Oluşturmayı ve tablo değerli parametreleri kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5aee6-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="5aee6-116">[Kullanıcı tanımlı tablo türlerinde](http://go.microsoft.com/fwlink/?LinkId=98364) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları</span><span class="sxs-lookup"><span data-stu-id="5aee6-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="5aee6-117">Tablo değerli parametreleri bildirmek için kullanılan kullanıcı tanımlı tablo türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5aee6-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="5aee6-118">SQL Server'ın önceki sürümlerinde birden çok satır geçirme</span><span class="sxs-lookup"><span data-stu-id="5aee6-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="5aee6-119">Tablo değerli parametreleri için sunulmadan önce [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, saklı yordam veya parametreli bir SQL komutu için verilerin birden çok satır geçirme seçenekleri sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5aee6-119">Before table-valued parameters were introduced to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="5aee6-120">Bir geliştirici sunucuya birden çok satır geçirme için aşağıdaki seçenekler arasından seçim:</span><span class="sxs-lookup"><span data-stu-id="5aee6-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="5aee6-121">Birden çok sütun ve veri satırı değerleri temsil etmek için bir dizi tek tek parametre kullanın.</span><span class="sxs-lookup"><span data-stu-id="5aee6-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="5aee6-122">Bu yöntem kullanılarak aktarılan veri miktarını izin parametrelerinin sayısı ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5aee6-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="5aee6-123">yordamlar, en fazla 2100 parametrelerine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-123"> procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="5aee6-124">Sunucu tarafı mantığı tablo değişkeni ya da geçici bir tablo işlem için ayrı ayrı bu değerleri derlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="5aee6-125">Birden çok veri değerleri ayrılmış dizeler veya XML belgelerini paketini ve ardından bu metin değerleri bir yordam veya deyimi geçirin.</span><span class="sxs-lookup"><span data-stu-id="5aee6-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="5aee6-126">Bu seçenek, yordam veya unbundling ve veri yapıları doğrulamak için gerekli mantığı bildirimini değerleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="5aee6-127">Bir dizi çağırarak oluşturulanlar gibi birden çok satır etkileyen veri değişiklikleri için ayrı SQL deyimi oluşturmak `Update` yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="5aee6-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="5aee6-128">Değişiklikler sunucuya gönderilen ayrı ayrı veya gruplar halinde toplu.</span><span class="sxs-lookup"><span data-stu-id="5aee6-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="5aee6-129">Ancak, hatta birden fazla deyim içeren toplu olarak gönderildiğinde her deyimi ayrı ayrı sunucu üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5aee6-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="5aee6-130">Kullanım `bcp` yardımcı programı veya <xref:System.Data.SqlClient.SqlBulkCopy> birçok veri satırı bir tabloya yüklemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="5aee6-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="5aee6-131">Bu teknik çok verimli olmakla birlikte, verileri bir geçici bir tablo veya tablo değişkeni içine yüklenir sürece, sunucu tarafı işleme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5aee6-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="5aee6-132">Tablo değerli parametre türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5aee6-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="5aee6-133">Tablo değerli parametreleri kullanılarak tanımlanmış kesin türü belirtilmiş tablo yapılarının dayanır [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE deyimleri.</span><span class="sxs-lookup"><span data-stu-id="5aee6-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="5aee6-134">Bir tablo türü oluşturmak ve yapısında tanımlamak zorunda [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] istemci uygulamalarınızda tablo değerli parametreleri kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="5aee6-134">You have to create a table type and define the structure in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="5aee6-135">Tablo türleri oluşturma hakkında daha fazla bilgi için bkz: [kullanıcı tanımlı tablo türlerinde](http://go.microsoft.com/fwlink/?LinkID=98364) içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span><span class="sxs-lookup"><span data-stu-id="5aee6-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="5aee6-136">Aşağıdaki deyim adlı kullanıcı, Categoryıd'si ve CategoryName sütundan oluşan CategoryTableType adlı bir tablo türü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5aee6-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="5aee6-137">Bir tablo türü oluşturduktan sonra o türüne göre tablo değerli parametreleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="5aee6-138">Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] parça tablo değerli bir parametre saklı yordam tanımında bildirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="5aee6-139">READONLY anahtar sözcüğü bir tablo değerli parametre bildirmek için gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5aee6-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="5aee6-140">Tablo değerli parametreleri (Transact-SQL) ile verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="5aee6-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="5aee6-141">Tablo değerli parametreleri tek bir deyimde yürüterek birden çok satır etkileyen veri kümesi tabanlı değişiklikleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="5aee6-142">Örneğin, bir tablo değerli parametre tüm satırları seçin ve bir veritabanı tablosuna eklemek veya güncelleştirmek istediğiniz tablonun tablo değerli bir parametre birleştirerek bir güncelleştirme deyimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="5aee6-143">Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] güncelleştirme deyimini kategorileri tabloya birleştirerek tablo değerli bir parametre kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="5aee6-144">Tablo değerli bir parametre FROM yan tümcesinde JOIN ile birlikte kullandığınızda, ayrıca diğer adı, burada tablo değerli parametre "AB" olarak diğer olduğu gösterildiği gibi gerekir:</span><span class="sxs-lookup"><span data-stu-id="5aee6-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="5aee6-145">Bu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] örnek tablo değerli bir parametre kümesi tabanlı tek bir işlem ile INSERT işlemi satırları seçmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="5aee6-146">Tablo değerli parametreleri sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="5aee6-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="5aee6-147">Tablo değerli parametreler için bazı sınırlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="5aee6-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="5aee6-148">Tablo değerli parametreleri geçiremezsiniz [CLR kullanıcı tanımlı işlevler](http://msdn.microsoft.com/library/ms131077.aspx).</span><span class="sxs-lookup"><span data-stu-id="5aee6-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="5aee6-149">Tablo değerli parametreleri yalnızca benzersiz veya birincil anahtar kısıtlamalarını desteklemek için sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="5aee6-150">Tablo değerli parametreleri istatistiklerle korumaz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-150"> does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="5aee6-151">Tablo değerli parametreleri salt okunur [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="5aee6-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="5aee6-152">Tablo değerli bir parametre satırlarını sütun değerleri güncelleştirilemiyor ve ekleyemez veya satırları silin.</span><span class="sxs-lookup"><span data-stu-id="5aee6-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="5aee6-153">Saklı yordama geçirilen veya tablo değerli parametre deyiminde parametreli verileri değiştirmek için geçici bir tablo veya tablo değişkeni verileri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="5aee6-154">Tablo değerli parametreleri tasarımını değiştirmek için ALTER TABLE deyimleri kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="5aee6-155">SqlParameter örnek yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5aee6-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="5aee6-156"><xref:System.Data.SqlClient>Tablo değerli parametrelerinden doldurma destekleyen <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> veya <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5aee6-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="5aee6-157">Tablo değerli parametre için bir tür adını kullanarak belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="5aee6-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="5aee6-158">`TypeName` Daha önce sunucuda oluşturulan uyumlu bir türü adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="5aee6-159">Aşağıdaki kod parçası nasıl yapılandırılacağını göstermektedir <xref:System.Data.SqlClient.SqlParameter> veri eklemek için.</span><span class="sxs-lookup"><span data-stu-id="5aee6-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
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
  
 <span data-ttu-id="5aee6-160">Türetilmiş herhangi bir nesne de kullanabilirsiniz <xref:System.Data.Common.DbDataReader> bu parçasını gösterildiği gibi tablo değerli bir parametre için veri akışı satırı için:</span><span class="sxs-lookup"><span data-stu-id="5aee6-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="5aee6-161">Tablo değerli bir parametre için bir saklı yordam geçirme</span><span class="sxs-lookup"><span data-stu-id="5aee6-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="5aee6-162">Bu örnek, bir saklı yordam tablo değerli parametre veri iletmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="5aee6-163">Kod satırlara yeni bir ayıklar <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.GetChanges%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5aee6-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="5aee6-164">Kod sonra tanımlayan bir <xref:System.Data.SqlClient.SqlCommand>, ayar <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliğine <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="5aee6-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="5aee6-165"><xref:System.Data.SqlClient.SqlParameter> Kullanılarak doldurulur <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> yöntemi ve <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ayarlanır `Structured`.</span><span class="sxs-lookup"><span data-stu-id="5aee6-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="5aee6-166"><xref:System.Data.SqlClient.SqlCommand> Kullanarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5aee6-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="5aee6-167">Parametreli SQL deyimi için tablo değerli bir parametre geçirme</span><span class="sxs-lookup"><span data-stu-id="5aee6-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="5aee6-168">Aşağıdaki örnek, dbo veri eklemek gösterilmiştir. Veri kaynağı olarak bir tablo değerli parametre içeren bir SELECT alt sorgu ile INSERT deyimi kullanarak kategorileri tablo.</span><span class="sxs-lookup"><span data-stu-id="5aee6-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="5aee6-169">Tablo değerli bir parametre parametreli bir SQL deyimi geçirirken, yeni kullanarak tablo değerli parametresi için bir tür adı belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="5aee6-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="5aee6-170">Bu `TypeName` daha önce sunucuda oluşturulan uyumlu bir türü adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="5aee6-171">Bu örnekteki kod kullanan `TypeName` dbo içinde tanımlanan tür yapısına başvurmak için özellik. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="5aee6-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aee6-172">Bir kimlik sütunu bir tablo değerli parametre için bir değer sağlarsanız, oturumu için AYARLANMIŞ IDENTITY_INSERT deyimi kesmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aee6-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="5aee6-173">DataReader akış satırları</span><span class="sxs-lookup"><span data-stu-id="5aee6-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="5aee6-174">Türetilmiş herhangi bir nesne de kullanabilirsiniz <xref:System.Data.Common.DbDataReader> tablo değerli bir parametre için veri akışı satırı için.</span><span class="sxs-lookup"><span data-stu-id="5aee6-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="5aee6-175">Aşağıdaki kod parçası kullanarak bir Oracle veritabanından veri alma gösteren bir <xref:System.Data.OracleClient.OracleCommand> ve bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="5aee6-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="5aee6-176">Kod sonra yapılandırır bir <xref:System.Data.SqlClient.SqlCommand> tek bir giriş parametresi olan bir saklı yordam çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="5aee6-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="5aee6-177"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Özelliği <xref:System.Data.SqlClient.SqlParameter> ayarlanır `Structured`.</span><span class="sxs-lookup"><span data-stu-id="5aee6-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="5aee6-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Geçirir `OracleDataReader` sonuç kümesi saklı yordama tablo değerli bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="5aee6-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5aee6-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5aee6-179">See Also</span></span>  
 [<span data-ttu-id="5aee6-180">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5aee6-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="5aee6-181">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="5aee6-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="5aee6-182">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="5aee6-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="5aee6-183">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="5aee6-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="5aee6-184">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5aee6-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
