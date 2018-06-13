---
title: Tablo değerli parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2cf517e3bd10dbed51c8a98d150bafcb023e438b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365949"
---
# <a name="table-valued-parameters"></a>Tablo değerli parametreleri
Tablo değerli parametreleri birden çok gidiş dönüş veya özel bir sunucu tarafı mantığı verileri işlemek için gerek olmadan birden çok SQL Server için bir istemci uygulamasından veri satırı sıralama için kolay bir yol sağlar. Bir istemci uygulamasında veri satırı kapsüllemek ve tek bir parametreli komut sunucusuna veri gönderme için tablo değerli parametreleri kullanabilirsiniz. Gelen veri satırları sonra üzerinde kullanarak çalıştırılan tablo değişkeni depolanmış [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Sütun değerleri tablo değerli parametrelerinde standart kullanarak erişilebilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT deyimi. Tablo değerli parametreleri kesin türü belirtilmiş ve bunların yapısı otomatik olarak doğrulanır. Tablo değerli parametre boyutu yalnızca sunucu belleği ile sınırlıdır.  
  
> [!NOTE]
>  Bir tablo değerli parametre veri döndüremez. Tablo değerli parametre yalnızca değildir; Çıktı anahtar sözcüğü desteklenmiyor.  
  
 Tablo değerli parametreleri hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tablo değerli parametreleri (veritabanı altyapısı)](http://go.microsoft.com/fwlink/?LinkId=98363) SQL Server Çevrimiçi Kitapları'nda|Oluşturmayı ve tablo değerli parametreleri kullanmayı açıklar.|  
|[Kullanıcı tanımlı tablo türlerinde](http://go.microsoft.com/fwlink/?LinkId=98364) SQL Server Çevrimiçi Kitapları'nda|Tablo değerli parametreleri bildirmek için kullanılan kullanıcı tanımlı tablo türleri açıklanmaktadır.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server'ın önceki sürümlerinde birden çok satır geçirme  
 Tablo değerli parametreleri SQL Server 2008'e sunulmadan önce bir saklı yordam veya parametreli bir SQL komutu için verilerin birden çok satır geçirme seçenekleri sınırlıdır. Bir geliştirici sunucuya birden çok satır geçirme için aşağıdaki seçenekler arasından seçim:  
  
-   Birden çok sütun ve veri satırı değerleri temsil etmek için bir dizi tek tek parametre kullanın. Bu yöntem kullanılarak aktarılan veri miktarını izin parametrelerinin sayısı ile sınırlıdır. SQL Server yordamları, en fazla 2100 parametrelerine sahip olabilirsiniz. Sunucu tarafı mantığı tablo değişkeni ya da geçici bir tablo işlem için ayrı ayrı bu değerleri derlemek için gereklidir.  
  
-   Birden çok veri değerleri ayrılmış dizeler veya XML belgelerini paketini ve ardından bu metin değerleri bir yordam veya deyimi geçirin. Bu seçenek, yordam veya unbundling ve veri yapıları doğrulamak için gerekli mantığı bildirimini değerleri gerektirir.  
  
-   Bir dizi çağırarak oluşturulanlar gibi birden çok satır etkileyen veri değişiklikleri için ayrı SQL deyimi oluşturmak `Update` yöntemi bir <xref:System.Data.SqlClient.SqlDataAdapter>. Değişiklikler sunucuya gönderilen ayrı ayrı veya gruplar halinde toplu. Ancak, hatta birden fazla deyim içeren toplu olarak gönderildiğinde her deyimi ayrı ayrı sunucu üzerinde yürütülür.  
  
-   Kullanım `bcp` yardımcı programı veya <xref:System.Data.SqlClient.SqlBulkCopy> birçok veri satırı bir tabloya yüklemek için nesne. Bu teknik çok verimli olmakla birlikte, verileri bir geçici bir tablo veya tablo değişkeni içine yüklenir sürece, sunucu tarafı işleme desteklemez.  
  
## <a name="creating-table-valued-parameter-types"></a>Tablo değerli parametre türleri oluşturma  
 Tablo değerli parametreleri kullanılarak tanımlanmış kesin türü belirtilmiş tablo yapılarının dayanır [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE deyimleri. Bir tablo türü oluşturmak, istemci uygulamalarınızda tablo değerli parametreleri kullanabilmeniz için önce SQL Server yapısı tanımlamanız gerekir. Tablo türleri oluşturma hakkında daha fazla bilgi için bkz: [kullanıcı tanımlı tablo türlerinde](http://go.microsoft.com/fwlink/?LinkID=98364) SQL Server Books Online.  
  
 Aşağıdaki deyim adlı kullanıcı, Categoryıd'si ve CategoryName sütundan oluşan CategoryTableType adlı bir tablo türü oluşturur:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Bir tablo türü oluşturduktan sonra o türüne göre tablo değerli parametreleri bildirebilirsiniz. Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] parça tablo değerli bir parametre saklı yordam tanımında bildirmeyi gösterir. READONLY anahtar sözcüğü bir tablo değerli parametre bildirmek için gerekli olduğunu unutmayın.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Tablo değerli parametreleri (Transact-SQL) ile verileri değiştirme  
 Tablo değerli parametreleri tek bir deyimde yürüterek birden çok satır etkileyen veri kümesi tabanlı değişiklikleri kullanılabilir. Örneğin, bir tablo değerli parametre tüm satırları seçin ve bir veritabanı tablosuna eklemek veya güncelleştirmek istediğiniz tablonun tablo değerli bir parametre birleştirerek bir güncelleştirme deyimi oluşturabilirsiniz.  
  
 Aşağıdaki [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] güncelleştirme deyimini kategorileri tabloya birleştirerek tablo değerli bir parametre kullanmayı gösterir. Tablo değerli bir parametre FROM yan tümcesinde JOIN ile birlikte kullandığınızda, ayrıca diğer adı, burada tablo değerli parametre "AB" olarak diğer olduğu gösterildiği gibi gerekir:  
  
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
  
## <a name="limitations-of-table-valued-parameters"></a>Tablo değerli parametreleri sınırlamaları  
 Tablo değerli parametreler için bazı sınırlamaları vardır:  
  
-   Tablo değerli parametreleri geçiremezsiniz [CLR kullanıcı tanımlı işlevler](http://msdn.microsoft.com/library/ms131077.aspx).  
  
-   Tablo değerli parametreleri yalnızca benzersiz veya birincil anahtar kısıtlamalarını desteklemek için sıralanabilir. SQL Server tablo değerli parametreleri istatistiklerle korumaz.  
  
-   Tablo değerli parametreleri salt okunur [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kodu. Tablo değerli bir parametre satırlarını sütun değerleri güncelleştirilemiyor ve ekleyemez veya satırları silin. Saklı yordama geçirilen veya tablo değerli parametre deyiminde parametreli verileri değiştirmek için geçici bir tablo veya tablo değişkeni verileri eklemeniz gerekir.  
  
-   Tablo değerli parametreleri tasarımını değiştirmek için ALTER TABLE deyimleri kullanamaz.  
  
## <a name="configuring-a-sqlparameter-example"></a>SqlParameter örnek yapılandırma  
 <xref:System.Data.SqlClient> Tablo değerli parametrelerinden doldurma destekleyen <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> veya <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> nesneleri. Tablo değerli parametre için bir tür adını kullanarak belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Daha önce sunucuda oluşturulan uyumlu bir türü adı eşleşmelidir. Aşağıdaki kod parçası nasıl yapılandırılacağını göstermektedir <xref:System.Data.SqlClient.SqlParameter> veri eklemek için.  
  
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
  
 Türetilmiş herhangi bir nesne de kullanabilirsiniz <xref:System.Data.Common.DbDataReader> bu parçasını gösterildiği gibi tablo değerli bir parametre için veri akışı satırı için:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a>Tablo değerli bir parametre için bir saklı yordam geçirme  
 Bu örnek, bir saklı yordam tablo değerli parametre veri iletmek gösterilmiştir. Kod satırlara yeni bir ayıklar <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.GetChanges%2A> yöntemi. Kod sonra tanımlayan bir <xref:System.Data.SqlClient.SqlCommand>, ayar <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> özelliğine <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Kullanılarak doldurulur <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> yöntemi ve <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> ayarlanır `Structured`. <xref:System.Data.SqlClient.SqlCommand> Kullanarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> yöntemi.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Parametreli SQL deyimi için tablo değerli bir parametre geçirme  
 Aşağıdaki örnek, dbo veri eklemek gösterilmiştir. Veri kaynağı olarak bir tablo değerli parametre içeren bir SELECT alt sorgu ile INSERT deyimi kullanarak kategorileri tablo. Tablo değerli bir parametre parametreli bir SQL deyimi geçirirken, yeni kullanarak tablo değerli parametresi için bir tür adı belirtmelisiniz <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> özelliği bir <xref:System.Data.SqlClient.SqlParameter>. Bu `TypeName` daha önce sunucuda oluşturulan uyumlu bir türü adı eşleşmelidir. Bu örnekteki kod kullanan `TypeName` dbo içinde tanımlanan tür yapısına başvurmak için özellik. CategoryTableType.  
  
> [!NOTE]
>  Bir kimlik sütunu bir tablo değerli parametre için bir değer sağlarsanız, oturumu için AYARLANMIŞ IDENTITY_INSERT deyimi kesmeniz gerekir.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>DataReader akış satırları  
 Türetilmiş herhangi bir nesne de kullanabilirsiniz <xref:System.Data.Common.DbDataReader> tablo değerli bir parametre için veri akışı satırı için. Aşağıdaki kod parçası kullanarak bir Oracle veritabanından veri alma gösteren bir <xref:System.Data.OracleClient.OracleCommand> ve bir <xref:System.Data.OracleClient.OracleDataReader>. Kod sonra yapılandırır bir <xref:System.Data.SqlClient.SqlCommand> tek bir giriş parametresi olan bir saklı yordam çağırmak için. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Özelliği <xref:System.Data.SqlClient.SqlParameter> ayarlanır `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Geçirir `OracleDataReader` sonuç kümesi saklı yordama tablo değerli bir parametre olarak.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Komutlar ve Parametreler](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter Parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
