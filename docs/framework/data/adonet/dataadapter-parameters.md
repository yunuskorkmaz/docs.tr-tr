---
title: DataAdapter parametreleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 600dd949ffbed5c1066f9e3c3d9cc09eb174a22e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="dataadapter-parameters"></a>DataAdapter parametreleri
<xref:System.Data.Common.DbDataAdapter> Verileri almak ve veri kaynağına verileri güncelleştirmek için kullanılan dört özelliklere sahiptir: <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> özelliği, veri kaynağından; verileri döndürür ve <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ve <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özellikleri yönetmek için kullanılır veri kaynağında değişiklikler. `SelectCommand` Özelliği çağırmadan önce ayarlanmalıdır `Fill` yöntemi `DataAdapter`. `InsertCommand`, `UpdateCommand`, Veya `DeleteCommand` özelliklerini ayarlamak, önce `Update` yöntemi `DataAdapter` olarak adlandırılan, hangi veri değişikliklerinin yapıldığı bağlı olarak <xref:System.Data.DataTable>. Satır eklenir, örneğin, `InsertCommand` çağırmadan önce ayarlanmalıdır `Update`. Zaman `Update` eklenen, güncellenen veya silinen satır işleme `DataAdapter` ilgili kullanan `Command` eylemi işlemek için özellik. Değiştirilen satır hakkında güncel bilgiler için geçirilir `Command` nesnesi aracılığıyla `Parameters` koleksiyonu.  
  
 Bir satır veri kaynağında'ı güncelleştirdiğinizde UPDATE deyiminin çağrı güncelleştirilmesi tablodaki satır tanımlamak için benzersiz bir tanımlayıcı kullanır. Benzersiz tanımlayıcısı genellikle bir birincil anahtar alanının değeri değil. UPDATE deyiminde benzersiz tanımlayıcı ve sütunları hem güncelleştirilmesi için değerleri aşağıdaki Transact-SQL deyiminde gösterildiği gibi içeren parametreleri kullanır.  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  Parametre yer tutucuları sözdizimi veri kaynağına bağlıdır. Bu örnek, bir SQL Server veri kaynağı için yer tutucuları gösterir. Soru işareti (?) yer tutucular kullanmak <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> parametreleri.  
  
 Bu Visual Basic örnekte `CompanyName` alanı değeriyle güncelleştirilir `@CompanyName` parametresi satır için burada `CustomerID` değerine eşit `@CustomerID` parametresi. Değiştirilen satır kullanımından parametreleri bilgileri almak <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> özelliği <xref:System.Data.SqlClient.SqlParameter> nesnesi. Önceki örnek UPDATE deyiminin için Parametreler şunlardır: Kod varsayar değişkeni `adapter` geçerli bir temsil eden <xref:System.Data.SqlClient.SqlDataAdapter> nesnesi.  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` Yöntemi `Parameters` koleksiyonu alır parametresi adını veri türü (türüne varsa) boyutu ve adını <xref:System.Data.Common.DbParameter.SourceColumn%2A> gelen `DataTable`. Dikkat <xref:System.Data.Common.DbParameter.SourceVersion%2A> , `@CustomerID` parametrenin ayarlanmış `Original`. Bu tanımlayıcı sütun veya sütun değeri değiştirildiğinde, varolan bir satır veri kaynağındaki güncelleştirilir garanti değiştirilmiş içinde <xref:System.Data.DataRow>. Bu durumda, `Original` satır değeri, veri kaynağında geçerli değeri eşleşir ve `Current` satır değeri güncelleştirilmiş değeri içerecektir. `SourceVersion` İçin `@CompanyName` parametresi ayarlı değildir ve varsayılan kullanır `Current` satır değeri.  
  
> [!NOTE]
>  Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü döndürülen türünden sözcüğünden [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı. Çıkarsanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve Microsoft SQL Server, OLE DB ve ODBC veri türleri için erişimci yöntemleri açıklanmıştır [ADO.NET veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 `SourceColumn` Ve `SourceVersion` bağımsız değişken olarak geçirilebilir `Parameter` oluşturucunun ya da varolan bir özellik kümesi `Parameter`. `SourceColumn` Adı <xref:System.Data.DataColumn> gelen <xref:System.Data.DataRow> burada değerini `Parameter` alınır. `SourceVersion` Belirtir `DataRow` sürümü, `DataAdapter` değerini almak için kullanır.  
  
 Aşağıdaki tabloda <xref:System.Data.DataRowVersion> numaralandırma değerleri için kullanılabilir kullanmak ile `SourceVersion`.  
  
|DataRowVersion numaralandırması|Açıklama|  
|--------------------------------|-----------------|  
|`Current`|Parametre geçerli sütun değeri kullanır. Bu varsayılandır.|  
|`Default`|Parametresini kullanır `DefaultValue` sütun.|  
|`Original`|Parametre sütun özgün değeri kullanır.|  
|`Proposed`|Önerilen bir değer parametresini kullanır.|  
  
 `SqlClient` Sonraki bölümde kod örneğinde tanımlayan bir parametre için bir <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> , `CustomerID` sütun olarak kullanılan bir `SourceColumn` iki parametre için: `@CustomerID` (`SET CustomerID = @CustomerID`), ve `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). `@CustomerID` Parametresi güncelleştirmek için kullanılan **CustomerID** geçerli değeri sütuna `DataRow`. Sonuç olarak, `CustomerID` `SourceColumn` ile bir `SourceVersion` , `Current` kullanılır. *@OldCustomerID* Parametresi geçerli satır veri kaynağındaki tanımlamak için kullanılır. İçinde eşleşen sütun değeri bulduğundan `Original` satır aynı sürümü `SourceColumn` (`CustomerID`) ile bir `SourceVersion` , `Original` kullanılır.  
  
## <a name="working-with-sqlclient-parameters"></a>SqlClient parametreleri ile çalışma  
 Aşağıdaki örnekte nasıl oluşturulduğunu gösteren bir <xref:System.Data.SqlClient.SqlDataAdapter> ve <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> için <xref:System.Data.MissingSchemaAction.AddWithKey> veritabanından ek şema bilgileri almak için. <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, Ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikler kümesini ve bunların karşılık gelen <xref:System.Data.SqlClient.SqlParameter> eklenen nesneleri <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyonu. Yöntem bir `SqlDataAdapter` nesnesi.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb parametre yer tutucuları  
 İçin <xref:System.Data.OleDb.OleDbDataAdapter> ve <xref:System.Data.Odbc.OdbcDataAdapter> nesneleri parametreler tanımlamak için soru işareti (?) yer tutucuları kullanmalısınız.  
  
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
  
 Parametreli sorgu deyimi, giriş tanımlar ve çıkış parametreleri oluşturulması gerekir. Bir parametre oluşturmak üzere kullanmanız `Parameters.Add` yöntemi veya `Parameter` Oluşturucusu sütun adı, veri türü ve boyutunu belirtin. İç veri türleri için aşağıdaki gibi `Integer`boyutu eklenecek yok veya varsayılan boyutu belirtebilirsiniz.  
  
 Aşağıdaki kod örneği bir SQL deyimi için parametreleri oluşturur ve ardından doldurur bir `DataSet`.  
  
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
>  Bir parametre adı için bir parametre sağlanmazsa, parametre parametresinin bir artımlı varsayılan adı verilen*N* *,* "Parametre1" ile başlayan. Parametresi kaçınmanızı öneririz*N* bir parametre adı sağladığında, sağladığınız ad mevcut bir varsayılan parametre adı çakışıyor çünkü adlandırma kuralı `ParameterCollection`. Sağlanan adı zaten varsa, özel durum oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
