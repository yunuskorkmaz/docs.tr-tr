---
title: ADO.NET büyük değer (Maks) verileri değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 285803d92474efd3268816d1af06eb3ff4abbc79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET büyük değer (Maks) verileri değiştirme
Büyük nesne (LOB) veri türleri 8 kilobayt (KB) en fazla satır boyutunu aşan olanlardır. SQL Server sağlayan bir `max` tanımlayıcısı için `varchar`, `nvarchar`, ve `varbinary` değerlerin depolama 2 büyüklüğünde izin vermek için veri türleri ^ 32 bayt. Tablo sütunları ve Transact-SQL değişkenleri belirtebilir `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` veri türleri. ADO.NET, `max` veri türleri getirilen tarafından bir `DataReader`ve herhangi bir özel işleme yapılmadan hem giriş ve çıkış parametresi değerleri olarak belirtilebilir. İçin büyük `varchar` veri türleri, veri alınır ve artımlı olarak güncelleştirildi.  
  
 `max` Transact-SQL değişkenleri olarak karşılaştırmaları ve birleştirme için veri türleri kullanılabilir. Bunlar, DISTINCT, ORDER BY, GROUP BY yan tümcesi SELECT deyiminin ve aynı zamanda toplamalar, birleştirmeler ve alt sorgular da kullanılabilir.  
  
 Aşağıdaki tabloda, SQL Server Books Online'da belgelere bağlantılar sağlar.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Değer büyük veri türlerini kullanma](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Büyük değer türü kısıtlamaları  
 Aşağıdaki kısıtlamalar uygulamak `max` daha küçük veri türleri için yok, veri türleri:  
  
-   A `sql_variant` büyük içeremez `varchar` veri türü.  
  
-   Büyük `varchar` sütunları, dizinde anahtar sütunu olarak belirtilemez. Kümelenmemiş bir dizin bulunan bir sütun kullanılabilir.  
  
-   Büyük `varchar` sütunlar anahtar sütunlarını bölümleme olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL büyük değer türleri ile çalışma  
 Transact-SQL `OPENROWSET` işlevidir bağlanma ve uzak veri erişim tek seferlik bir yöntem. Tüm bir OLE DB veri kaynağından uzak verilere erişmek gerekli bağlantı bilgilerini içerir. `OPENROWSET` dizinindeymiş gibi bir tablo adı bir sorgu FROM yan tümcesinde başvuruda bulunulabilir. Ayrıca bir INSERT, UPDATE, hedef tablo olarak başvurulabilir veya OLE DB sağlayıcısı yeteneklerine tabi deyimi SİLİN.  
  
 `OPENROWSET` İşlevi içeren `BULK` doğrudan bir dosyadan bir hedef tabloya veri yüklemeden okumaya izin veren satır kümesi sağlayıcısı. Bu kullanmanızı sağlayan `OPENROWSET` basit INSERT SELECT deyimi içinde.  
  
 `OPENROWSET``BULK` Seçenek bağımsız başlamak ve verileri okuma bitiş konumu, hatalarla ilgilenir etme ve verilerin nasıl yorumlanacağını üzerinde önemli denetim sağlar. Örneğin, veri dosyası türü tek satır, tek sütunlu satır okunacak belirtebilirsiniz `varbinary`, `varchar`, veya `nvarchar`. Tam sözdizimi ve seçenekler için SQL Server Books Online'a bakın.  
  
 Aşağıdaki örnekte AdventureWorks örnek veritabanını ProductPhoto tabloda bir fotoğraf ekler. Kullanırken `BULK``OPENROWSET` sağlayıcısı sağlamanız sütunlar bile adlandırılmış listesi değerleri her sütununa ekleme olmayan durumunda. Birincil anahtar bu durumda kimlik sütunu olarak tanımlanır ve sütun listesinden atlanabilir. Ayrıca, sonunda bir bağıntı adı sağlamanız gerektiğini unutmayın `OPENROWSET` ThumbnailPhoto bu durumda olan ifade. Bu sütunda ile karşılık gelen `ProductPhoto` tablo hangi dosya yükleniyor içine.  
  
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
  
## <a name="updating-data-using-update-write"></a>Güncelleştirme kullanarak verileri güncelleştiriliyor. YAZMA  
 Transact-SQL UPDATE deyiminin içeriğini değiştirmek için yeni yazma sözdizimine sahip `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` sütun. Bu verilerin kısmi güncelleştirmeler gerçekleştirmenizi sağlar. GÜNCELLEŞTİRME. Sözdizimi kısaltılmış formunda burada gösterilen yazma:  
  
 GÜNCELLEŞTİR  
  
 {  *\<nesnesi >* }  
  
 AYARLAMA  
  
 { *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}  
  
 WRITE yöntemi belirleyen değerinin bir bölümünü *column_name* değiştirilecek. İfade kopyalanacak değerdir *column_name*, `@Offset` hangi ifade yazılır, başlangıç noktasıdır ve `@Length` bağımsız değişkeni olan sütun bölümünde uzunluğu.  
  
|Eğer|Ardından|  
|--------|----------|  
|İfade NULL olarak ayarlandı|`@Length` göz ardı edilir ve değer *column_name* kesilir belirtilen `@Offset`.|  
|`@Offset` NULL.|Güncelleştirme işlemi var olan sonunda ifade ekler *column_name* değeri ve `@Length` göz ardı edilir.|  
|`@Offset` column_name değeri uzunluğundan daha büyük|SQL Server hata döndürür.|  
|`@Length` NULL.|Güncelleştirme işlemi tüm verileri kaldırır `@Offset` sonuna `column_name` değeri.|  
  
> [!NOTE]
>  Ne `@Offset` ya da `@Length` negatif bir sayı olabilir.  
  
## <a name="example"></a>Örnek  
 Bu Transact-SQL örneği DocumentSummary, kısmi bir değerinde güncelleştirmeleri bir `nvarchar(max)` AdventureWorks veritabanını belge tablodaki sütun. Word 'Bileşenleri' sözcük 'Özellikler' değiştirme word, var olan verileri ve değiştirilen (uzunluk) olacak şekilde karakter sayısını değiştirilmesi için Word'ü başlangıç konumunu (uzaklık) belirterek değiştirilir. Örnek önce ve sonra sonuçları karşılaştırmak için UPDATE deyiminin SELECT deyimi içerir.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET büyük değer türleri ile çalışma  
 ADO.NET büyük değer türlerinde büyük değer türleri olarak belirterek çalışabileceğiniz <xref:System.Data.SqlClient.SqlParameter> nesnelerini bir <xref:System.Data.SqlClient.SqlDataReader> bir sonuç kümesinden veya kullanarak döndürmek için bir <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için bir `DataSet` / `DataTable`. Büyük değer türü ile çalışmayı yolu ile ilgili, daha küçük değer veri türü arasında fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Veri almak için GetSqlBytes kullanma  
 `GetSqlBytes` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Veri almak için GetSqlChars kullanma  
 `GetSqlChars` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varchar(max)` veya `nvarchar(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `nvarchar(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` verileri alır.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Veri almak için GetSqlBinary kullanma  
 `GetSqlBinary` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodan veri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır bir <xref:System.Data.SqlTypes.SqlBinary> akış.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Veri almak için GetBytes kullanma  
 `GetBytes` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> belirtilen dizi uzaklıkta başlayan bir bayt dizisi halinde belirtilen sütun uzaklığı bayt akışı okur. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , baytı bir bayt dizisine alır. Farklı Not `GetSqlBytes`, `GetBytes` dizi arabellek için bir boyut gerektirir.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>GetValue veri almak için kullanma  
 `GetValue` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> değeri belirtilen sütun uzaklığı bir diziye okur. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` alır ikili verileri ilk sütun uzaklığı ve ikinci sütun uzaklığı verilerden dize.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>CLR türleri için büyük değer türlerini dönüştürme  
 İçeriğini dönüştürebilirsiniz bir `varchar(max)` veya `nvarchar(max)` gibi dize dönüştürme yöntemlerden birini kullanarak sütun `ToString`. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` verileri alır.  
  
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
 Aşağıdaki kod adını alır ve `LargePhoto` nesnesinin `ProductPhoto` tablosundaki `AdventureWorks` veritabanı ve bir dosyaya kaydeder. Derleme başvuru derlenmesi gerekiyor <xref:System.Drawing> ad alanı.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Yöntemi <xref:System.Data.SqlClient.SqlDataReader> döndüren bir <xref:System.Data.SqlTypes.SqlBytes> gösteren nesne bir `Stream` özelliği. Bu yeni bir oluşturmak için kodunu kullanır `Bitmap` nesne ve GIF kaydeder `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük değer türü parametrelerini kullanma  
 Büyük değer türleri kullanılabilir <xref:System.Data.SqlClient.SqlParameter> daha küçük olan değeri kullandığınız aynı şekilde türleri nesneleri <xref:System.Data.SqlClient.SqlParameter> nesneleri. Büyük değer türleri olarak alabilir <xref:System.Data.SqlClient.SqlParameter> , aşağıdaki örnekte gösterildiği gibi değerler. Kod GetDocumentSummary saklı yordamını AdventureWorks örnek veritabanında var olduğunu varsayar. Saklı yordam adlı bir giriş parametresi alan @DocumentID ve DocumentSummary sütununda içeriğini döndürür @DocumentSummary çıkış parametresi.  
  
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
 ADO.NET kod oluşturur <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> büyük değer türü olarak depolanan GetDocumentSummary saklı yordamı yürütme ve belge özeti, almak için nesneleri. Bir değer kodu geçirir @DocumentID giriş parametresi ve sonuçları geçirilen geri görüntüler @DocumentSummary çıkış konsol penceresinde parametresi.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server İkili ve Büyük Değerli Veriler](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
