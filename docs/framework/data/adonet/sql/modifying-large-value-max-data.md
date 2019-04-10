---
title: ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: eb938cfae645a9cc3811f1b5a02cddef742bac89
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317109"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme
Büyük nesne (LOB) veri türleri 8 kilobayt (KB) maksimum satır boyutu aşan olanlardır. SQL Server sağlayan bir `max` tanımlayıcısı için `varchar`, `nvarchar`, ve `varbinary` veri türleri değerlerinin depolama 2 büyüklüğünde izin vermek için ^ 32 bayt. Tablo sütunları ve Transact-SQL değişkenleri belirtin `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` veri türleri. ADO.NET, `max` veri türleri getirilen tarafından bir `DataReader`ve iki giriş ve çıkış parametresi değerleri olmadan herhangi bir özel işleme olarak belirtilebilir. İçin büyük `varchar` veri türleri, veriler alınır ve artımlı olarak güncelleştirildi.  
  
 `max` Veri türleri, birleştirme ve karşılaştırma, Transact-SQL değişkenleri için kullanılabilir. Bunlar ayrıca DISTINCT, ORDER BY, GROUP BY yan tümcesi SELECT deyiminin toplamalar, birleştirmeler ve alt sorgularda yanı sıra kullanılabilir.  
  
 Aşağıdaki tabloda, SQL Server Books Online belgelerine bağlantılar sağlar.  
  
 **SQL Server Çevrimiçi Kitaplar**  
  
1. [Büyük değerli veri türlerini kullanma](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Büyük bir değer türü kısıtlamaları  
 Aşağıdaki kısıtlamalar uygulamak `max` veri türleri, daha küçük veri türleri için mevcut değildir:  
  
-   A `sql_variant` büyük içeremez `varchar` veri türü.  
  
-   Büyük `varchar` sütunları dizin anahtar sütunu olarak belirtilemez. Kümelenmemiş bir dizin içinde bulunan bir sütunda verilir.  
  
-   Büyük `varchar` sütunları bölümleme anahtar sütunu olarak kullanılamaz.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Transact-SQL büyük değerli türlerle çalışma  
 Transact-SQL `OPENROWSET` işlev, bağlanma ve uzak veri erişim tek seferlik bir yöntem. Tüm bir OLE DB veri kaynağından uzak verilere erişmek gerekli bağlantı bilgilerini içerir. `OPENROWSET` işlevmiş gibi bir tablo adı sorgusunun FROM yan tümcesinde başvuruda bulunulabilir. Ayrıca bir INSERT, UPDATE, hedef tablo olarak başvurulabilir veya silme deyiminin, OLE DB sağlayıcısı yeteneklerini tabidir.  
  
 `OPENROWSET` İşlevi içeren `BULK` satır kümesi sağlayıcısı, bir hedef tabloya veri yüklenirken olmadan doğrudan bir dosyadan veri okumanıza izin verir. Bu sayede kullanılacak `OPENROWSET` basit INSERT SELECT deyimi içinde.  
  
 `OPENROWSET BULK` Seçeneği bağımsız değişkenleri nereden başlamalı ve bitmelidir verileri okuma, hatalarla başa çıkma ve verileri nasıl yorumlanacağını üzerinde önemli denetim sağlayın. Örneğin, veri dosyasındaki bir türü tek satır, tek bir sütun kümesi okunacak belirtebilirsiniz `varbinary`, `varchar`, veya `nvarchar`. Tam sözdizimi ve seçenekleri için SQL Server Books Online'a bakın.  
  
 Aşağıdaki örnekte, AdventureWorks örnek veritabanındaki ProductPhoto tabloya bir fotoğraf ekler. Kullanırken `BULK OPENROWSET` sağlayıcısı, sağlaması gerekir sütun bile adlandırılmış listesi değerleri her sütununa ekleme değil ise. Birincil anahtarı bu durumda kimlik sütunu olarak tanımlanır ve sütun listesinden dahil edilmeyebilir. Ayrıca, sonunda bir bağıntı adı sağlamanız gerektiğini unutmayın `OPENROWSET` ThumbnailPhoto bu durumda olan ifade. Bu sütunda ile ilişkilendiren `ProductPhoto` tablo, dosya yüklenirken içine.  
  
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
 Transact-SQL UPDATE deyiminin içeriğini değiştirmek için yeni yazma söz dizimine sahip `varchar(max)`, `nvarchar(max)`, veya `varbinary(max)` sütunları. Bu, verileri kısmi güncelleştirmelerin yapılmasını sağlar. GÜNCELLEŞTİRME. Söz dizimi burada kısaltılmış formunda gösterilen yazma:  
  
 GÜNCELLEŞTİR  
  
 {  *\<Nesne >* }  
  
 SET  
  
 { *column_name* = {. YAZMA ( *ifade* , @Offset , @Length )}  
  
 YAZMA yönteminin belirten değerinin bir bölümü *column_name* değiştirilecek. İfade kopyalanacağı değerdir *column_name*, `@Offset` başlangıçtan ifade yazılır, başlangıç noktasıdır ve `@Length` bağımsız değişkeni olan sütun bölümde uzunluğu.  
  
|Eğer|Ardından|  
|--------|----------|  
|İfade NULL olarak ayarlandı|`@Length` göz ardı edilir ve değer *column_name* kesilmiş belirtilen `@Offset`.|  
|`@Offset` null|Güncelleştirme işlemi sonunda varolan ifade ekler *column_name* değeri ve `@Length` göz ardı edilir.|  
|`@Offset` column_name değeri uzunluğundan büyüktür|SQL Server bir hata döndürür.|  
|`@Length` null|Güncelleştirme işlemi tüm verileri kaldırır `@Offset` sonuna `column_name` değeri.|  
  
> [!NOTE]
>  Ne `@Offset` ya da `@Length` negatif bir sayı olabilir.  
  
## <a name="example"></a>Örnek  
 Bu Transact-SQL örnek DocumentSummary, kısmi bir değer güncelleştirmeleri bir `nvarchar(max)` AdventureWorks veritabanını Belge tablosuna sütun. ' % S'sözcük 'Bileşenler' sözcük 'Özellikler' değiştirme metni, mevcut verileri ve değiştirilen (uzunluk) olacak şekilde karakter sayısına göre değiştirilecek Word'ün başlangıç konumunu (kaydırma) belirterek değiştirilir. Örnek, önce ve sonra sonuçları karşılaştırmak için UPDATE deyiminin SELECT deyimleri içerir.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>ADO.NET içinde büyük değerli türlerle çalışma  
 Büyük bir değer türleri olarak belirterek ADO.NET içinde büyük değer türleri ile çalışabilir <xref:System.Data.SqlClient.SqlParameter> nesneler bir <xref:System.Data.SqlClient.SqlDataReader> kullanarak veya kümesinden bir sonuç döndürmek için bir <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için bir `DataSet` / `DataTable`. Büyük bir değer türüyle çalışma biçiminizi ve ilgili, daha küçük değer veri türü arasında bir fark yoktur.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Veri almak için GetSqlBytes kullanma  
 `GetSqlBytes` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
 `GetSqlChars` Yöntemi <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varchar(max)` veya `nvarchar(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `nvarchar(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , verileri alır.  
  
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
 `GetSqlBinary` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> içeriğini almak için kullanılan bir `varbinary(max)` sütun. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlCommand> adlı nesne `cmd` , seçer `varbinary(max)` bir tablodaki verileri ve <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` olarak verilerini alır bir <xref:System.Data.SqlTypes.SqlBinary> akış.  
  
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
 `GetBytes` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> belirtilen uzaklıkta başlayan belirli bir bayt dizisi olarak belirtilen sütun uzaklığı bayt akışı okur. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , bayt bayt dizisine alır. Aksine, Not `GetSqlBytes`, `GetBytes` dizi arabelleği için bir boyut gerektirir.  
  
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
 `GetValue` Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> değeri belirtilen sütun uzaklığı bir diziye okur. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` ilk sütun ikili verilerden alır uzaklığı ve ardından verileri ikinci sütun uzaklığı dize.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>CLR türlerine büyük değer türlerinden dönüştürme  
 İçeriğini dönüştürebilirsiniz bir `varchar(max)` veya `nvarchar(max)` gibi dize dönüştürme yöntemlerinden herhangi birini kullanarak sütun `ToString`. Aşağıdaki kod parçası varsayar bir <xref:System.Data.SqlClient.SqlDataReader> adlı nesne `reader` , verileri alır.  
  
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
 Aşağıdaki kod adını alır ve `LargePhoto` nesnesinden `ProductPhoto` tablosundaki `AdventureWorks` veritabanı ve bir dosyaya kaydeder. Derlemeyi bir başvuru ile derlenmesi gerekiyor <xref:System.Drawing> ad alanı.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Yöntemi <xref:System.Data.SqlClient.SqlDataReader> döndürür bir <xref:System.Data.SqlTypes.SqlBytes> kullanıma sunan bir nesne bir `Stream` özelliği. Bu yeni bir kullanan kod `Bitmap` nesne ve sonra GIF kaydeder `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Büyük bir değer türü parametrelerini kullanma  
 Büyük değer türleri kullanılabilir <xref:System.Data.SqlClient.SqlParameter> daha küçük değer kullandığınız aynı şekilde türleri, nesneleri <xref:System.Data.SqlClient.SqlParameter> nesneleri. Büyük bir değer türleri olarak alabilir <xref:System.Data.SqlClient.SqlParameter> , aşağıdaki örnekte gösterildiği gibi değerleri. Kod aşağıdaki GetDocumentSummary depolanan yordamı AdventureWorks örnek veritabanındaki var olduğunu varsayar. Saklı yordam adlı giriş parametresi alan @DocumentID ve DocumentSummary sütununda içeriğini döndürür @DocumentSummary çıkış parametresi.  
  
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
 ADO.NET kod oluşturur <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> büyük değer türü olarak depolanan GetDocumentSummary saklı yordamı yürütme ve Özet, belge almak için nesneleri. Kod bir değer geçirir @DocumentID giriş parametresi ve sonuçları geçirilen geri görüntüler @DocumentSummary çıkış parametresi konsol penceresinde.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server İkili ve Büyük Değerli Veriler](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
