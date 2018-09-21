---
title: DataAdapter parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539615"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="149fd-102">DataAdapter parametreleri</span><span class="sxs-lookup"><span data-stu-id="149fd-102">DataAdapter Parameters</span></span>
<span data-ttu-id="149fd-103"><xref:System.Data.Common.DbDataAdapter> Verileri almak ve verileri için veri kaynağını güncelleştirmek için kullanılan dört özelliklere sahiptir: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> özelliği veri kaynağından; veri döndürür ve <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri yönetmek için kullanılır veri kaynağındaki değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="149fd-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="149fd-104">`SelectCommand` Özelliği çağırmadan önce ayarlanmalıdır `Fill` yöntemi `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="149fd-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="149fd-105">`InsertCommand`, `UpdateCommand`, Veya `DeleteCommand` özelliklerini ayarlamak, önce `Update` yöntemi `DataAdapter` , hangi değişiklikleri verilerde yapılan bağlı olarak adlandırılır <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="149fd-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="149fd-106">Satırlar eklenir, örneğin, `InsertCommand` çağırmadan önce ayarlanmalıdır `Update`.</span><span class="sxs-lookup"><span data-stu-id="149fd-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="149fd-107">Zaman `Update` eklenen, güncelleştirilen veya silinen satır işleme `DataAdapter` ilgili kullanan `Command` eylemi işlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="149fd-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="149fd-108">Değiştirilen satır hakkında güncel bilgiler geçirildiğinde `Command` nesnesi aracılığıyla `Parameters` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="149fd-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="149fd-109">Veri kaynağındaki satırı güncelleştirmek, güncelleştirme bildirimi arama tablosunda bir satırı tanımlamak için benzersiz bir tanımlayıcı kullanan güncelleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="149fd-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="149fd-110">Benzersiz tanımlayıcı genellikle bir birincil anahtar alanı değeridir.</span><span class="sxs-lookup"><span data-stu-id="149fd-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="149fd-111">UPDATE deyimini aşağıdaki Transact-SQL deyiminde gösterildiği gibi benzersiz tanımlayıcısı ve sütunları hem güncelleştirilmesi için değerleri içeren parametrelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="149fd-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="149fd-112">Parametre yer tutucuları sözdizimi veri kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="149fd-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="149fd-113">Bu örnek, bir SQL Server veri kaynağı için yer tutucular gösterir.</span><span class="sxs-lookup"><span data-stu-id="149fd-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="149fd-114">Soru işareti (?) yer tutucuları kullanan <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="149fd-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="149fd-115">Bu Visual Basic örnekte `CompanyName` alanın değeriyle güncelleştirilir `@CompanyName` parametre satır için burada `CustomerID` değeri eşittir `@CustomerID` parametresi.</span><span class="sxs-lookup"><span data-stu-id="149fd-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="149fd-116">Değiştirilen satır kullanımından parametreleri bilgileri almak <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> özelliği <xref:System.Data.SqlClient.SqlParameter> nesne.</span><span class="sxs-lookup"><span data-stu-id="149fd-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="149fd-117">Önceki örnek UPDATE deyimi için Parametreler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="149fd-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="149fd-118">Kod olduğunu varsayar değişkeni `adapter` temsil eden geçerli bir <xref:System.Data.SqlClient.SqlDataAdapter> nesne.</span><span class="sxs-lookup"><span data-stu-id="149fd-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="149fd-119">`Add` Yöntemi `Parameters` koleksiyon parametresi adını veri türü boyutu (türüne varsa) ve adını alır <xref:System.Data.Common.DbParameter.SourceColumn%2A> gelen `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="149fd-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="149fd-120">Dikkat <xref:System.Data.Common.DbParameter.SourceVersion%2A> , `@CustomerID` parametrenin ayarlanmış `Original`.</span><span class="sxs-lookup"><span data-stu-id="149fd-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="149fd-121">Bu tanımlayıcı sütun veya sütunlar değerini değiştirilmişse, veri kaynağı olarak var olan satır güncelleştirilir garanti eder, değiştirilmiş <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="149fd-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="149fd-122">Bu durumda, `Original` satır değeri, geçerli değerin veri kaynağında eşleşir ve `Current` satır değeri, güncelleştirilmiş değeri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="149fd-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="149fd-123">`SourceVersion` İçin `@CompanyName` parametre ayarlı değil ve varsayılan olarak kullandığı `Current` satır değeri.</span><span class="sxs-lookup"><span data-stu-id="149fd-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="149fd-124">Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü döndürüldüğü türünden çıkarılan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="149fd-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="149fd-125">Çıkarsanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve Microsoft SQL Server, OLE DB ve ODBC veri türleri için erişimci metotlarını bölümünde açıklanmıştır [ADO.NET'te veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="149fd-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="149fd-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="149fd-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="149fd-127">`SourceColumn` Ve `SourceVersion` bağımsız değişken olarak geçirilebilir `Parameter` oluşturucu veya varolan özellikleri kümesi `Parameter`.</span><span class="sxs-lookup"><span data-stu-id="149fd-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="149fd-128">`SourceColumn` Adıdır <xref:System.Data.DataColumn> gelen <xref:System.Data.DataRow> nerede değerini `Parameter` alınır.</span><span class="sxs-lookup"><span data-stu-id="149fd-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="149fd-129">`SourceVersion` Belirtir `DataRow` sürümü, `DataAdapter` değerini almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="149fd-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="149fd-130">Aşağıdaki tabloda <xref:System.Data.DataRowVersion> numaralandırma değerleri için kullanılabilir kullanın ile `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="149fd-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="149fd-131">DataRowVersion numaralandırması</span><span class="sxs-lookup"><span data-stu-id="149fd-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="149fd-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="149fd-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="149fd-133">Parametresi, geçerli sütun değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="149fd-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="149fd-134">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="149fd-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="149fd-135">Parametre kullanan `DefaultValue` sütun.</span><span class="sxs-lookup"><span data-stu-id="149fd-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="149fd-136">Parametresi özgün sütununun değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="149fd-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="149fd-137">Önerilen değer parametresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="149fd-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="149fd-138">`SqlClient` Sonraki bölümde kod örneği için bir parametre tanımlayan bir <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> hangi `CustomerID` sütun olarak kullanılan bir `SourceColumn` iki parametre için: `@CustomerID` (`SET CustomerID = @CustomerID`), ve `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="149fd-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="149fd-139">`@CustomerID` Güncelleştirmek için kullanılan parametre **CustomerID** sütun geçerli değeri `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="149fd-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="149fd-140">Sonuç olarak, `CustomerID` `SourceColumn` ile bir `SourceVersion` , `Current` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="149fd-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="149fd-141">`@OldCustomerID` Parametresi veri kaynağındaki geçerli satırı tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="149fd-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="149fd-142">Eşleşen sütun değeri bulunur çünkü `Original` satır aynı sürümünü `SourceColumn` (`CustomerID`) ile bir `SourceVersion` , `Original` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="149fd-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="149fd-143">SqlClient parametreleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="149fd-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="149fd-144">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Data.SqlClient.SqlDataAdapter> ayarlayıp <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> için <xref:System.Data.MissingSchemaAction.AddWithKey> veritabanından ek şema bilgilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="149fd-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="149fd-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, Ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri kümesi ve bunlara karşılık gelen <xref:System.Data.SqlClient.SqlParameter> eklenen nesneleri <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="149fd-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="149fd-146">Yöntem döndürür bir `SqlDataAdapter` nesne.</span><span class="sxs-lookup"><span data-stu-id="149fd-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="149fd-147">OleDb parametre yer tutucuları</span><span class="sxs-lookup"><span data-stu-id="149fd-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="149fd-148">İçin <xref:System.Data.OleDb.OleDbDataAdapter> ve <xref:System.Data.Odbc.OdbcDataAdapter> nesnelerini parametrelerini belirlemek için soru işareti (?) yer tutucuları kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="149fd-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 <span data-ttu-id="149fd-149">Parametreli sorgu deyimi, giriş tanımlar ve çıkış parametreleri oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="149fd-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="149fd-150">Bir parametreyi oluşturmak üzere kullanmak `Parameters.Add` yöntemi veya `Parameter` sütun adı, veri türü ve boyutunu belirlemek için oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="149fd-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="149fd-151">İç veri türleri gibi `Integer`, boyuta dahil gerekmez veya varsayılan boyutu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="149fd-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="149fd-152">Aşağıdaki kod örneği bir SQL deyimi için parametreleri oluşturur ve ardından dolduran bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="149fd-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="149fd-153">OleDb örneği</span><span class="sxs-lookup"><span data-stu-id="149fd-153">OleDb Example</span></span>  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a><span data-ttu-id="149fd-154">ODBC parametreleri</span><span class="sxs-lookup"><span data-stu-id="149fd-154">Odbc Parameters</span></span>  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="149fd-155">Parametre adı için bir parametre sağlanmazsa, parametre parametresinin bir artımlı varsayılan ad verilir*N* *,* "Parametre1" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="149fd-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="149fd-156">Parametre kaçınmanızı öneririz*N* bir parametre adı sağlayın, mevcut bir varsayılan parametre adı ile sağladığınız ad çakışması nedeniyle adlandırma kuralı `ParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="149fd-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="149fd-157">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="149fd-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149fd-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="149fd-158">See Also</span></span>  
 [<span data-ttu-id="149fd-159">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="149fd-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="149fd-160">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="149fd-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="149fd-161">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="149fd-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="149fd-162">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="149fd-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="149fd-163">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="149fd-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="149fd-164">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="149fd-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
