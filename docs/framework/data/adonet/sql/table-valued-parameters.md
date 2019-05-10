---
title: Tablo Değerli Parametreler
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: ccef487eb27a5a170d197a6bc670ec4d2bcf8bdf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645793"
---
# <a name="table-valued-parameters"></a>Tablo Değerli Parametreler
Tablo değerli parametreler birden çok gidiş dönüş veya özel sunucu tarafı mantık verilerin işlenmesi için gerek kalmadan birden çok SQL Server için bir istemci uygulamasından veri satırı sıralama için kolay bir yol sağlar. Bir istemci uygulamasında veri satırı kapsüllemek ve tek bir Parametreli komutu sunucuda veri göndermek için tablo değerli parametreleri kullanabilirsiniz. Gelen veri satırları sonra üzerinde kullanarak işletilebilir bir tablo değişkeninde depolanan [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Sütun değerleri tablo değerli parametreleri standardını kullanarak erişilebilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT deyimleri. Tablo değerli parametre kesin olarak belirlenmiştir ve yapılarını otomatik olarak doğrulanır. Tablo değerli parametre boyutunu, yalnızca sunucu bellekle sınırlıdır.  
  
> [!NOTE]
>  Tablo değerli parametre veri döndüremez. Tablo değerli salt giriş parametreleridir; Çıkış anahtar sözcüğü desteklenmiyor.  
  
 Tablo değerli parametreler hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tablo değerli parametreleri (veritabanı altyapısı)](https://go.microsoft.com/fwlink/?LinkId=98363) SQL Server Çevrimiçi Kitapları'nda|Tablo değerli parametreleri oluşturup kullanacağınızı açıklar.|  
|[Kullanıcı tanımlı tablo türleri](https://go.microsoft.com/fwlink/?LinkId=98364) SQL Server Çevrimiçi Kitapları'nda|Tablo değerli parametreleri bildirmek için kullanılan kullanıcı tanımlı tablo türleri açıklanmaktadır.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server'ın önceki sürümlerinde birden çok satır geçirme  
 Tablo değerli parametreleri SQL Server 2008'e sunulmadan önce bir saklı yordam ya da bir parametreleştirilmiş SQL komutu için birden çok sayıda veri geçirmek için seçenekleri sınırlıdır. Bir geliştirici, birden çok satır sunucuya geçirmek için aşağıdaki seçeneklerden seçebilirsiniz:  
  
- Birden çok sütun ve satır veri değerleri temsil etmek için bir dizi bağımsız parametreleri kullanın. Bu yöntem kullanılarak geçirilebilir veri miktarı tarafından izin verilen parametre sayısı sınırlıdır. SQL Server yordamları en fazla 2100 parametreleri olabilir. Sunucu tarafı mantık tablo değişkeni veya geçici bir tablo işleme için bu değerlerin derlemek için gereklidir.  
  
- Birden çok veri değeri, ayrılmış bir dize veya XML belgeleri paket ve ardından bu metin değerlerini bir yordam veya deyimi geçirin. Bu yordamı veya veri yapılarını ve unbundling doğrulamak için gerekli mantığı bildirimini değerleri gerektirir.  
  
- Bir dizi çağırarak oluşturulanlar gibi birden çok satır etkileyen değişiklikleri için ayrı SQL deyimi oluşturmak `Update` yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter>. Değişiklikler tek tek sunucuya gönderilen veya gruplar halinde toplu. Ancak, hatta birden fazla deyim içeren toplu olarak gönderildiğinde her deyim ayrı ayrı sunucuda yürütülür.  
  
- Kullanım `bcp` yardımcı programı veya <xref:System.Data.SqlClient.SqlBulkCopy> birçok veri satırı bir tabloya yüklemek için nesne. Bu teknik çok etkili olsa da, verileri bir geçici tablo veya tablo değişkeni içine yüklenen sürece, sunucu tarafı işleme desteklemez.  
  
## <a name="creating-table-valued-parameter-types"></a>Tablo değerli parametre türleri oluşturma  
 Tablo değerli parametreleri kullanılarak tanımlanmış tabloyu kesin tür belirtilmiş yapıları dayanır [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] türü oluştur deyimleri. Bir tablo türü oluştur, istemci uygulamalarınız tablo değerli parametre kullanmadan önce SQL Server'da yapısı tanımlamanız gerekir. Tablo türleri oluşturma hakkında daha fazla bilgi için bkz. [kullanıcı tanımlı tablo türleri](https://go.microsoft.com/fwlink/?LinkID=98364) SQL Server Books Online.  
  
 Aşağıdaki deyim, kullanıcı, Categoryıd'si ve CategoryName sütundan oluşan CategoryTableType adlı bir tablo türü oluşturur:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Bir tablo türü oluşturduktan sonra o türde bağlı tablo değerli parametreler bildirebilirsiniz. Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] parça bir saklı yordam tanımında tablo değerli bir parametre bildirmek nasıl gösterir. READONLY anahtar sözcüğü bir tablo değerli parametre bildirmek için gerekli olduğunu unutmayın.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Tablo değerli parametreleri (Transact-SQL) ile verileri değiştirme  
 Tablo değerli parametre birden çok satır tek bir deyimde yürüterek etkileyen veri kümesi tabanlı değişiklikler kullanılabilir. Örneğin, bir tablo değerli parametre tüm satırları seçin ve bunları bir veritabanı tablosuna eklemek veya güncelleştirmek istediğiniz tabloya bir tablo değerli parametre katılarak bir güncelleştirme deyimiyle oluşturabilirsiniz.  
  
 Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] güncelleştirme bildirimi kategorileri tabloya katılarak tablo değerli bir parametre kullanmayı gösterir. Bir birleştirme işleminde bir FROM yan tümcesi içeren bir tablo değerli parametre kullandığınızda, ayrıca diğer adı, tablo değerli parametre "AB" Next olduğu burada gösterildiği gibi gerekir:  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Bu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] örnek tablo değerli bir parametre kümesi tabanlı tek bir işlem ile INSERT işlemi satırları seçmek nasıl gösterir.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Tablo değerli parametre sınırlamaları  
 Tablo değerli parametrelere birkaç sınırlama vardır:  
  
- Tablo değerli parametre geçirilemez [kullanıcı tanımlı CLR işlevleri](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Tablo değerli parametrelere, yalnızca UNIQUE ve PRIMARY KEY kısıtlamaları destekleyecek şekilde sıralanabilir. SQL Server tablo değerli parametre istatistiklerle korumaz.  
  
- Tablo değerli parametre, salt okunur [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kod. Tablo değerli bir parametre satırlarını sütun değerleri güncelleştirilemiyor ve ekleyemez veya satırları sil. Bir saklı yordam için geçirilen veya tablo değerli parametre deyiminde parametreli verileri değiştirmek için verileri geçici bir tablo veya tablo değişkeni eklemeniz gerekir.  
  
- Tablo değerli parametre tasarımını değiştirmek için ALTER TABLE deyimleri kullanamazsınız.  
  
## <a name="configuring-a-sqlparameter-example"></a>SqlParameter örnek yapılandırma  
 <xref:System.Data.SqlClient> Tablo değerli parametreler doldurma destekler <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> veya <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> nesneleri. Tablo değerli parametresi için bir tür adını kullanarak belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Sunucuda daha önce oluşturduğunuz uyumlu bir tür adıyla eşleşmelidir. Aşağıdaki kod parçası nasıl yapılandırılacağını gösteren <xref:System.Data.SqlClient.SqlParameter> veri eklemek için.  
 
Aşağıdaki örnekte, `addedCategories` değişkenini içeren bir <xref:System.Data.DataTable>. Değişken nasıl doldurulur görmek için sonraki bölümde yer alan örnekler görmek [Table-Valued parametresi için bir saklı yordam geçirme](#passing).

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
  
 Öğesinden türetilen herhangi bir nesne kullanabilirsiniz <xref:System.Data.Common.DbDataReader> bu parçasını gösterildiği gibi bir tablo değerli parametre veri akışı satır:  
  
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
  
## <a name="passing"></a> Tablo değerli bir parametre için bir saklı yordam geçirme  
 Bu örnek nasıl tablo değerli parametre veri saklı yordama geçirileceğini gösterir. Eklenen satırlarla kod yeni bir ayıklar <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.GetChanges%2A> yöntemi. Ardından kodu tanımlayan bir <xref:System.Data.SqlClient.SqlCommand>ayarını <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliğini <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Kullanarak doldurulur <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> yöntemi ve <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ayarlanır `Structured`. <xref:System.Data.SqlClient.SqlCommand> Kullanarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Bir parametreli SQL deyimi için tablo değerli bir parametre geçirme  
 Aşağıdaki örnek veri dbo nasıl ekleneceğini gösterir. Veri kaynağı olarak bir tablo değerli parametresi olan bir SELECT alt sorgu INSERT deyimini kullanarak tablo kategorileri. Bir parametreli SQL deyimi için tablo değerli bir parametre geçirerek, yeni kullanarak tablo değerli parametresi için bir tür adı belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>. Bu `TypeName` sunucuda daha önce oluşturduğunuz uyumlu bir tür adıyla eşleşmelidir. Bu örnekteki kod `TypeName` dbo içinde tanımlanan tür yapısına başvurmak için özellik. CategoryTableType.  
  
> [!NOTE]
>  Tablo değerli bir parametre olarak bir kimlik sütunu için bir değer sağlarsanız, oturumu için AYARLANMIŞ IDENTITY_INSERT deyimi yayımlamanız gerekir.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>DataReader ile akış satırları  
 Öğesinden türetilen herhangi bir nesne kullanabilirsiniz <xref:System.Data.Common.DbDataReader> tablo değerli bir parametre veri akışı satır. Aşağıdaki kod parçası kullanarak bir Oracle veritabanından veri alma gösterir bir <xref:System.Data.OracleClient.OracleCommand> ve <xref:System.Data.OracleClient.OracleDataReader>. Kodu daha sonra yapılandırır bir <xref:System.Data.SqlClient.SqlCommand> tek bir giriş parametresi olan bir saklı yordam çağırmak için. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Özelliği <xref:System.Data.SqlClient.SqlParameter> ayarlanır `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Geçirir `OracleDataReader` sonuç kümesi saklı yordam tablo değerli bir parametre olarak.  
  
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

- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Komutlar ve Parametreler](../../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapter Parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
