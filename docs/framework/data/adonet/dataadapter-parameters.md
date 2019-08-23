---
title: DataAdapter Parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 772763b5927ca845d6c2ccba50382652e410ae4f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951237"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="cee44-102">DataAdapter Parametreleri</span><span class="sxs-lookup"><span data-stu-id="cee44-102">DataAdapter Parameters</span></span>
<span data-ttu-id="cee44-103">, <xref:System.Data.Common.DbDataAdapter> Veri kaynağına veri almak ve verileri güncelleştirmek için kullanılan dört özelliğe sahiptir <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> : özelliği <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> veri kaynağından veri döndürür;, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri yönetmek için kullanılır veri kaynağındaki değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="cee44-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="cee44-104">Yöntemini çağırmadan önce `SelectCommand` özelliğin ayarlanması gerekir `DataAdapter`. `Fill`</span><span class="sxs-lookup"><span data-stu-id="cee44-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="cee44-105">`Update` ,,`DataAdapter` Veya özelliklerinin,<xref:System.Data.DataTable>içindeki verilerde yapılan değişikliklere bağlı olarak çağrılmadan önce ayarlanması gerekir. `DeleteCommand` `InsertCommand` `UpdateCommand`</span><span class="sxs-lookup"><span data-stu-id="cee44-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="cee44-106">Örneğin, satırlar eklendiyse `InsertCommand` , çağrısından `Update`önce ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cee44-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="cee44-107">Ekli, güncelleştirilmiş veya silinmiş bir satırı `DataAdapter` işlerken, eylemi işlemek için ilgili `Command` özelliği kullanır. `Update`</span><span class="sxs-lookup"><span data-stu-id="cee44-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="cee44-108">Değiştirilen satır hakkındaki güncel bilgiler `Command` nesneye `Parameters` koleksiyon aracılığıyla geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cee44-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="cee44-109">Veri kaynağındaki bir satırı güncelleştirdiğinizde, güncelleştirilecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE ifadesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="cee44-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="cee44-110">Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir.</span><span class="sxs-lookup"><span data-stu-id="cee44-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="cee44-111">UPDATE ifadesinde, aşağıdaki Transact-SQL bildiriminde gösterildiği gibi, her iki benzersiz tanımlayıcıyı ve güncelleştirilecek sütunları ve değerleri içeren parametreler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cee44-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="cee44-112">Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cee44-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="cee44-113">Bu örnekte bir SQL Server veri kaynağı için yer tutucular gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cee44-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="cee44-114"><xref:System.Data.OleDb> Ve<xref:System.Data.Odbc> parametreleri için soru işareti (?) yer tutucuları kullanın.</span><span class="sxs-lookup"><span data-stu-id="cee44-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="cee44-115">Bu Visual Basic `CompanyName` örnekte, alanı `@CustomerID` parametresinin değerine `CustomerID` eşit olan satır için `@CompanyName` parametresinin değeri ile güncellenir.</span><span class="sxs-lookup"><span data-stu-id="cee44-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="cee44-116">Parametreler, <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> nesne özelliğini kullanarak değiştirilen satırdan bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="cee44-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="cee44-117">Önceki örnek UPDATE ifadesinin parametreleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cee44-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="cee44-118">Kod, değişkenin `adapter` geçerli <xref:System.Data.SqlClient.SqlDataAdapter> bir nesneyi temsil ettiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="cee44-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="cee44-119">Koleksiyonun yöntemi, parametrenin adını, veri türünü, boyutunu (Eğer varsa) <xref:System.Data.Common.DbParameter.SourceColumn%2A> ve öğesinden `DataTable`adını alır. `Add` `Parameters`</span><span class="sxs-lookup"><span data-stu-id="cee44-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="cee44-120">Parametresinin olarak ayarlandığınıunutmayın`Original`. <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID`</span><span class="sxs-lookup"><span data-stu-id="cee44-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="cee44-121">Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen <xref:System.Data.DataRow>' de değiştirilmişse veri kaynağındaki mevcut satırın güncelleştirilmesini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="cee44-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="cee44-122">Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle eşleşir `Current` ve satır değeri güncelleştirilmiş değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="cee44-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="cee44-123">Parametresi için ayarlanmamış ve varsayılan, `Current` satır değeri kullanır. `SourceVersion` `@CompanyName`</span><span class="sxs-lookup"><span data-stu-id="cee44-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cee44-124">Ve yöntemlerinin her `Fill`iki işlemiiçin,.NETFrameworktürü.NETFrameworkverisağlayıcısındandöndürülentürdenalgılanır.`Get` `DataAdapter` `DataReader`</span><span class="sxs-lookup"><span data-stu-id="cee44-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="cee44-125">Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri, [ADO.net Içindeki veri türü eşlemelerinde](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cee44-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="cee44-126">Parameter. SourceColumn, parametre. SourceVersion</span><span class="sxs-lookup"><span data-stu-id="cee44-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="cee44-127">Ve, oluşturucuya bağımsız değişken olarak `Parameter`geçirilebilir veya var olan bir özellik olarak ayarlanabilir. `Parameter` `SourceVersion` `SourceColumn`</span><span class="sxs-lookup"><span data-stu-id="cee44-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="cee44-128">, Değerinin <xref:System.Data.DataColumn> alınacağıyerin<xref:System.Data.DataRow> adından oluşur. `Parameter` `SourceColumn`</span><span class="sxs-lookup"><span data-stu-id="cee44-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="cee44-129">, `SourceVersion` Değerini almak `DataRow` için `DataAdapter` kullandığı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cee44-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="cee44-130">Aşağıdaki tabloda ile birlikte <xref:System.Data.DataRowVersion> `SourceVersion`kullanılabilecek sabit listesi değerleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cee44-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="cee44-131">DataRowVersion numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cee44-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="cee44-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cee44-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="cee44-133">Parametresi, sütunun geçerli değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cee44-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="cee44-134">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cee44-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="cee44-135">Parametresi, sütununun öğesini `DefaultValue` kullanır.</span><span class="sxs-lookup"><span data-stu-id="cee44-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="cee44-136">Parametresi, sütunun orijinal değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cee44-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="cee44-137">Parametresi önerilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="cee44-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="cee44-138">`@CustomerID` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `SourceColumn` `SET CustomerID = @CustomerID``WHERE CustomerID = @OldCustomerID` `@OldCustomerID` Sonraki bölümde `CustomerID` kod örneği, sütununun iki parametre için olarak kullanıldığı bir parametresi tanımlar: () ve (). `SqlClient`</span><span class="sxs-lookup"><span data-stu-id="cee44-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="cee44-139">Parametresi, **MüşteriNo sütununu** içindeki geçerli değere güncelleştirmek için kullanılır. `DataRow` `@CustomerID`</span><span class="sxs-lookup"><span data-stu-id="cee44-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="cee44-140">`CustomerID` Sonuç olarak, ' `SourceColumn` a `SourceVersion` ilebirliktekullanılır`Current` .</span><span class="sxs-lookup"><span data-stu-id="cee44-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="cee44-141">`@OldCustomerID` Parametresi, veri kaynağındaki geçerli satırı tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cee44-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="cee44-142">Eşleşen sütun `Original` değeri satırın sürümünde bulunduğundan, ile `SourceVersion` `Original` aynı `SourceColumn` (`CustomerID`) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cee44-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="cee44-143">SqlClient parametreleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="cee44-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="cee44-144">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> bir oluşturma ve veritabanından ek şema bilgileri almak için <xref:System.Data.MissingSchemaAction.AddWithKey> öğesini olarak ayarlama işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cee44-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="cee44-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> , ,<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>Ve özelliklerikümesi<xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> ve bunlara karşılık gelen nesneler koleksiyona eklenir. <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A></span><span class="sxs-lookup"><span data-stu-id="cee44-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="cee44-146">Yöntemi bir `SqlDataAdapter` nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="cee44-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="cee44-147">OleDb parametre yer tutucuları</span><span class="sxs-lookup"><span data-stu-id="cee44-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="cee44-148"><xref:System.Data.OleDb.OleDbDataAdapter> Ve<xref:System.Data.Odbc.OdbcDataAdapter> nesneleri için, parametreleri tanımlamak üzere soru işareti (?) yer tutucuları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cee44-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="cee44-149">Parametreli sorgu deyimleri hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cee44-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="cee44-150">Bir parametre oluşturmak için, sütun adı `Parameters.Add` , veri türü `Parameter` ve boyutunu belirtmek üzere yöntemini veya oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cee44-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="cee44-151">Gibi iç veri türleri `Integer`için, boyutu eklemeniz gerekmez veya varsayılan boyutu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cee44-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="cee44-152">Aşağıdaki kod örneği, bir SQL deyimin parametrelerini oluşturur ve sonra bir `DataSet`doldurur.</span><span class="sxs-lookup"><span data-stu-id="cee44-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="cee44-153">OleDb örneği</span><span class="sxs-lookup"><span data-stu-id="cee44-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="cee44-154">ODBC parametreleri</span><span class="sxs-lookup"><span data-stu-id="cee44-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="cee44-155">Parametre için bir parametre adı sağlanmadığında parametreye, "parametre1" ile başlayarak*N* parametresinin artımlı bir varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="cee44-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="cee44-156">Bir parametre adı belirlediğinizde parametre*N* adlandırma kuralını kullanmaktan kaçınmanızı öneririz, çünkü sağladığınız ad içinde `ParameterCollection`varolan bir varsayılan parametre adıyla çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="cee44-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="cee44-157">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cee44-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee44-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cee44-158">See also</span></span>

- [<span data-ttu-id="cee44-159">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="cee44-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="cee44-160">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="cee44-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="cee44-161">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cee44-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="cee44-162">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="cee44-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="cee44-163">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cee44-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="cee44-164">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="cee44-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
