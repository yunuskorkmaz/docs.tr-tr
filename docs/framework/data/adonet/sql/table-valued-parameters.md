---
title: Tablo Değerli Parametreler
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174478"
---
# <a name="table-valued-parameters"></a>Tablo Değerli Parametreler
Tablo değeri olan parametreler, birden çok tur gezisi veya verileri işlemek için özel sunucu tarafı mantığı gerektirmeden istemci uygulamasından SQL Server'a birden çok veri satırını işlemenin kolay bir yolunu sağlar. Bir istemci uygulamasında veri satırları kapsüllemek ve tek bir parametreli komutverileri sunucuya göndermek için tablo değerli parametreleri kullanabilirsiniz. Gelen veri satırları, Transact-SQL kullanılarak çalıştırılabilen bir tablo değişkeninde depolanır.  
  
 Tablo değeri olan parametrelerdeki sütun değerlerine standart Transact-SQL SELECT deyimleri kullanılarak erişilebilir. Tablo değeri olan parametreler güçlü bir şekilde yazılır ve yapıları otomatik olarak doğrulanır. Tablo değeri olan parametrelerin boyutu yalnızca sunucu belleğiyle sınırlıdır.  
  
> [!NOTE]
> Tablo değerindeki parametrede veri döndüremezsiniz. Tablo değeri olan parametreler yalnızca giriştedir; OUTPUT anahtar sözcüğü desteklenmez.  
  
 Tablo değeri olan parametreler hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tablo Değeri Olan Parametreleri Kullanın (Veritabanı Motoru)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|Tablo değeri olan parametrelerin nasıl oluşturulup kullanılacağını açıklar.|  
|[Kullanıcı Tanımlı Tablo Türleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Tablo değeri olan parametreleri bildirmek için kullanılan kullanıcı tanımlı tablo türlerini açıklar.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server'ın Önceki Sürümlerinde Birden Çok Satır Geçme  
 SQL Server 2008'e tablo değeri olan parametreler kullanılmadan önce, birden çok veri satırını depolanmış bir yordam veya parametreli SQL komutuna geçirme seçenekleri sınırlıydı. Geliştirici, birden çok satırı sunucuya geçirmek için aşağıdaki seçenekler arasından seçim yapabilir:  
  
- Birden çok sütun ve veri satırındaki değerleri temsil etmek için bir dizi tek tek parametre kullanın. Bu yöntem kullanılarak geçirilebilen veri miktarı, izin verilen parametre sayısıyla sınırlıdır. SQL Server yordamları, en fazla 2100 parametreye sahip olabilir. Sunucu tarafı mantığı, bu tek tek değerleri bir tablo değişkeninde veya işleme için geçici bir tabloda birleştirmek için gereklidir.  
  
- Birden çok veri değerini sınırlı dizeleri veya XML belgelerine paketleyin ve ardından bu metin değerlerini bir yordam veya deyime geçirin. Bu, yordam ın veya deyimin veri yapılarını doğrulamak ve değerleri boşaltmak için gerekli mantığı içermesini gerektirir.  
  
- Birden çok satırı etkileyen veri modifikasyonları için bir dizi ayrı SQL `Update` deyimi oluşturun, örneğin bir <xref:System.Data.SqlClient.SqlDataAdapter>. Değişiklikler sunucuya tek tek gönderilebilir veya gruplara ayrılabilir. Ancak, birden çok deyim içeren toplu gruplar halinde gönderildiğinde bile, her deyim sunucuda ayrı olarak yürütülür.  
  
- Bir `bcp` tabloya çok <xref:System.Data.SqlClient.SqlBulkCopy> sayıda veri satırı yüklemek için yardımcı program veya nesneyi kullanın. Bu teknik çok verimli olmasına rağmen, veriler geçici bir tabloya veya tablo değişkenine yüklenmediği sürece sunucu tarafı işlemeyi desteklemez.  
  
## <a name="creating-table-valued-parameter-types"></a>Tablo Değeri Nekadar Parametre Türleri Oluşturma  
 Tablo değeri olan parametreler, Transact-SQL CREATE TYPE deyimleri kullanılarak tanımlanan güçlü bir şekilde yazılan tablo yapılarını temel almaktadır. İstemci uygulamalarınızda tablo değeri olan parametreleri kullanabilmek için önce bir tablo türü oluşturmanız ve SQL Server'daki yapıyı tanımlamanız gerekir. Tablo türleri oluşturma hakkında daha fazla bilgi için [Bkz. Kullanıcı Tanımlı Tablo Türleri.](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))  
  
 Aşağıdaki deyim, CategoryID ve CategoryName sütunlarından oluşan CategoryTableType adlı bir tablo türü oluşturur:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Bir tablo türü oluşturduktan sonra, tablo değerindeki parametreleri bu türe göre bildirebilirsiniz. Aşağıdaki Transact-SQL parçası, depolanmış yordam tanımında tablo değeri olan bir parametrenin nasıl bildirilen ihtir. READONLY anahtar kelimesinin tablo değerinde bir parametre yi bildirmek için gerekli olduğunu unutmayın.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Tablo Değeri Olan Parametrelerle Veri Değiştirme (Transact-SQL)  
 Tablo değeri olan parametreler, tek bir deyim çalıştırılarak birden çok satırı etkileyen ayar tabanlı veri modifikasyonlarında kullanılabilir. Örneğin, tablo değerindeki parametredeki tüm satırları seçebilir ve bunları bir veritabanı tablosuna ekleyebilir veya güncelleştirmek istediğiniz tabloya tablo değeri olan bir parametreyi birleştirerek güncelleştirme deyimi oluşturabilirsiniz.  
  
 Aşağıdaki Transact-SQL UPDATE deyimi, tablo değeri olan bir parametrenin Kategoriler tablosuna katılarak nasıl kullanılacağını gösterir. FROM yan tümcesinde JOIN içeren tablo değeri nereli bir parametre kullandığınızda, tablo değeri olan parametrenin "ec" olarak kullanıldığı burada da diğer adı verilmelidir:  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Bu İşlemel-SQL örneği, tek bir küme tabanlı işlemde INSERT gerçekleştirmek için tablo değerindeki bir parametreden satırların nasıl seçilebildiğini gösterir.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Tablo Değeri Nekadar Değerlenen Parametrelerin Sınırlamaları  
 Tablo değeri olan parametreleriçin çeşitli sınırlamalar vardır:  
  
- Tablo değeri olan parametreleri [CLR kullanıcı tanımlı işlevlere geçiremezsiniz.](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)  
  
- Tablo değeri olan parametreler yalnızca UNIQUE veya PRIMARY KEY kısıtlamalarını desteklemek için dizine eklenebilir. SQL Server, tablo değeri olan parametrelerle ilgili istatistikleri korumaz.  
  
- Tablo değeri olan parametreler Transact-SQL kodunda salt okunur. Tablo değerindeki parametrenin satırlarında sütun değerlerini güncelleştiremezsiniz ve satır lar ekleyemez veya silemezsiniz. Tablo değerindeki parametrede depolanan yordamveya parametreli ifadeye geçirilen verileri değiştirmek için, verileri geçici bir tabloya veya tablo değişkenine eklemeniz gerekir.  
  
- Tablo değeri olan parametrelerin tasarımını değiştirmek için ALTER TABLE deyimlerini kullanamazsınız.  
  
## <a name="configuring-a-sqlparameter-example"></a>SqlParameter Örneğini Yapılandırma  
 <xref:System.Data.SqlClient>tablo değeri olan parametrelerin <xref:System.Data.DataTable>veya <xref:System.Data.Common.DbDataReader> <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> nesnelerin doldurulmalarını destekler. Tablo değeri taşıyan parametre için bir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. özelliğini kullanarak bir tür adı belirtmeniz gerekir Sunucuda `TypeName` daha önce oluşturulmuş uyumlu bir türün adı eşleşmelidir. Aşağıdaki kod parçası, veri eklemek <xref:System.Data.SqlClient.SqlParameter> için nasıl yapılandırılabildiğini gösterir.  

Aşağıdaki örnekte, `addedCategories` değişken . <xref:System.Data.DataTable> Değişkenin nasıl doldurulur olduğunu görmek için, tablo [değeri olan parametreyi Depolanmış Yordam'a geçirmek](#passing)için bir sonraki bölümdeki örneklere bakın.

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
  
 Bu parçada gösterildiği gibi, veri satırlarını tablo değerindeki bir parametreye akışı <xref:System.Data.Common.DbDataReader> için türetilen herhangi bir nesneyi de kullanabilirsiniz:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a>Tablo Değeri Olan Parametreyi Depolanan Yordama Geçirme  
 Bu örnek, tablo değerindeki parametre verilerinin depolanan bir yordama nasıl geçirilebildiğini gösterir. Kod ayıkları <xref:System.Data.DataTable> <xref:System.Data.DataTable.GetChanges%2A> yöntemi kullanarak yeni bir satır ekledi. Kod daha sonra <xref:System.Data.SqlClient.SqlCommand>bir , <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliği <xref:System.Data.CommandType.StoredProcedure>ayarlar tanımlar . Yöntem <xref:System.Data.SqlClient.SqlParameter> kullanılarak <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> doldurulur ve <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> `Structured`ayarlanır. Daha <xref:System.Data.SqlClient.SqlCommand> sonra <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntem kullanılarak yürütülür.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Tablo Değeri Nekadar Parametreli Bir Parametreyi Parametreli SQL Deyimine Geçirme  
 Aşağıdaki örnek, dbo'ya nasıl veri ekilir gösteriş gösterir. Veri kaynağı olarak tablo değeri olan bir parametreye sahip SELECT alt sorgusu içeren bir INSERT deyimi ni kullanarak kategoriler tablosu. Tablo değeri olan bir parametreyi parametreli SQL deyimine aktarırken, bir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>. ' nin yeni özelliğini kullanarak tablo değeri taşıyan parametre için bir tür adı belirtmeniz gerekir Bu, `TypeName` sunucuda daha önce oluşturulmuş uyumlu bir türün adı ile eşleşmelidir. Bu örnekteki kod, `TypeName` dbo'da tanımlanan tür yapısına başvurmak için özelliği kullanır. CategoryTableType.  
  
> [!NOTE]
> Tablo değerindeki bir parametrede bir kimlik sütunu için değer sağlıyorsanız, oturum için SET IDENTITY_INSERT deyimini vermeniz gerekir.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>DataReader ile Satır Ları Akış  
 Ayrıca, tablo değeri olan <xref:System.Data.Common.DbDataReader> bir parametreye veri satırları akışı için türetilen herhangi bir nesneyi de kullanabilirsiniz. Aşağıdaki kod parçası, bir Oracle veritabanından bir ve <xref:System.Data.OracleClient.OracleCommand> bir <xref:System.Data.OracleClient.OracleDataReader>. Kod daha sonra <xref:System.Data.SqlClient.SqlCommand> a'yı, tek bir giriş parametresi ile depolanan yordamı çağırmak için yapılandırır. <xref:System.Data.SqlClient.SqlParameter> `Structured`Özelliği <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ayarlanır. Tablo <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> değeri `OracleDataReader` olan parametre olarak depolanan yordama ayarlanan sonucu geçer.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [Komutlar ve Parametreler](../commands-and-parameters.md)
- [DataAdapter Parametreleri](../dataadapter-parameters.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
