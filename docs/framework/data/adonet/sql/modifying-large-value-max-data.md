---
title: Büyük değer (max) verilerini değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 4748740379df689669ee87f66dce58a7015d1217
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172703"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme

Büyük nesne (LOB) veri türleri, 8 kilobayt (KB) olan en büyük satır boyutunu aşacak olanlardır. SQL Server,, `max` `varchar` `nvarchar` ve veri türleri için, `varbinary` 2 ^ 32 bayt kadar büyük değerler depolamaya izin vermek için bir tanımlayıcı sağlar. Tablo sütunları ve Transact-SQL değişkenleri `varchar(max)` , `nvarchar(max)` veya `varbinary(max)` veri türlerini belirtebilir. ADO.NET ' de, `max` veri türleri bir tarafından getirilebilir `DataReader` ve özel bir işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir. Büyük `varchar` veri türleri için veriler artımlı olarak alınabilir ve güncelleştirilir.  
  
 `max`Veri türleri, karşılaştırmalar Için Transact-SQL değişkenleri olarak ve birleştirme için kullanılabilir. Ayrıca, bir SELECT ifadesinin yanı sıra toplamaların, birleşimlerin ve alt sorgularda DISTINCT, ORDER BY, GROUP BY yan tümcelerinde de kullanılabilirler.  
  
 Aşağıdaki tabloda SQL Server Books Online 'daki belgelerin bağlantıları verilmiştir.  
  
 **SQL Server belgeleri**  
  
1. [Büyük değer veri türlerini kullanma](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Büyük değer türü kısıtlamaları  

 Aşağıdaki kısıtlamalar `max` , daha küçük veri türleri için mevcut olmayan veri türleri için geçerlidir:  
  
- `sql_variant`, Büyük bir `varchar` veri türü içeremez.  
  
- Büyük `varchar` sütunlar, bir dizinde anahtar sütun olarak belirtilemez. Bunlar, kümelenmemiş bir dizinde içerilen bir sütunda izin verilir.  
  
- Büyük `varchar` sütunlar bölümlendirme anahtar sütunları olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL ' de büyük değer türleriyle çalışma  

 Transact-SQL `OPENROWSET` işlevi, uzak verilere bağlanmak ve bu verilere erişmek için tek seferlik bir yöntemdir. Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir. `OPENROWSET` bir sorgunun FROM yan tümcesinde tablo adı gibi bir sorgu oluşturulabilir. Ayrıca, bir INSERT, UPDATE veya DELETE deyimlerinin hedef tablosu olarak, OLE DB sağlayıcının özelliklerine tabi olabilir.  
  
 `OPENROWSET`İşlevi, `BULK` verileri bir hedef tabloya yüklemeden doğrudan bir dosyadan okumanıza olanak sağlayan satır kümesi sağlayıcısını içerir. Bu, `OPENROWSET` Basit BIR INSERT SELECT ifadesinde kullanmanıza olanak sağlar.  
  
 `OPENROWSET BULK`Seçenek bağımsız değişkenleri, verilerin okunması ve bitmesi, hatalarla ilgilenme ve verilerin nasıl yorumlanacağı konusunda önemli bir denetim sağlar. Örneğin, veri dosyasının, veya türünde tek satırlık, tek sütunlu satır kümesi olarak okunacağını belirtebilirsiniz `varbinary` `varchar` `nvarchar` . Tüm sözdizimi ve seçenekler için bkz. Books Online SQL Server.  
  
 Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler. `BULK OPENROWSET`Sağlayıcıyı kullanırken, her sütuna değer yerleştirmeseniz bile adlandırılmış sütun listesini sağlamanız gerekir. Bu örnekte birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir. Ayrıca, bu örnekte ThumbnailPhoto olan deyimin sonunda bir bağıntı adı belirtmeniz gerektiğini unutmayın `OPENROWSET` . Bu, `ProductPhoto` dosyanın yüklendiği tablodaki sütunuyla ilişkili olur.  
  
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

 Transact-SQL UPDATE bildiriminde,, veya sütunlarının içeriğini değiştirmek için yeni yazma sözdizimi `varchar(max)` vardır `nvarchar(max)` `varbinary(max)` . Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır. GÜNCELLEŞTIRME. WRITE söz dizimi kısaltılmış biçimde gösteriliyor:  
  
 UPDATE  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}  
  
 WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirildiğini belirtir. İfade, *column_name*kopyalanacak değerdir, `@Offset` ifadenin yazılacağı başlangıç noktasıdır ve `@Length` bağımsız değişken, sütundaki bölümün uzunluğudur ve bağımsız değişkeni, sütununda bulunan bölümdür.  
  
|Eğer|Ardından|  
|--------|----------|  
|İfade NULL olarak ayarlandı|`@Length` yok sayılır ve *column_name* değeri belirtilen şekilde kesilir `@Offset` .|  
|`@Offset` NULL|Güncelleştirme işlemi, ifadeyi varolan *column_name* değerinin sonuna ekler ve `@Length` yok sayılır.|  
|`@Offset` column_name değerinin uzunluğundan büyük|SQL Server bir hata döndürür.|  
|`@Length` NULL|Güncelleştirme işlemi, tüm verileri içinden `@Offset` değeri sonuna kaldırır `column_name` .|  
  
> [!NOTE]
> Ne `@Offset` de `@Length` negatif bir sayı olabilir.  
  
## <a name="example"></a>Örnek  

 Bu Transact-SQL örneği, `nvarchar(max)` AdventureWorks veritabanındaki belge tablosundaki bir sütun olan DocumentSummary içindeki kısmi bir değeri günceller. "Bileşenler" sözcüğünün yerini, var olan verilerde değiştirilecek sözcüğün başlangıç konumunu (kaydır) ve değiştirilecek karakter sayısını (uzunluk) belirterek ' Özellikler ' sözcüğü ile değiştirilmiştir. Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.  
  
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

 Büyük değer türlerini <xref:System.Data.SqlClient.SqlParameter> bir sonuç kümesi döndürmek için bir içinde nesne olarak belirterek veya bir öğesini dolduracak şekilde kullanarak ADO.NET içinde büyük değer türleriyle çalışabilirsiniz <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> `DataSet` / `DataTable` . Büyük bir değer türü ve ilgili, daha küçük değer veri türü ile çalışma şekli arasında fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Verileri almak için GetSqlBytes kullanma  

 `GetSqlBytes`Öğesinin yöntemi <xref:System.Data.SqlClient.SqlDataReader> bir sütunun içeriğini almak için kullanılabilir `varbinary(max)` . Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan veri seçen adlı bir nesne `varbinary(max)` ve <xref:System.Data.SqlClient.SqlDataReader> verileri olarak alan adlı bir nesne olduğunu varsayar `reader` <xref:System.Data.SqlTypes.SqlBytes> .  
  
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

 `GetSqlChars`Yöntemi <xref:System.Data.SqlClient.SqlDataReader> bir veya sütununun içeriğini almak için kullanılabilir `varchar(max)` `nvarchar(max)` . Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan verileri seçen adlı bir `nvarchar(max)` nesne ve verileri alan adlı bir <xref:System.Data.SqlClient.SqlDataReader> nesne olduğunu varsayar `reader` .  
  
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

 `GetSqlBinary`Bir <xref:System.Data.SqlClient.SqlDataReader> sütunun içeriğini almak için, bir yöntemi kullanılabilir `varbinary(max)` . Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> `cmd` bir tablodan veri seçen adlı bir nesne `varbinary(max)` ve <xref:System.Data.SqlClient.SqlDataReader> `reader` verileri akış olarak alan adlı bir nesne olarak varsayar <xref:System.Data.SqlTypes.SqlBinary> .  
  
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

 `GetBytes`Bir a yöntemi belirtilen <xref:System.Data.SqlClient.SqlDataReader> sütundan bir bayt akışını belirtilen dizi uzaklığında başlayarak bir bayt dizisine okur. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> `reader` bayt dizisine bayt alan adlı bir nesne olduğunu varsayar. Öğesinin aksine, `GetSqlBytes` `GetBytes` dizi arabelleği için bir boyut gerektirdiğini unutmayın.  
  
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

 `GetValue`Bir öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> belirtilen sütun içindeki değeri bir diziye okur. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> `reader` ilk sütun kaydırından ikili verileri alan adlı bir nesneyi ve sonra ikinci sütun kaydırından dize verilerini alır.  
  
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

 Bir `varchar(max)` veya `nvarchar(max)` sütununun içeriğini, gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak dönüştürebilirsiniz `ToString` . Aşağıdaki kod parçası, verileri alan <xref:System.Data.SqlClient.SqlDataReader> adlı bir nesnenin olduğunu varsayar `reader` .  
  
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

 Aşağıdaki kod, `LargePhoto` veritabanındaki tablodaki adı ve nesneyi alır `ProductPhoto` `AdventureWorks` ve bir dosyaya kaydeder. Derlemenin ad alanı başvurusuyla derlenmesi gerekir <xref:System.Drawing> .  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>Öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlTypes.SqlBytes> bir özelliği kullanıma sunan bir nesne döndürür `Stream` . Kod bunu, yeni bir nesne oluşturmak için kullanır `Bitmap` ve ardından gif öğesine kaydeder `ImageFormat` .  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük değer türü parametrelerini kullanma  

 Büyük değer türleri nesnelerde <xref:System.Data.SqlClient.SqlParameter> , nesnelerde daha küçük değer türlerini kullandığınız şekilde de kullanılabilir <xref:System.Data.SqlClient.SqlParameter> . <xref:System.Data.SqlClient.SqlParameter>Aşağıdaki örnekte gösterildiği gibi büyük değer türlerini değer olarak alabilirsiniz. Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary saklı yordamının bulunduğunu varsayar. Saklı yordam adlı bir giriş parametresi alır @DocumentID ve çıkış parametresindeki DocumentSummary sütununun içeriğini döndürür @DocumentSummary .  
  
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

 ADO.NET kodu, <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> GetDocumentSummary saklı yordamını yürütmek ve büyük bir değer türü olarak depolanan belge özetini almak için nesneler oluşturur. Kod, giriş parametresi için bir değer geçirir @DocumentID ve @DocumentSummary konsol penceresinde çıkış parametresine geri geçirilen sonuçları görüntüler.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
