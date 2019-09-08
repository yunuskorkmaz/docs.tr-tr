---
title: ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 34f0a61329667a42aa42693e93169a5b6fb0aa5e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792046"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
Büyük nesne (LOB) veri türleri, 8 kilobayt (KB) olan en büyük satır boyutunu aşacak olanlardır. SQL Server,, `max` ve `nvarchar` `varchar` veri`varbinary` türleri için, 2 ^ 32 bayt kadar büyük değerler depolamaya izin vermek için bir tanımlayıcı sağlar. Tablo sütunları ve Transact-SQL değişkenleri, `varchar(max)` `nvarchar(max)`veya `varbinary(max)` veri türlerini belirtebilir. ADO.net `max` ' de, veri türleri bir tarafından getirilebilir ve özel `DataReader`bir işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir. Büyük `varchar` veri türleri için veriler artımlı olarak alınabilir ve güncelleştirilir.  
  
 `max` Veri türleri, karşılaştırmalar için Transact-SQL değişkenleri olarak ve birleştirme için kullanılabilir. Ayrıca, bir SELECT ifadesinin yanı sıra toplamaların, birleşimlerin ve alt sorgularda DISTINCT, ORDER BY, GROUP BY yan tümcelerinde de kullanılabilirler.  
  
 Aşağıdaki tabloda SQL Server Books Online 'daki belgelerin bağlantıları verilmiştir.  
  
 **Books Online SQL Server**  
  
1. [Büyük değer veri türlerini kullanma](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Büyük değer türü kısıtlamaları  
 Aşağıdaki kısıtlamalar, daha küçük veri `max` türleri için mevcut olmayan veri türleri için geçerlidir:  
  
- `sql_variant` , Büyük`varchar` bir veri türü içeremez.  
  
- Büyük `varchar` sütunlar, bir dizinde anahtar sütun olarak belirtilemez. Bunlar, kümelenmemiş bir dizinde içerilen bir sütunda izin verilir.  
  
- Büyük `varchar` sütunlar bölümlendirme anahtar sütunları olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL ' de büyük değer türleriyle çalışma  
 Transact-SQL `OPENROWSET` işlevi, uzak verilere bağlanmak ve bu verilere erişmek için tek seferlik bir yöntemdir. Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir. `OPENROWSET`bir sorgunun FROM yan tümcesinde tablo adı gibi bir sorgu oluşturulabilir. Ayrıca, bir INSERT, UPDATE veya DELETE deyimlerinin hedef tablosu olarak, OLE DB sağlayıcının özelliklerine tabi olabilir.  
  
 İşlevi, verileri bir `BULK` hedef tabloya yüklemeden doğrudan bir dosyadan okumanıza olanak sağlayan satır kümesi sağlayıcısını içerir. `OPENROWSET` Bu, basit bir INSERT `OPENROWSET` Select ifadesinde kullanmanıza olanak sağlar.  
  
 `OPENROWSET BULK` Seçenek bağımsız değişkenleri, verilerin okunması ve bitmesi, hatalarla ilgilenme ve verilerin nasıl yorumlanacağı konusunda önemli bir denetim sağlar. Örneğin, veri dosyasının, veya `varbinary` `nvarchar`türünde `varchar`tek satırlık, tek sütunlu satır kümesi olarak okunacağını belirtebilirsiniz. Tüm sözdizimi ve seçenekler için bkz. Books Online SQL Server.  
  
 Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler. `BULK OPENROWSET` Sağlayıcıyı kullanırken, her sütuna değer yerleştirmeseniz bile adlandırılmış sütun listesini sağlamanız gerekir. Bu örnekte birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir. Ayrıca, bu örnekte thumbnailPhoto olan `OPENROWSET` deyimin sonunda bir bağıntı adı belirtmeniz gerektiğini unutmayın. Bu, dosyanın yüklendiği `ProductPhoto` tablodaki sütunuyla ilişkili olur.  
  
```  
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
 Transact-SQL Update bildiriminde `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` sütunlarının içeriğini değiştirmek için yeni yazma sözdizimi vardır. Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır. GÜNCELLEŞTIRME. WRITE söz dizimi kısaltılmış biçimde gösteriliyor:  
  
 GÜNCELLEŞTİR  
  
 *{\<nesne >* }  
  
 SET  
  
 { *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}  
  
 WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirildiğini belirtir. İfade, *column_name*' a kopyalanacak değerdir, `@Offset` ifadenin `@Length` yazılacağı başlangıç noktasıdır ve bağımsız değişkeni, sütunundaki bölümün uzunluğudur ve bağımsız değişkendir.  
  
|Eğer|Ardından|  
|--------|----------|  
|İfade NULL olarak ayarlandı|`@Length`yok sayılır ve *column_name* içindeki değer belirtilen `@Offset`şekilde kesilir.|  
|`@Offset`NULL|Güncelleştirme işlemi, ifadeyi varolan *column_name* değerinin sonuna ekler ve `@Length` yok sayılır.|  
|`@Offset`column_name değerinin uzunluğundan büyük|SQL Server bir hata döndürür.|  
|`@Length`NULL|Güncelleştirme işlemi, tüm verileri içinden `@Offset` `column_name` değeri sonuna kaldırır.|  
  
> [!NOTE]
> Ne `@Offset` de`@Length` negatif bir sayı olabilir.  
  
## <a name="example"></a>Örnek  
 Bu Transact-SQL örneği, AdventureWorks veritabanındaki belge tablosundaki bir `nvarchar(max)` sütun olan DocumentSummary içindeki kısmi bir değeri günceller. "Bileşenler" sözcüğünün yerini, var olan verilerde değiştirilecek sözcüğün başlangıç konumunu (kaydır) ve değiştirilecek karakter sayısını (uzunluk) belirterek ' Özellikler ' sözcüğü ile değiştirilmiştir. Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.  
  
```  
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
 Büyük değer türlerini bir sonuç kümesi döndürmek <xref:System.Data.SqlClient.SqlParameter> için bir <xref:System.Data.SqlClient.SqlDataReader> içinde nesne olarak belirterek veya bir <xref:System.Data.SqlClient.SqlDataAdapter> öğesini dolduracak `DataSet` /şekilde `DataTable`kullanarak ADO.NET içinde büyük değer türleriyle çalışabilirsiniz. Büyük bir değer türü ve ilgili, daha küçük değer veri türü ile çalışma şekli arasında fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Verileri almak için GetSqlBytes kullanma  
 Öğesinin yöntemi bir sütunun`varbinary(max)` içeriğini almak için kullanılabilir. `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> Aşağıdaki kod parçası, bir tablodan <xref:System.Data.SqlClient.SqlCommand> veri seçen `cmd` `varbinary(max)` adlı bir nesne ve <xref:System.Data.SqlClient.SqlDataReader> verileri olarak <xref:System.Data.SqlTypes.SqlBytes>alan adlı `reader` bir nesne olduğunu varsayar.  
  
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
 `GetSqlChars` Yöntemi`varchar(max)` bir veya sütununun`nvarchar(max)` içeriğini almak için kullanılabilir. <xref:System.Data.SqlClient.SqlDataReader> Aşağıdaki kod parçası, bir tablodan <xref:System.Data.SqlClient.SqlCommand> verileri seçen `cmd` `nvarchar(max)` adlı bir nesne ve <xref:System.Data.SqlClient.SqlDataReader> verileri alan adlı `reader` bir nesne olduğunu varsayar.  
  
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
 Bir sütunun içeriğini <xref:System.Data.SqlClient.SqlDataReader> almak için, bir yöntemikullanılabilir.`GetSqlBinary` `varbinary(max)` Aşağıdaki kod parçası, bir tablodan <xref:System.Data.SqlClient.SqlCommand> veri seçen `cmd` `varbinary(max)` adlı bir nesne ve <xref:System.Data.SqlClient.SqlDataReader> verileri <xref:System.Data.SqlTypes.SqlBinary> akış olarak alan adlı `reader` bir nesne olarak varsayar.  
  
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
 Bir `GetBytes` a<xref:System.Data.SqlClient.SqlDataReader> yöntemi belirtilen sütundan bir bayt akışını belirtilen dizi uzaklığında başlayarak bir bayt dizisine okur. Aşağıdaki kod parçası, bayt dizisine <xref:System.Data.SqlClient.SqlDataReader> bayt alan `reader` adlı bir nesne olduğunu varsayar. Öğesinin aksine `GetSqlBytes` `GetBytes` , dizi arabelleği için bir boyut gerektirdiğini unutmayın.  
  
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
 `GetValue` Bir<xref:System.Data.SqlClient.SqlDataReader> öğesinin yöntemi, belirtilen sütun içindeki değeri bir diziye okur. Aşağıdaki kod parçası, ilk sütun <xref:System.Data.SqlClient.SqlDataReader> kaydırından `reader` ikili verileri alan adlı bir nesneyi ve sonra ikinci sütun kaydırından dize verilerini alır.  
  
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
 Bir `varchar(max)` `ToString`veya `nvarchar(max)` sütununun içeriğini, gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak dönüştürebilirsiniz. Aşağıdaki kod parçası, verileri alan <xref:System.Data.SqlClient.SqlDataReader> adlı `reader` bir nesnenin olduğunu varsayar.  
  
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
 Aşağıdaki kod, `LargePhoto` `AdventureWorks` veritabanındaki `ProductPhoto` tablodaki adı ve nesneyi alır ve bir dosyaya kaydeder. Derlemenin <xref:System.Drawing> ad alanı başvurusuyla derlenmesi gerekir.  Öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlTypes.SqlBytes> bir özelliği`Stream` kullanıma sunan bir nesne döndürür. <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Kod bunu, yeni `Bitmap` bir nesne oluşturmak için kullanır ve ardından gif `ImageFormat`öğesine kaydeder.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük değer türü parametrelerini kullanma  
 Büyük değer türleri nesnelerde, <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter> nesnelerde daha küçük değer türlerini kullandığınız şekilde de kullanılabilir. Aşağıdaki örnekte gösterildiği gibi büyük değer türlerini <xref:System.Data.SqlClient.SqlParameter> değer olarak alabilirsiniz. Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary saklı yordamının bulunduğunu varsayar. Saklı yordam adlı @DocumentID bir giriş parametresi alır ve @DocumentSummary çıkış parametresindeki DocumentSummary sütununun içeriğini döndürür.  
  
```  
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
 ADO.NET kodu, GetDocumentSummary saklı yordamını yürütmek ve büyük bir değer türü olarak depolanan belge özetini almak için <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> nesneler oluşturur. Kod, @DocumentID giriş parametresi için bir değer geçirir ve konsol penceresinde @DocumentSummary çıkış parametresine geri geçirilen sonuçları görüntüler.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
