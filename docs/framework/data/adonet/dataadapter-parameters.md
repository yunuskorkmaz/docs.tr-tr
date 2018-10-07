---
title: DataAdapter parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845625"
---
# <a name="dataadapter-parameters"></a>DataAdapter parametreleri
<xref:System.Data.Common.DbDataAdapter> Verileri almak ve verileri için veri kaynağını güncelleştirmek için kullanılan dört özelliklere sahiptir: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> özelliği veri kaynağından; veri döndürür ve <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri yönetmek için kullanılır veri kaynağındaki değişiklikleri. `SelectCommand` Özelliği çağırmadan önce ayarlanmalıdır `Fill` yöntemi `DataAdapter`. `InsertCommand`, `UpdateCommand`, Veya `DeleteCommand` özelliklerini ayarlamak, önce `Update` yöntemi `DataAdapter` , hangi değişiklikleri verilerde yapılan bağlı olarak adlandırılır <xref:System.Data.DataTable>. Satırlar eklenir, örneğin, `InsertCommand` çağırmadan önce ayarlanmalıdır `Update`. Zaman `Update` eklenen, güncelleştirilen veya silinen satır işleme `DataAdapter` ilgili kullanan `Command` eylemi işlemek için özellik. Değiştirilen satır hakkında güncel bilgiler geçirildiğinde `Command` nesnesi aracılığıyla `Parameters` koleksiyonu.  
  
 Veri kaynağındaki satırı güncelleştirmek, güncelleştirme bildirimi arama tablosunda bir satırı tanımlamak için benzersiz bir tanımlayıcı kullanan güncelleştirilemiyor. Benzersiz tanımlayıcı genellikle bir birincil anahtar alanı değeridir. UPDATE deyimini aşağıdaki Transact-SQL deyiminde gösterildiği gibi benzersiz tanımlayıcısı ve sütunları hem güncelleştirilmesi için değerleri içeren parametrelerini kullanır.  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Parametre yer tutucuları sözdizimi veri kaynağına bağlıdır. Bu örnek, bir SQL Server veri kaynağı için yer tutucular gösterir. Soru işareti (?) yer tutucuları kullanan <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> parametreleri.  
  
 Bu Visual Basic örnekte `CompanyName` alanın değeriyle güncelleştirilir `@CompanyName` parametre satır için burada `CustomerID` değeri eşittir `@CustomerID` parametresi. Değiştirilen satır kullanımından parametreleri bilgileri almak <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> özelliği <xref:System.Data.SqlClient.SqlParameter> nesne. Önceki örnek UPDATE deyimi için Parametreler aşağıda verilmiştir. Kod olduğunu varsayar değişkeni `adapter` temsil eden geçerli bir <xref:System.Data.SqlClient.SqlDataAdapter> nesne.  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Yöntemi `Parameters` koleksiyon parametresi adını veri türü boyutu (türüne varsa) ve adını alır <xref:System.Data.Common.DbParameter.SourceColumn%2A> gelen `DataTable`. Dikkat <xref:System.Data.Common.DbParameter.SourceVersion%2A> , `@CustomerID` parametrenin ayarlanmış `Original`. Bu tanımlayıcı sütun veya sütunlar değerini değiştirilmişse, veri kaynağı olarak var olan satır güncelleştirilir garanti eder, değiştirilmiş <xref:System.Data.DataRow>. Bu durumda, `Original` satır değeri, geçerli değerin veri kaynağında eşleşir ve `Current` satır değeri, güncelleştirilmiş değeri içerecektir. `SourceVersion` İçin `@CompanyName` parametre ayarlı değil ve varsayılan olarak kullandığı `Current` satır değeri.  
  
> [!NOTE]
>  Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü döndürüldüğü türünden çıkarılan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı. Çıkarsanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve Microsoft SQL Server, OLE DB ve ODBC veri türleri için erişimci metotlarını bölümünde açıklanmıştır [ADO.NET'te veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 `SourceColumn` Ve `SourceVersion` bağımsız değişken olarak geçirilebilir `Parameter` oluşturucu veya varolan özellikleri kümesi `Parameter`. `SourceColumn` Adıdır <xref:System.Data.DataColumn> gelen <xref:System.Data.DataRow> nerede değerini `Parameter` alınır. `SourceVersion` Belirtir `DataRow` sürümü, `DataAdapter` değerini almak için kullanır.  
  
 Aşağıdaki tabloda <xref:System.Data.DataRowVersion> numaralandırma değerleri için kullanılabilir kullanın ile `SourceVersion`.  
  
|DataRowVersion numaralandırması|Açıklama|  
|--------------------------------|-----------------|  
|`Current`|Parametresi, geçerli sütun değeri kullanır. Bu varsayılandır.|  
|`Default`|Parametre kullanan `DefaultValue` sütun.|  
|`Original`|Parametresi özgün sütununun değerini kullanır.|  
|`Proposed`|Önerilen değer parametresini kullanır.|  
  
 `SqlClient` Sonraki bölümde kod örneği için bir parametre tanımlayan bir <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> hangi `CustomerID` sütun olarak kullanılan bir `SourceColumn` iki parametre için: `@CustomerID` (`SET CustomerID = @CustomerID`), ve `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Güncelleştirmek için kullanılan parametre **CustomerID** sütun geçerli değeri `DataRow`. Sonuç olarak, `CustomerID` `SourceColumn` ile bir `SourceVersion` , `Current` kullanılır. `@OldCustomerID` Parametresi veri kaynağındaki geçerli satırı tanımlamak için kullanılır. Eşleşen sütun değeri bulunur çünkü `Original` satır aynı sürümünü `SourceColumn` (`CustomerID`) ile bir `SourceVersion` , `Original` kullanılır.  
  
## <a name="working-with-sqlclient-parameters"></a>SqlClient parametreleri ile çalışma  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Data.SqlClient.SqlDataAdapter> ayarlayıp <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> için <xref:System.Data.MissingSchemaAction.AddWithKey> veritabanından ek şema bilgilerini almak için. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, Ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri kümesi ve bunlara karşılık gelen <xref:System.Data.SqlClient.SqlParameter> eklenen nesneleri <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyonu. Yöntem döndürür bir `SqlDataAdapter` nesne.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb parametre yer tutucuları  
 İçin <xref:System.Data.OleDb.OleDbDataAdapter> ve <xref:System.Data.Odbc.OdbcDataAdapter> nesnelerini parametrelerini belirlemek için soru işareti (?) yer tutucuları kullanmalısınız.  
  
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
  
 Parametreli sorgu deyimi, giriş tanımlar ve çıkış parametreleri oluşturulması gerekir. Bir parametreyi oluşturmak üzere kullanmak `Parameters.Add` yöntemi veya `Parameter` sütun adı, veri türü ve boyutunu belirlemek için oluşturucu. İç veri türleri gibi `Integer`, boyuta dahil gerekmez veya varsayılan boyutu belirtebilirsiniz.  
  
 Aşağıdaki kod örneği bir SQL deyimi için parametreleri oluşturur ve ardından dolduran bir `DataSet`.  
  
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
>  Parametre adı için bir parametre sağlanmazsa, parametre parametresinin bir artımlı varsayılan ad verilir*N* *,* "Parametre1" ile başlayan. Parametre kaçınmanızı öneririz*N* bir parametre adı sağlayın, mevcut bir varsayılan parametre adı ile sağladığınız ad çakışması nedeniyle adlandırma kuralı `ParameterCollection`. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
