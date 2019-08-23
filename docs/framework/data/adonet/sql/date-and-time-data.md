---
title: Tarih ve Saat Verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 016e2efae68c02c8c5a10ab74419599bc41be3a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959387"
---
# <a name="date-and-time-data"></a>Tarih ve Saat Verileri
SQL Server 2008, tarih ve saat bilgilerini işlemeye yönelik yeni veri türlerini tanıtır. Yeni veri türleri tarih ve saat için ayrı türler, daha fazla Aralık, duyarlık ve saat dilimi tanıma ile genişletilmiş veri türleri içerir. .NET Framework sürüm 3,5 hizmet paketi (SP) 1 ' den başlayarak, SQL Server (<xref:System.Data.SqlClient>) için .NET Framework veri sağlayıcısı, SQL Server 2008 veritabanı altyapısının tüm yeni özellikleri için tam destek sağlar. Bu yeni özellikleri SqlClient kullanmak için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.  
  
 SQL Server 2008 ' den önceki SQL Server sürümlerinde yalnızca tarih ve saat değerleriyle çalışma için iki veri türü vardı: `datetime` ve. `smalldatetime` Bu veri türlerinin her ikisi de tarih değerini ve bir saat değerini içerir. Bu, yalnızca tarih veya yalnızca saat değerleriyle çalışmayı zorlaştırır. Ayrıca, bu veri türleri yalnızca 1753 içinde England 'da Gregoryen takvime giriş sonrasında oluşan tarihleri destekler. Diğer bir sınırlama, bu eski veri türlerinin zaman dilimi açısından farkında olmamasıdır ve bu sayede birden çok saat diliminden kaynaklanan verilerle çalışmayı zorlaştırır.  
  
 SQL Server veri türleri için tüm belgeler, çevrimiçi SQL Server Books Online 'da bulunabilir. Aşağıdaki tabloda tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listelenmektedir.  
  
 **Books Online SQL Server**  
  
1. [Tarih ve saat verilerini kullanma](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>SQL Server 2008 ' de tanıtılan tarih/saat veri türleri  
 Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.  
  
|SQL Server veri türü|Açıklama|  
|--------------------------|-----------------|  
|`date`|`date` Veri türü 1 Ocak 01 ile 31 Aralık 9999 arasında bir aralığa sahiptir ve 1 gün doğruluk sağlar. Varsayılan değer 1 Ocak 1900 ' dir. Depolama boyutu 3 bayttır.|  
|`time`|`time` Veri türü yalnızca saat değerlerini, 24 saatlik bir saate göre depolar. `time` Veri türü 00:00:00.0000000 ila 23:59:59.9999999 ile 100 nanosaniye arasında bir aralığa sahiptir. Varsayılan değer 00:00:00.0000000 (gece yarısı) olur. `time` Veri türü, Kullanıcı tanımlı kesirli ikinci duyarlığı destekler ve depolama boyutu, belirtilen duyarlığa göre 3 ile 6 bayt arasında değişir.|  
|`datetime2`|Veri türü, `date` ve`time` veri türlerinin aralığını ve duyarlığını tek bir veri türünde birleştirir. `datetime2`<br /><br /> Varsayılan değerler ve dize değişmez biçimleri, `date` ve `time` veri türlerinde tanımlananlarla aynıdır.|  
|`datetimeoffset`|Veri türünün tüm `datetime2` özellikleri ek saat dilimi farkına sahiptir. `datetimeoffset` Saat dilimi boşluğu [+&#124;-] hh: mm olarak gösterilir. SS, saat dilimi kaydırmasında saat sayısını temsil eden 00 ile 14 arasında 2 basamaklı bir sayıdır. Aa, saat dilimi kaydırmasında ek dakika sayısını temsil eden 00 ila 59 arasında 2 basamaklı bir sayıdır. Zaman biçimleri 100 nanosaniye için desteklenir. Zorunlu + veya-imzala, saat dilimi kaydırın UTC (evrensel saat koordinatı veya Greenwich saati) ile yerel saati elde edilip edilmeyeceğini belirtir.|  
  
> [!NOTE]
> `Type System Version` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Tarih biçimi ve tarih sırası  
 SQL Server Tarih ve saat değerlerini nasıl ayrıştırdığı, yalnızca sistem sürümüne ve sunucu sürümüne değil, ayrıca sunucunun varsayılan diline ve biçim ayarlarına bağlıdır. Sorgu farklı bir dil ve tarih biçimi ayarı kullanan bir bağlantı tarafından yürütülürse, bir dilin tarih biçimleri için çalıştırılan bir tarih dizesi tanınmıyor olabilir.  
  
 Transact-SQL SET LANGUAGE deyimleri, tarih bölümlerinin sırasını belirleyen DATEFORMAT öğesini örtülü olarak ayarlar. Tarih değerlerini MDY, DMY, YıMD, YıDM, MYD veya DYM Order içindeki Tarih kısımlarını sıralamaya göre ayırt etmek için bir bağlantıda DATEFORMAT Transact-SQL ifadesini ayarla ' yı kullanabilirsiniz.  
  
 Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantıyla ilişkili varsayılan dili kullanır. Örneğin, bir tarih dizesi ' 01/02/03 ', dil Birleşik Devletler ayarı olan bir sunucu üzerinde MDY (2 Ocak 2003) ve Ingiliz Ingilizcesi dil ayarı olan bir sunucuda DMY (1 Şubat 2003) olarak yorumlanır. Yıl, yüzyıl değerini atamak için kesme tarihini tanımlayan SQL Server kesme yılı kuralı kullanılarak belirlenir. Daha fazla bilgi için SQL Server Books Online 'da [iki basamaklı yıl kesme seçeneği](https://go.microsoft.com/fwlink/?LinkId=120473) konusuna bakın.  
  
> [!NOTE]
> Bir `date`dize biçiminden `time` ,`datetime2`, veya`datetimeoffset`olarak dönüştürülürken, yıdm tarih biçimi desteklenmez.  
  
 SQL Server Tarih ve saat verilerini yorumlama hakkında daha fazla bilgi için, bkz. SQL Server 2008 Books Online 'da [Tarih ve saat verileri kullanma](https://go.microsoft.com/fwlink/?LinkID=98361) .  
  
## <a name="datetime-data-types-and-parameters"></a>Tarih/saat veri türleri ve parametreleri  
 Yeni tarih ve saat veri türlerini desteklemek <xref:System.Data.SqlDbType> için aşağıdaki numaralandırmalar eklenmiştir.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Bir <xref:System.Data.SqlClient.SqlParameter> öğesinin veri türünü, önceki <xref:System.Data.SqlDbType> Numaralandırmalardan birini kullanarak belirtebilirsiniz. 

> [!NOTE]
> Öğesinin `DbType`özelliğini olarak`SqlDbType.Date`ayarlayamazsınız. `SqlParameter`

 <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> Bir nesnenin`SqlParameter` özelliğini belirli<xref:System.Data.DbType> bir numaralandırma değerine ayarlayarak, bir genel olarak türünü de belirtebilirsiniz. `datetime2` <xref:System.Data.DbType> Ve`datetimeoffset` veri türlerini desteklemek için aşağıdaki numaralandırma değerleri eklenmiştir:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Bu yeni numaralandırmalar, `Date`.NET Framework `Time`önceki sürümlerinde `DateTime` mevcut olan, ve Numaralandırmalar için ek niteliğindedir.  
  
 Parametre nesnesinin .NET Framework veri sağlayıcısı türü, parametre nesnesinin değerinin .NET Framework türünden veya parametre nesnesinin öğesinden `DbType` çıkarsanamıyor. Yeni tarih <xref:System.Data.SqlTypes> ve saat veri türlerini desteklemek için yeni veri türleri tanıtılmadı. Aşağıdaki tabloda SQL Server 2008 tarih ve saat veri türleri ile CLR veri türleri arasındaki eşlemeler açıklanmaktadır.  
  
|SQL Server veri türü|.NET Framework türü|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Tarih|System.DateTime|Tarih|Tarih|  
|zaman|System.TimeSpan|Zaman|Zaman|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|türünde|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter özellikleri  
 Aşağıdaki tabloda tarih ve `SqlParameter` saat veri türleriyle ilgili özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Değerin null yapılabilir olup olmayacağını alır veya ayarlar. Sunucuya null bir parametre değeri gönderdiğinizde, <xref:System.DBNull> `null` (`Nothing` Visual Basic) yerine belirtmeniz gerekir. Veritabanı boş değerleri hakkında daha fazla bilgi için bkz. [null değerlerini işleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Değeri temsil etmek için kullanılan en fazla basamak sayısını alır veya ayarlar. Tarih ve saat veri türleri için bu ayar yok sayılır.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|, `Time` `DateTime2`Ve içindeğerinsaatkısmınınçözümlendiğiondalıkbasamaklarınsayısınıalırveyaayarlar.`DateTimeOffset` Varsayılan değer 0 ' dır. Bu, gerçek ölçeğin değerden çıkarılan ve sunucuya gönderildiği anlamına gelir.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Tarih ve saat veri türleri için yoksayıldı.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Parametre değerini alır veya ayarlar.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Parametre değerini alır veya ayarlar.|  
  
> [!NOTE]
> Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir <xref:System.ArgumentException>oluşturacak.  
  
### <a name="creating-parameters"></a>Parametreleri oluşturma  
 <xref:System.Data.SqlClient.SqlParameter> Yapıcısını kullanarak veya metodunu`Add` <xref:System.Data.SqlClient.SqlCommand> çağırarakbirkoleksiyonaekleyerek<xref:System.Data.SqlClient.SqlCommand.Parameters%2A> bir nesne oluşturabilirsiniz. <xref:System.Data.SqlClient.SqlParameterCollection> Yöntemi `Add` , Oluşturucu bağımsız değişkenleri ya da varolan bir parametre nesnesi olarak alınır.  
  
 Bu konunun sonraki bölümlerinde tarih ve saat parametrelerinin nasıl belirtilme örnekleri verilmiştir. Parametrelerle çalışma hakkında daha fazla örnek için bkz. [parametreleri ve parametre veri türlerini](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametrelerini](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)yapılandırma.  
  
### <a name="date-example"></a>Tarih örneği  
 Aşağıdaki kod parçası, bir `date` parametrenin nasıl belirtileceğini göstermektedir.  
  
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
  
### <a name="time-example"></a>Zaman örneği  
 Aşağıdaki kod parçası, bir `time` parametrenin nasıl belirtileceğini göstermektedir.  
  
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
 Aşağıdaki kod parçası, hem tarih hem de saat `datetime2` parçalarıyla bir parametrenin nasıl belirtileceğini göstermektedir.  
  
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
 Aşağıdaki kod parçası, bir `DateTimeOffSet` parametrenin Tarih, saat ve saat dilimi fark değeri olan 0 ' ı nasıl belirteceğinizi gösterir.  
  
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
 Ayrıca, aşağıdaki kod parçasında gösterildiği gibi, `AddWithValue` bir <xref:System.Data.SqlClient.SqlCommand>öğesinin yöntemini kullanarak parametreler sağlayabilirsiniz. Ancak, `AddWithValue` yöntemi parametresi için <xref:System.Data.SqlClient.SqlParameter.DbType%2A> veya <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> belirtmenize izin vermez.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Parametresi, sunucusundaki bir `date`, `datetime`veya `datetime2` veri türüyle eşleşgelebilir. `@date` Yeni `datetime` veri türleriyle çalışırken, <xref:System.Data.SqlDbType> parametrenin özelliğini, örneğin veri türüne açık olarak ayarlamanız gerekir. Parametre <xref:System.Data.SqlDbType.Variant> değerlerini kullanmak veya örtük olarak sağlamak, `datetime` ve `smalldatetime` veri türleriyle geriye dönük uyumlulukla ilgili sorunlara neden olabilir.  
  
 Aşağıdaki tabloda, hangi CLR `SqlDbTypes` türlerinden çıkarılan gösterilmektedir:  
  
|CLR türü|Çıkarılan SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Tarih ve saat verilerini alma  
 Aşağıdaki tabloda SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanmaktadır.  
  
|SqlClient yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Belirtilen sütun değerini bir <xref:System.DateTime> yapı olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Belirtilen sütun değerini bir <xref:System.DateTimeOffset> yapı olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Alan için sağlayıcıya özgü temel tür olan türü döndürür. Yeni tarih ve saat türleri `GetFieldType` için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Belirtilen sütunun değerini alır. Yeni tarih ve saat türleri `GetValue` için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Sütun değerini bir <xref:System.Data.SqlTypes.SqlString>olarak alır. Veriler bir`SqlString`olarak ifade edilenemediğinde oluşur.<xref:System.InvalidCastException>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Sütun verilerini varsayılan `SqlDbType`olarak alır. Yeni tarih ve saat türleri `GetValue` için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Tür sistemi sürümü SQL Server 2005 olarak ayarlandıysa, sütun değerini bir dize olarak alır. Veriler bir dize olarak ifade edilenemediğinde oluşur.<xref:System.InvalidCastException>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Belirtilen sütun değerini bir <xref:System.TimeSpan> yapı olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Belirtilen sütun değerini temel alınan CLR türü olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Bir dizideki sütun değerlerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Sonuç kümesinin <xref:System.Data.DataTable> meta verilerini açıklayan bir döndürür.|  
  
> [!NOTE]
> Yeni tarih ve saat `SqlDbTypes` , SQL Server içinde işlem sırasında yürütülen kod için desteklenmez. Bu türlerden biri sunucuya geçirilirse bir özel durum oluşur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Tarih ve saat değerlerini değişmez değer olarak belirtme  
 Tarih ve saat veri türlerini SQL Server, daha sonra çalışma zamanında değerlendiren ve bunları iç tarih/saat yapılarına dönüştüren çeşitli farklı değişmez dize biçimlerini kullanarak belirtebilirsiniz. SQL Server, tek tırnak işareti (') içine alınmış tarih ve saat verilerini tanır. Aşağıdaki örneklerde bazı biçimler gösterilmektedir:  
  
- Alfabetik tarih biçimleri, `'October 15, 2006'`örneğin.  
  
- Gibi sayısal Tarih biçimleri `'10/15/2006'`.  
  
- ISO standart tarih biçimini kullanıyorsanız, örneğin `'20061015'`, 15 Ekim 2006 olarak yorumlanabilecek, gibi ayrılmamış dize biçimleri.  
  
> [!NOTE]
> Tüm sabit dize biçimlerinin ve SQL Server Books Online 'daki tarih ve saat veri türlerinin diğer özelliklerine ilişkin tüm belgeleri bulabilirsiniz.  
  
 Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir <xref:System.ArgumentException>oluşturacak.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>SQL Server 2008 Books Online 'daki kaynaklar  
 SQL Server 2008 ' de tarih ve saat değerleriyle çalışma hakkında daha fazla bilgi için SQL Server 2008 Books Online 'da aşağıdaki kaynaklara bakın.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Tarih ve saat veri türleri ve Işlevleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Tüm Transact-SQL tarih ve saat veri türleri ve işlevlerine genel bir bakış sağlar.|  
|[Tarih ve saat verilerini kullanma](https://go.microsoft.com/fwlink/?LinkId=98361)|Tarih ve saat veri türleri ve işlevleri hakkında bilgi ve bunları kullanma örnekleri sağlar.|  
|[Veri türleri (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|SQL Server 2008 ' de sistem veri türlerini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
