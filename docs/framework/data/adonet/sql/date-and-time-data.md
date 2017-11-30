---
title: Tarih ve saat verilerini
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bd9fa595281f7dfda50ef22914ccce7bf814a36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="date-and-time-data"></a>Tarih ve saat verilerini
SQL Server 2008, tarih ve saat bilgilerini işleme yeni veri türleri tanıtır. Yeni veri türleri, tarih ve saat için ayrı türleri ve büyük aralık, duyarlık ve saat dilimi tanıma ile genişletilmiş veri türleri içerir. İle .NET Framework sürüm 3.5 hizmet paketi (SP) 1, SQL Server için .NET Framework veri sağlayıcısı başlatılıyor (<xref:System.Data.SqlClient>) SQL Server 2008 veritabanı altyapısı için yeni özellikler hakkında tam destek sağlar. .NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) bu yeni özellikleri ile SqlClient kullanılacak.  
  
 İki veri türü yalnızca vardı tarih ve saat değerleri ile çalışmak için SQL Server 2008'den önceki SQL Server sürümleri: `datetime` ve `smalldatetime`. Bu iki veri türü tarih değeri ve yalnızca tarih veya saat değerleri ile çalışmak zorlaştırır bir saat değeri içerir. Ayrıca, bu veri türleri yalnızca 1753 İngiltere'deki Gregoryen takvim girişte sonra ortaya tarihleri destekler. Bu eski veri türleri saat dilimi olmayan başka bir kısıtlamadır kullanan, birden çok zaman bölgelerinden kaynaklandığı verilerle çalışmak zorlaştıran.  
  
 SQL Server veri türleri için kapsamlı belgeler SQL Server Books Online içinde kullanılabilir. Aşağıdaki tabloda, tarih ve saat verilerini için sürüme özgü giriş seviyesi konuları listeler.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Tarih ve saat verilerini kullanma](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Veri türleri SQL Server 2008 ' sunulan tarih  
 Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.  
  
|SQL Server veri türü|Açıklama|  
|--------------------------|-----------------|  
|`date`|`date` Veri türüne sahip bir aralığı 1 Ocak-31 Aralık 01 bir doğruluğu, 1 gün ile 9999. Varsayılan değer 1 Ocak 1900 ' dir. Depolama boyutu 3 bayttır.|  
|`time`|`time` Veri türü, 24 saatlik dayalı yalnızca saat değerleri depolar. `time` Aralığıyla 100 nanosaniye bir doğruluğunu 00:00:00.0000000 23:59:59.9999999 aracılığıyla veri türüne sahip. 00:00:00.0000000 (gece yarısı) varsayılan değerdir. `time` Veri türü kullanıcı tanımlı kesirli ikinci duyarlık destekler ve depolama boyutu 3 ile 6 bayt cinsinden belirtilen duyarlılık göre farklılık gösterir.|  
|`datetime2`|`datetime2` Veri türü, aralık ve kesinliğini birleştirir `date` ve `time` tek bir veri türüne içine veri türleri.<br /><br /> Dize değişmez değer biçimleri ve varsayılan değerleri tanımlanan aynıdır `date` ve `time` veri türleri.|  
|`datetimeoffset`|`datetimeoffset` Veri türüne sahip tüm özelliklerini `datetime2` ek saat dilimi konumu ile. Saat dilimi konumu olarak temsil edilir [+ &#124;-] hh: mm. HH 00-saat dilimi kaymasını saat sayısını temsil eden 14 arasında değişen 2 basamaktan oluşur. AA 00-saat dilimi kaymasını ek dakika sayısını temsil eden 59 arasında değişen 2 basamaktan oluşur. Saat biçimleri 100 nanosaniye desteklenir. Zorunlu + veya - saat dilimi kaymasını eklendiğinde veya (Evrensel Saat eşgüdümü veya Greenwich saati) yerel zamanını elde etmek için UTC çıkarılır işareti gösterir.|  
  
> [!NOTE]
>  Kullanma hakkında daha fazla bilgi için `Type System Version` anahtar sözcüğü, bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Tarih biçimi ve tarih sırası  
 SQL Server tarih ve saat değerleri nasıl ayrıştırır yalnızca türü sistemi sürümü ve sunucu sürümü, aynı zamanda sunucunun varsayılan dil ve biçim ayarlarına bağlıdır. Farklı dil ve tarih biçimi ayarını kullanan bir tarih dizesi Works tarih biçimleri bir dil için bir bağlantı tarafından sorgu yürütülürse tanınmayan olabilir.  
  
 Transact-SQL Dil Ayarla deyimi tarih kısımlarını sırasını belirleyen DATEFORMAT örtük olarak ayarlar. Tarih değerlerini tarih kısımlarını AGY, GAY, YAG'dir, YDM, MYD veya DYM sırada sıralama tarafından belirsizliğini ortadan kaldırmak için bir bağlantı üzerinden AYARLAMAK DATEFORMAT Transact-SQL deyimini kullanın.  
  
 Bağlantı için tüm DATEFORMAT belirtmezseniz, SQL Server bağlantı ile ilişkili varsayılan dilini kullanır. Örneğin, tarih dizisi 02 / ' 01/03 ' İngiliz İngilizce dil ayarı ile bir sunucu üzerinde Amerika Birleşik Devletleri İngilizce dil ayarı olan bir sunucuda AGY (2 Ocak 2003) ve GAY (1 Şubat 2003) olarak yorumlanacağını. Yılın century değer atamak için kesme tarihi tanımlar SQL Server'ın kesme yıl kuralı kullanılarak belirlenir. Daha fazla bilgi için bkz: [iki rakamlı yıl kesme seçeneği](http://go.microsoft.com/fwlink/?LinkId=120473) SQL Server Books Online.  
  
> [!NOTE]
>  Bir dize biçimine dönüştürülürken YDM tarih biçimi desteklenmiyor `date`, `time`, `datetime2`, veya `datetimeoffset`.  
  
 SQL Server tarih ve saat verilerini yorumlaması hakkında daha fazla bilgi için bkz: [kullanarak tarih ve saat verilerini](http://go.microsoft.com/fwlink/?LinkID=98361) SQL Server 2008 Books Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Tarih/saat veri türleri ve parametreleri  
 Veri türünü belirleyebileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> birini kullanarak <xref:System.Data.SqlDbType> numaralandırmalar. Aşağıdaki sabit listeleri için eklenene <xref:System.Data.SqlDbType> yeni tarih ve saat veri türlerini desteklemek için.  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 Ayrıca türünü belirtebilirsiniz bir <xref:System.Data.SqlClient.SqlParameter> ayarlayarak genel <xref:System.Data.SqlClient.SqlParameter.DbType%2A> özelliği bir `SqlParameter` belirli bir nesneye <xref:System.Data.DbType> numaralandırma değeri. Aşağıdaki numaralandırma değerleri için eklenene <xref:System.Data.DbType> desteklemek için `datetime2` ve `datetimeoffset` veri türleri:  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 Bu yeni numaralandırmalar tamamlayacak `Date`, `Time`, ve `DateTime` .NET Framework'ün önceki sürümlerde var olan numaralandırmalar.  
  
 .NET Framework veri sağlayıcısı türü parameter nesnesinin değerin parametre nesnesinin ya da .NET Framework tür çıkarımı yapılan `DbType` parametre nesnesinin. Yeni <xref:System.Data.SqlTypes> veri türlerine sunulan yeni tarih ve saat veri türlerini desteklemek için. Aşağıdaki tabloda, SQL Server 2008 tarih ve saat veri türleri ve CLR veri türleri arasındaki eşlemeleri açıklanmaktadır.  
  
|SQL Server veri türü|.NET Framework türü|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Tarih|System.DateTime|Tarih|Tarih|  
|zaman|System.TimeSpan|Zaman|Zaman|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter özellikleri  
 Aşağıdaki tabloda açıklanmaktadır `SqlParameter` tarih ve saat veri türleri ile ilgili özellikler.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Alır veya değer boş değer atanabilir olup olmadığını ayarlar. Sunucuya bir null parametre değeri gönderdiğinizde belirtmelisiniz <xref:System.DBNull>, yerine `null` (`Nothing` Visual Basic'te). Veritabanı null değerler hakkında daha fazla bilgi için bkz: [boş değerler işleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Alır veya değeri temsil etmek için kullanılan basamak sayısını ayarlar. Bu ayar, tarih ve saat veri türleri için göz ardı edilir.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Alır veya ayarlar için değer saat bölümünü olduğu için çözümlenmiş ondalık basamak sayısını `Time`, `DateTime2`, ve `DateTimeOffset`. Varsayılan değer gerçek ölçek değerinden çıkarımı yapılan ve sunucuya gönderilen anlamına gelir 0 ' dır.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Tarih ve saat veri türleri için yoksayıldı.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Alır veya parametre değeri ayarlar.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Alır veya parametre değeri ayarlar.|  
  
> [!NOTE]
>  Sıfır veya daha büyük veya eşittir 24 saat küçüktür saat değerleri oluşturur bir <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Parametreleri oluşturma  
 Oluşturabileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> nesne kendi oluşturucusunu kullanarak veya eklemeyi bir <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> çağırarak koleksiyonu `Add` yöntemi <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Yöntemi olarak sürer oluşturucu bağımsız değişkenleri veya varolan bir parametre nesnesi girin.  
  
 Bu konunun sonraki bölümlerinde, tarih ve saat parametrelerini belirtmek nasıl örnekler sağlar. Parametrelerle çalışma ek örnekler için bkz: [yapılandırma parametreleri ve parametre veri türleri](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Tarih örneği  
 Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `date` parametresi.  
  
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
  
### <a name="time-example"></a>Saat örneği  
 Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `time` parametresi.  
  
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
 Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `datetime2` tarih ve saat bölümleri parametresiyle.  
  
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
 Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `DateTimeOffSet` parametresi bir tarih, bir saat ve saat dilimi uzaklığı 0 ile.  
  
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
 Kullanarak parametreleri sağlayabilir `AddWithValue` yöntemi bir <xref:System.Data.SqlClient.SqlCommand>, aşağıdaki kod parçasında gösterildiği gibi. Ancak, `AddWithValue` yöntemi izin vermez belirtmek <xref:System.Data.SqlClient.SqlParameter.DbType%2A> veya <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametresi için.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametresini eşleştirmek için bir `date`, `datetime`, veya `datetime2` sunucudaki veri türü. Yeni çalışırken `datetime` veri türleri, parametrenin açıkça ayarlamalısınız <xref:System.Data.SqlDbType> örnek veri türü için özellik. Kullanarak <xref:System.Data.SqlDbType.Variant> ya da örtük olarak parametre değerlerini sağladığını ile geriye dönük uyumluluk sorunları neden olabilecek `datetime` ve `smalldatetime` veri türleri.  
  
 Aşağıdaki tabloda gösterir `SqlDbTypes` hangi CLR türlerinden sonuçlandı:  
  
|CLR türü|Çıkarsanan SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Tarih ve saat verilerini alma  
 Aşağıdaki tabloda, SQL Server 2008 tarih ve saat değerleri almak için kullanılan yöntemleri açıklar.  
  
|SqlClient yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.DateTime> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.DateTimeOffset> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Alan için temel alınan sağlayıcıya özgü tür türü döndürür. Aynı türlerine döndürür `GetFieldType` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Belirtilen sütunun değeri alır. Aynı türlerine döndürür `GetValue` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Belirtilen dizideki alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Sütun değeri olarak alır bir <xref:System.Data.SqlTypes.SqlString>. Bir <xref:System.InvalidCastException> veri olarak açıklanamayan saptanmışsa bir `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Sütun verileri varsayılan olarak alır `SqlDbType`. Aynı türlerine döndürür `GetValue` yeni tarih ve saat türleri için.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Belirtilen dizideki alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Tür sistemi sürümü SQL Server 2005'e ayarlanırsa sütun değeri bir dize olarak alır. Bir <xref:System.InvalidCastException> verileri dize olarak açıklanamayan ortaya çıkar.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Belirtilen sütun değeri olarak alır bir <xref:System.TimeSpan> yapısı.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Belirtilen sütun değeri temel CLR türünü alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Bir dizi sütun değerlerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Döndürür bir <xref:System.Data.DataTable> sonuç kümesi meta verilerini açıklar.|  
  
> [!NOTE]
>  Yeni tarih ve saat `SqlDbTypes` işlemdeki SQL Server'da yürütüyor kod için desteklenmez. Şu türlerden birine sunucuya aktarılırsa bir özel durum oluşturulur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Tarih ve saat değerleri değişmez değerleri belirtme  
 Tarih ve saat veri türleri, çeşitli farklı değişmez değer dize biçimlerde, hangi SQL Server'ı kullanarak belirtebilirsiniz ardından iç tarih yapılara dönüştürme çalışma zamanında değerlendirir. SQL Server (') tek tırnak işaretleri içine tarih ve saat verilerini tanır. Aşağıdaki örnekler, bazı biçimleri göstermektedir:  
  
-   Alfabetik tarih biçimleri, gibi `'October 15, 2006'`.  
  
-   Sayısal tarih biçimleri, gibi `'10/15/2006'`.  
  
-   Dize biçimleri gibi unseparated `'20061015'`, hangi kabul 15 Ekim 2006 ISO standart tarih biçimi kullanıyorsanız.  
  
> [!NOTE]
>  Değişmez değer dize biçimleri tümünün ve SQL Server Books Online'da tarih ve saat veri türlerinin diğer özellikler için kapsamlı belgeler bulabilirsiniz.  
  
 Sıfır veya daha büyük veya eşittir 24 saat küçüktür saat değerleri oluşturur bir <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>SQL Server 2008 Çevrimiçi Kitapları kaynakları  
 SQL Server 2008'deki tarih ve saat değerleri ile çalışma hakkında daha fazla bilgi için SQL Server 2008 Çevrimiçi Kitapları'nda aşağıdaki kaynaklara bakın.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Tarih ve saat verilerini türler ve İşlevler (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|Tüm Transact-SQL tarih ve saat veri türleri ve işlevleri hakkında genel bir bakış sağlar.|  
|[Tarih ve saat verilerini kullanma](http://go.microsoft.com/fwlink/?LinkId=98361)|Tarih ve saat veri türleri ve işlevleri ve onları kullanma örnekleri hakkında bilgi sağlar.|  
|[Veri türleri (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98362)|SQL Server 2008 sistem veri türlerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server veri türü eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Yapılandırma parametreleri ve parametre veri türleri](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [SQL Server veri türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
