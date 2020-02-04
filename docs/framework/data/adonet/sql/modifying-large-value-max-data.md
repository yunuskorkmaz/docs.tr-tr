---
title: Büyük değer (max) verilerini değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: cb37fdb85d323d4f0816a3667a4624da8ec75e65
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979852"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
Büyük nesne (LOB) veri türleri, 8 kilobayt (KB) olan en büyük satır boyutunu aşacak olanlardır. SQL Server, 2 ^ 32 bayt kadar büyük değerler depolamaya izin vermek için `varchar`, `nvarchar`ve `varbinary` veri türleri için `max` belirleyicisi sağlar. Tablo sütunları ve Transact-SQL değişkenleri `varchar(max)`, `nvarchar(max)`veya `varbinary(max)` veri türlerini belirtebilir. ADO.NET ' de `max` veri türleri bir `DataReader`tarafından getirilebilir ve ayrıca özel bir işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir. Büyük `varchar` veri türleri için veriler artımlı olarak alınabilir ve güncelleştirilir.  
  
 `max` veri türleri, karşılaştırmalar için Transact-SQL değişkenleri olarak ve birleştirme için kullanılabilir. Ayrıca, bir SELECT ifadesinin yanı sıra toplamaların, birleşimlerin ve alt sorgularda DISTINCT, ORDER BY, GROUP BY yan tümcelerinde de kullanılabilirler.  
  
 Aşağıdaki tabloda SQL Server Books Online 'daki belgelerin bağlantıları verilmiştir.  
  
 **Books Online SQL Server**  
  
1. [Büyük değer veri türlerini kullanma](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Büyük değer türü kısıtlamaları  
 Aşağıdaki kısıtlamalar, daha küçük veri türleri için mevcut olmayan `max` veri türleri için geçerlidir:  
  
- `sql_variant`, büyük bir `varchar` veri türü içeremez.  
  
- Büyük `varchar` sütunları, dizinde anahtar sütun olarak belirtilemez. Bunlar, kümelenmemiş bir dizinde içerilen bir sütunda izin verilir.  
  
- Büyük `varchar` sütunları bölümlendirme anahtar sütunları olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL ' de büyük değer türleriyle çalışma  
 Transact-SQL `OPENROWSET` işlevi, uzak verilere bağlanmak ve bu verilere erişmek için tek seferlik bir yöntemdir. Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir. `OPENROWSET`, bir sorgunun FROM yan tümcesinde tablo adı gibi başvuruda bulunabilir. Ayrıca, bir INSERT, UPDATE veya DELETE deyimlerinin hedef tablosu olarak, OLE DB sağlayıcının özelliklerine tabi olabilir.  
  
 `OPENROWSET` işlevi, verileri bir hedef tabloya yüklemeden doğrudan bir dosyadan okumanıza olanak sağlayan `BULK` satır kümesi sağlayıcısını içerir. Bu, basit bir INSERT SELECT ifadesinde `OPENROWSET` kullanmanıza olanak sağlar.  
  
 `OPENROWSET BULK` seçenek bağımsız değişkenleri, verilerin okunması ve bitmesi, hatalarla ilgilenme ve verilerin nasıl yorumlanacağı konusunda önemli bir denetim sağlar. Örneğin, veri dosyasının `varbinary`, `varchar`veya `nvarchar`türünde tek satırlık, tek sütunlu bir satır kümesi olarak okunacağını belirtebilirsiniz. Tüm sözdizimi ve seçenekler için bkz. Books Online SQL Server.  
  
 Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler. `BULK OPENROWSET` sağlayıcıyı kullanırken, her sütuna değer yerleştirmeseniz bile adlandırılmış sütun listesini sağlamanız gerekir. Bu örnekte birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir. Ayrıca, bu örnekte ThumbnailPhoto olan `OPENROWSET` deyimin sonunda bir bağıntı adı belirtmeniz gerektiğini unutmayın. Bu, dosyanın yüklendiği `ProductPhoto` tablodaki sütunla ilişkili olur.  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>GÜNCELLEŞTIRME kullanılarak veriler güncelleştiriliyor. YAZARKEN  
 Transact-SQL UPDATE bildiriminde `varchar(max)`, `nvarchar(max)`veya `varbinary(max)` sütunlarının içeriğini değiştirmek için yeni yazma sözdizimi vardır. Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır. GÜNCELLEŞTIRME. WRITE söz dizimi kısaltılmış biçimde gösteriliyor:  
  
 GÜNCELLEŞTİR  
  
 { *\<nesnesi >* }  
  
 SET  
  
 { *column_name* = {. WRITE ( *ifade* , @Offset, @Length)}  
  
 WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirildiğini belirtir. İfade, *column_name*kopyalanacak değerdir, `@Offset` ifadenin yazılacağı başlangıç noktasıdır ve `@Length` bağımsız değişkeni, sütunundaki bölümün uzunluktadır. ()  
  
|Eğer|Sonrasında, bu ücretsiz uygulamayı Microsoft'tan|  
|--------|----------|  
|İfade NULL olarak ayarlandı|`@Length` yoksayıldı ve *column_name* değeri belirtilen `@Offset`kesildi.|  
|`@Offset` NULL|Güncelleştirme işlemi, ifadeyi varolan *column_name* değerinin sonuna ekler ve `@Length` yok sayılır.|  
|`@Offset`, column_name değerinin uzunluğundan daha büyük|SQL Server bir hata döndürür.|  
|`@Length` NULL|Güncelleştirme işlemi `@Offset` tüm verileri `column_name` değerinin sonuna kaldırır.|  
  
> [!NOTE]
> Ne `@Offset` ne de `@Length` negatif bir sayı olabilir.  
  
## <a name="example"></a>Örnek  
 Bu Transact-SQL örneği, AdventureWorks veritabanındaki belge tablosundaki `nvarchar(max)` bir sütun olan DocumentSummary içindeki kısmi bir değeri günceller. "Bileşenler" sözcüğünün yerini, var olan verilerde değiştirilecek sözcüğün başlangıç konumunu (kaydır) ve değiştirilecek karakter sayısını (uzunluk) belirterek ' Özellikler ' sözcüğü ile değiştirilmiştir. Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET 'de büyük değerli türlerle çalışma  
 ADO.NET ' de büyük değer türleriyle, bir sonuç kümesi döndürmek için bir <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlParameter> nesneleri olarak veya bir `DataSet`/`DataTable`dolduracak şekilde <xref:System.Data.SqlClient.SqlDataAdapter> kullanarak çalışabilirsiniz. Büyük bir değer türü ve ilgili, daha küçük değer veri türü ile çalışma şekli arasında fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Verileri almak için GetSqlBytes kullanma  
 <xref:System.Data.SqlClient.SqlDataReader> `GetSqlBytes` yöntemi `varbinary(max)` sütununun içeriğini almak için kullanılabilir. Aşağıdaki kod parçası, bir tablodan `varbinary(max)` verileri seçen `cmd` adlı bir <xref:System.Data.SqlClient.SqlCommand> nesnesini ve verileri `reader` olarak alan <xref:System.Data.SqlTypes.SqlBytes>adlı <xref:System.Data.SqlClient.SqlDataReader> bir nesne olduğunu varsayar.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Verileri almak için GetSqlChars kullanma  
 <xref:System.Data.SqlClient.SqlDataReader> `GetSqlChars` yöntemi, bir `varchar(max)` veya `nvarchar(max)` sütununun içeriğini almak için kullanılabilir. Aşağıdaki kod parçası, bir tablodaki `nvarchar(max)` verileri ve verileri alan `reader` adlı bir <xref:System.Data.SqlClient.SqlDataReader> nesnesini seçen `cmd` adlı bir <xref:System.Data.SqlClient.SqlCommand> nesnesini varsayar.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Verileri almak için GetSqlBinary kullanma  
 Bir <xref:System.Data.SqlClient.SqlDataReader> `GetSqlBinary` yöntemi bir `varbinary(max)` sütununun içeriğini almak için kullanılabilir. Aşağıdaki kod parçası, bir tabloda `varbinary(max)` verileri seçen `cmd` adlı bir <xref:System.Data.SqlClient.SqlCommand> nesnesini ve verileri `reader` akışı olarak alan <xref:System.Data.SqlTypes.SqlBinary> adlı <xref:System.Data.SqlClient.SqlDataReader> bir nesne olduğunu varsayar.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Verileri almak için GetBytes kullanma  
 Bir <xref:System.Data.SqlClient.SqlDataReader> `GetBytes` yöntemi belirtilen sütun uzaklığında belirtilen dizi uzaklığında başlayarak bir bayt dizisine kadar olan bir bayt akışını okur. Aşağıdaki kod parçası, bayt dizisine bayt alan `reader` adlı bir <xref:System.Data.SqlClient.SqlDataReader> nesnesi olduğunu varsayar. `GetSqlBytes`farklı olarak, `GetBytes` dizi arabelleği için bir boyut gerektirdiğini unutmayın.  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Verileri almak için GetValue 'yi kullanma  
 Bir <xref:System.Data.SqlClient.SqlDataReader> `GetValue` yöntemi, belirtilen sütun içindeki değeri bir diziye okur. Aşağıdaki kod parçası, ilk sütun kaydırından ikili verileri alan ve ardından ikinci sütun kaydırından dize verileri alan `reader` adlı <xref:System.Data.SqlClient.SqlDataReader> bir nesne olduğunu varsayar.  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Büyük değer türlerinden CLR türlerine dönüştürme  
 `ToString`gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak bir `varchar(max)` veya `nvarchar(max)` sütununun içeriğini dönüştürebilirsiniz. Aşağıdaki kod parçası, verileri alan `reader` adlı bir <xref:System.Data.SqlClient.SqlDataReader> nesne olduğunu varsayar.  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod `AdventureWorks` veritabanındaki `ProductPhoto` tablosundan adı ve `LargePhoto` nesnesini alır ve bir dosyaya kaydeder. Derlemenin <xref:System.Drawing> ad alanına bir başvuru ile derlenmesi gerekir.  <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> yöntemi, `Stream` özelliği sunan bir <xref:System.Data.SqlTypes.SqlBytes> nesnesi döndürür. Kod bunu, yeni bir `Bitmap` nesnesi oluşturmak için kullanır ve sonra GIF `ImageFormat`kaydeder.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük değer türü parametrelerini kullanma  
 Büyük değer türleri, <xref:System.Data.SqlClient.SqlParameter> nesnelerinde daha küçük değer türlerini kullandığınız şekilde <xref:System.Data.SqlClient.SqlParameter> nesnelerinde kullanılabilir. Büyük değer türlerini, aşağıdaki örnekte gösterildiği gibi <xref:System.Data.SqlClient.SqlParameter> değerler olarak alabilirsiniz. Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary saklı yordamının bulunduğunu varsayar. Saklı yordam, @DocumentID adlı bir giriş parametresi alır ve @DocumentSummary output parametresindeki DocumentSummary sütununun içeriğini döndürür.  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Örnek  
 ADO.NET kodu, GetDocumentSummary saklı yordamını yürütmek için <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> nesneleri oluşturur ve büyük bir değer türü olarak depolanan belge özetini alır. Kod @DocumentID giriş parametresi için bir değer geçirir ve konsol penceresinde @DocumentSummary output parametresine geri geçirilen sonuçları görüntüler.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
