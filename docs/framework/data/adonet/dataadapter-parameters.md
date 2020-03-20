---
title: DataAdapter Parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 9954570dcf33c5eea4dcccf880de2c307de0aeca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151552"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="c940a-102">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="c940a-102">DataAdapter Parameters</span></span>
<span data-ttu-id="c940a-103">Veri <xref:System.Data.Common.DbDataAdapter> kaynağından veri almak ve verileri veri kaynağına güncelleştirmek <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> için kullanılan dört özelliğe sahiptir: özellik verileri veri kaynağından döndürür; ve <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri veri kaynağındaki değişiklikleri yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="c940a-104">Özelliğin `SelectCommand` yöntemini çağırmadan `Fill` önce ayarlanabilmesi `DataAdapter`gerekir.</span><span class="sxs-lookup"><span data-stu-id="c940a-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="c940a-105">, `InsertCommand` `UpdateCommand`, `DeleteCommand` veya özellikleri denir `Update` yöntemi `DataAdapter` önce ayarlanmalıdır, hangi değişiklikler veri yapıldı bağlı <xref:System.Data.DataTable>olarak.</span><span class="sxs-lookup"><span data-stu-id="c940a-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c940a-106">Örneğin, satırlar eklendiyse, `InsertCommand` aramadan `Update`önce ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c940a-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="c940a-107">Eklenen, güncelleştirilen veya silinen bir satır `Update` `DataAdapter` işlenirken, eylemi işlemek için ilgili `Command` özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="c940a-108">Değiştirilen satırla ilgili güncel bilgiler `Command` `Parameters` koleksiyon aracılığıyla nesneye aktarılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="c940a-109">Veri kaynağında bir satırı güncelleştirdiğinizde, güncellenecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE deyimini çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="c940a-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="c940a-110">Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir.</span><span class="sxs-lookup"><span data-stu-id="c940a-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="c940a-111">UPDATE deyimi, aşağıdaki Transact-SQL deyiminde gösterildiği gibi hem benzersiz tanımlayıcıyı hem de güncellenecek sütunları ve değerleri içeren parametreler kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="c940a-112">Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c940a-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="c940a-113">Bu örnekte, bir SQL Server veri kaynağının yer tutucuları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c940a-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="c940a-114">Soru <xref:System.Data.OleDb> işareti (?) yer <xref:System.Data.Odbc> tutucularını ve parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c940a-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="c940a-115">Bu `CompanyName` Görsel Temel örnekte, alan, `@CompanyName` `CustomerID` `@CustomerID` parametrenin değerine eşit olan satırın parametresinin değeriyle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c940a-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="c940a-116">Parametreler, nesnenin özelliğini <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> kullanarak değiştirilen satırdan bilgi alır. <xref:System.Data.SqlClient.SqlParameter></span><span class="sxs-lookup"><span data-stu-id="c940a-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="c940a-117">Önceki örnek UPDATE deyiminin parametreleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c940a-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="c940a-118">Kod, değişkenin `adapter` geçerli <xref:System.Data.SqlClient.SqlDataAdapter> bir nesneyi temsil ettiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="c940a-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="c940a-119">`Parameters` Toplama `Add` yöntemi parametrenin adını, veri türünü, boyutunu (türe uygunsa) ve <xref:System.Data.Common.DbParameter.SourceColumn%2A> `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="c940a-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="c940a-120">Parametrenin `Original`' in ' olarak ayarlı olduğuna dikkat edin `@CustomerID` <xref:System.Data.Common.DbParameter.SourceVersion%2A></span><span class="sxs-lookup"><span data-stu-id="c940a-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="c940a-121">Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen <xref:System.Data.DataRow>değiştirildiyse, veri kaynağındaki varolan satırın güncelleştirildiğini garanti eder.</span><span class="sxs-lookup"><span data-stu-id="c940a-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="c940a-122">Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle `Current` eşleşir ve satır değeri güncelleştirilmiş değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="c940a-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="c940a-123">`SourceVersion` For `@CompanyName` parametresi ayarlanmaz ve varsayılan `Current` satır değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c940a-124">.NET `Fill` Framework türü, hem iştretleri `DataAdapter` hem de `Get` .NET `DataReader`Framework veri sağlayıcısından döndürülen türden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="c940a-125">Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri [ADO.NET'daki Veri Türü Eşlemeleri'nde](data-type-mappings-in-ado-net.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c940a-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="c940a-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="c940a-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="c940a-127">Ve `SourceColumn` `SourceVersion` `Parameter` oluşturucuya bağımsız değişken olarak geçirilebilir veya varolan `Parameter`bir .</span><span class="sxs-lookup"><span data-stu-id="c940a-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="c940a-128">Bu, `SourceColumn` alacağın <xref:System.Data.DataColumn> değerinin <xref:System.Data.DataRow> alındığı yerden gelen in adıdır. `Parameter`</span><span class="sxs-lookup"><span data-stu-id="c940a-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="c940a-129">Değer `SourceVersion` almak için `DataRow` `DataAdapter` kullandığı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c940a-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="c940a-130">Aşağıdaki tabloda <xref:System.Data.DataRowVersion> kullanılabilir numaralandırma değerleri gösterilmektedir. `SourceVersion`</span><span class="sxs-lookup"><span data-stu-id="c940a-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="c940a-131">DataRowVersion Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="c940a-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="c940a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c940a-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="c940a-133">Parametre sütunun geçerli değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="c940a-134">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c940a-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="c940a-135">Parametre sütunun `DefaultValue` kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="c940a-136">Parametre sütunun özgün değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="c940a-137">Parametre önerilen bir değer kullanır.</span><span class="sxs-lookup"><span data-stu-id="c940a-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="c940a-138">Sonraki `SqlClient` bölümdeki <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> kod örneği, sütunun `CustomerID` iki parametre `SourceColumn` için kullanıldığı bir parametreyi tanımlar:`WHERE CustomerID = @OldCustomerID` `@CustomerID` (`SET CustomerID = @CustomerID`), ve `@OldCustomerID` ( ).</span><span class="sxs-lookup"><span data-stu-id="c940a-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="c940a-139">Parametre, **CustomerID** sütunundaki geçerli değere güncelleştirmek için `DataRow`kullanılır. `@CustomerID`</span><span class="sxs-lookup"><span data-stu-id="c940a-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="c940a-140">Sonuç `CustomerID` `SourceColumn` olarak, bir `SourceVersion` ile `Current` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="c940a-141">`@OldCustomerID` Parametre, veri kaynağındaki geçerli satırı tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="c940a-142">Eşleşen sütun değeri `Original` satırın sürümünde bulunduğundan, `SourceColumn` a`CustomerID` `SourceVersion` `Original` ile aynı ( ) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="c940a-143">SqlClient Parametreleri ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="c940a-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="c940a-144">Aşağıdaki örnek, veritabanından ek <xref:System.Data.SqlClient.SqlDataAdapter> şema <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> bilgileri almak için nasıl oluşturulup ayarlanınmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c940a-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="c940a-145">, <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> ve özellikleri <xref:System.Data.SqlClient.SqlParameter> kümesi ve bunların <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> karşılık gelen nesneleri koleksiyona eklendi.</span><span class="sxs-lookup"><span data-stu-id="c940a-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="c940a-146">Yöntem bir `SqlDataAdapter` nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c940a-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="c940a-147">OleDb Parametre Yer Tutucular</span><span class="sxs-lookup"><span data-stu-id="c940a-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="c940a-148">Parametreleri <xref:System.Data.OleDb.OleDbDataAdapter> <xref:System.Data.Odbc.OdbcDataAdapter> tanımlamak için soru işareti (?) yer tutucuları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c940a-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="c940a-149">Parametreli sorgu deyimleri, hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c940a-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="c940a-150">Bir parametre oluşturmak için, sütun adını, veri türünü ve boyutunu belirtmek için `Parameters.Add` yöntemi veya `Parameter` oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c940a-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="c940a-151">Gibi içsel veri türleri için `Integer`, boyutu eklemek zorunda değildir, ya da varsayılan boyutu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c940a-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="c940a-152">Aşağıdaki kod örneği, BIR SQL deyimi için parametreleroluşturur `DataSet`ve sonra bir .</span><span class="sxs-lookup"><span data-stu-id="c940a-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="c940a-153">OleDb Örneği</span><span class="sxs-lookup"><span data-stu-id="c940a-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="c940a-154">Odbc Parametreleri</span><span class="sxs-lookup"><span data-stu-id="c940a-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="c940a-155">Bir parametre adı bir parametre için sağlanmazsa, parametreye "Parameter1" ile *başlayan* *N* parametresi artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="c940a-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="c940a-156">Bir parametre adı sağladığınızda Parametre*N* adlandırma kuralından kaçınmanızı öneririz, çünkü sağladığınız ad. `ParameterCollection`</span><span class="sxs-lookup"><span data-stu-id="c940a-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="c940a-157">Sağlanan ad zaten varsa, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="c940a-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c940a-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c940a-158">See also</span></span>

- [<span data-ttu-id="c940a-159">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="c940a-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="c940a-160">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="c940a-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="c940a-161">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c940a-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="c940a-162">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c940a-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="c940a-163">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="c940a-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="c940a-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c940a-164">ADO.NET Overview</span></span>](ado-net-overview.md)
