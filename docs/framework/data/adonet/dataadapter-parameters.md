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
# <a name="dataadapter-parameters"></a>DataAdapter Parametreleri
Veri <xref:System.Data.Common.DbDataAdapter> kaynağından veri almak ve verileri veri kaynağına güncelleştirmek <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> için kullanılan dört özelliğe sahiptir: özellik verileri veri kaynağından döndürür; ve <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri veri kaynağındaki değişiklikleri yönetmek için kullanılır. Özelliğin `SelectCommand` yöntemini çağırmadan `Fill` önce ayarlanabilmesi `DataAdapter`gerekir. , `InsertCommand` `UpdateCommand`, `DeleteCommand` veya özellikleri denir `Update` yöntemi `DataAdapter` önce ayarlanmalıdır, hangi değişiklikler veri yapıldı bağlı <xref:System.Data.DataTable>olarak. Örneğin, satırlar eklendiyse, `InsertCommand` aramadan `Update`önce ayarlanmalıdır. Eklenen, güncelleştirilen veya silinen bir satır `Update` `DataAdapter` işlenirken, eylemi işlemek için ilgili `Command` özelliği kullanır. Değiştirilen satırla ilgili güncel bilgiler `Command` `Parameters` koleksiyon aracılığıyla nesneye aktarılır.  
  
 Veri kaynağında bir satırı güncelleştirdiğinizde, güncellenecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE deyimini çağırırsınız. Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir. UPDATE deyimi, aşağıdaki Transact-SQL deyiminde gösterildiği gibi hem benzersiz tanımlayıcıyı hem de güncellenecek sütunları ve değerleri içeren parametreler kullanır.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır. Bu örnekte, bir SQL Server veri kaynağının yer tutucuları gösterilmektedir. Soru <xref:System.Data.OleDb> işareti (?) yer <xref:System.Data.Odbc> tutucularını ve parametreleri kullanın.  
  
 Bu `CompanyName` Görsel Temel örnekte, alan, `@CompanyName` `CustomerID` `@CustomerID` parametrenin değerine eşit olan satırın parametresinin değeriyle güncelleştirilir. Parametreler, nesnenin özelliğini <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> kullanarak değiştirilen satırdan bilgi alır. <xref:System.Data.SqlClient.SqlParameter> Önceki örnek UPDATE deyiminin parametreleri aşağıda verilmiştir. Kod, değişkenin `adapter` geçerli <xref:System.Data.SqlClient.SqlDataAdapter> bir nesneyi temsil ettiğini varsayar.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Parameters` Toplama `Add` yöntemi parametrenin adını, veri türünü, boyutunu (türe uygunsa) ve <xref:System.Data.Common.DbParameter.SourceColumn%2A> `DataTable`. Parametrenin `Original`' in ' olarak ayarlı olduğuna dikkat edin `@CustomerID` <xref:System.Data.Common.DbParameter.SourceVersion%2A> Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen <xref:System.Data.DataRow>değiştirildiyse, veri kaynağındaki varolan satırın güncelleştirildiğini garanti eder. Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle `Current` eşleşir ve satır değeri güncelleştirilmiş değeri içerir. `SourceVersion` For `@CompanyName` parametresi ayarlanmaz ve varsayılan `Current` satır değerini kullanır.  
  
> [!NOTE]
> .NET `Fill` Framework türü, hem iştretleri `DataAdapter` hem de `Get` .NET `DataReader`Framework veri sağlayıcısından döndürülen türden çıkarılır. Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri [ADO.NET'daki Veri Türü Eşlemeleri'nde](data-type-mappings-in-ado-net.md)açıklanmıştır.  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 Ve `SourceColumn` `SourceVersion` `Parameter` oluşturucuya bağımsız değişken olarak geçirilebilir veya varolan `Parameter`bir . Bu, `SourceColumn` alacağın <xref:System.Data.DataColumn> değerinin <xref:System.Data.DataRow> alındığı yerden gelen in adıdır. `Parameter` Değer `SourceVersion` almak için `DataRow` `DataAdapter` kullandığı sürümü belirtir.  
  
 Aşağıdaki tabloda <xref:System.Data.DataRowVersion> kullanılabilir numaralandırma değerleri gösterilmektedir. `SourceVersion`  
  
|DataRowVersion Numaralandırma|Açıklama|  
|--------------------------------|-----------------|  
|`Current`|Parametre sütunun geçerli değerini kullanır. Bu varsayılandır.|  
|`Default`|Parametre sütunun `DefaultValue` kullanır.|  
|`Original`|Parametre sütunun özgün değerini kullanır.|  
|`Proposed`|Parametre önerilen bir değer kullanır.|  
  
 Sonraki `SqlClient` bölümdeki <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> kod örneği, sütunun `CustomerID` iki parametre `SourceColumn` için kullanıldığı bir parametreyi tanımlar:`WHERE CustomerID = @OldCustomerID` `@CustomerID` (`SET CustomerID = @CustomerID`), ve `@OldCustomerID` ( ). Parametre, **CustomerID** sütunundaki geçerli değere güncelleştirmek için `DataRow`kullanılır. `@CustomerID` Sonuç `CustomerID` `SourceColumn` olarak, bir `SourceVersion` ile `Current` kullanılır. `@OldCustomerID` Parametre, veri kaynağındaki geçerli satırı tanımlamak için kullanılır. Eşleşen sütun değeri `Original` satırın sürümünde bulunduğundan, `SourceColumn` a`CustomerID` `SourceVersion` `Original` ile aynı ( ) kullanılır.  
  
## <a name="working-with-sqlclient-parameters"></a>SqlClient Parametreleri ile Çalışma  
 Aşağıdaki örnek, veritabanından ek <xref:System.Data.SqlClient.SqlDataAdapter> şema <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> bilgileri almak için nasıl oluşturulup ayarlanınmayı gösterir. , <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> ve özellikleri <xref:System.Data.SqlClient.SqlParameter> kümesi ve bunların <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> karşılık gelen nesneleri koleksiyona eklendi. Yöntem bir `SqlDataAdapter` nesneyi döndürür.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb Parametre Yer Tutucular  
 Parametreleri <xref:System.Data.OleDb.OleDbDataAdapter> <xref:System.Data.Odbc.OdbcDataAdapter> tanımlamak için soru işareti (?) yer tutucuları kullanmanız gerekir.  
  
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
  
 Parametreli sorgu deyimleri, hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar. Bir parametre oluşturmak için, sütun adını, veri türünü ve boyutunu belirtmek için `Parameters.Add` yöntemi veya `Parameter` oluşturucuyu kullanın. Gibi içsel veri türleri için `Integer`, boyutu eklemek zorunda değildir, ya da varsayılan boyutu belirtebilirsiniz.  
  
 Aşağıdaki kod örneği, BIR SQL deyimi için parametreleroluşturur `DataSet`ve sonra bir .  
  
## <a name="oledb-example"></a>OleDb Örneği  
  
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
  
## <a name="odbc-parameters"></a>Odbc Parametreleri  
  
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
> Bir parametre adı bir parametre için sağlanmazsa, parametreye "Parameter1" ile *başlayan* *N* parametresi artımlı varsayılan adı verilir. Bir parametre adı sağladığınızda Parametre*N* adlandırma kuralından kaçınmanızı öneririz, çünkü sağladığınız ad. `ParameterCollection` Sağlanan ad zaten varsa, bir özel durum atılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
