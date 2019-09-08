---
title: DataAdapter Parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 83fc3101b0eb428def6cbc446e634e9bb45de350
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785603"
---
# <a name="dataadapter-parameters"></a>DataAdapter Parametreleri
, <xref:System.Data.Common.DbDataAdapter> Veri kaynağına veri almak ve verileri güncelleştirmek için kullanılan dört özelliğe sahiptir <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> : özelliği <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> veri kaynağından veri döndürür;, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri yönetmek için kullanılır veri kaynağındaki değişiklikler. Yöntemini çağırmadan önce `SelectCommand` özelliğin ayarlanması gerekir `DataAdapter`. `Fill` `Update` ,,`DataAdapter` Veya özelliklerinin,<xref:System.Data.DataTable>içindeki verilerde yapılan değişikliklere bağlı olarak çağrılmadan önce ayarlanması gerekir. `DeleteCommand` `InsertCommand` `UpdateCommand` Örneğin, satırlar eklendiyse `InsertCommand` , çağrısından `Update`önce ayarlanmalıdır. Ekli, güncelleştirilmiş veya silinmiş bir satırı `DataAdapter` işlerken, eylemi işlemek için ilgili `Command` özelliği kullanır. `Update` Değiştirilen satır hakkındaki güncel bilgiler `Command` nesneye `Parameters` koleksiyon aracılığıyla geçirilir.  
  
 Veri kaynağındaki bir satırı güncelleştirdiğinizde, güncelleştirilecek tablodaki satırı tanımlamak için benzersiz bir tanımlayıcı kullanan UPDATE ifadesini çağırın. Benzersiz tanımlayıcı genellikle birincil anahtar alanının değeridir. UPDATE ifadesinde, aşağıdaki Transact-SQL bildiriminde gösterildiği gibi, her iki benzersiz tanımlayıcıyı ve güncelleştirilecek sütunları ve değerleri içeren parametreler kullanılır.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır. Bu örnekte bir SQL Server veri kaynağı için yer tutucular gösterilmektedir. <xref:System.Data.OleDb> Ve<xref:System.Data.Odbc> parametreleri için soru işareti (?) yer tutucuları kullanın.  
  
 Bu Visual Basic `CompanyName` örnekte, alanı `@CustomerID` parametresinin değerine `CustomerID` eşit olan satır için `@CompanyName` parametresinin değeri ile güncellenir. Parametreler, <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> nesne özelliğini kullanarak değiştirilen satırdan bilgi alır. Önceki örnek UPDATE ifadesinin parametreleri aşağıda verilmiştir. Kod, değişkenin `adapter` geçerli <xref:System.Data.SqlClient.SqlDataAdapter> bir nesneyi temsil ettiğini varsayar.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 Koleksiyonun yöntemi, parametrenin adını, veri türünü, boyutunu (Eğer varsa) <xref:System.Data.Common.DbParameter.SourceColumn%2A> ve öğesinden `DataTable`adını alır. `Add` `Parameters` Parametresinin olarak ayarlandığınıunutmayın`Original`. <xref:System.Data.Common.DbParameter.SourceVersion%2A> `@CustomerID` Bu, tanımlayıcı sütun veya sütunların değeri değiştirilen <xref:System.Data.DataRow>' de değiştirilmişse veri kaynağındaki mevcut satırın güncelleştirilmesini güvence altına alır. Bu durumda, `Original` satır değeri veri kaynağındaki geçerli değerle eşleşir `Current` ve satır değeri güncelleştirilmiş değeri içerir. Parametresi için ayarlanmamış ve varsayılan, `Current` satır değeri kullanır. `SourceVersion` `@CompanyName`  
  
> [!NOTE]
> Ve yöntemlerinin her `Fill`iki işlemiiçin,.NETFrameworktürü.NETFrameworkverisağlayıcısındandöndürülentürdenalgılanır.`Get` `DataAdapter` `DataReader` Microsoft SQL Server, OLE DB ve ODBC veri türleri için çıkarılan .NET Framework türleri ve erişimci yöntemleri, [ADO.net Içindeki veri türü eşlemelerinde](data-type-mappings-in-ado-net.md)açıklanmıştır.  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter. SourceColumn, parametre. SourceVersion  
 Ve, oluşturucuya bağımsız değişken olarak `Parameter`geçirilebilir veya var olan bir özellik olarak ayarlanabilir. `Parameter` `SourceVersion` `SourceColumn` , Değerinin <xref:System.Data.DataColumn> alınacağıyerin<xref:System.Data.DataRow> adından oluşur. `Parameter` `SourceColumn` , `SourceVersion` Değerini almak `DataRow` için `DataAdapter` kullandığı sürümü belirtir.  
  
 Aşağıdaki tabloda ile birlikte <xref:System.Data.DataRowVersion> `SourceVersion`kullanılabilecek sabit listesi değerleri gösterilmektedir.  
  
|DataRowVersion numaralandırması|Açıklama|  
|--------------------------------|-----------------|  
|`Current`|Parametresi, sütunun geçerli değerini kullanır. Bu varsayılandır.|  
|`Default`|Parametresi, sütununun öğesini `DefaultValue` kullanır.|  
|`Original`|Parametresi, sütunun orijinal değerini kullanır.|  
|`Proposed`|Parametresi önerilen değeri kullanır.|  
  
 `@CustomerID` <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> `SourceColumn` `SET CustomerID = @CustomerID``WHERE CustomerID = @OldCustomerID` `@OldCustomerID` Sonraki bölümde `CustomerID` kod örneği, sütununun iki parametre için olarak kullanıldığı bir parametresi tanımlar: () ve (). `SqlClient` Parametresi, **MüşteriNo sütununu** içindeki geçerli değere güncelleştirmek için kullanılır. `DataRow` `@CustomerID` `CustomerID` Sonuç olarak, ' `SourceColumn` a `SourceVersion` ilebirliktekullanılır`Current` . `@OldCustomerID` Parametresi, veri kaynağındaki geçerli satırı tanımlamak için kullanılır. Eşleşen sütun `Original` değeri satırın sürümünde bulunduğundan, ile `SourceVersion` `Original` aynı `SourceColumn` (`CustomerID`) kullanılır.  
  
## <a name="working-with-sqlclient-parameters"></a>SqlClient parametreleriyle çalışma  
 Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> bir oluşturma ve veritabanından ek şema bilgileri almak için <xref:System.Data.MissingSchemaAction.AddWithKey> öğesini olarak ayarlama işlemlerinin nasıl yapılacağını gösterir. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> , ,<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>Ve özelliklerikümesi<xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> ve bunlara karşılık gelen nesneler koleksiyona eklenir. <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> Yöntemi bir `SqlDataAdapter` nesnesi döndürür.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb parametre yer tutucuları  
 <xref:System.Data.OleDb.OleDbDataAdapter> Ve<xref:System.Data.Odbc.OdbcDataAdapter> nesneleri için, parametreleri tanımlamak üzere soru işareti (?) yer tutucuları kullanmanız gerekir.  
  
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
  
 Parametreli sorgu deyimleri hangi giriş ve çıkış parametrelerinin oluşturulması gerektiğini tanımlar. Bir parametre oluşturmak için, sütun adı `Parameters.Add` , veri türü `Parameter` ve boyutunu belirtmek üzere yöntemini veya oluşturucuyu kullanın. Gibi iç veri türleri `Integer`için, boyutu eklemeniz gerekmez veya varsayılan boyutu belirtebilirsiniz.  
  
 Aşağıdaki kod örneği, bir SQL deyimin parametrelerini oluşturur ve sonra bir `DataSet`doldurur.  
  
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
> Parametre için bir parametre adı sağlanmadığında *parametreye, "* parametre1" ile başlayarak*N* parametresinin artımlı bir varsayılan adı verilir. Bir parametre adı belirlediğinizde parametre*N* adlandırma kuralını kullanmaktan kaçınmanızı öneririz, çünkü sağladığınız ad içinde `ParameterCollection`varolan bir varsayılan parametre adıyla çakışabilir. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
