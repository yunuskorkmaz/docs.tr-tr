---
title: Büyük Değer (max) Veri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174283"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
Büyük nesne (LOB) veri türleri, maksimum satır boyutunu 8 kilobayt (KB) aşan veri türleridir. SQL Server, `max` 2^32 `nvarchar`bayt kadar büyük değerlerin depolanmasına izin vermek için , ve `varbinary` veri türleri için `varchar`bir belirtim sağlar. Tablo sütunları ve Transact-SQL `varchar(max)` `nvarchar(max)`değişkenleri `varbinary(max)` , veya veri türleri belirtebilir. ADO.NET olarak, `max` veri türleri bir , `DataReader`tarafından getirilebilir ve ayrıca herhangi bir özel işleme olmadan hem giriş hem de çıkış parametre değerleri olarak belirtilebilir. Büyük `varchar` veri türleri için veriler alınabilir ve artımlı olarak güncellenebilir.  
  
 Veri `max` türleri karşılaştırmalar, Transact-SQL değişkenleri olarak ve birlikteleştirme için kullanılabilir. Ayrıca, SELECT deyiminin DISTINCT, ORDER BY, GROUP by yan tümcelerinde ve toplamlar, birleştirmeler ve alt sorgularda da kullanılabilir.  
  
 Aşağıdaki tablo, SQL Server Books Online'daki belgelere bağlantılar sağlar.  
  
 **SQL Server belgeleri**  
  
1. [Büyük Değer Veri Türlerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Büyük Değer Türü Kısıtlamaları  
 Aşağıdaki kısıtlamalar, daha `max` küçük veri türleri için bulunmayan veri türleri için geçerlidir:  
  
- A `sql_variant` büyük `varchar` bir veri türü içeremez.  
  
- Büyük `varchar` sütunlar bir dizinteki anahtar sütun olarak belirtilemez. Kümelenmiş olmayan bir dizinde dahil edilmiş bir sütunda izin verilir.  
  
- Büyük `varchar` sütunlar, anahtar sütunları bölümleme olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL'de Büyük Değer Türleri ile Çalışma  
 Transact-SQL `OPENROWSET` işlevi, uzak verileri bağlamak ve erişmek için tek seferlik bir yöntemdir. Bir OLE DB veri kaynağından uzak verilere erişmek için gereken tüm bağlantı bilgilerini içerir. `OPENROWSET`bir sorgunun FROM yan tümcesinde tablo adıymış gibi başvurulabilir. OLE DB sağlayıcısının yeteneklerine bağlı olarak bir INSERT, UPDATE veya DELETE deyiminin hedef tablosu olarak da başvurulabilir.  
  
 İşlev, `OPENROWSET` `BULK` verileri hedef tabloya yüklemeden verileri doğrudan bir dosyadan okumanızı sağlayan satır kümesi sağlayıcısını içerir. Bu, basit bir `OPENROWSET` INSERT SELECT deyiminde kullanmanıza olanak sağlar.  
  
 Seçenek `OPENROWSET BULK` bağımsız değişkenleri, okuma verilerinin nereden başlanacağı ve sonlanacağı, hatalarla nasıl başa çıkılabilen ve verilerin nasıl yorumlanacağı konusunda önemli denetim sağlar. Örneğin, veri dosyasının tek satırlı, tek sütunlu bir satır türü `varbinary`, `varchar`veya `nvarchar`. Sözdiziminin ve seçeneklerin tamamı için SQL Server Books Online'a bakın.  
  
 Aşağıdaki örnek, AdventureWorks örnek veritabanındaki ProductPhoto tablosuna bir fotoğraf ekler. Sağlayıcıkullanırken, `BULK OPENROWSET` her sütuna değerler eklemeseniz bile adlandırılmış sütun listesini sağlamanız gerekir. Bu durumda birincil anahtar bir kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir. `OPENROWSET` Ayrıca, bu durumda ThumbnailPhoto olan bildirimin sonunda bir korelasyon adı sağlamanız gerektiğini unutmayın. Bu, dosyanın yüklendiği `ProductPhoto` tablodaki sütunla ilişkilidir.  
  
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
  
## <a name="updating-data-using-update-write"></a>UPDATE kullanarak Verileri Güncelleme . Yazmak  
 Transact-SQL UPDATE deyimi, sütunların `varchar(max)` `nvarchar(max)`veya `varbinary(max)` sütunların içeriğini değiştirmek için yeni WRITE sözdizimine sahiptir. Bu, verilerin kısmi güncelleştirmelerini gerçekleştirmenize olanak tanır. GÜNCELLEME . WRITE sözdizimi burada kısaltılmış biçimde gösterilmiştir:  
  
 UPDATE  
  
 { * \<nesne>* }  
  
 SET  
  
 { *column_name* = { . WRITE *expression* ( @Offset ifade @Length , , ) }  
  
 WRITE yöntemi, *column_name* değerinin bir bölümünün değiştirileceğini belirtir. İfade, *column_name*kopyalanacak `@Offset` değerdir, ifadenin yazılacağı başlangıç noktasıdır ve `@Length` bağımsız değişken sütundaki bölümün uzunluğudur.  
  
|Eğer|Ardından|  
|--------|----------|  
|İfade NULL olarak ayarlanır|`@Length`yoksayılmalı ve *column_name* değeri belirtilen `@Offset`de kesilir.|  
|`@Offset`NULL olduğunu|Güncelleştirme işlemi, varolan *column_name* değerinin sonundaki ifadeyi ekler ve `@Length` yoksayılır.|  
|`@Offset`column_name değerinin uzunluğundan büyüktür|SQL Server bir hata döndürür.|  
|`@Length`NULL olduğunu|Güncelleştirme `column_name` işlemi, değerin `@Offset` sonuna kadar tüm verileri kaldırır.|  
  
> [!NOTE]
> Negatif `@Offset` `@Length` sayı ne de olabilir.  
  
## <a name="example"></a>Örnek  
 Bu Transact-SQL örneği, AdventureWorks veritabanındaki `nvarchar(max)` Belge tablosundaki bir sütun olan DocumentSummary'de kısmi bir değeri güncelleştirir. 'Bileşenler' sözcüğü, değiştirilen sözcük, varolan verilerde değiştirilecek sözcüğün başlangıç konumu (mahsup) ve değiştirilecek karakter sayısı (uzunluk) belirtilerek 'özellikler' sözcüğü yle değiştirilir. Örnek, sonuçları karşılaştırmak için UPDATE deyiminden önce ve sonra SELECT deyimlerini içerir.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET Büyük Değer Türleri ile Çalışma  
 ADO.NET'da büyük değer türleri ile bir sonuç <xref:System.Data.SqlClient.SqlParameter> kümesini döndürmek <xref:System.Data.SqlClient.SqlDataReader> için büyük değer türlerini <xref:System.Data.SqlClient.SqlDataAdapter> nesneler olarak `DataSet` / `DataTable`belirterek veya bir . Büyük bir değer türüyle çalışma şekliniz ile ilgili, daha küçük değer veri türü arasında hiçbir fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Veri Almak için GetSqlBytes kullanma  
 <xref:System.Data.SqlClient.SqlDataReader> Yöntem bir `varbinary(max)` `GetSqlBytes` sütunun içeriğini almak için kullanılabilir. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `varbinary(max)` veri seçen adlı <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri <xref:System.Data.SqlTypes.SqlBytes>. olarak alan adlı bir nesneyi varsayar  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Veri Almak için GetSqlChars kullanma  
 Yöntem, `GetSqlChars` bir `varchar(max)` veya `nvarchar(max)` sütunun içeriğini almak için kullanılabilir. <xref:System.Data.SqlClient.SqlDataReader> Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `nvarchar(max)` veri seçen adlandırılmış <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri alan adlı bir nesneyi varsayar.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Veri Almak için GetSqlBinary kullanma  
 Bir `GetSqlBinary` `varbinary(max)` sütunun <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için bir yöntem kullanılabilir. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlCommand> bir `cmd` tablodan `varbinary(max)` veri seçen adlandırılmış <xref:System.Data.SqlClient.SqlDataReader> bir `reader` nesneyi ve verileri <xref:System.Data.SqlTypes.SqlBinary> akış olarak alan adlı bir nesneyi varsayar.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Veri Almak için GetBytekullanma  
 Bir `GetBytes` yöntem, <xref:System.Data.SqlClient.SqlDataReader> belirtilen sütun ofset bir bayt akışı okur belirtilen dizi ofset başlayan bir bayt dizi. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> bayt `reader` dizisini alan adlandırılmış bir nesneyi varsayar. Aksine, `GetSqlBytes` `GetBytes` dizi arabelleği için bir boyut gerektirdiğini unutmayın.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Veri Almak için GetValue'i kullanma  
 Bir `GetValue` <xref:System.Data.SqlClient.SqlDataReader> yöntem, belirtilen sütun ofset bir dizi içine değeri okur. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> ilk `reader` sütun ofsetinden ikili veri alan ve ardından ikinci sütun ofsetinden veri dizen adlı bir nesneyi varsayar.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Büyük Değer Türlerinden CLR Türlerine Dönüştürme  
 Bir `varchar(max)` veya `nvarchar(max)` sütunun içeriğini dize dönüştürme yöntemlerinden herhangi `ToString`birini kullanarak dönüştürebilirsiniz. Aşağıdaki kod parçası, <xref:System.Data.SqlClient.SqlDataReader> verileri `reader` alan adlı bir nesneyi varsayar.  
  
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
 Aşağıdaki kod, `LargePhoto` `ProductPhoto` `AdventureWorks` veritabanındaki tablodan adı ve nesneyi alır ve bir dosyaya kaydeder. Derlemenin <xref:System.Drawing> ad alanına bir başvuruyla derlemesi gerekir.  Bir <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> `Stream` özelliği <xref:System.Data.SqlClient.SqlDataReader> ortaya <xref:System.Data.SqlTypes.SqlBytes> çıkaran bir nesneyi döndürür yöntemi. Kod bunu yeni `Bitmap` bir nesne oluşturmak için kullanır ve sonra `ImageFormat`Gif'e kaydeder.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük Değer Türü Parametrelerini Kullanma  
 Büyük değer türleri, <xref:System.Data.SqlClient.SqlParameter> nesnelerde daha küçük değer türlerini <xref:System.Data.SqlClient.SqlParameter> kullandığınız gibi nesnelerde de kullanılabilir. Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlParameter> gibi, büyük değer türlerini değer olarak alabilirsiniz. Kod, AdventureWorks örnek veritabanında aşağıdaki GetDocumentSummary depolanan yordamın var olduğunu varsayar. Depolanan yordam, adlı @DocumentID bir giriş parametresi alır ve @DocumentSummary çıkış parametresinde DocumentSummary sütununun içeriğini döndürür.  
  
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
 ADO.NET kodu, <xref:System.Data.SqlClient.SqlConnection> GetDocumentSummary depolanan yordamı yürütmek ve büyük bir değer türü olarak depolanan belge özetini almak için oluşturur ve <xref:System.Data.SqlClient.SqlCommand> nesneler. Kod giriş parametresi @DocumentID için bir değer geçirir ve Konsol @DocumentSummary penceresindeçıktı parametresinde geçirilen sonuçları görüntüler.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [ADO.NET’te SQL Server Veri İşlemleri](sql-server-data-operations.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
