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
# <a name="dataadapter-parameters"></a>DataAdapter Parametreleri

, Veri kaynağına veri <xref:System.Data.Common.DbDataAdapter> almak ve verileri güncelleştirmek için kullanılan dört özelliğe sahiptir: özelliği veri kaynağından <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> veri döndürür; <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> ,, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri veri kaynağındaki değişiklikleri yönetmek için kullanılır. `SelectCommand`Yöntemini çağırmadan önce özelliğin ayarlanması gerekir `Fill` `DataAdapter` . , `InsertCommand` , `UpdateCommand` Veya `DeleteCommand` özelliklerinin, `Update` `DataAdapter` içindeki verilerde yapılan değişikliklere bağlı olarak çağrılmadan önce ayarlanması gerekir <xref:System.Data.DataTable> . Örneğin, satırlar eklendiyse, `InsertCommand` çağrısından önce ayarlanmalıdır `Update` . `Update`Ekli, güncelleştirilmiş veya silinmiş bir satırı işlerken, `DataAdapter` `Command` eylemi işlemek için ilgili özelliği kullanır. Değiştirilen satır hakkındaki güncel bilgiler `Command` nesneye koleksiyon aracılığıyla geçirilir `Parameters` .  
  
 Veri kaynağındaki bir satırı güncelleştirdiğinizde, güncelleştirilecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE ifadesini çağırın. Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir. UPDATE ifadesinde, aşağıdaki Transact-SQL bildiriminde gösterildiği gibi, her iki benzersiz tanımlayıcıyı ve güncelleştirilecek sütunları ve değerleri içeren parametreler kullanılır.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır. Bu örnekte bir SQL Server veri kaynağı için yer tutucular gösterilmektedir. Ve parametreleri için soru işareti (?) yer tutucuları kullanın <xref:System.Data.OleDb> <xref:System.Data.Odbc> .  
  
 Bu Visual Basic örnekte, `CompanyName` alanı `@CompanyName` parametresinin değerine eşit olan satır için parametresinin değeri ile güncellenir `CustomerID` `@CustomerID` . Parametreler, nesne özelliğini kullanarak değiştirilen satırdan bilgi alır <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> . Önceki örnek UPDATE ifadesinin parametreleri aşağıda verilmiştir. Kod, değişkenin `adapter` geçerli bir nesneyi temsil ettiğini varsayar <xref:System.Data.SqlClient.SqlDataAdapter> .  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` `Parameters` Koleksiyonun yöntemi, parametrenin adını, veri türünü, boyutunu (Eğer varsa) ve öğesinden adını alır <xref:System.Data.Common.DbParameter.SourceColumn%2A> `DataTable` . <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` Parametresinin olarak ayarlandığını unutmayın `Original` . Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen ' de değiştirilmişse veri kaynağındaki mevcut satırın güncelleştirilmesini güvence altına alır <xref:System.Data.DataRow> . Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle eşleşir ve `Current` satır değeri güncelleştirilmiş değeri içerir. `SourceVersion` `@CompanyName` Parametresi için ayarlanmamış ve varsayılan, `Current` satır değeri kullanır.  
  
> [!NOTE]
> `Fill`Ve yöntemlerinin her iki işlemi için `DataAdapter` `Get` `DataReader` , .NET Framework türü .NET Framework veri sağlayıcısından döndürülen türden algılanır. Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri, [ADO.net Içindeki veri türü eşlemelerinde](data-type-mappings-in-ado-net.md)açıklanmıştır.  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter. SourceColumn, parametre. SourceVersion  

 `SourceColumn`Ve, `SourceVersion` oluşturucuya bağımsız değişken olarak geçirilebilir `Parameter` veya var olan bir özellik olarak ayarlanabilir `Parameter` . , `SourceColumn` <xref:System.Data.DataColumn> <xref:System.Data.DataRow> Değerinin alınacağı yerin adından oluşur `Parameter` . , `SourceVersion` `DataRow` `DataAdapter` Değerini almak için kullandığı sürümü belirtir.  
  
 Aşağıdaki tabloda <xref:System.Data.DataRowVersion> ile birlikte kullanılabilecek sabit listesi değerleri gösterilmektedir `SourceVersion` .  
  
|DataRowVersion numaralandırması|Açıklama|  
|--------------------------------|-----------------|  
|`Current`|Parametresi, sütunun geçerli değerini kullanır. Bu varsayılan seçenektir.|  
|`Default`|Parametresi, sütununun öğesini kullanır `DefaultValue` .|  
|`Original`|Parametresi, sütunun orijinal değerini kullanır.|  
|`Proposed`|Parametresi önerilen değeri kullanır.|  
  
 `SqlClient`Sonraki bölümde kod örneği, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `CustomerID` sütununun iki parametre için olarak kullanıldığı bir parametresi tanımlar `SourceColumn` : `@CustomerID` ( `SET CustomerID = @CustomerID` ) ve `@OldCustomerID` ( `WHERE CustomerID = @OldCustomerID` ). `@CustomerID`Parametresi, **MüşteriNo** sütununu içindeki geçerli değere güncelleştirmek için kullanılır `DataRow` . Sonuç olarak, ' `CustomerID` `SourceColumn` a ile birlikte `SourceVersion` `Current` kullanılır. `@OldCustomerID`Parametresi, veri kaynağındaki geçerli satırı tanımlamak için kullanılır. Eşleşen sütun değeri `Original` satırın sürümünde bulunduğundan, `SourceColumn` ile aynı ( `CustomerID` ) `SourceVersion` `Original` kullanılır.  
  
## <a name="working-with-sqlclient-parameters"></a>SqlClient parametreleriyle çalışma  

 Aşağıdaki örnek, bir oluşturma <xref:System.Data.SqlClient.SqlDataAdapter> ve <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> <xref:System.Data.MissingSchemaAction.AddWithKey> veritabanından ek şema bilgileri almak için öğesini olarak ayarlama işlemlerinin nasıl yapılacağını gösterir. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>,, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> Ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri kümesi ve bunlara karşılık gelen <xref:System.Data.SqlClient.SqlParameter> nesneler koleksiyona eklenir <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> . Yöntemi bir nesnesi döndürür `SqlDataAdapter` .  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb parametre yer tutucuları  

 <xref:System.Data.OleDb.OleDbDataAdapter>Ve nesneleri için <xref:System.Data.Odbc.OdbcDataAdapter> , parametreleri tanımlamak üzere soru işareti (?) yer tutucuları kullanmanız gerekir.  
  
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
  
 Parametreli sorgu deyimleri hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar. Bir parametre oluşturmak için, `Parameters.Add` `Parameter` sütun adı, veri türü ve boyutunu belirtmek üzere yöntemini veya oluşturucuyu kullanın. Gibi iç veri türleri için, `Integer` boyutu eklemeniz gerekmez veya varsayılan boyutu belirtebilirsiniz.  
  
 Aşağıdaki kod örneği, bir SQL deyimin parametrelerini oluşturur ve sonra bir doldurur `DataSet` .  
  
## <a name="oledb-example"></a>OleDb örneği  
  
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
  
## <a name="odbc-parameters"></a>ODBC parametreleri  
  
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
> Parametre için bir parametre adı sağlanmadığında *parametreye, "* parametre1" ile başlayarak*N* parametresinin artımlı bir varsayılan adı verilir. Bir parametre adı belirlediğinizde parametre*N* adlandırma kuralını kullanmaktan kaçınmanızı öneririz, çünkü sağladığınız ad içinde varolan bir varsayılan parametre adıyla çakışabilir `ParameterCollection` . Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
