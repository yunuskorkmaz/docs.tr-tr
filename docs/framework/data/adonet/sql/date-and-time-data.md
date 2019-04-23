---
title: Tarih ve Saat Verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 80b7df4922e1398c7290e769e53627a1d46ebc83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344187"
---
# <a name="date-and-time-data"></a>Tarih ve Saat Verileri
SQL Server 2008, tarih ve saat bilgilerini işlemek için yeni veri türlerini tanıtır. Yeni veri türleri, tarih ve saat için farklı türler ve büyük aralığı, hassasiyet ve saat dilimini tanıma ile genişletilmiş veri türleri içerir. İle .NET Framework sürüm 3.5 Service Pack 1, SQL Server için .NET Framework veri sağlayıcısı (SP) Başlangıç (<xref:System.Data.SqlClient>) SQL Server 2008 veritabanı altyapısı için yeni özellikler hakkında tam destek sağlar. .NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üzeri) ile SqlClient bu yeni özellikleri kullanmak için.  
  
 İki veri türü yalnızca olduğu tarih ve saat değerleri ile çalışmak için SQL Server 2008'den önceki SQL Server sürümleri: `datetime` ve `smalldatetime`. Bu iki veri türü, hem tarih değeri hem de yalnızca tarih veya saat değerleri ile çalışmak zorlaştırır bir saat değeri içerir. Ayrıca, bu veri türlerini, yalnızca giriş Gregoryen takviminin İngiltere'deki 1753 sonra gerçekleşen tarihleri destekler. Bu eski veri türleri saat dilimi olmayan başka bir sınırlamadır kullanan, birden çok zaman bölgelerinden kaynaklanan verilerle çalışmak zorlaştıran.  
  
 SQL Server veri türleri için kapsamlı belgeler, SQL Server Books Online içinde kullanılabilir. Aşağıdaki tablo, tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listeler.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1. [Tarih ve saat verilerini kullanma](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Tarih/saat veri türleri SQL Server 2008 ' tanıtılan  
 Yeni tarih ve saat veri türleri aşağıdaki tabloda açıklanmaktadır.  
  
|SQL Server veri türü|Açıklama|  
|--------------------------|-----------------|  
|`date`|`date` Veri türüne sahip bir dizi 1 Ocak, 01 ile 31 Aralık 9999 ile bir doğruluk 1 gün. 1 Ocak 1900 varsayılan değerdir. Depolama boyutu 3 bayttır.|  
|`time`|`time` Tabanlı bir 24 saatlik düzende veri türü yalnızca saat değerlerini depolar. `time` Aralığıyla 100 nanosaniyelik bir doğruluğunu 00:00:00.0000000 23:59:59.9999999 aracılığıyla veri türüne sahip. 00:00:00.0000000 (gece yarısı) varsayılan değerdir. `time` Veri türü kullanıcı tanımlı kesirli ikinci duyarlık destekler ve depolama alanı boyutu 3'ten 6 bayt cinsinden belirtilen Duyarlığı'göre farklılık gösterir.|  
|`datetime2`|`datetime2` Veri türü, aralık ve duyarlık birleştirir `date` ve `time` veri türleri tek bir veri türü.<br /><br /> Varsayılan değerleri ve dize değişmez değer biçimleri tanımlanan aynıdır `date` ve `time` veri türleri.|  
|`datetimeoffset`|`datetimeoffset` Veri türüne sahip tüm özelliklerini `datetime2` ek saat dilimi uzaklığı ile. Saat dilimi kaymasını olarak temsil edilen [+&#124;-] ss: dd. HH 00-saat dilimi kaymasını saat sayısını temsil eden 14 arasında değişen 2 basamaktan oluşur. AA 00-saat dilimi kaymasını ek dakika sayısını temsil eden 59 arasında değişen 2 basamaktan oluşur. 100 nanosaniyelik için saat biçimleri desteklenir. Zorunlu + veya - saat dilimi kaymasını eklendiğinde veya çıkarıldığında UTC'den (Evrensel Saat koordine veya Greenwich saati) yerel saate almak için oturum gösterir.|  
  
> [!NOTE]
>  Kullanma hakkında daha fazla bilgi için `Type System Version` anahtar sözcüğü, bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Tarih biçimi ve tarih sırası  
 SQL Server'ın tarih ve saat değerlerini nasıl ayrıştırır, yalnızca tür sistemi sürümü ve sunucu sürümü, aynı zamanda sunucunun varsayılan dili ve biçimi ayarlarına bağlıdır. Farklı dili ve tarih biçimi ayarını kullanan bir tarih dizesini tarih biçimlerinden biri bir dil için çalışır sorgu bir bağlantı tarafından yürütülürse tanınmayan olabilir.  
  
 Transact-SQL Dil Ayarla ifadesi örtük olarak DATEFORMAT tarih kısımlarını sırasını belirleyen ayarlar. Tarih değerlerini tarih kısımlarını AGY, GAY, YAG'dir, YDM, MYD veya DYM sırayla sıralamaya göre ayırt etmek için bir bağlantı üzerinde AYARLAMAK DATEFORMAT Transact-SQL deyimini kullanın.  
  
 Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantı ile ilişkili varsayılan dili kullanır. Örneğin, bir tarih dizesi ' 01/02/03, ' İngiliz İngilizce dil ayarı ile bir sunucu üzerinde Amerika Birleşik Devletleri İngilizce dil ayarı ile bir sunucu üzerinde AGY (2 Ocak 2003) ve GAY (1 Şubat 2003) olarak yorumlanacağını. Yılın tanımlar. yüzyıla uygun değer atamak için kesme tarihinden SQL Server'ın kesme yıl kuralı kullanılarak belirlenir. Daha fazla bilgi için [iki basamaklı yıl kesme seçeneği](https://go.microsoft.com/fwlink/?LinkId=120473) SQL Server Books Online.  
  
> [!NOTE]
>  Bir dize biçimine dönüştürme iken YDM tarih biçimi desteklenmiyor `date`, `time`, `datetime2`, veya `datetimeoffset`.  
  
 SQL Server'ın tarih ve saat verileri nasıl yorumlayacağını hakkında daha fazla bilgi için bkz. [kullanarak tarih ve saat verilerini](https://go.microsoft.com/fwlink/?LinkID=98361) SQL Server 2008 Books Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Tarih/saat veri türleri ve parametreleri  
 Aşağıdaki numaralandırmalar eklenmiş <xref:System.Data.SqlDbType> yeni tarih ve saat veri türleri desteklemek için.  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

Veri türünü belirleyebileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> önceki birini kullanarak <xref:System.Data.SqlDbType> numaralandırma. 

> [!NOTE]
> Ayarlayamazsınız `DbType` özelliği bir `SqlParameter` için `SqlDbType.Date`.

 Türünü belirtebilirsiniz bir <xref:System.Data.SqlClient.SqlParameter> ayarlayarak genel <xref:System.Data.SqlClient.SqlParameter.DbType%2A> özelliği bir `SqlParameter` belirli bir nesneye <xref:System.Data.DbType> numaralandırma değeri. Aşağıdaki sabit listesi değerleri eklenmiş <xref:System.Data.DbType> desteklemek için `datetime2` ve `datetimeoffset` veri türleri:  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 Bu yeni numaralandırmalara ek `Date`, `Time`, ve `DateTime` .NET Framework'ün önceki sürümlerinde var olan bir numaralandırma.  
  
 .NET Framework veri sağlayıcısı türü bir parametre nesnenin değerinin parametre nesnenin ya da .NET Framework türü gösterilir `DbType` parametresi nesne. Yeni <xref:System.Data.SqlTypes> veri türleri kullanıma sunulmuştur yeni tarih ve saat veri türleri desteklemek için. Aşağıdaki tabloda, SQL Server 2008 tarih ve saat veri türleri ve CLR veri türleri arasındaki eşlemeleri açıklanmaktadır.  
  
|SQL Server veri türü|.NET Framework türü|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Tarih|System.DateTime|Tarih|Tarih|  
|zaman|System.TimeSpan|Zaman|Zaman|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter özellikleri  
 Aşağıdaki tabloda açıklanmıştır `SqlParameter` tarih ve saat veri türleri için uygun olan özellikleri.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Alır veya bir değerin boş değer atanabilir olup olmadığını ayarlar. Null parametre değeri sunucuya gönderdiğinizde, belirtmelisiniz <xref:System.DBNull>, yerine `null` (`Nothing` Visual Basic'te). Veritabanı null değerler hakkında daha fazla bilgi için bkz. [boş değerler işleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Alır veya ayarlar değeri temsil etmek için kullanılan basamak sayısı. Bu ayar, tarih ve saat veri türleri için göz ardı edilir.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Değerin saat kısmı olduğu için çözümlenen ondalık sayıyı alır veya ayarlar `Time`, `DateTime2`, ve `DateTimeOffset`. Varsayılan değer, gerçek ölçek değerinden çıkarılan ve sunucuya gönderilen anlamına gelen 0 ' dır.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Tarih ve saat veri türleri için yok sayıldı.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Alır veya parametre değerini ayarlar.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Alır veya parametre değerini ayarlar.|  
  
> [!NOTE]
>  Sıfır veya daha büyük veya eşittir 24 saat daha az zaman değerler oluşturur bir <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Parametreleri oluşturma  
 Oluşturabileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> nesnesi oluşturucusuna kullanarak ya da ekleyerek bir <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> çağırarak koleksiyonu `Add` yöntemi <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Yöntemi olarak alacağınız oluşturucu bağımsız değişkenleri veya var olan bir parametre nesnesi girin.  
  
 Bu konunun sonraki bölümlerinde, tarih ve saat parametreleri belirtmek örnekler sağlar. Parametreler ile çalışmaya ilişkin ek örnekler için bkz. [yapılandırma parametreleri ve parametre veri türlerini](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Tarih örneği  
 Aşağıdaki kod parçası nasıl belirtildiğini gösterir bir `date` parametresi.  
  
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
  
### <a name="time-example"></a>Örnek saati  
 Aşağıdaki kod parçası nasıl belirtildiğini gösterir bir `time` parametresi.  
  
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
  
### <a name="datetime2-example"></a>Datetime2 örneği  
 Aşağıdaki kod parçası nasıl belirtildiğini gösterir bir `datetime2` tarih ve saat bölümleri içeren bir parametre.  
  
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
  
### <a name="datetimeoffset-example"></a>DateTimeOffSet örneği  
 Aşağıdaki kod parçası nasıl belirtildiğini gösterir bir `DateTimeOffSet` tarih, bir saat ve bir saat dilimi uzaklığı 0 ile parametre.  
  
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
  
### <a name="addwithvalue"></a>AddWithValue  
 Parametreleri kullanarak da sağlayabilirsiniz `AddWithValue` yöntemi bir <xref:System.Data.SqlClient.SqlCommand>aşağıdaki kod parçasını gösterildiği gibi. Ancak, `AddWithValue` yöntemi izin vermemektedir belirtmek <xref:System.Data.SqlClient.SqlParameter.DbType%2A> veya <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametresi için.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametreyi eşlemek için bir `date`, `datetime`, veya `datetime2` sunucudaki veri türü. Yeni çalışırken `datetime` veri türleri, parametrenin açıkça ayarlamalısınız <xref:System.Data.SqlDbType> örnek veri türünün özelliğini. Kullanarak <xref:System.Data.SqlDbType.Variant> ya da örtük olarak parametre değerlerini sağlama ile geriye dönük uyumluluk ile sorunlara neden olabilir `datetime` ve `smalldatetime` veri türleri.  
  
 Aşağıdaki tabloda gösterir `SqlDbTypes` hangi CLR Türleri algılanır:  
  
|CLR türü|Çıkarsanan SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Tarih ve saat verilerini alma  
 Aşağıdaki tabloda, SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanır.  
  
|SqlClient yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.DateTime> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.DateTimeOffset> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Temel alınan sağlayıcıya özgü türü alanın türünü döndürür. Aynı türlerini döndürür `GetFieldType` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Belirtilen sütunun değeri alır. Aynı türlerini döndürür `GetValue` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Sütun değeri olarak alır. bir <xref:System.Data.SqlTypes.SqlString>. Bir <xref:System.InvalidCastException> veri olarak ifade edilemediğinde gerçekleşir bir `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Sütun verileri varsayılan olarak alır `SqlDbType`. Aynı türlerini döndürür `GetValue` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Tür sistemi sürümü, SQL Server 2005'e ayarlanırsa, sütun değeri bir dize olarak alır. Bir <xref:System.InvalidCastException> verileri dize olarak ifade edilemediğinde gerçekleşir.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.TimeSpan> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Belirtilen sütun değeri temel alınan CLR türünü alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Bir dizideki sütun değerlerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Döndürür bir <xref:System.Data.DataTable> , sonuç kümesinin meta veriler açıklanmaktadır.|  
  
> [!NOTE]
>  Yeni tarih ve saat `SqlDbTypes` işlemde SQL Server'da çalışan kod için desteklenmez. Şu türlerden birinde sunucuya geçirilmişse, bir özel durum oluşturulur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Değişmez değer olarak tarih ve saat değerleri belirtme  
 Tarih ve saat veri türleri, birçok farklı değişmez değer dize biçimleri, hangi SQL Server'ı kullanarak belirtebilirsiniz, sonra bunları yapılarını iç tarih/saat dönüştürme, çalışma zamanında değerlendirir. SQL Server tek tırnak işareti (') tarih ve saat verilerini tanır. Aşağıdaki örnekler, bazı biçimler göstermektedir:  
  
-   Alfabetik tarih biçimleri, gibi `'October 15, 2006'`.  
  
-   Gibi sayısal tarih biçimleri `'10/15/2006'`.  
  
-   Dize biçimleri gibi unseparated `'20061015'`, hangi yorumlanabilir 15 Ekim 2006 ISO standart tarih biçimi kullanıyorsanız.  
  
> [!NOTE]
>  Tüm değişmez değer dize biçimleri ve diğer özellikler SQL Server Books Online tarih ve saat veri türleri için kapsamlı belgeler bulabilirsiniz.  
  
 Sıfır veya daha büyük veya eşittir 24 saat daha az zaman değerler oluşturur bir <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>SQL Server 2008 Çevrimiçi Kitapları'nda kaynaklar  
 SQL Server 2008'deki tarih ve saat değerleri ile çalışma hakkında daha fazla bilgi için SQL Server 2008 Çevrimiçi Kitapları'nda aşağıdaki kaynaklara bakın.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Tarih ve saat veri türleri ve işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Tüm Transact-SQL tarih ve saat veri türleri ve işlevleri hakkında genel bir bakış sağlar.|  
|[Tarih ve saat verilerini kullanma](https://go.microsoft.com/fwlink/?LinkId=98361)|Tarih ve saat veri türleri ve işlevleri ve bunları kullanma örnekleri hakkında bilgi sağlar.|  
|[Veri türleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|SQL Server 2008 sistem veri türlerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
