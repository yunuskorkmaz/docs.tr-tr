---
title: SQL Server Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
ms.openlocfilehash: ebb0cea20aede3d04e37536c7c615678e109337a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197670"
---
# <a name="sql-server-schema-collections"></a>SQL Server Şema Koleksiyonları

SQL Server için Microsoft .NET Framework Veri Sağlayıcısı, ortak şema koleksiyonlarına ek olarak ek şema koleksiyonlarını da destekler. Şema koleksiyonları, kullanmakta olduğunuz SQL Server sürümüne göre biraz farklılık gösterir. Desteklenen şema koleksiyonlarının listesini öğrenmek için, **GetSchema** yöntemini bağımsız değişken olmadan veya "MetaDataCollections" şema koleksiyonu adıyla çağırın. Bu, <xref:System.Data.DataTable> Desteklenen şema koleksiyonlarının listesi, her birinin desteklediği kısıtlamaların sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısı ile birlikte döndürülür.  
  
## <a name="databases"></a>Veritabanları  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|database_name|Dize|Veritabanının adı.|  
|DBID|Int16|Veritabanı KIMLIĞI.|  
|create_date|DateTime|Veritabanının Oluşturulma tarihi.|  
  
## <a name="foreign-keys"></a>Yabancı anahtarlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|Dize|Kısıtlamanın ait olduğu katalog.|  
|CONSTRAINT_SCHEMA|Dize|Kısıtlamayı içeren şema.|  
|CONSTRAINT_NAME|Dize|Ada.|  
|TABLE_CATALOG|Dize|Tablo adı kısıtlaması bir parçasıdır.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo Adı|  
|CONSTRAINT_TYPE|Dize|Kısıtlama türü. Yalnızca "yabancı anahtar" kullanımına izin verilir.|  
|IS_DEFERRABLE|Dize|Kısıtlamanın erteedilip edilmeyeceğini belirtir. Hayır döndürür.|  
|INITIALLY_DEFERRED|Dize|Kısıtlamanın başlangıçta erteedilip edilmeyeceğini belirtir. Hayır döndürür.|  
  
## <a name="indexes"></a>Dizinler  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Dizinin ait olduğu katalog.|  
|constraint_schema|Dize|Dizini içeren şema.|  
|constraint_name|Dize|Dizinin adı.|  
|table_catalog|Dize|Dizinin ilişkilendirildiği tablo adı.|  
|table_schema|Dize|Dizinin ilişkilendirildiği tabloyu içeren şema.|  
|table_name|Dize|Tablo adı.|  
|index_name|Dize|Dizin adı.|  
  
### <a name="indexes-sql-server-2008"></a>Dizinler (SQL Server 2008)  

 .NET Framework sürüm 3,5 SP1 ve SQL Server 2008 ' den başlayarak yeni uzamsal türler, FILESTREAM ve seyrek sütunları desteklemek üzere dizinler şema koleksiyonuna aşağıdaki sütunlar eklenmiştir. Bu sütunlar .NET Framework ve SQL Server önceki sürümlerinde desteklenmez.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|type_desc|Dize|Dizinin türü aşağıdakilerden biri olacaktır:<br /><br /> -YıĞıN<br />-KÜMELENMIŞ<br />-KÜMELENMEMIŞ<br />-XML<br />-UZAMSAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Dizinin ait olduğu katalog.|  
|constraint_schema|Dize|Dizini içeren şema.|  
|constraint_name|Dize|Dizinin adı.|  
|table_catalog|Dize|Dizinin ilişkilendirildiği tablo adı.|  
|table_schema|Dize|Dizinin ilişkilendirildiği tabloyu içeren şema.|  
|table_name|Dize|Tablo adı.|  
|column_name|Dize|Dizinin ilişkilendirildiği sütun adı.|  
|ordinal_position|Int32|Sütun sırası konumu.|  
|Anahtar|Bayt|Nesne türü.|  
|index_name|Dize|Dizin adı.|  
  
## <a name="procedures"></a>Yordamlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Kataloğun özel adı.|  
|SPECIFIC_SCHEMA|Dize|Şemanın özel adı.|  
|SPECIFIC_NAME|Dize|Kataloğun özel adı.|  
|ROUTINE_CATALOG|Dize|Saklı yordamın ait olduğu katalog.|  
|ROUTINE_SCHEMA|Dize|Saklı yordamı içeren şema.|  
|ROUTINE_NAME|Dize|Saklı yordamın adı.|  
|ROUTINE_TYPE|Dize|Saklı yordamlar ve işlevler için Işlev prosedürü döndürür.|  
|YARATıL|DateTime|Yordamın oluşturulduğu zaman.|  
|LAST_ALTERED|DateTime|Yordamın son değiştirildiği zaman.|  
  
## <a name="procedure-parameters"></a>Yordam parametreleri  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Bu parametre olduğu yordamın Katalog adı.|  
|SPECIFIC_SCHEMA|Dize|Bu parametrenin parçası olduğu yordamı içeren şema.|  
|SPECIFIC_NAME|Dize|Bu parametrenin bir parçası olduğu yordamın adı.|  
|ORDINAL_POSITION|Int32|Parametrenin sıra konumu 1 ' den başlayarak. Bir yordamın dönüş değeri için bu 0 ' dır.|  
|PARAMETER_MODE|Dize|Giriş parametresi ise, çıkış parametresi ise ve giriş/çıkış parametresi varsa, ' de döndürür.|  
|IS_RESULT|Dize|Bir işlev olan yordamın sonucunu gösteriyorsa Evet ' i döndürür. Aksi takdirde Hayır ' ı döndürür.|  
|AS_LOCATOR|Dize|Bulucu olarak bildirilirse Evet döndürür. Aksi takdirde Hayır ' ı döndürür.|  
|PARAMETER_NAME|Dize|Parametrenin adı. Bu, bir işlevin dönüş değerine karşılık geliyorsa NULL.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veya karakter veri türleri için en fazla karakter uzunluğu. Aksi takdirde, NULL döndürür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veya karakter veri türleri için bayt cinsinden maksimum uzunluk. Aksi takdirde, NULL döndürür.|  
|COLLATION_CATALOG|Dize|Parametrenin harmanlamasının Katalog adı. Karakter türlerinden biri değilse, NULL değerini döndürür.|  
|COLLATION_SCHEMA|Dize|Her zaman NULL döndürür.|  
|COLLATION_NAME|Dize|Parametrenin harmanlamasının adı. Karakter türlerinden biri değilse, NULL değerini döndürür.|  
|CHARACTER_SET_CATALOG|Dize|Parametrenin karakter kümesinin Katalog adı. Karakter türlerinden biri değilse, NULL değerini döndürür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Parametrenin karakter kümesinin adı. Karakter türlerinden biri değilse, NULL değerini döndürür.|  
|NUMERIC_PRECISION|Bayt|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin doğruluğu. Aksi takdirde, NULL döndürür.|  
|NUMERIC_PRECISION_RADIX|Int16|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin duyarlık taban 'i. Aksi takdirde, NULL döndürür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal verilerin ölçeğini, tam sayısal verileri, tamsayı verileri veya parasal verileri ölçeklendirin. Aksi takdirde, NULL döndürür.|  
|DATETIME_PRECISION|Int16|Parametre türü DateTime veya smalldatetime ise kesirli saniye cinsinden duyarlık. Aksi takdirde, NULL döndürür.|  
|INTERVAL_TYPE|Dize|Değer. SQL Server tarafından gelecekte kullanılmak üzere ayrılmıştır.|  
|INTERVAL_PRECISION|Int16|Değer. SQL Server tarafından gelecekte kullanılmak üzere ayrılmıştır.|  
  
## <a name="tables"></a>Tablolar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablonun kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|TABLE_TYPE|Dize|Tablo türü. Görünüm veya temel tablo olabilir.|  
  
## <a name="columns"></a>Sütunlar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablonun kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütunun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütunun Nullable değeri. Bu sütun NULL izin veriyorsa, bu sütun Evet değerini döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7 düzenlemeleri|İkili veriler, karakter verileri veya metin ve görüntü verileri için en fazla karakter uzunluğunda. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7 düzenlemeleri|İkili veriler, karakter verileri veya metin ve resim verileri için bayt cinsinden maksimum uzunluk. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İşaretsiz bayt|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin doğruluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin duyarlık taban 'i. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal verilerin ölçeğini, tam sayısal verileri, tamsayı verileri veya parasal verileri ölçeklendirin. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|DateTime ve SQL-92 Interval veri türleri için alt tür kodu. Diğer veri türleri için NULL döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Sütun karakter verisi veya metin veri türü ise, karakter kümesinin bulunduğu veritabanını gösteren ana öğeyi döndürür. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun karakter verisi veya metin veri türü ise, karakter kümesi için benzersiz adı döndürür. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütunun karakter verisi veya metin veri türü olması halinde, harmanlamanın tanımlandığı veritabanını belirten ana öğeyi döndürür. Aksi takdirde, bu sütun NULL olur.|  
  
### <a name="columns-sql-server-2008"></a>Sütunlar (SQL Server 2008)  

 .NET Framework sürüm 3,5 SP1 ve SQL Server 2008 ' den başlayarak, yeni uzamsal türler, FILESTREAM ve seyrek sütunları desteklemek için sütunlar şema koleksiyonuna aşağıdaki sütunlar eklenmiştir. Bu sütunlar .NET Framework ve SQL Server önceki sürümlerinde desteklenmez.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|Dize|Sütunda FıLESTREAM özniteliği varsa evet.<br /><br /> Sütunda FıLESTREAM özniteliği yoksa hayır.|  
|IS_SPARSE|Dize|Sütun bir seyrek sütun ise Evet.<br /><br /> Sütun seyrek sütun değilse Hayır.|  
|IS_COLUMN_SET|Dize|Sütun, sütun kümesi sütunu ise Evet.<br /><br /> Sütun, sütun kümesi sütunu değilse Hayır.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  

 .NET Framework sürüm 3,5 SP1 ve SQL Server 2008 ' den başlayarak seyrek sütunları desteklemek için AllColumns şema koleksiyonu eklenmiştir. AllColumns, .NET Framework önceki sürümlerinde ve SQL Server desteklenmez.  
  
 AllColumns, sütunlar şema koleksiyonuyla aynı kısıtlamalara ve sonuç DataTable şemasına sahiptir. Tek fark, sütunlar şema koleksiyonunda bulunmayan sütun kümesi sütunları içeren sütunlardır. Aşağıdaki tabloda bu sütunlar açıklanmaktadır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablonun kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütunun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütunun Nullable değeri. Bu sütun NULL izin veriyorsa, bu sütun Evet değerini döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veriler, karakter verileri veya metin ve görüntü verileri için en fazla karakter uzunluğunda. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veriler, karakter verileri veya metin ve resim verileri için bayt cinsinden maksimum uzunluk. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İşaretsiz bayt|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin doğruluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin duyarlık taban 'i. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal verilerin ölçeğini, tam sayısal verileri, tamsayı verileri veya parasal verileri ölçeklendirin. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|DateTime ve SQL-92 Interval veri türleri için alt tür kodu. Diğer veri türleri için NULL döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Sütun karakter verisi veya metin veri türü ise, karakter kümesinin bulunduğu veritabanını gösteren ana öğeyi döndürür. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun karakter verisi veya metin veri türü ise, karakter kümesi için benzersiz adı döndürür. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütunun karakter verisi veya metin veri türü olması halinde, harmanlamanın tanımlandığı veritabanını belirten ana öğeyi döndürür. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütunda FıLESTREAM özniteliği varsa evet.<br /><br /> Sütunda FıLESTREAM özniteliği yoksa hayır.|  
|IS_SPARSE|Dize|Sütun bir seyrek sütun ise Evet.<br /><br /> Sütun seyrek sütun değilse Hayır.|  
|IS_COLUMN_SET|Dize|Sütun, sütun kümesi sütunu ise Evet.<br /><br /> Sütun, sütun kümesi sütunu değilse Hayır.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  

 .NET Framework sürüm 3,5 SP1 ve SQL Server 2008 ' den başlayarak seyrek sütunları desteklemek için ColumnSetColumns şema koleksiyonu eklenmiştir. ColumnSetColumns, önceki .NET Framework ve SQL Server sürümlerinde desteklenmez. ColumnSetColumns şema koleksiyonu, bir sütun kümesindeki tüm sütunların şemasını döndürür. Aşağıdaki tabloda bu sütunlar açıklanmaktadır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablonun kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütunun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütunun Nullable değeri. Bu sütun NULL izin veriyorsa, bu sütun Evet değerini döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veriler, karakter verileri veya metin ve görüntü verileri için en fazla karakter uzunluğunda. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veriler, karakter verileri veya metin ve resim verileri için bayt cinsinden maksimum uzunluk. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION|İşaretsiz bayt|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin doğruluğu. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Yaklaşık sayısal verilerin, tam sayısal verilerin, tamsayı verilerinin veya parasal verilerin duyarlık taban 'i. Aksi takdirde, NULL döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal verilerin ölçeğini, tam sayısal verileri, tamsayı verileri veya parasal verileri ölçeklendirin. Aksi takdirde, NULL döndürülür.|  
|DATETIME_PRECISION|Int16|DateTime ve SQL-92 Interval veri türleri için alt tür kodu. Diğer veri türleri için NULL döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Sütun karakter verisi veya metin veri türü ise, karakter kümesinin bulunduğu veritabanını gösteren ana öğeyi döndürür. Aksi takdirde, NULL döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütun karakter verisi veya metin veri türü ise, karakter kümesi için benzersiz adı döndürür. Aksi takdirde, NULL döndürülür.|  
|COLLATION_CATALOG|Dize|Sütunun karakter verisi veya metin veri türü olması halinde, harmanlamanın tanımlandığı veritabanını belirten ana öğeyi döndürür. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütunda FıLESTREAM özniteliği varsa evet.<br /><br /> Sütunda FıLESTREAM özniteliği yoksa hayır.|  
|IS_SPARSE|Dize|Sütun bir seyrek sütun ise Evet.<br /><br /> Sütun seyrek sütun değilse Hayır.|  
|IS_COLUMN_SET|Dize|Sütun, sütun kümesi sütunu ise Evet.<br /><br /> Sütun, sütun kümesi sütunu değilse Hayır.|  
  
## <a name="users"></a>Kullanıcılar  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|'sini|Int16|Kullanıcı KIMLIĞI, bu veritabanında benzersiz. 1, veritabanı sahibidir.|  
|user_name|Dize|Bu veritabanında benzersiz Kullanıcı adı veya grup adı.|  
|CreateDate|DateTime|Hesabın eklendiği tarih.|  
|updatedate|DateTime|Hesabın son değiştirilme tarihi.|  
  
## <a name="views"></a>Görünümler  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Görünümün kataloğu.|  
|TABLE_SCHEMA|Dize|Görünümü içeren şema.|  
|TABLE_NAME|Dize|Görünüm adı.|  
|CHECK_OPTION|Dize|WıTH CHECK SEÇENEĞININ türü. Özgün görünüm WıTH CHECK SEÇENEĞI kullanılarak oluşturulduysa CASCADE olur. Aksi takdirde, NONE döndürülür.|  
|IS_UPDATABLE|Dize|Görünümün güncelleştirilebilir olup olmadığını belirtir. Her zaman Hayır döndürür.|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|Dize|Görünümün kataloğu.|  
|VIEW_SCHEMA|Dize|Görünümü içeren şema.|  
|VIEW_NAME|Dize|Görünüm adı.|  
|TABLE_CATALOG|Dize|Bu görünümle ilişkili tablonun kataloğu.|  
|TABLE_SCHEMA|Dize|Bu görünümle ilişkili tabloyu içeren şema.|  
|TABLE_NAME|Dize|Görünümle ilişkili tablonun adı. Temel tablo.|  
|COLUMN_NAME|Dize|Sütun adı.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|assembly_name|Dize|Derlemenin dosyasının adı.|  
|udt_name|Dize|Derlemenin sınıf adı.|  
|version_major|Nesne|Ana sürüm numarası.|  
|version_minor|Nesne|İkincil sürüm numarası.|  
|version_build|Nesne|Yapı numarası.|  
|version_revision|Nesne|Düzeltme numarası.|  
|culture_info|Nesne|Bu UDT ile ilişkili kültür bilgileri.|  
|public_key|Nesne|Bu derleme tarafından kullanılan ortak anahtar.|  
|is_fixed_length|Boole|Türün uzunluğunun max_length her zaman aynı olup olmadığını belirtir.|  
|max_length|Int16|Bayt cinsinden tür uzunluğu üst sınırı.|  
|Create_Date|DateTime|Derlemenin oluşturulduğu/kaydedildiği tarih.|  
|Permission_set_desc|Dize|Derleme için izin kümesi/güvenlik düzeyi için kolay ad.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
