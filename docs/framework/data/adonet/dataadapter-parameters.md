---
title: DataAdapter Parametreleri
description: Veri kaynağından veri döndüren ve veri kaynağındaki değişiklikleri yöneten DbDataAdapter 'ın özellikleri hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 1264d678b4823149498150f13d8783a82890f6a0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177721"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="97897-103">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="97897-103">DataAdapter Parameters</span></span>

<span data-ttu-id="97897-104">, Veri kaynağına veri <xref:System.Data.Common.DbDataAdapter> almak ve verileri güncelleştirmek için kullanılan dört özelliğe sahiptir: özelliği veri kaynağından <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> veri döndürür; <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> ,, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri veri kaynağındaki değişiklikleri yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97897-104">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="97897-105">`SelectCommand`Yöntemini çağırmadan önce özelliğin ayarlanması gerekir `Fill` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="97897-105">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="97897-106">, `InsertCommand` , `UpdateCommand` Veya `DeleteCommand` özelliklerinin, `Update` `DataAdapter` içindeki verilerde yapılan değişikliklere bağlı olarak çağrılmadan önce ayarlanması gerekir <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="97897-106">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="97897-107">Örneğin, satırlar eklendiyse, `InsertCommand` çağrısından önce ayarlanmalıdır `Update` .</span><span class="sxs-lookup"><span data-stu-id="97897-107">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="97897-108">`Update`Ekli, güncelleştirilmiş veya silinmiş bir satırı işlerken, `DataAdapter` `Command` eylemi işlemek için ilgili özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="97897-108">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="97897-109">Değiştirilen satır hakkındaki güncel bilgiler `Command` nesneye koleksiyon aracılığıyla geçirilir `Parameters` .</span><span class="sxs-lookup"><span data-stu-id="97897-109">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="97897-110">Veri kaynağındaki bir satırı güncelleştirdiğinizde, güncelleştirilecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE ifadesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97897-110">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="97897-111">Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir.</span><span class="sxs-lookup"><span data-stu-id="97897-111">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="97897-112">UPDATE ifadesinde, aşağıdaki Transact-SQL bildiriminde gösterildiği gibi, her iki benzersiz tanımlayıcıyı ve güncelleştirilecek sütunları ve değerleri içeren parametreler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97897-112">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="97897-113">Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="97897-113">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="97897-114">Bu örnekte bir SQL Server veri kaynağı için yer tutucular gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="97897-114">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="97897-115">Ve parametreleri için soru işareti (?) yer tutucuları kullanın <xref:System.Data.OleDb> <xref:System.Data.Odbc> .</span><span class="sxs-lookup"><span data-stu-id="97897-115">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="97897-116">Bu Visual Basic örnekte, `CompanyName` alanı `@CompanyName` parametresinin değerine eşit olan satır için parametresinin değeri ile güncellenir `CustomerID` `@CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="97897-116">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="97897-117">Parametreler, nesne özelliğini kullanarak değiştirilen satırdan bilgi alır <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="97897-117">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="97897-118">Önceki örnek UPDATE ifadesinin parametreleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97897-118">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="97897-119">Kod, değişkenin `adapter` geçerli bir nesneyi temsil ettiğini varsayar <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="97897-119">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="97897-120">`Add` `Parameters` Koleksiyonun yöntemi, parametrenin adını, veri türünü, boyutunu (Eğer varsa) ve öğesinden adını alır <xref:System.Data.Common.DbParameter.SourceColumn%2A> `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="97897-120">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="97897-121"><xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` Parametresinin olarak ayarlandığını unutmayın `Original` .</span><span class="sxs-lookup"><span data-stu-id="97897-121">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="97897-122">Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen ' de değiştirilmişse veri kaynağındaki mevcut satırın güncelleştirilmesini güvence altına alır <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="97897-122">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="97897-123">Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle eşleşir ve `Current` satır değeri güncelleştirilmiş değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="97897-123">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="97897-124">`SourceVersion` `@CompanyName` Parametresi için ayarlanmamış ve varsayılan, `Current` satır değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="97897-124">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97897-125">`Fill`Ve yöntemlerinin her iki işlemi için `DataAdapter` `Get` `DataReader` , .NET Framework türü .NET Framework veri sağlayıcısından döndürülen türden algılanır.</span><span class="sxs-lookup"><span data-stu-id="97897-125">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="97897-126">Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri, [ADO.net Içindeki veri türü eşlemelerinde](data-type-mappings-in-ado-net.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97897-126">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="97897-127">Parameter. SourceColumn, parametre. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="97897-127">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  

 <span data-ttu-id="97897-128">`SourceColumn`Ve, `SourceVersion` oluşturucuya bağımsız değişken olarak geçirilebilir `Parameter` veya var olan bir özellik olarak ayarlanabilir `Parameter` .</span><span class="sxs-lookup"><span data-stu-id="97897-128">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="97897-129">, `SourceColumn` <xref:System.Data.DataColumn> <xref:System.Data.DataRow> Değerinin alınacağı yerin adından oluşur `Parameter` .</span><span class="sxs-lookup"><span data-stu-id="97897-129">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="97897-130">, `SourceVersion` `DataRow` `DataAdapter` Değerini almak için kullandığı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="97897-130">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="97897-131">Aşağıdaki tabloda <xref:System.Data.DataRowVersion> ile birlikte kullanılabilecek sabit listesi değerleri gösterilmektedir `SourceVersion` .</span><span class="sxs-lookup"><span data-stu-id="97897-131">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="97897-132">DataRowVersion numaralandırması</span><span class="sxs-lookup"><span data-stu-id="97897-132">DataRowVersion Enumeration</span></span>|<span data-ttu-id="97897-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97897-133">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="97897-134">Parametresi, sütunun geçerli değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="97897-134">The parameter uses the current value of the column.</span></span> <span data-ttu-id="97897-135">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="97897-135">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="97897-136">Parametresi, sütununun öğesini kullanır `DefaultValue` .</span><span class="sxs-lookup"><span data-stu-id="97897-136">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="97897-137">Parametresi, sütunun orijinal değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="97897-137">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="97897-138">Parametresi önerilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="97897-138">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="97897-139">`SqlClient`Sonraki bölümde kod örneği, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `CustomerID` sütununun iki parametre için olarak kullanıldığı bir parametresi tanımlar `SourceColumn` : `@CustomerID` ( `SET CustomerID = @CustomerID` ) ve `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ).</span><span class="sxs-lookup"><span data-stu-id="97897-139">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="97897-140">`@CustomerID`Parametresi, **MüşteriNo** sütununu içindeki geçerli değere güncelleştirmek için kullanılır `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="97897-140">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="97897-141">Sonuç olarak, ' `CustomerID` `SourceColumn` a ile birlikte `SourceVersion` `Current` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97897-141">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="97897-142">`@OldCustomerID`Parametresi, veri kaynağındaki geçerli satırı tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97897-142">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="97897-143">Eşleşen sütun değeri `Original` satırın sürümünde bulunduğundan, `SourceColumn` ile aynı ( `CustomerID` ) `SourceVersion` `Original` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97897-143">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="97897-144">SqlClient parametreleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="97897-144">Working with SqlClient Parameters</span></span>  

 <span data-ttu-id="97897-145">Aşağıdaki örnek, bir oluşturma <xref:System.Data.SqlClient.SqlDataAdapter> ve <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> veritabanından ek şema bilgileri almak için öğesini olarak ayarlama işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97897-145">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="97897-146"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>,, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> Ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri kümesi ve bunlara karşılık gelen <xref:System.Data.SqlClient.SqlParameter> nesneler koleksiyona eklenir <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> .</span><span class="sxs-lookup"><span data-stu-id="97897-146">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="97897-147">Yöntemi bir nesnesi döndürür `SqlDataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="97897-147">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="97897-148">OleDb parametre yer tutucuları</span><span class="sxs-lookup"><span data-stu-id="97897-148">OleDb Parameter Placeholders</span></span>  

 <span data-ttu-id="97897-149"><xref:System.Data.OleDb.OleDbDataAdapter>Ve nesneleri için <xref:System.Data.Odbc.OdbcDataAdapter> , parametreleri tanımlamak üzere soru işareti (?) yer tutucuları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="97897-149">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="97897-150">Parametreli sorgu deyimleri hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97897-150">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="97897-151">Bir parametre oluşturmak için, `Parameters.Add` `Parameter` sütun adı, veri türü ve boyutunu belirtmek üzere yöntemini veya oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="97897-151">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="97897-152">Gibi iç veri türleri için, `Integer` boyutu eklemeniz gerekmez veya varsayılan boyutu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97897-152">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="97897-153">Aşağıdaki kod örneği, bir SQL deyimin parametrelerini oluşturur ve sonra bir doldurur `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="97897-153">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="97897-154">OleDb örneği</span><span class="sxs-lookup"><span data-stu-id="97897-154">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="97897-155">ODBC parametreleri</span><span class="sxs-lookup"><span data-stu-id="97897-155">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="97897-156">Parametre için bir parametre adı sağlanmadığında *parametreye, "* parametre1" ile başlayarak*N* parametresinin artımlı bir varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="97897-156">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="97897-157">Bir parametre adı belirlediğinizde parametre*N* adlandırma kuralını kullanmaktan kaçınmanızı öneririz, çünkü sağladığınız ad içinde varolan bir varsayılan parametre adıyla çakışabilir `ParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="97897-157">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="97897-158">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97897-158">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97897-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97897-159">See also</span></span>

- [<span data-ttu-id="97897-160">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="97897-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="97897-161">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="97897-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="97897-162">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="97897-162">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="97897-163">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="97897-163">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="97897-164">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="97897-164">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="97897-165">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97897-165">ADO.NET Overview</span></span>](ado-net-overview.md)
