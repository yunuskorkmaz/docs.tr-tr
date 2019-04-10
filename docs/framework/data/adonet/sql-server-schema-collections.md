---
title: SQL Server Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: 79bf9f1253b64863d3eabddff8c33b6ffab70f41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224578"
---
# <a name="sql-server-schema-collections"></a>SQL Server Şema Koleksiyonları
SQL Server için Microsoft .NET Framework veri sağlayıcısı, ortak şema koleksiyonları yanı sıra ek şema koleksiyonları destekler. Şema koleksiyonları kullanmakta olduğunuz SQL Server sürümüne göre biraz farklılık gösterir. Desteklenen şema koleksiyonları listesi belirlemek için çağrı **GetSchema** yöntemi bağımsız değişken olmadan veya şema koleksiyonu adı "MetaDataCollections". Bu döndürür bir <xref:System.Data.DataTable> listesiyle desteklenen şema koleksiyonları, desteklediği her kısıtlama sayısı ve kullandıkları tanımlayıcısı parçaların sayısı.  
  
## <a name="databases"></a>Veritabanları  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|database_name|Dize|Veritabanının adı.|  
|DBID|Int16|Veritabanı kimliği|  
|create_date|DateTime|Veritabanı oluşturma tarihi.|  
  
## <a name="foreign-keys"></a>Yabancı anahtarlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|Dize|Kısıtlama Kataloğu aittir.|  
|CONSTRAINT_SCHEMA|Dize|Kısıtlama içeren şema.|  
|CONSTRAINT_NAME|Dize|Adı.|  
|TABLE_CATALOG|Dize|Tablo adı kısıtlaması, bir parçasıdır.|  
|TABLE_SCHEMA|Dize|Tablo içeren şema.|  
|TABLE_NAME|Dize|Tablo Adı|  
|CONSTRAINT_TYPE|Dize|Kısıtlama türü. Yalnızca "yabancı anahtarı" izin verilir.|  
|IS_DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığını belirtir. Hayır döndürür|  
|INITIALLY_DEFERRED|Dize|Kısıtlama başlangıçta deferrable olup olmadığını belirtir. Hayır döndürür|  
  
## <a name="indexes"></a>Dizinleri  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Katalog, dizine ait.|  
|constraint_schema|Dize|Dizin içeren şema.|  
|constraint_name|Dize|Dizinin adı.|  
|TABLE_CATALOG|Dize|Dizin tablo adı ile ilişkilidir.|  
|TABLE_SCHEMA|Dize|Dizin tablosu içeren şema ilişkilidir.|  
|TABLE_NAME|Dize|Tablo adı.|  
|index_name|Dize|Dizin adı.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, aşağıdaki sütunlar yeni uzamsal türler, FILESTREAM ve seyrek sütun desteklemek için dizinleri şema koleksiyonu eklendi. Bu sütunlar, .NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|type_desc|Dize|Dizin türü, aşağıdakilerden birini olacaktır:<br /><br /> -HEAP<br />-KÜMELENMİŞ<br />-KÜMELENMEMİŞ<br />-   XML<br />-UZAMSAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Katalog, dizine ait.|  
|constraint_schema|Dize|Dizin içeren şema.|  
|constraint_name|Dize|Dizinin adı.|  
|TABLE_CATALOG|Dize|Dizin tablo adı ile ilişkilidir.|  
|TABLE_SCHEMA|Dize|Dizin tablosu içeren şema ilişkilidir.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı dizin ile ilişkilidir.|  
|ORDINAL_POSITION|Int32|Sütun sıralı konumu.|  
|KeyType|Bayt|Nesnenin türü.|  
|index_name|Dize|Dizin adı.|  
  
## <a name="procedures"></a>Yordamlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Katalog için belirli ad.|  
|SPECIFIC_SCHEMA|Dize|Belirli şemasının adı.|  
|SPECIFIC_NAME|Dize|Belirli bir katalog adı.|  
|ROUTINE_CATALOG|Dize|Katalog saklı yordamı aittir.|  
|ROUTINE_SCHEMA|Dize|Saklı yordam içeren şema.|  
|ROUTINE_NAME|Dize|Saklı yordamın adı.|  
|ROUTINE_TYPE|Dize|YORDAMI, İşlevler için saklı yordamlar ve işlev döndürür.|  
|OLUŞTURULAN|DateTime|Yordamı oluşturulduğu zaman.|  
|LAST_ALTERED|DateTime|Son yordamı değiştirildi.|  
  
## <a name="procedure-parameters"></a>Yordam parametreleri  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Bu parametre olduğu yordamın adını katalog.|  
|SPECIFIC_SCHEMA|Dize|Bu parametre bir parçası olduğu yordam içeren şema.|  
|SPECIFIC_NAME|Dize|Bu parametre bir parçası olduğu yordamın adı.|  
|ORDINAL_POSITION|Int32|Parametre 1'den başlayarak sıralı konumu. Bir yordam için dönüş değeri bir 0'dır.|  
|PARAMETER_MODE|Dize|Sahipse IF bir giriş parametresi bir output parametresi ve giriş/çıkış parametresi varsa INOUT döndürür.|  
|IS_RESULT|Dize|Evet döndüren bir işlev, yordamın sonucunu gösterir. Aksi halde döndürür No|  
|AS_LOCATOR|Dize|Evet Bulucu bildirilmişlerse döndürür. Aksi halde döndürür No|  
|PARAMETER_NAME|Dize|Parametrenin adı. Bu işlevin dönüş değerine karşılık gelen yoksa NULL.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veya karakter veri türleri için karakter cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veya karakter veri türleri için bayt cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürür.|  
|COLLATION_CATALOG|Dize|Katalog harmanlama parametrenin adıdır. Aksi durumda NULL karakter türlerinden birini döndürür.|  
|COLLATION_SCHEMA|Dize|Her zaman NULL döndürür.|  
|COLLATION_NAME|Dize|Harmanlama parametrenin adı. Aksi durumda NULL karakter türlerinden birini döndürür.|  
|CHARACTER_SET_CATALOG|Dize|Katalog adı karakter parametresini ayarlayın. Aksi durumda NULL karakter türlerinden birini döndürür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Karakter kümesi parametresinin adı. Aksi durumda NULL karakter türlerinden birini döndürür.|  
|NUMERIC_PRECISION|Bayt|Duyarlık yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürür.|  
|NUMERIC_PRECISION_RADIX|Int16|Duyarlık taban yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürür.|  
|NUMERIC_SCALE|Int32|Ölçek yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürür.|  
|DATETIME_PRECISION|Int16|Parametre türü, TarihSaat ya da smalldatetime ise Kesirli saniye duyarlık. Aksi takdirde, NULL döndürür.|  
|INTERVAL_TYPE|Dize|NULL. SQL Server tarafından gelecekte kullanım için ayrılmıştır.|  
|INTERVAL_PRECISION|Int16|NULL. SQL Server tarafından gelecekte kullanım için ayrılmıştır.|  
  
## <a name="tables"></a>Tabloları  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tablo içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|TABLE_TYPE|Dize|Tablo türü. Görünüm veya temel tablo olabilir.|  
  
## <a name="columns"></a>Sütunlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tablo içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütununun null atanabilirliği. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|İkili verileri, karakter verileri veya metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|İkili verileri, karakter verileri veya metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Duyarlık yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Duyarlık taban yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Ölçek yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|Alt tür kodu datetime ve SQL 92 aralığı veri türleri için'nı tıklatın. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun metin verilerini veya karakter verileri ise belirten döndürür asıl türü. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun metin verilerini veya karakter verileri ise karakter için benzersiz bir ad ayarlayın döndürür yazın. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun metin verilerini veya karakter verileri ise harmanlama tanımlanmış veritabanı belirten döndürür asıl türü. Aksi takdirde, bu sütun NULL olur.|  
  
### <a name="columns-sql-server-2008"></a>Sütunlar (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, aşağıdaki sütunları sütunlar şema koleksiyonuna yeni uzamsal türler, FILESTREAM ve seyrek sütun desteklemek için eklendi. Bu sütunlar, .NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise, Evet.<br /><br /> Hayır sütunu bir seyrek sütun değil.|  
|IS_COLUMN_SET|Dize|Evet, bir sütun kümesi sütunu sütun ise.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değil ise.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, seyrek sütun desteklemek için AllColumns şema koleksiyonu eklendi. .NET Framework ve SQL Server'ın önceki sürümlerinde AllColumns desteklenmiyor.  
  
 AllColumns sütunları şema koleksiyonu elde edilen DataTable şema ve aynı kısıtlamalara sahiptir. Tek fark, AllColumns sütunları şema koleksiyonunda bulunmayan sütun kümesi sütunları içerir. Aşağıdaki tabloda, bu sütunların açıklanmaktadır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tablo içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütununun null atanabilirliği. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili verileri, karakter verileri veya metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili verileri, karakter verileri veya metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Duyarlık yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Duyarlık taban yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Ölçek yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|Alt tür kodu datetime ve SQL 92 aralığı veri türleri için'nı tıklatın. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun metin verilerini veya karakter verileri ise belirten döndürür asıl türü. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun metin verilerini veya karakter verileri ise karakter için benzersiz bir ad ayarlayın döndürür yazın. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun metin verilerini veya karakter verileri ise harmanlama tanımlanmış veritabanı belirten döndürür asıl türü. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise, Evet.<br /><br /> Hayır sütunu bir seyrek sütun değil.|  
|IS_COLUMN_SET|Dize|Evet, bir sütun kümesi sütunu sütun ise.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değil ise.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, seyrek sütun desteklemek için ColumnSetColumns şema koleksiyonu eklendi. .NET Framework ve SQL Server'ın önceki sürümlerinde ColumnSetColumns desteklenmiyor. ColumnSetColumns şema koleksiyonu, bir sütun kümesinde tüm sütunlar için şemayı döndürür. Aşağıdaki tabloda, bu sütunların açıklanmaktadır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tablo içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütununun null atanabilirliği. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili verileri, karakter verileri veya metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili verileri, karakter verileri veya metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Duyarlık yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Duyarlık taban yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Ölçek yaklaşık sayısal veriler, sayısal verileri tam, tamsayı veri ya da parasal veri. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|Alt tür kodu datetime ve SQL 92 aralığı veri türleri için'nı tıklatın. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun metin verilerini veya karakter verileri ise belirten döndürür asıl türü. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun metin verilerini veya karakter verileri ise karakter için benzersiz bir ad ayarlayın döndürür yazın. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun metin verilerini veya karakter verileri ise harmanlama tanımlanmış veritabanı belirten döndürür asıl türü. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise, Evet.<br /><br /> Hayır sütunu bir seyrek sütun değil.|  
|IS_COLUMN_SET|Dize|Evet, bir sütun kümesi sütunu sütun ise.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değil ise.|  
  
## <a name="users"></a>Kullanıcılar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|Kullanıcı Kimliği|Int16|Kullanıcı kimliği, bu veritabanında benzersiz. 1 veritabanı sahibi değil.|  
|User_name|Dize|Kullanıcı adı veya grup adı, bu veritabanında benzersiz.|  
|CREATEDATE|DateTime|Tarih hesap eklendi.|  
|updatedate|DateTime|Hesap en son değiştirildiği tarih.|  
  
## <a name="views"></a>Görünümler  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Katalog görünümün.|  
|TABLE_SCHEMA|Dize|Şema görünümü içerir.|  
|TABLE_NAME|Dize|Görünüm adı.|  
|CHECK_OPTION|Dize|ONAY SEÇENEĞİYLE türü. Orijinal görünümde WITH CHECK OPTION'ı kullanarak oluşturduysanız CASCADE ' dir. Aksi takdirde, hiçbir döndürülür.|  
|IS_UPDATABLE|Dize|Görünüm güncelleştirilebilir olup olmadığını belirtir. Her zaman döndürür No|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|Dize|Katalog görünümün.|  
|VIEW_SCHEMA|Dize|Şema görünümü içerir.|  
|VIEW_NAME|Dize|Görünüm adı.|  
|TABLE_CATALOG|Dize|Bu görünümle ilişkili olan tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Bu görünümle ilişkili olan tablo içeren şema.|  
|TABLE_NAME|Dize|Görünümle ilişkili olan tablonun adı. Temel tablo.|  
|COLUMN_NAME|Dize|Sütun adı.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|assembly_name|Dize|Derleme için dosya adı.|  
|udt_name|Dize|Derleme için sınıf adı.|  
|version_major|Nesne|Ana sürüm numarası.|  
|version_minor|Nesne|İkincil sürüm numarası.|  
|version_build|Nesne|Yapı numarası.|  
|version_revision|Nesne|Düzeltme numarası.|  
|culture_info|Nesne|Kültür bilgilerini bu UDT ile ilişkili.|  
|publıc_key|Nesne|Bu derleme tarafından kullanılan ortak anahtar.|  
|is_fixed_length|Boole değeri|Tür uzunluğunu her zaman max_length aynı olup olmadığını belirtir.|  
|max_length|Int16|Türü bayt cinsinden en büyük uzunluğu.|  
|Create_Date|DateTime|Oluşturulan ve kayıtlı derleme tarihi.|  
|Permission_set_desc|Dize|İzni-Ayarla/güvenlik düzeyi derleme için bir kolay ad.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
