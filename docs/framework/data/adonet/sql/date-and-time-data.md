---
title: Tarih ve Saat Verileri
description: SQL Server için .NET Framework Veri Sağlayıcısı tarih ve saat bilgilerini işlemeye yönelik veri türleri hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 43b3349b2a35385dcc49d0866e0695b08eac2d2e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551497"
---
# <a name="date-and-time-data"></a>Tarih ve Saat Verileri
SQL Server 2008, tarih ve saat bilgilerini işlemeye yönelik yeni veri türlerini tanıtır. Yeni veri türleri tarih ve saat için ayrı türler, daha fazla Aralık, duyarlık ve saat dilimi tanıma ile genişletilmiş veri türleri içerir. .NET Framework sürüm 3,5 hizmet paketi (SP) 1 ' den başlayarak, SQL Server () için .NET Framework Veri Sağlayıcısı, <xref:System.Data.SqlClient> SQL Server 2008 veritabanı altyapısının tüm yeni özellikleri için tam destek sağlar. Bu yeni özellikleri SqlClient kullanmak için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.  
  
 SQL Server 2008 ' den önceki SQL Server sürümlerinde yalnızca tarih ve saat değerleriyle çalışma için iki veri türü vardı: `datetime` ve `smalldatetime` . Bu veri türlerinin her ikisi de tarih değerini ve bir saat değerini içerir. Bu, yalnızca tarih veya yalnızca saat değerleriyle çalışmayı zorlaştırır. Ayrıca, bu veri türleri yalnızca 1753 içinde England 'da Gregoryen takvime giriş sonrasında oluşan tarihleri destekler. Diğer bir sınırlama, bu eski veri türlerinin zaman dilimi açısından farkında olmamasıdır ve bu sayede birden çok saat diliminden kaynaklanan verilerle çalışmayı zorlaştırır.  
  
 SQL Server veri türleri için tüm belgeler, çevrimiçi SQL Server Books Online 'da bulunabilir. Aşağıdaki tabloda tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listelenmektedir.  
  
 **SQL Server belgeleri**  
  
1. [Tarih ve saat verilerini kullanma](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>SQL Server 2008 ' de tanıtılan tarih/saat veri türleri  
 Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.  
  
|SQL Server veri türü|Description|  
|--------------------------|-----------------|  
|`date`|`date`Veri türü 1 Ocak 01 ile 31 aralık 9999 arasında bir aralığa sahiptir ve 1 gün doğruluk sağlar. Varsayılan değer 1 Ocak 1900 ' dir. Depolama boyutu 3 bayttır.|  
|`time`|`time`Veri türü yalnızca saat değerlerini, 24 saatlik bir saate göre depolar. `time`Veri türü 00:00:00.0000000 ila 23:59:59.9999999 ile 100 nanosaniye arasında bir aralığa sahiptir. Varsayılan değer 00:00:00.0000000 (gece yarısı) olur. `time`Veri türü, Kullanıcı tanımlı kesirli ikinci duyarlığı destekler ve depolama boyutu, belirtilen duyarlığa göre 3 ile 6 bayt arasında değişir.|  
|`datetime2`|`datetime2`Veri türü, `date` ve veri türlerinin aralığını ve duyarlığını `time` tek bir veri türünde birleştirir.<br /><br /> Varsayılan değerler ve dize değişmez biçimleri, `date` ve veri türlerinde tanımlananlarla aynıdır `time` .|  
|`datetimeoffset`|`datetimeoffset`Veri türünün tüm özellikleri `datetime2` ek saat dilimi farkına sahiptir. Saat dilimi boşluğu [+&#124;-] HH: MM olarak gösterilir. SS, saat dilimi kaydırmasında saat sayısını temsil eden 00 ile 14 arasında 2 basamaklı bir sayıdır. Aa, saat dilimi kaydırmasında ek dakika sayısını temsil eden 00 ila 59 arasında 2 basamaklı bir sayıdır. Zaman biçimleri 100 nanosaniye için desteklenir. Zorunlu + veya-imzala, saat dilimi kaydırın UTC (evrensel saat koordinatı veya Greenwich saati) ile yerel saati elde edilip edilmeyeceğini belirtir.|  
  
> [!NOTE]
> Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `Type System Version` bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> ..  
  
## <a name="date-format-and-date-order"></a>Tarih biçimi ve tarih sırası  
 SQL Server Tarih ve saat değerlerini nasıl ayrıştırdığı, yalnızca sistem sürümüne ve sunucu sürümüne değil, ayrıca sunucunun varsayılan diline ve biçim ayarlarına bağlıdır. Sorgu farklı bir dil ve tarih biçimi ayarı kullanan bir bağlantı tarafından yürütülürse, bir dilin tarih biçimleri için çalıştırılan bir tarih dizesi tanınmıyor olabilir.  
  
 Transact-SQL SET LANGUAGE deyimleri, tarih bölümlerinin sırasını belirleyen DATEFORMAT öğesini örtülü olarak ayarlar. Tarih değerlerini MDY, DMY, YıMD, YıDM, MYD veya DYM Order içindeki Tarih kısımlarını sıralamaya göre ayırt etmek için bir bağlantıda DATEFORMAT Transact-SQL ifadesini ayarla ' yı kullanabilirsiniz.  
  
 Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantıyla ilişkili varsayılan dili kullanır. Örneğin, bir tarih dizesi ' 01/02/03 ', dil Birleşik Devletler ayarı olan bir sunucu üzerinde MDY (2 Ocak 2003) ve Ingiliz Ingilizcesi dil ayarı olan bir sunucuda DMY (1 Şubat 2003) olarak yorumlanır. Yıl, yüzyıl değerini atamak için kesme tarihini tanımlayan SQL Server kesme yılı kuralı kullanılarak belirlenir. Daha fazla bilgi için bkz. [iki basamaklı yıl kesme seçeneği](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Bir dize biçiminden,, veya olarak dönüştürülürken, yıdm tarih biçimi desteklenmez `date` `time` `datetime2` `datetimeoffset` .  
  
 SQL Server Tarih ve saat verilerini yorumlama hakkında daha fazla bilgi için bkz. [Tarih ve saat verilerini kullanma](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Tarih/saat veri türleri ve parametreleri  
 <xref:System.Data.SqlDbType>Yeni tarih ve saat veri türlerini desteklemek için aşağıdaki numaralandırmalar eklenmiştir.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Bir öğesinin veri türünü, <xref:System.Data.SqlClient.SqlParameter> önceki Numaralandırmalardan birini kullanarak belirtebilirsiniz <xref:System.Data.SqlDbType> .

> [!NOTE]
> `DbType`Öğesinin özelliğini `SqlParameter` olarak ayarlayamazsınız `SqlDbType.Date` .

 Bir <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> `SqlParameter` nesnenin özelliğini belirli bir numaralandırma değerine ayarlayarak, bir genel olarak türünü de belirtebilirsiniz <xref:System.Data.DbType> . <xref:System.Data.DbType> `datetime2` Ve veri türlerini desteklemek için aşağıdaki numaralandırma değerleri eklenmiştir `datetimeoffset` :  
  
- DbType. DateTime2  
  
- DbType. DateTimeOffset  
  
 Bu yeni numaralandırmalar `Date` , `Time` `DateTime` .NET Framework önceki sürümlerinde mevcut olan, ve Numaralandırmalar için ek niteliğindedir.  
  
 Parametre nesnesinin .NET Framework veri sağlayıcısı türü, parametre nesnesinin değerinin .NET Framework türünden veya parametre nesnesinin öğesinden çıkarsanamıyor `DbType` . <xref:System.Data.SqlTypes>Yeni tarih ve saat veri türlerini desteklemek için yeni veri türleri tanıtılmadı. Aşağıdaki tabloda SQL Server 2008 tarih ve saat veri türleri ile CLR veri türleri arasındaki eşlemeler açıklanmaktadır.  
  
|SQL Server veri türü|.NET Framework türü|System. Data. SqlDbType|System. Data. DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|tarih|System. DateTime|Tarih|Tarih|  
|time|System. TimeSpan|Süre|Süre|  
|datetime2|System. DateTime|DateTime2|DateTime2|  
|türünde|System. DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System. DateTime|DateTime|DateTime|  
|girişin|System. DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>SqlParameter özellikleri  
 Aşağıdaki tabloda `SqlParameter` Tarih ve saat veri türleriyle ilgili özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Değerin null yapılabilir olup olmayacağını alır veya ayarlar. Sunucuya null bir parametre değeri gönderdiğinizde, <xref:System.DBNull> `null` (Visual Basic) yerine belirtmeniz gerekir `Nothing` . Veritabanı boş değerleri hakkında daha fazla bilgi için bkz. [null değerlerini işleme](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Değeri temsil etmek için kullanılan en fazla basamak sayısını alır veya ayarlar. Tarih ve saat veri türleri için bu ayar yok sayılır.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|, Ve için değerin saat kısmının çözümlendiği ondalık basamakların sayısını alır veya ayarlar `Time` `DateTime2` `DateTimeOffset` . Varsayılan değer 0 ' dır. Bu, gerçek ölçeğin değerden çıkarılan ve sunucuya gönderildiği anlamına gelir.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Tarih ve saat veri türleri için yoksayıldı.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Parametre değerini alır veya ayarlar.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Parametre değerini alır veya ayarlar.|  
  
> [!NOTE]
> Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir oluşturacak <xref:System.ArgumentException> .  
  
### <a name="creating-parameters"></a>Parametreleri oluşturma  
 <xref:System.Data.SqlClient.SqlParameter>Yapıcısını kullanarak veya metodunu çağırarak bir koleksiyona ekleyerek bir nesne oluşturabilirsiniz <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> `Add` <xref:System.Data.SqlClient.SqlParameterCollection> . `Add`Yöntemi, Oluşturucu bağımsız değişkenleri ya da varolan bir parametre nesnesi olarak alınır.  
  
 Bu konunun sonraki bölümlerinde tarih ve saat parametrelerinin nasıl belirtilme örnekleri verilmiştir. Parametrelerle çalışma hakkında daha fazla örnek için bkz. [parametreleri ve parametre veri türlerini](../configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametrelerini](../dataadapter-parameters.md)yapılandırma.  
  
### <a name="date-example"></a>Tarih örneği  
 Aşağıdaki kod parçası, bir parametrenin nasıl belirtileceğini göstermektedir `date` .  
  
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
 Aşağıdaki kod parçası, bir parametrenin nasıl belirtileceğini göstermektedir `time` .  
  
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
 Aşağıdaki kod parçası, `datetime2` hem tarih hem de saat parçalarıyla bir parametrenin nasıl belirtileceğini göstermektedir.  
  
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
 Ayrıca `AddWithValue` <xref:System.Data.SqlClient.SqlCommand> , aşağıdaki kod parçasında gösterildiği gibi, bir öğesinin yöntemini kullanarak parametreler sağlayabilirsiniz. Ancak, `AddWithValue` yöntemi <xref:System.Data.SqlClient.SqlParameter.DbType%2A> parametresi için veya belirtmenize izin vermez <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> .  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date`Parametresi `date` , sunucusundaki bir, `datetime` veya `datetime2` veri türüyle eşleşgelebilir. Yeni `datetime` veri türleriyle çalışırken, parametrenin özelliğini, örneğin veri türüne açık olarak ayarlamanız gerekir <xref:System.Data.SqlDbType> . <xref:System.Data.SqlDbType.Variant>Parametre değerlerini kullanmak veya örtük olarak sağlamak, `datetime` ve veri türleriyle geriye dönük uyumlulukla ilgili sorunlara neden olabilir `smalldatetime` .  
  
 Aşağıdaki tabloda, hangi `SqlDbTypes` CLR türlerinden çıkarılan gösterilmektedir:  
  
|CLR türü|Çıkarılan SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType. DateTime|  
|TimeSpan|SqlDbType. Time|  
|DateTimeOffset|SqlDbType. DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Tarih ve saat verilerini alma  
 Aşağıdaki tabloda SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanmaktadır.  
  
|SqlClient yöntemi|Description|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Belirtilen sütun değerini bir yapı olarak alır <xref:System.DateTime> .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Belirtilen sütun değerini bir yapı olarak alır <xref:System.DateTimeOffset> .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Alan için sağlayıcıya özgü temel tür olan türü döndürür. `GetFieldType`Yeni tarih ve saat türleri için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Belirtilen sütunun değerini alır. `GetValue`Yeni tarih ve saat türleri için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Sütun değerini bir olarak alır <xref:System.Data.SqlTypes.SqlString> . <xref:System.InvalidCastException>Veriler bir olarak ifade edilenemediğinde oluşur `SqlString` .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Sütun verilerini varsayılan olarak alır `SqlDbType` . `GetValue`Yeni tarih ve saat türleri için aynı türleri döndürür.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Belirtilen dizideki değerleri alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Tür sistemi sürümü SQL Server 2005 olarak ayarlandıysa, sütun değerini bir dize olarak alır. <xref:System.InvalidCastException>Veriler bir dize olarak ifade edilenemediğinde oluşur.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Belirtilen sütun değerini bir yapı olarak alır <xref:System.TimeSpan> .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Belirtilen sütun değerini temel alınan CLR türü olarak alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Bir dizideki sütun değerlerini alır.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<xref:System.Data.DataTable>Sonuç kümesinin meta verilerini açıklayan bir döndürür.|  
  
> [!NOTE]
> Yeni tarih ve saat, `SqlDbTypes` SQL Server içinde işlem sırasında yürütülen kod için desteklenmez. Bu türlerden biri sunucuya geçirilirse bir özel durum oluşur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Tarih ve saat değerlerini değişmez değer olarak belirtme  
 Tarih ve saat veri türlerini SQL Server, daha sonra çalışma zamanında değerlendiren ve bunları iç tarih/saat yapılarına dönüştüren çeşitli farklı değişmez dize biçimlerini kullanarak belirtebilirsiniz. SQL Server, tek tırnak işareti (') içine alınmış tarih ve saat verilerini tanır. Aşağıdaki örneklerde bazı biçimler gösterilmektedir:  
  
- Alfabetik tarih biçimleri, örneğin `'October 15, 2006'` .  
  
- Gibi sayısal Tarih biçimleri `'10/15/2006'` .  
  
- `'20061015'`ISO standart tarih biçimini kullanıyorsanız, örneğin, 15 ekim 2006 olarak yorumlanabilecek, gibi ayrılmamış dize biçimleri.  
  
> [!NOTE]
> Tüm sabit dize biçimlerinin ve SQL Server Books Online 'daki tarih ve saat veri türlerinin diğer özelliklerine ilişkin tüm belgeleri bulabilirsiniz.  
  
 Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir oluşturacak <xref:System.ArgumentException> .  
  
## <a name="resources-in-sql-server-books-online"></a>SQL Server Books Online 'daki kaynaklar  
 SQL Server Tarih ve saat değerleriyle çalışma hakkında daha fazla bilgi için SQL Server Books Online 'da aşağıdaki kaynaklara bakın.  
  
|Konu|Description|  
|-----------|-----------------|  
|[Tarih ve saat veri türleri ve Işlevleri (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Tüm Transact-SQL tarih ve saat veri türleri ve işlevlerine genel bir bakış sağlar.|  
|[Tarih ve saat verilerini kullanma](/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Tarih ve saat veri türleri ve işlevleri hakkında bilgi ve bunları kullanma örnekleri sağlar.|  
|[Veri türleri (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|SQL Server içindeki sistem veri türlerini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
