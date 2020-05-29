---
title: Tablo Değerli Parametreler
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: b968c599cf061fbd03b7ba8fb19470f6ace11a55
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202169"
---
# <a name="table-valued-parameters"></a>Tablo Değerli Parametreler
Tablo değerli parametreler, bir istemci uygulamasından birden çok veri satırını, verilerin işlenmesine yönelik birden çok gidiş dönüş veya özel sunucu tarafı mantığı gerekmeden SQL Server için kolay bir yol sağlar. Bir istemci uygulamasındaki veri satırlarını kapsüllemek ve verileri sunucuya tek parametreli bir komutta göndermek için tablo değerli parametreleri kullanabilirsiniz. Gelen veri satırları, daha sonra Transact-SQL kullanılarak üzerinde çalışabilecek bir tablo değişkeninde depolanır.  
  
 Tablo değerli parametrelerdeki sütun değerlerine, standart Transact-SQL SELECT deyimleri kullanılarak erişilebilir. Tablo değerli parametreler kesin şekilde türdedir ve yapısı otomatik olarak onaylanır. Tablo değerli parametrelerin boyutu yalnızca sunucu belleği ile sınırlıdır.  
  
> [!NOTE]
> Tablo değerli bir parametreye veri döndüremez. Tablo değerli parametreler yalnızca giriş amaçlıdır; OUTPUT anahtar sözcüğü desteklenmiyor.  
  
 Tablo değerli parametreler hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tablo değerli parametreleri kullanın (veritabanı altyapısı)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|Tablo değerli parametrelerin nasıl oluşturulduğunu ve kullanıldığını açıklar.|  
|[Kullanıcı tanımlı tablo türleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Tablo değerli parametreleri bildirmek için kullanılan Kullanıcı tanımlı tablo türlerini açıklar.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server önceki sürümlerinde birden çok satır geçirme  
 Tablo değerli parametreler SQL Server 2008 ' e sunulmadan önce, bir saklı yordama veya parametreli bir SQL komutuna birden fazla veri satırı geçirme seçenekleri sınırlandı. Bir geliştirici, sunucuya birden çok satır geçirmek için aşağıdaki seçeneklerden birini seçebilir:  
  
- Birden çok sütundaki ve veri satırlarındaki değerleri temsil etmek için tek bir parametre serisi kullanın. Bu yöntem kullanılarak geçirilebilecek veri miktarı izin verilen parametrelerin sayısıyla sınırlıdır. SQL Server yordamlar, en çok 2100 parametreye sahip olabilir. Bu tek değerleri bir tablo değişkeninde veya işlemek üzere geçici bir tabloda birleştirmek için sunucu tarafı mantığı gerekir.  
  
- Birden çok veri değerini ayrılmış dizelere veya XML belgelerine paketleyin ve sonra bu metin değerlerini bir yordama veya ifadeye geçirin. Bu yordam veya deyimin veri yapılarını doğrulamak ve değerleri yeniden paketlemek için gereken mantığı içermesini gerektirir.  
  
- ' In yöntemini çağırarak oluşturulanlar gibi birden çok satırı etkileyen veri değişiklikleri için bir dizi tekil SQL deyimi oluşturun `Update` <xref:System.Data.SqlClient.SqlDataAdapter> . Değişiklikler sunucuya ayrı ayrı veya toplu olarak gönderilebilir. Ancak, birden çok deyim içeren toplu işlemlere gönderilse bile, her bir deyim sunucu üzerinde ayrı olarak yürütülür.  
  
- `bcp` <xref:System.Data.SqlClient.SqlBulkCopy> Bir tabloya birçok veri satırı yüklemek için yardımcı program programını veya nesnesini kullanın. Bu teknik çok verimli olsa da, veriler geçici bir tabloya veya tablo değişkenine yüklenmedikleri takdirde sunucu tarafı işlemeyi desteklemez.  
  
## <a name="creating-table-valued-parameter-types"></a>Tablo değerli parametre türleri oluşturma  
 Tablo değerli parametreler, Transact-SQL CREATE TYPE deyimleri kullanılarak tanımlanan, türü kesin belirlenmiş tablo yapılarını temel alır. İstemci uygulamalarınızda tablo değerli parametreleri kullanabilmeniz için bir tablo türü oluşturmanız ve yapıyı SQL Server tanımlamanız gerekir. Tablo türleri oluşturma hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı tablo türleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).  
  
 Aşağıdaki ifade CategoryID ve CategoryName sütunlarından oluşan CategoryTableType adlı bir tablo türü oluşturur:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Tablo türü oluşturduktan sonra, bu türe göre tablo değerli parametreler bildirebilirsiniz. Aşağıdaki Transact-SQL parçası, saklı yordam tanımında tablo değerli bir parametre bildirme işlemini gösterir. Tablo değerli bir parametre bildirmek için READONLY anahtar sözcüğünün gerekli olduğunu unutmayın.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Tablo değerli parametrelerle verileri değiştirme (Transact-SQL)  
 Tablo değerli parametreler, tek bir ifadeyi yürüterek birden çok satırı etkileyen küme tabanlı veri değişiklikleri içinde kullanılabilir. Örneğin, tablo değerli bir parametrede tüm satırları seçebilir ve bunları bir veritabanı tablosuna ekleyebilir veya tablo değerli bir parametreye güncelleştirmek istediğiniz tabloya katılarak bir Update bildirisi oluşturabilirsiniz.  
  
 Aşağıdaki Transact-SQL UPDATE bildiriminde, tablo değerli bir parametresinin Kategoriler tablosuna katılarak nasıl kullanılacağı gösterilmektedir. FROM yan tümcesinde JOIN ile tablo değerli bir parametre kullandığınızda, burada gösterildiği gibi, aynı zamanda tablo değerli parametrenin "EC" olarak diğer adı da yer almalıdır:  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Bu Transact-SQL örneği, tek bir küme tabanlı işlemde bir INSERT işlemini gerçekleştirmek için tablo değerli bir parametreden satırları nasıl seçeceğinizi gösterir.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Tablo değerli parametrelerin sınırlamaları  
 Tablo değerli parametrelere yönelik çeşitli sınırlamalar vardır:  
  
- Tablo değerli parametreleri [clr kullanıcı tanımlı işlevlere](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)geçiremezsiniz.  
  
- Tablo değerli parametrelerin yalnızca BENZERSIZ veya BIRINCIL anahtar kısıtlamalarını destekleyecek şekilde dizini oluşturulabilir. SQL Server tablo değerli parametrelerde istatistik bulundurmaz.  
  
- Tablo değerli parametreler Transact-SQL kodunda salt okunurdur. Tablo değerli bir parametrenin satırlarındaki sütun değerlerini güncelleştiremezsiniz ve satır ekleyemez veya silemezsiniz. Bir saklı yordama veya tablo değerli parametrede parametreli deyime geçirilen verileri değiştirmek için, verileri geçici bir tabloya veya tablo değişkenine eklemeniz gerekir.  
  
- Tablo değerli parametrelerin tasarımını değiştirmek için ALTER TABLE deyimlerini kullanamazsınız.  
  
## <a name="configuring-a-sqlparameter-example"></a>SqlParameter örneğini yapılandırma  
 <xref:System.Data.SqlClient><xref:System.Data.DataTable>, veya nesnelerinden tablo değerli parametrelerin doldurulmasına <xref:System.Data.Common.DbDataReader> Destek <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> . Öğesinin özelliğini kullanarak tablo değerli parametre için bir tür adı belirtmeniz gerekir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter> . , `TypeName` Sunucuda daha önce oluşturulmuş olan uyumlu bir türün adıyla eşleşmelidir. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlParameter> verileri eklemek için nasıl yapılandırılacağını gösterir.  

Aşağıdaki örnekte, `addedCategories` değişkeni bir içerir <xref:System.Data.DataTable> . Değişkenin nasıl doldurulduğuna bakmak için, bir sonraki bölümdeki örneklere bakın ve bir [saklı yordama tablo değerli parametre geçirirsiniz](#passing).

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
  
 Ayrıca <xref:System.Data.Common.DbDataReader> , bu parçada gösterildiği gibi, veri satırlarını tablo değerli bir parametreye akışı için öğesinden türetilmiş herhangi bir nesneyi de kullanabilirsiniz:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a>Bir saklı yordama tablo değerli parametre geçirme  
 Bu örnek, bir saklı yordama tablo değerli parametre verilerinin nasıl geçirileceğini gösterir. Kod, yöntemi kullanılarak eklenen satırları yeni içine ayıklar <xref:System.Data.DataTable> <xref:System.Data.DataTable.GetChanges%2A> . Kodu daha sonra bir tanımlar <xref:System.Data.SqlClient.SqlCommand> , <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliği olarak ayarlar <xref:System.Data.CommandType.StoredProcedure> . , <xref:System.Data.SqlClient.SqlParameter> Yöntemi kullanılarak doldurulur <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> ve, <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> olarak ayarlanır `Structured` . <xref:System.Data.SqlClient.SqlCommand>Daha sonra yöntemi kullanılarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> .  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Parametreli bir SQL bildirimine tablo değerli parametre geçirme  
 Aşağıdaki örnek, dbo 'ya nasıl veri ekleneceğini gösterir. Veri kaynağı olarak tablo değerli parametreye sahip bir SELECT deyimini içeren bir INSERT deyimini kullanarak Kategoriler tablosu. Tablo değerli bir parametreyi parametreli bir SQL ifadesine geçirirken, öğesinin yeni özelliğini kullanarak tablo değerli parametre için bir tür adı belirtmeniz gerekir <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter> . Bu, `TypeName` sunucuda daha önce oluşturulmuş olan uyumlu bir türün adıyla eşleşmelidir. Bu örnekteki kod, `TypeName` dbo içinde tanımlanan tür yapısına başvurmak için özelliğini kullanır. CategoryTableType.  
  
> [!NOTE]
> Tablo değerli bir parametrede kimlik sütunu için bir değer sağlarsanız, oturum için SET IDENTITY_INSERT ifadesini vermeniz gerekir.  
  
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
 Ayrıca, <xref:System.Data.Common.DbDataReader> veri satırlarını tablo değerli bir parametreye akışı için öğesinden türetilmiş herhangi bir nesneyi kullanabilirsiniz. Aşağıdaki kod parçası, ve kullanarak bir Oracle veritabanından veri almayı gösterir <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> . Daha sonra kod, bir <xref:System.Data.SqlClient.SqlCommand> saklı yordamı tek bir giriş parametresiyle çağırmak üzere bir yapılandırır. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>Öğesinin özelliği <xref:System.Data.SqlClient.SqlParameter> olarak ayarlanır `Structured` . , <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` Sonuç kümesini saklı yordama tablo değerli bir parametre olarak geçirir.  
  
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
