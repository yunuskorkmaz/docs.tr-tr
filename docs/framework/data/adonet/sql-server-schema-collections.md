---
title: "SQL Server şeması koleksiyonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e95c6dc6bceb367000f4aa174a368bf046bc1b93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-schema-collections"></a>SQL Server şeması koleksiyonları
SQL Server için Microsoft .NET Framework veri sağlayıcısı ortak şeması koleksiyonları yanı sıra ek şeması koleksiyonları destekler. Şema koleksiyonları, kullanmakta olduğunuz SQL Server sürümü tarafından biraz farklılık gösterir. Desteklenen şeması koleksiyonları listesini belirlemek için çağrı **GetSchema** yöntemi bağımsız değişken içermeyen veya şema koleksiyonu adı "MetaDataCollections". Bu döndürülecek bir <xref:System.Data.DataTable> desteklenen şeması koleksiyonları, her destekledikleri kısıtlama sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısını listesini içeren.  
  
## <a name="databases"></a>Veritabanları  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|database_name|Dize|Veritabanının adı.|  
|DBID|Int16|Veritabanı kimliği.|  
|create_date|DateTime|Veritabanı oluşturma tarihi.|  
  
## <a name="foreign-keys"></a>Yabancı anahtarlar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CONSTRAINT_CATALOG|Dize|Katalog kısıtlaması ait.|  
|CONSTRAINT_SCHEMA|Dize|Şema kısıtlaması içeriyor.|  
|CONSTRAINT_NAME|Dize|Adı.|  
|TABLE_CATALOG|Dize|Tablo adı kısıtlaması, bir parçasıdır.|  
|TABLE_SCHEMA|Dize|Şema, tablo içeriyor.|  
|TABLE_NAME|Dize|Tablo adı|  
|CONSTRAINT_TYPE|Dize|Kısıtlama türü. Yalnızca "yabancı anahtarı" izin verilmiyor.|  
|IS_DEFERRABLE|Dize|Kısıtlama deferrable olup olmadığını belirtir. Hayır döndürür.|  
|INITIALLY_DEFERRED|Dize|Kısıtlama başlangıçta deferrable olup olmadığını belirtir. Hayır döndürür.|  
  
## <a name="indexes"></a>Dizinler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Katalog dizin ait.|  
|constraint_schema|Dize|Şema dizini içerir.|  
|constraint_name|Dize|Dizinin adı.|  
|table_catalog|Dize|Tablo adı dizin ile ilişkilendirilir.|  
|table_schema|Dize|Tabloyu içeren şeması dizini ile ilişkili.|  
|TABLE_NAME|Dize|Tablo adı.|  
|index_name|Dize|Dizin adı.|  
  
### <a name="indexes-sql-server-2008"></a>Indexes (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, aşağıdaki sütunları yeni uzamsal türler, FILESTREAM ve seyrek sütun desteklemek için dizinler şema koleksiyonu eklenmiştir. Bu sütun, önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|type_desc|Dize|Dizin türünü aşağıdakilerden biri olacaktır:<br /><br /> -   HEAP<br />-KÜMELENMİŞ<br />-KÜMELENMEMİŞ<br />-   XML<br />-UZAMSAL|  
  
## <a name="indexcolumns"></a>IndexColumns  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|constraint_catalog|Dize|Katalog dizin ait.|  
|constraint_schema|Dize|Şema dizini içerir.|  
|constraint_name|Dize|Dizinin adı.|  
|table_catalog|Dize|Tablo adı dizin ile ilişkilendirilir.|  
|table_schema|Dize|Tabloyu içeren şeması dizini ile ilişkili.|  
|TABLE_NAME|Dize|Tablo adı.|  
|column_name|Dize|Sütun adı dizin ile ilişkilendirilir.|  
|ORDINAL_POSITION|Int32|Sütun sıralı konumu.|  
|keyType|Bayt|Nesnenin türü.|  
|index_name|Dize|Dizin adı.|  
  
## <a name="procedures"></a>Yordamlar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Katalog için belirli ad.|  
|SPECIFIC_SCHEMA|Dize|Şema belirli adıdır.|  
|SPECIFIC_NAME|Dize|Kataloğun belirli adı.|  
|ROUTINE_CATALOG|Dize|Katalog saklı yordamı ait.|  
|ROUTINE_SCHEMA|Dize|Saklı yordam içeren şema.|  
|ROUTINE_NAME|Dize|Saklı yordam adı.|  
|ROUTINE_TYPE|Dize|YORDAM işlevleri için saklı yordamları ve işlevi döndürür.|  
|OLUŞTURULAN|DateTime|Yordam oluşturulduğu zaman.|  
|LAST_ALTERED|DateTime|En son ne zaman yordamı değiştirildi.|  
  
## <a name="procedure-parameters"></a>Yordam parametreleri  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|SPECIFIC_CATALOG|Dize|Katalog bir parametre olan bu yordamın adı.|  
|SPECIFIC_SCHEMA|Dize|Bu parametre bir parçası olduğu yordamı içeren şema.|  
|SPECIFIC_NAME|Dize|Bu parametre bir parçası olduğu yordamın adı.|  
|ORDINAL_POSITION|Int32|Parametre 1'den başlayarak sıralı konumunu. Bir yordam dönüş değeri için bir 0'dır.|  
|PARAMETER_MODE|Dize|IF IF bir giriş parametresi bir output parametresi ve INOUT bir giriş/çıkış parametresi varsa döndürür.|  
|IS_RESULT|Dize|Evet döndüren bir işlev yordamı sonucunu gösterir. Aksi takdirde, döndürür No|  
|AS_LOCATOR|Dize|Evet Bulucu bildirilen varsa döndürür. Aksi takdirde, döndürür No|  
|PARAMETER_NAME|Dize|Parametrenin adı. Bu işlevin dönüş değerine karşılık gelen yoksa NULL.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veya karakter veri türleri için karakter cinsinden en büyük uzunluğu. Aksi takdirde NULL döndürür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veya karakter veri türleri için bayt cinsinden en büyük uzunluğu. Aksi takdirde NULL döndürür.|  
|COLLATION_CATALOG|Dize|Parametrenin harmanlaması katalog adı. Aksi halde NULL karakter türlerinden birini döndürür.|  
|COLLATION_SCHEMA|Dize|Her zaman NULL döndürür.|  
|COLLATION_NAME|Dize|Harmanlama parametresinin adı. Aksi halde NULL karakter türlerinden birini döndürür.|  
|CHARACTER_SET_CATALOG|Dize|Katalog parametresinin karakter kümesinin adı. Aksi halde NULL karakter türlerinden birini döndürür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Karakter kümesi parametresinin adı. Aksi halde NULL karakter türlerinden birini döndürür.|  
|NUMERIC_PRECISION|Bayt|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri duyarlığını. Aksi takdirde NULL döndürür.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision taban yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri. Aksi takdirde NULL döndürür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri ölçeğini. Aksi takdirde NULL döndürür.|  
|DATETIME_PRECISION|Int16|Duyarlık parametre türü datetime veya smalldatetime'a ise Kesirli saniye cinsinden. Aksi takdirde NULL döndürür.|  
|INTERVAL_TYPE|Dize|NULL. SQL Server tarafından gelecekte kullanım için ayrılmıştır.|  
|INTERVAL_PRECISION|Int16|NULL. SQL Server tarafından gelecekte kullanım için ayrılmıştır.|  
  
## <a name="tables"></a>tabloları  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|TABLE_TYPE|Dize|Tablo türü. Görünüm veya temel tablo olabilir.|  
  
## <a name="columns"></a>Sütunlar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütun null atanabilirlik. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32 – Sql8, Int16 – Sql7|İkili veriler, karakter verilerinin ya da metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32 – SQL8, Int16 – Sql7|İkili veriler, karakter verilerinin ya da metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri duyarlığını. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision taban yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri ölçeğini. Aksi takdirde null değeri döndürülür.|  
|DATETIME_PRECISION|Int16|Datetime ve SQL-92 aralığı veri türleri için kod alt tür. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun karakter veri veya metin veri ise belirten döndürür ana türü. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütunu karakter veya metin verilerini ise benzersiz bir ad karakter kümesi getirir yazın. Aksi takdirde null değeri döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun karakter veri veya metin veri ise harmanlama tanımlanmış veritabanı belirten döndürür ana türü. Aksi takdirde, bu sütun NULL olur.|  
  
### <a name="columns-sql-server-2008"></a>Columns (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, aşağıdaki sütunları yeni uzamsal türler, FILESTREAM ve seyrek sütun desteklemek için sütunları şema koleksiyonu eklenmiştir. Bu sütun, önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise Evet.<br /><br /> Sütunu bir seyrek sütun değilse yok.|  
|IS_COLUMN_SET|Dize|Sütunu bir sütun kümesi sütunu ise Evet.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değilse.|  
  
### <a name="allcolumns-sql-server-2008"></a>AllColumns (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, seyrek sütun desteklemek için AllColumns şema koleksiyonu eklendi. AllColumns önceki .NET Framework ve SQL Server sürümlerinde desteklenmiyor.  
  
 AllColumns aynı kısıtlamalara ve sonuçta elde edilen DataTable şema sütunları şema koleksiyonu vardır. Tek fark AllColumns sütunları şema koleksiyonunda bulunmayan sütun kümesi sütunlarından dahildir. Aşağıdaki tabloda bu sütunlar açıklanmaktadır.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütun null atanabilirlik. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veriler, karakter verilerinin ya da metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veriler, karakter verilerinin ya da metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri duyarlığını. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision taban yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri ölçeğini. Aksi takdirde null değeri döndürülür.|  
|DATETIME_PRECISION|Int16|Datetime ve SQL-92 aralığı veri türleri için kod alt tür. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun karakter veri veya metin veri ise belirten döndürür ana türü. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütunu karakter veya metin verilerini ise benzersiz bir ad karakter kümesi getirir yazın. Aksi takdirde null değeri döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun karakter veri veya metin veri ise harmanlama tanımlanmış veritabanı belirten döndürür ana türü. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise Evet.<br /><br /> Sütunu bir seyrek sütun değilse yok.|  
|IS_COLUMN_SET|Dize|Sütunu bir sütun kümesi sütunu ise Evet.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değilse.|  
  
### <a name="columnsetcolumns-sql-server-2008"></a>ColumnSetColumns (SQL Server 2008)  
 SQL Server 2008 ve .NET Framework sürüm 3.5 SP1 ile başlayarak, seyrek sütun desteklemek için ColumnSetColumns şema koleksiyonu eklendi. ColumnSetColumns önceki .NET Framework ve SQL Server sürümlerinde desteklenmiyor. ColumnSetColumns şema koleksiyonu tüm sütunlar için şema sütun kümesinde döndürür. Aşağıdaki tabloda bu sütunlar açıklanmaktadır.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Tabloyu içeren şema.|  
|TABLE_NAME|Dize|Tablo adı.|  
|COLUMN_NAME|Dize|Sütun adı.|  
|ORDINAL_POSITION|Int32|Sütun kimlik numarası.|  
|COLUMN_DEFAULT|Dize|Sütununun varsayılan değeri|  
|IS_NULLABLE|Dize|Sütun null atanabilirlik. Bu sütun NULL izin veriyorsa, bu sütunda Evet döndürür. Aksi takdirde, Hayır döndürülür.|  
|DATA_TYPE|Dize|Sistem tarafından sağlanan veri türü.|  
|CHARACTER_MAXIMUM_LENGTH|Int32|İkili veriler, karakter verilerinin ya da metin ve resim veri için karakter cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_OCTET_LENGTH|Int32|İkili veriler, karakter verilerinin ya da metin ve resim veri için bayt cinsinden en büyük uzunluğu. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION|İmzasız bayt|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri duyarlığını. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_PRECISION_RADIX|Int16|Precision taban yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri. Aksi takdirde null değeri döndürülür.|  
|NUMERIC_SCALE|Int32|Yaklaşık sayısal veriler, tam sayısal veriler, tamsayı veri veya para veri ölçeğini. Aksi takdirde null değeri döndürülür.|  
|DATETIME_PRECISION|Int16|Datetime ve SQL-92 aralığı veri türleri için kod alt tür. Diğer veri türleri için null değeri döndürülür.|  
|CHARACTER_SET_CATALOG|Dize|Karakter kümesi bulunduğu, veritabanı sütun karakter veri veya metin veri ise belirten döndürür ana türü. Aksi takdirde null değeri döndürülür.|  
|CHARACTER_SET_SCHEMA|Dize|Her zaman NULL döndürür.|  
|CHARACTER_SET_NAME|Dize|Bu sütunu karakter veya metin verilerini ise benzersiz bir ad karakter kümesi getirir yazın. Aksi takdirde null değeri döndürülür.|  
|COLLATION_CATALOG|Dize|Sütun karakter veri veya metin veri ise harmanlama tanımlanmış veritabanı belirten döndürür ana türü. Aksi takdirde, bu sütun NULL olur.|  
|IS_FILESTREAM|Dize|Sütun FILESTREAM özniteliğine sahipse, Evet.<br /><br /> Sütun FILESTREAM özniteliğine sahip değilse yok.|  
|IS_SPARSE|Dize|Sütunu bir seyrek sütun ise Evet.<br /><br /> Sütunu bir seyrek sütun değilse yok.|  
|IS_COLUMN_SET|Dize|Sütunu bir sütun kümesi sütunu ise Evet.<br /><br /> Hayır sütunu bir sütun kümesi sütunu değilse.|  
  
## <a name="users"></a>Kullanıcılar  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|Kullanıcı Kimliği|Int16|Kullanıcı kimliği, bu veritabanında benzersiz. 1 veritabanı sahibi olur.|  
|User_name|Dize|Kullanıcı adı veya grup adı, bu veritabanında benzersiz.|  
|CREATEDATE|DateTime|Hesap eklendi tarih.|  
|updatedate|DateTime|Hesap en son değiştirildiği tarihi.|  
  
## <a name="views"></a>Görünümler  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TABLE_CATALOG|Dize|Katalog görünümünün.|  
|TABLE_SCHEMA|Dize|Şema görünümü içerir.|  
|TABLE_NAME|Dize|Görünüm adı.|  
|CHECK_OPTION|Dize|ONAY SEÇENEĞİYLE türü. CASCADE özgün görünüm WITH CHECK OPTION kullanılarak oluşturulmuş olur. Aksi takdirde, hiçbiri döndürülür.|  
|IS_UPDATABLE|Dize|Görünüm güncelleştirilebilir olup olmadığını belirtir. Her zaman döndürür No|  
  
## <a name="viewcolumns"></a>ViewColumns  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|VIEW_CATALOG|Dize|Katalog görünümünün.|  
|VIEW_SCHEMA|Dize|Şema görünümü içerir.|  
|VIEW_NAME|Dize|Görünüm adı.|  
|TABLE_CATALOG|Dize|Bu görünümle ilişkili olan tablo Kataloğu.|  
|TABLE_SCHEMA|Dize|Bu görünümle ilişkili olan tablo içeren şema.|  
|TABLE_NAME|Dize|Görünümle ilişkili olan tablonun adı. Temel tablo.|  
|COLUMN_NAME|Dize|Sütun adı.|  
  
## <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|assembly_name|Dize|Derlemenin dosya adı.|  
|udt_name|Dize|Derleme için sınıfı adı.|  
|version_major|Nesne|Ana sürüm numarası.|  
|version_minor|Nesne|İkincil sürüm numarası.|  
|version_build|Nesne|Yapı numarası.|  
|version_revision|Nesne|Düzeltme numarası.|  
|culture_info|Nesne|Bu UDT ile ilişkili kültür bilgileri.|  
|public_key|Nesne|Bu derleme tarafından kullanılan ortak anahtarı.|  
|is_fixed_length|Boole değeri|Türün her zaman max_length aynı olup olmadığını belirtir.|  
|max_length|Int16|Tür bayt cinsinden en büyük uzunluğu.|  
|Create_Date|DateTime|Oluşturulan ve kayıtlı derleme tarihi.|  
|Permission_set_desc|Dize|İzni-kümesi /-için güvenlik düzeyini derleme için kolay ad.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
