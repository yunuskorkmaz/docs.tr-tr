---
title: Tarih ve Saat Verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: d7a016b8911cee3091dec24bc26d1f1965f54749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148770"
---
# <a name="date-and-time-data"></a>Tarih ve Saat Verileri
SQL Server 2008 tarih ve saat bilgilerini işlemek için yeni veri türleri sunar. Yeni veri türleri, tarih ve saat için ayrı türler ve daha geniş aralık, kesinlik ve saat dilimi farkındalığı yla genişletilmiş veri türlerini içerir. .NET Framework sürüm 3.5 Service Pack (SP) 1 ile başlayan SQL<xref:System.Data.SqlClient>Server için .NET Framework Data Provider ( ) SQL Server 2008 Veritabanı Motoru'nun tüm yeni özellikleri için tam destek sağlar. SqlClient ile bu yeni özellikleri kullanmak için .NET Framework 3.5 SP1 (veya sonraki) yüklemeniz gerekir.  
  
 SQL Server 2008'den önceki SQL Server sürümlerinde tarih ve saat `datetime` `smalldatetime`değerleriyle çalışmak için yalnızca iki veri türü vardı: ve . Bu veri türlerinin her ikisi de hem tarih değeri hem de bir saat değeri içerir, bu da yalnızca tarih veya yalnızca saat değerleriyle çalışmayı zorlaştırır. Ayrıca, bu veri türleri yalnızca 1753 yılında İngiltere'de Gregoryen takviminin piyasaya sürülmesinden sonra oluşan tarihleri destekler. Başka bir sınırlama, bu eski veri türlerinin saat dilimi farkında olmamasıdır, bu da birden çok saat diliminden kaynaklanan verilerle çalışmayı zorlaştırır.  
  
 SQL Server veri türleri için eksiksiz belgeler SQL Server Books Online'da mevcuttur. Aşağıdaki tabloda, tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listeleneb.r.  
  
 **SQL Server belgeleri**  
  
1. [Tarih ve Saat Verilerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>SQL Server 2008'de Tanıtılan Tarih/Saat Veri Türleri  
 Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.  
  
|SQL Server veri türü|Açıklama|  
|--------------------------|-----------------|  
|`date`|Veri `date` türü 1 gün doğruluk ile 31 Aralık 9999 1 Ocak 01 ile 9999 bir dizi vardır. Varsayılan değer 1 Ocak 1900'dür. Depolama boyutu 3 bayt.|  
|`time`|Veri `time` türü, 24 saatlik bir saate bağlı olarak yalnızca zaman değerlerini depolar. Veri `time` türü 100 nanosaniye doğruluk ile 23:59:59:99999999 00:00:0000000 00:00.0000000 bir dizi vardır. Varsayılan değer 00:00:00.0000000 (gece yarısı) olur. `time` Veri türü kullanıcı tanımlı kısmi ikinci kesinliği destekler ve depolama boyutu belirtilen duyarlıkbağlı olarak 3 ile 6 bayt arasında değişir.|  
|`datetime2`|Veri `datetime2` türü, ve veri türlerinin `date` `time` aralığını ve kesinliğini tek bir veri türünde birleştirir.<br /><br /> Varsayılan değerler ve dize gerçek biçimleri, `date` `time` veri türlerinde tanımlananlarla aynıdır.|  
|`datetimeoffset`|Veri `datetimeoffset` türü ek bir `datetime2` saat dilimi mahsup ile tüm özelliklere sahiptir. Saat dilimi mahsulü [+&#124;-] HH:MM olarak temsil edilir. HH, saat dilimi mahsupundaki saat sayısını temsil eden 00 ile 14 arasında değişen 2 basamaktır. MM, saat dilimi mahsupundaki ek dakika sayısını temsil eden 00 ile 59 arasında değişen 2 basamaktır. Zaman biçimleri 100 nanosaniye ye desteklenir. Zorunlu + veya - işareti, yerel saati elde etmek için saat dilimi mahsulünün UTC'den (Evrensel Zaman Koordinatı veya Greenwich Ortalama Saati) eklenip eklenmediğini veya çıkarılıp çıkarılmadığını gösterir.|  
  
> [!NOTE]
> Anahtar kelimeyi `Type System Version` kullanma hakkında daha <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>fazla bilgi için bkz.  
  
## <a name="date-format-and-date-order"></a>Tarih Biçimi ve Tarih Sırası  
 SQL Server'ın tarih ve saat değerlerini nasıl ayrıştırdığı yalnızca tür sistemi sürümüne ve sunucu sürümüne değil, aynı zamanda sunucunun varsayılan dil ve biçim ayarlarına da bağlıdır. Sorgu farklı bir dil ve tarih biçimi ayarı kullanan bir bağlantı tarafından yürütülürse, bir dilin tarih biçimleri için çalışan bir tarih dizesi tanınmaz olabilir.  
  
 Transact-SQL SET LANGUAGE deyimi, tarih parçalarının sırasını belirleyen DATEFORMAT'ı zımni olarak ayarlar. MDY, DMY, YMD, YDM, MYD veya DYM siparişindeki tarih parçalarını sıralayarak, disambiguate tarih değerlerine bağlantı da SET DATEFORMAT Transact-SQL deyimini kullanabilirsiniz.  
  
 Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantıyla ilişkili varsayılan dili kullanır. Örneğin, '01/02/03' tarih dizesi, ABD İngilizcesi dil ayarlı bir sunucuda MDY (2 Ocak 2003) ve İngiliz İngilizcesi dil ayarlı bir sunucuda DMY (1 Şubat 2003) olarak yorumlanır. Yıl, sql server'ın yüzyıl değerini atamak için kesme tarihini tanımlayan kesme yılı kuralı kullanılarak belirlenir. Daha fazla bilgi için [iki basamaklı yıl kesme Seçeneği'ne](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)bakın.  
  
> [!NOTE]
> YDM tarih biçimi, dize `date`biçiminden , , `time` `datetime2`veya `datetimeoffset`.  
  
 SQL Server'ın tarih ve saat verilerini nasıl yorumladığı hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-and-parameters"></a>Tarih/Saat Veri Türleri ve Parametreleri  
 Yeni tarih ve saat veri <xref:System.Data.SqlDbType> türlerini desteklemek için aşağıdaki eklemeler eklendi.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Önceki <xref:System.Data.SqlDbType> tümumerasyonlardan <xref:System.Data.SqlClient.SqlParameter> birini kullanarak a'nın veri türünü belirtebilirsiniz.

> [!NOTE]
> Bir `DbType` `SqlParameter` özelliği ni 'ye `SqlDbType.Date`ayarlayamazsınız.

 Ayrıca, bir nesnenin <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> özelliğini belirli `SqlParameter` <xref:System.Data.DbType> bir numaralandırma değerine ayarlayarak genel olarak bir tür belirtebilirsiniz. Veri türlerini desteklemek <xref:System.Data.DbType> `datetime2` `datetimeoffset` için aşağıdaki numaralandırma değerleri eklenmiştir:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Bu yeni sayılar,.NET Framework'ün `Date`önceki sürümlerinde bulunan , `Time`ve `DateTime` sayılmaları tamamlar.  
  
 Bir parametre nesnesinin .NET Framework veri sağlayıcısı türü, parametre nesnesinin değerinin .NET Framework türünden veya parametre `DbType` nesnesinin değerinden çıkarılır. Yeni <xref:System.Data.SqlTypes> tarih ve saat veri türlerini desteklemek için yeni veri türleri kullanılmadı. Aşağıdaki tabloda SQL Server 2008 tarih ve saat veri türleri ile CLR veri türleri arasındaki eşlemeler açıklanmaktadır.  
  
|SQL Server veri türü|.NET Framework türü|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|Datetime|Tarih|Tarih|  
|time|Timespan|Zaman|Zaman|  
|datetime2|Datetime|DateTime2|DateTime2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|Datetime|DateTime|DateTime|  
|Smalldatetime|Datetime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter Özellikleri  
 Aşağıdaki tabloda `SqlParameter` tarih ve saat veri türleri ile ilgili özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Bir değerin nullable olup olmadığını alır veya ayarlar. Sunucuya null parametre değeri gönderdiğinde, (Visual <xref:System.DBNull> `null` `Nothing` Basic'te) yerine belirtmeniz gerekir. Veritabanı nulls hakkında daha fazla bilgi için [bkz.](handling-null-values.md)|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Değeri temsil etmek için kullanılan en büyük basamak sayısını alır veya ayarlar. Bu ayar, tarih ve saat veri türleri için yoksayılır.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Değerin zaman bölümünün ,, `Time` `DateTime2`ve `DateTimeOffset`. için çözüldüğü ondalık basamak sayısını alır veya ayarlar. Varsayılan değer 0'dır, bu da gerçek ölçeğin değerden çıkarıldığı ve sunucuya gönderildiği anlamına gelir.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Tarih ve saat veri türleri için yoksayılır.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Parametre değerini alır veya ayarlar.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Parametre değerini alır veya ayarlar.|  
  
> [!NOTE]
> Sıfırdan az veya 24 saatten büyük veya eşit olan <xref:System.ArgumentException>zaman değerleri bir .  
  
### <a name="creating-parameters"></a>Parametreler oluşturma  
 Bir <xref:System.Data.SqlClient.SqlParameter> nesneyi oluşturucusu kullanarak veya bir <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyona `Add` ekleyerek . <xref:System.Data.SqlClient.SqlParameterCollection> Yöntem, `Add` kurucu bağımsız değişkenler veya varolan bir parametre nesnesi olarak kabul edilecektir.  
  
 Bu konudaki sonraki bölümlerde tarih ve saat parametrelerinin nasıl belirtilen örnekler verilmiştir. Parametrelerle çalışma ek örnekleri için, [Parametreleri ve Parametre Veri Türlerini ve](../configuring-parameters-and-parameter-data-types.md) [DataAdapter Parametrelerini](../dataadapter-parameters.md)Yapılandırma bölümüne bakın.  
  
### <a name="date-example"></a>Tarih Örneği  
 Aşağıdaki kod parçası, bir `date` parametrenin nasıl belirtilen nasıl olduğunu gösterir.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Zaman Örneği  
 Aşağıdaki kod parçası, bir `time` parametrenin nasıl belirtilen nasıl olduğunu gösterir.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Datetime2 Örneği  
 Aşağıdaki kod parçası, hem tarih `datetime2` hem de saat parçalarıyla bir parametrenin nasıl belirtilen olduğunu gösterir.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>DateTimeOffSet Örneği  
 Aşağıdaki kod parçası, tarih, `DateTimeOffSet` saat ve saat dilimi ofset 0 olan bir parametrenin nasıl belirtilen olduğunu gösterir.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>Katma Değer  
 Aşağıdaki kod parçasında `AddWithValue` gösterildiği gibi, <xref:System.Data.SqlClient.SqlCommand>bir , yöntemini kullanarak parametreleri de sağlayabilirsiniz. Ancak, `AddWithValue` yöntem parametreyi <xref:System.Data.SqlClient.SqlParameter.DbType%2A> belirtmenize <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> izin vermez.  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametre, sunucudaki `date`bir `datetime`, `datetime2` veya veri türüyle eşleyebilir. Yeni `datetime` veri türleri ile çalışırken, <xref:System.Data.SqlDbType> parametrenin özelliğini açıkça örneğin veri türüne ayarlamanız gerekir. Parametre değerlerinin kullanılması <xref:System.Data.SqlDbType.Variant> veya dolaylı olarak sağlanması, parametre değerleri `datetime` ve `smalldatetime` veri türleri ile geriye dönük uyumluluk la ilgili sorunlara neden olabilir.  
  
 Aşağıdaki tablo, `SqlDbTypes` hangi CLR türlerinden çıkarılan ları gösterir:  
  
|CLR türü|Çıkarılan SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Tarih ve Saat Verilerini Alma  
 Aşağıdaki tabloda SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanmaktadır.  
  
|SqlClient yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Bir <xref:System.DateTime> yapı olarak belirtilen sütun değerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Bir <xref:System.DateTimeOffset> yapı olarak belirtilen sütun değerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Alan için temel sağlayıcıya özgü türü döndürür. Yeni tarih ve `GetFieldType` saat türleri ile aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Belirtilen sütunun değerini alır. Yeni tarih ve `GetValue` saat türleri ile aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Sütun değerini ' <xref:System.Data.SqlTypes.SqlString>olarak alır. Veriler <xref:System.InvalidCastException> bir `SqlString`. olarak ifade edilemiyorsa oluşur|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Sütun verilerini varsayılan `SqlDbType`olarak alır. Yeni tarih ve `GetValue` saat türleri ile aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Tip Sistem Sürümü SQL Server 2005 olarak ayarlanmışsa sütun değerini dize olarak alır. Veriler <xref:System.InvalidCastException> dize olarak ifade edilemiyorsa oluşur.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Bir <xref:System.TimeSpan> yapı olarak belirtilen sütun değerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Belirtilen sütun değerini temel CLR türü olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Bir dizideki sütun değerlerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Sonuç <xref:System.Data.DataTable> kümesinin meta verilerini açıklayan bir döndürür.|  
  
> [!NOTE]
> Yeni tarih ve `SqlDbTypes` saat, SQL Server'da işlem içinde yürütülen kod için desteklenmez. Bu türlerden biri sunucuya aktarılırsa bir özel durum yükseltilir.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Tarih ve Saat Değerlerini Literal olarak belirtme  
 SQL Server'ın çalışma zamanında değerlendirdiği çeşitli gerçek dize biçimlerini kullanarak tarih ve saat veri türlerini belirterek bunları dahili tarih/saat yapılarına dönüştürebilirsiniz. SQL Server, tek tırnak işaretleri (') ile kapatılan tarih ve saat verilerini tanır. Aşağıdaki örnekler bazı biçimleri gösterir:  
  
- Alfabetik tarih biçimleri, `'October 15, 2006'`gibi .  
  
- Gibi sayısal tarih biçimleri, `'10/15/2006'`  
  
- ISO standart tarih biçimini `'20061015'`kullanıyorsanız, 15 Ekim 2006 olarak yorumlanacak olan ayrılmamış dize biçimleri.  
  
> [!NOTE]
> SQL Server Books Online'da tüm gerçek dize biçimleri ve tarih ve saat veri türlerinin diğer özellikleri için tam dokümantasyon bulabilirsiniz.  
  
 Sıfırdan az veya 24 saatten büyük veya eşit olan <xref:System.ArgumentException>zaman değerleri bir .  
  
## <a name="resources-in-sql-server-books-online"></a>SQL Server Books Online'daki Kaynaklar  
 SQL Server'da tarih ve saat değerleriyle çalışma hakkında daha fazla bilgi için SQL Server Books Online'da aşağıdaki kaynaklara bakın.  
  
|Konu başlığı|Açıklama|  
|-----------|-----------------|  
|[Tarih ve Saat Veri Türleri ve Fonksiyonları (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Tüm Transact-SQL tarih ve saat veri türlerine ve işlevlerine genel bir bakış sağlar.|  
|[Tarih ve Saat Verilerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Tarih ve saat veri türleri ve işlevleri ve bunları kullanma örnekleri hakkında bilgi sağlar.|  
|[Veri Türleri (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|SQL Server'daki sistem veri türlerini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
